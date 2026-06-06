---


---

<h1 id="grafana-server-setup">Grafana Server Setup</h1>
<h2 id="overview">Overview</h2>
<p>Grafana is an open-source analytics and monitoring platform that allows you to visualize metrics collected from various data sources such as Prometheus, InfluxDB, MySQL, PostgreSQL, Elasticsearch, and more.</p>
<p>In this project, Grafana is used to create dashboards for monitoring server health, system performance, and infrastructure metrics.</p>
<hr>
<h2 id="prerequisites">Prerequisites</h2>
<ul>
<li>Rocky Linux 9 / RHEL 9</li>
<li>Root or sudo privileges</li>
<li>Internet connectivity</li>
<li>Prometheus installed and running</li>
</ul>
<hr>
<h2 id="step-1-update-system-packages">Step 1: Update System Packages</h2>
<pre><code>sudo dnf update -y
</code></pre>
<hr>
<h2 id="step-2-install-grafana-repository">Step 2: Install Grafana Repository</h2>
<p>Create the Grafana repository file:</p>
<pre><code>sudo tee /etc/yum.repos.d/grafana.repo &gt; /dev/null &lt;&lt;EOF
[grafana]
name=Grafana OSS
baseurl=https://rpm.grafana.com
repo_gpgcheck=1
enabled=1
gpgcheck=1
gpgkey=https://rpm.grafana.com/gpg.key
sslverify=1
sslcacert=/etc/pki/tls/certs/ca-bundle.crt
EOF
</code></pre>
<hr>
<h2 id="step-3-install-grafana">Step 3: Install Grafana</h2>
<pre><code>sudo dnf install grafana -y
</code></pre>
<p>Verify installation:</p>
<pre><code>grafana-server -v
</code></pre>
<hr>
<h2 id="step-4-enable-and-start-grafana-service">Step 4: Enable and Start Grafana Service</h2>
<p>Enable Grafana to start automatically on boot:</p>
<pre><code>sudo systemctl enable grafana-server
</code></pre>
<p>Start Grafana:</p>
<pre><code>sudo systemctl start grafana-server
</code></pre>
<p>Check service status:</p>
<pre><code>sudo systemctl status grafana-server
</code></pre>
<hr>
<h2 id="step-5-configure-firewall">Step 5: Configure Firewall</h2>
<p>Allow Grafana default port (3000):</p>
<pre><code>sudo firewall-cmd --permanent --add-port=3000/tcp
sudo firewall-cmd --reload
</code></pre>
<p>Verify:</p>
<pre><code>sudo firewall-cmd --list-ports
</code></pre>
<hr>
<h2 id="step-6-access-grafana-web-ui">Step 6: Access Grafana Web UI</h2>
<p>Open your browser:</p>
<pre><code>http://&lt;SERVER-IP&gt;:3000
</code></pre>
<p>Example:</p>
<pre><code>http://192.168.1.100:3000
</code></pre>
<p>Default Credentials:</p>
<pre><code>Username: admin
Password: admin
</code></pre>
<p>You will be prompted to change the password after first login.</p>
<hr>
<h2 id="step-7-configure-prometheus-data-source">Step 7: Configure Prometheus Data Source</h2>
<ol>
<li>
<p>Login to Grafana.</p>
</li>
<li>
<p>Navigate to:</p>
<pre><code>Connections → Data Sources
</code></pre>
</li>
<li>
<p>Click:</p>
<pre><code>Add Data Source
</code></pre>
</li>
<li>
<p>Select:</p>
<pre><code>Prometheus
</code></pre>
</li>
<li>
<p>Enter Prometheus URL:</p>
<pre><code>http://localhost:9090
</code></pre>
</li>
<li>
<p>Click:</p>
<pre><code>Save &amp; Test
</code></pre>
</li>
</ol>
<p>Expected Result:</p>
<pre><code>Data source is working
</code></pre>
<hr>
<h2 id="step-8-import-monitoring-dashboard">Step 8: Import Monitoring Dashboard</h2>
<ol>
<li>
<p>Click:</p>
<pre><code>Dashboards → Import
</code></pre>
</li>
<li>
<p>Enter Dashboard ID.</p>
</li>
</ol>
<p>Common Dashboard IDs:</p>
<p>Dashboard</p>
<p>ID</p>
<p>Node Exporter Full</p>
<p>1860</p>
<p>Linux Server Monitoring</p>
<p>11074</p>
<p>Prometheus Statistics</p>
<p>3662</p>
<ol start="3">
<li>Select Prometheus Data Source.</li>
<li>Click Import.</li>
</ol>

