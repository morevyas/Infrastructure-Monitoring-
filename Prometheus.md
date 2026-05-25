---


---

<h1 id="prometheus">Prometheus</h1>
<p>Prometheus is an open-source toolkit designed for <strong>system monitoring and alerting</strong>.<br>
It was originally developed at SoundCloud in 2012 and has since become widely adopted by companies and organizations around the world. Thanks to its active developer and user community, Prometheus has grown into an independent open-source project. In 2016, it joined the Cloud Native Computing Foundation (CNCF) as its second hosted project after Kubernetes, highlighting its strong governance and community-driven development.</p>
<p>At its core, Prometheus collects and stores metrics as time-series data. This means each piece of metric information is recorded along with a timestamp and can also include additional details in the form of key-value pairs called labels. These labels make it easier to organize, filter, and analyze monitoring data.</p>
<p>Today, Prometheus is considered one of the most popular tools for monitoring cloud-native applications and infrastructure.</p>
<p>Ex :-</p>
<ul>
<li>CPU usage</li>
<li>Memory usage</li>
<li>Disk space</li>
<li>HTTP requests</li>
<li>Application response time</li>
<li>Number of active users</li>
</ul>
<h3 id="features--">Features :-</h3>
<p>Prometheus offers several powerful features that make it a popular choice for monitoring modern systems and cloud-native applications.</p>
<p>One of its key strengths is its multi-dimensional data model, where metrics are stored as time-series data and identified not only by a metric name but also by key-value pairs known as labels. This structure allows users to organize and filter metrics efficiently.</p>
<p>Prometheus also includes PromQL, a flexible and powerful query language that enables users to analyze and work with collected metrics in meaningful ways.</p>
<p>Another important feature is that Prometheus does not depend on distributed storage. Each Prometheus server operates independently, which simplifies deployment and improves reliability.</p>
<p>Metrics collection is mainly based on a pull model over HTTP, where Prometheus periodically retrieves metrics from configured targets. However, it also supports pushing metrics through an intermediary component called the Pushgateway, which is useful for short-lived jobs.</p>
<p>Prometheus can automatically discover monitoring targets using service discovery mechanisms or through static configurations, making it adaptable to dynamic environments such as Kubernetes.</p>
<p>In addition, Prometheus supports multiple graphing and dashboarding options, allowing users to visualize metrics and build monitoring dashboards effectively.</p>
<h4 id="what-are-metrics--">What are metrics :-</h4>
<p>Metrics are numerical values used to measure the performance and behavior of a system or application. In simple terms, they help track what is happening within a system over time. When these measurements are recorded continuously with timestamps, they form what is known as time-series data.</p>
<p>Different applications use different types of metrics depending on what needs to be monitored. For example:</p>
<ul>
<li>
<p>A web server may track request response times or the number of incoming requests.</p>
</li>
<li>
<p>A database may monitor active connections, query execution times, or the number of running queries.</p>
</li>
<li>
<p>A system server may measure CPU usage, memory consumption, or disk activity.</p>
</li>
</ul>
<p>Metrics are extremely important because they help explain why an application behaves in a certain way. For instance, if a web application becomes slow, metrics can help identify the root cause. A sudden increase in request count might indicate that the server is overloaded. By analyzing this metric, administrators can decide to scale the application by adding more servers or resources.</p>
<p>In short, metrics provide visibility into system performance and help teams monitor, troubleshoot, and improve applications effectively.</p>
<h4 id="component--">Component :-</h4>
<p>The Prometheus ecosystem is made up of several components that work together to provide monitoring and alerting capabilities. Some of these components are essential, while others are optional depending on the monitoring requirements.</p>
<p>The core component is the <strong>Prometheus server</strong>, which collects metrics from target systems, stores them as time-series data, and allows users to query the data.</p>
<p>To enable applications to expose metrics, Prometheus provides <strong>client libraries</strong> for different programming languages. These libraries help developers instrument their application code and generate metrics.</p>
<p>For short-lived or batch jobs that cannot be scraped directly, Prometheus includes a <strong>Pushgateway</strong>. This component allows temporary jobs to push their metrics to Prometheus indirectly.</p>
<p>Prometheus also supports many <strong>exporters</strong>, which are special-purpose tools that collect metrics from third-party systems and services such as HAProxy, StatsD, Graphite, databases, operating systems, and more. Exporters convert existing metrics into a format that Prometheus can understand.</p>
<p>Another important component is the <strong>Alertmanager</strong>, which manages alerts generated by Prometheus. It handles alert grouping, deduplication, silencing, and routing notifications to channels such as email, Slack, or PagerDuty.</p>
<p>In addition, the ecosystem includes various <strong>support and visualization tools</strong> that help users analyze and display monitoring data.</p>
<p>Most Prometheus components are written in <strong>Go</strong>, which makes them lightweight, portable, and easy to deploy as standalone static binaries.</p>
<h3 id="architecture">Architecture</h3>
<p><img src="https://prometheus.io/assets/docs/architecture.svg" alt="Prometheus architecture"></p>
<h3 id="how-to-work--">How to work :-</h3>

