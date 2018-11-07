# Elastic references
Here you will find Elastic references to documentation, examples, and other good resources.

## To start with
You can always access our _**public demo environment**_ [accessible online](https://demo.elastic.co/app/kibana#/dashboard/welcome_dashboard), check our [website](https://www.elastic.co) for fresh blog posts and videos or subscribe on our Youtube channel.

You can also learn a lot from Elastic, through our _**trainings**_ [listed online](https://training.elastic.co/). You can now get [certified](https://training.elastic.co/exam/elastic-certified-engineer) as _**Elastic Engineer**_!

## New content
You are using _**Docker or Kubernetes**_ ? Read [this](https://www.elastic.co/blog/docker-and-kubernetes-hints-based-autodiscover-with-beats) and [that](https://www.elastic.co/blog/monitoring-an-application-running-in-docker-containers-and-kubernetes-with-the-elastic-stack), watch the [French webinar](https://www.elastic.co/fr/webinars/elasticsearch-log-collection-with-kubernetes-docker-and-containers) and try it by yourself in 10mn on [Katacoda](https://www.katacoda.com/dan_roscigno/scenarios/logs-and-metrics-elasticsearch-kibana)!

Is _**GDPR**_ a concern for you? Watch our [French webinar](https://www.elastic.co/fr/webinars/fr-gdpr-compliance-and-elasticsearch), read the related [whitepaper](https://www.elastic.co/fr/gdpr) and play with our [GDPR scanner](https://github.com/blookot/elastic-gdpr-scanner) to inventory your Elasticsearch instances and check for compliance.

## Coming events
We run a serie of 3 French webinars dedicated to _**Security Analytics**_. [Subscribe here](https://events.elastic.co/french-security-webinar-series) and watch replays of [episode 1](https://www.elastic.co/fr/webinars/security-analytics-webinar-french-episode-1) and [episode 2](https://www.elastic.co/fr/webinars/security-analytics-webinar-french-episode-2).

We often organize daily _**hands-on workshops**_ on Operational Analytics, Security Analytics or Search typically. Contact us if you wish to participate.

We often organize _**meetups**_ in France. You can [subscribe](https://www.meetup.com/fr-FR/ElasticFR) for coming ones or watch the [recordings](https://www.youtube.com/playlist?list=PLhLSfisesZIuhYrMtNXL7RUh-b3hwNokk) of previous meetups.

## Content related to Security Analytics
### Readings and watchings
Using the Elastic stack for Security Analytics
- To start with, of course, the [website page](https://www.elastic.co/solutions/security-analytics), [videos & webinars](https://www.elastic.co/search?q=security+analytics&section=Learn%2FVideos) and [blog posts](https://www.elastic.co/search?q=security+analytics&section=Learn%2FBlog)
- watch our serie of 3 French webinars: [episode 1](https://www.elastic.co/fr/webinars/security-analytics-webinar-french-episode-1) and [episode 2](https://www.elastic.co/fr/webinars/security-analytics-webinar-french-episode-2) and episode 3 (coming soon)
- and [another webinar](https://www.elastic.co/webinars/using-elasticsearch-and-the-elastic-stack-for-advanced-threat-hunting) dedicated to threat hunting!
- Great [blog post](https://www.elastic.co/blog/using-the-elastic-stack-as-a-saas-based-security-operations-swiss-army-knife) showing the use of beats and watches to build a SOC
- and our great [Security Analytics training course](https://training.elastic.co/static/pdf/Elastic.Security.Analytics.pdf)

### Ingesting data...
Ingestion is all about capture as widely as possible, and enriching to bring value to the raw data:
- Using beats to _**capture**_ processes, OS events, file integrity changes, etc. Check the [osquery module](https://www.elastic.co/blog/brewing-in-beats-osquery-module-in-filebeat) and the [IDS coupling](https://www.elastic.co/fr/blog/improve-security-analytics-with-the-elastic-stack-wazuh-and-ids) as well as many distros combining the Elastic stack with IDS/IPS like Security Onion, RockNSM, SOF-ELK, HELK, CAPESstack, SELKS...
- Enrich data with threat intelligence feeds like [Blueliv](https://www.elastic.co/blog/how-blueliv-uses-the-elastic-stack-to-combat-cyber-threats), [AlienVault OTX](https://otx.alienvault.com/api) (direct link to the [IP reputation list](https://reputation.alienvault.com/reputation.generic) and a [quick script](https://www.syspanda.com/index.php/2017/08/26/detecting-outbound-connections-pt-2-logstash-threat-intelligence/) to fetch it), [URL blacklist](https://urlhaus.abuse.ch/browse/), Alexa's [URL whitelist](https://support.alexa.com/hc/en-us/articles/200449834-Does-Alexa-have-a-list-of-its-top-ranked-websites-) or the similar one from [Majestic](https://majestic.com/reports/majestic-million) (direct link to the [million URL](http://downloads.majestic.com/majestic_million.csv)), and finally a [combine script](https://github.com/mlsecproject/combine) to fetch these feeds into Logstash.

How do you _**enrich**_? mostly using Logstash, see below:
- a first [Logstash enrichment webinar](https://www.elastic.co/webinars/logstash-event-enrichment), as well as the [Logstash enrichment page](https://www.elastic.co/guide/en/logstash/current/lookup-enrichment.html) that includes [GeoIP](https://www.elastic.co/guide/en/logstash/current/plugins-filters-geoip.html), [DNS](https://www.elastic.co/guide/en/logstash/current/plugins-filters-dns.html), [CIDR](https://www.elastic.co/guide/en/logstash/current/plugins-filters-cidr.html), [User agent](https://www.elastic.co/guide/en/logstash/current/plugins-filters-useragent.html) and other filters
- examples of applying Logstash enrichment in this Security Analytics use case in a [blog post](https://www.elastic.co/blog/elasticsearch-data-enrichment-with-logstash-a-few-security-examples)

_**Pseudonizing data**_ at ingestion is key, considering the GDPR regulation (see our related [blog post](https://www.elastic.co/blog/gdpr-personal-data-pseudonymization-part-1)).

_Tip_: use the newly defined [Elastic Common Schema](https://github.com/elastic/ecs) to normalize your data and ease correlation, filtering and eventually sharing of dashboards, ML jobs, etc.

### ... to running advanced analytics using Elastic Machine Learning and Graph
Once data are in, you can leverage the awesomeness of Elastic ML and Graph:
TBC...

### Correlating and alerting
Elastic Watcher is used to correlate events (static or dynamically identified by ML) and alert via email, Slack, Jira, PagerDuty or any other system (see [documentation](https://www.elastic.co/guide/en/elastic-stack-overview/6.3/actions.html)). A few additional resources: 
- first learn about Watcher on our [website](https://www.elastic.co/products/stack/alerting)
- a few [examples of watches](https://github.com/elastic/examples/tree/master/Alerting/Sample%20Watches)
- the [Sigma rules](https://github.com/Neo23x0/sigma) translated for Watcher on [Uncoder](https://uncoder.io/) (Select a sigma rule on the left, then Watcher on the droplist on the right and click Translate!)
- integration with external SOAR (Security Orchestration and Automated Response) like [CyberSponse](https://cybersponse.com/resources/CyberSponse-Elastic-SolutionBrief.pdf)

## Content related to Machine Learning
Here is a list of content refs to help start and understand Elastic ML:
- beyond our [website intro](https://www.elastic.co/products/stack/machine-learning) and public demo listed up here, a lot of good stuff can be found in [blog posts](https://www.elastic.co/search?q=machine+learning&section=Learn%2FBlog), including  [intro](https://www.elastic.co/blog/introducing-machine-learning-for-the-elastic-stack), [how it works](https://www.elastic.co/blog/machine-learning-anomaly-scoring-elasticsearch-how-it-works), [advanced aggregations with derivative](https://www.elastic.co/blog/custom-elasticsearch-aggregations-for-machine-learning-jobs), [forecasting](https://www.elastic.co/blog/elasticsearch-machine-learning-on-demand-forecasting) 
- ML recipes [here](https://www.elastic.co/products/stack/machine-learning/recipes)
- examples of ML jobs on [github](https://github.com/blookot/ml-examples)
- how to display the model in multi-metric jobs on [discuss](https://discuss.elastic.co/t/model-bounds-are-not-available/132529)
- there are many other tips & tricks, so come and ping us to learn some more!

## Helpful sets of examples
Beyond our awesome online documentation, you might be interested in further resources:
- the Elastic stack comes with more and more datasets: 
- examples of ML jobs, watches, etc on [Elastic github](https://github.com/elastic/examples)
- examples of canvas on [github](https://github.com/alexfrancoeur/kibana_canvas_examples)
- examples of ML jobs focused on Security Analytics on [github](https://github.com/blookot/ml-examples)
