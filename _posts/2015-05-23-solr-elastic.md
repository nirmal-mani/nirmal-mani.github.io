---
layout: post
title: Solr vs Elastic Search
---

This page summarizes the thoughts on what is today on SolrCloud with NRT indexing/searching vs elastic search. Most of comparison is done at (http://solr-vs-elasticsearch.com/)

|   |  Solr Cloud |Elastic Search   |
|---|---|---|
|  License | Full Apache project with huge community  |  Apache license but Private with vibrant community |
|  Orientation | By far mostly on text searches(Information Retrieval)  | Moving towards analytics and exploratory analytics.(Information Intelligence) with investments around ELK stack  |
| Monitoring  |  JMX |  REST api. Also has some new relic plugins/others |
| Deployment | Self |		Self/Hosted on AWS/Mesos integration|
| *Feature sets* (Pros not available in other)|  - Pluggable search/updateworkflows - Better java client|- Per document Analyzer - Multiple schema/document types within collection - Percolation - Parent-child relationship in documents (Important for social?) - Advanced aggregations compared to slow facets in solr - Better REST Api|
|Distribution|Completely partition-tolerant: Depends on ZK for Sharding/cluster management	|No ZK but prone to split brains.|
|Replication|	Master serves requests. Slaves polls. More prone to corruption/intermittent downtimes.|	No ZK. Writes are configurable but defaults to persisting on quorum which may affect performance.|
|Clustering(Pros not available in other) |Shard splitting, Change # of shards, pluggable replica assignment|Automatic shard rebalancing|

Elastic search was envisioned when SolrCloud didn't come in place. In terms of feature set, these engines usually keep up with each other.

Key points:

* Is pluggablity of features critical for  indexing/query workflow?
* Parent-child relationships in ES seems to be promising . Percolation is nice to have, Solr is catching up with streaming subscribe.
