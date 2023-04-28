---
layout: default
title: Creating correlation rules
parent: Setting up Security Analytics
nav_order: 16
---

# Creating correlation rules

The correlation engine is an experimental feature released in OpenSearch 2.7. Therefore, we do not recommend using the feature in a production environment at this time. For updates on the progress of correlation engine, see [Security Analytics Correlation Engine](https://github.com/opensearch-project/security-analytics/issues/369) at GitHub. To share ideas and provide feedback, join the [Security Analytics forum](https://forum.opensearch.org/c/plugins/security-analytics/73).
{: .warning }

Correlation rules allow you to define threat scenarios involving multiple systems in an infrastructure by matching the signatures of threat events occuring in different log types. Once a rule contains at least two different log sources and the preferred fields and field values that define an intended threat secenario, the correlation engine can query the indexes specified in the correlation rule and draw any correlations found between the findings.


## Configuring rules

Having at least two data sources in the rule configuration is the basis for making connections between different systems in an infrastructure and identifying correlations. Therefore, a minimum of two queries is required for each correlation rule. However, you can include more than two queries to better define a threat scenario and look for correlations between multiple systems. Follow the steps in this section to create a correlation rule.

1. Begin by selecting **Security Analytics** in the Dashboards home page menu. Then select **Correlation rules** from the Security Analytics menu on the left side of the screen. The **Correlation rules** page is displayed.
   
   <img src="{{site.url}}{{site.baseurl}}/images/Security/sec-analytics/create-corr-rule.png" alt="The correlation rules page" width="85%">

1. Select **Create correlation rule**. The **Create correlation rule** window opens.
1. In the **Correlation rule details** field, enter a name for the rule.
  
   <img src="{{site.url}}{{site.baseurl}}/images/Security/sec-analytics/corr-rule-config1.png" alt="The correlation rule name" width="50%">

1. The **Correlation queries** field contains two dropdown lists. In the **Select index** dropdown list, specify an index or index pattern for the data source. In the **Log type** dropdown list, specify the log type associated with the index.
  
   <img src="{{site.url}}{{site.baseurl}}/images/Security/sec-analytics/corr-rule-config2.png" alt="The data source and log type for the query" width="45%">
  
1. In the **Field** dropdown list, specify a log field. In the **Field value** text box, enter a value for the field.
  
   <img src="{{site.url}}{{site.baseurl}}/images/Security/sec-analytics/corr-rule-config3.png" alt="The field and field value for the query" width="45%">

1. To add more fields to the query, select **Add field**.    
1. After configuring the first query, repeat the previous step to configure a second query. You can select **Add query** at the bottom of the window to add more queries for the rule.
  
   <img src="{{site.url}}{{site.baseurl}}/images/Security/sec-analytics/corr-rule-config4.png" alt="A second query for the correlation rule" width="50%">

1. Once the rule is complete, select **Create correlation rule** in the lower-right corner of the window. OpenSearch creates a new rule, the screen returns to the **Correlation rules** window, and the new rule appears in the table of correlation rules.


## Setting a time window

The Cluster Settings API allows you to correlate findings within a set time window. For example, if your time window is three minutes, the system attempts to correlate findings defined in the threat scenario only when they occur within three minutes of one another. By default, the time window is five minutes. For more information about the Cluster Settings API, see [Cluster settings]({{site.url}}{{site.baseurl}}/api-reference/cluster-api/cluster-settings/).

### Example request

The following PUT call sets the time window to two minutes.

```json
PUT /_cluster/settings
{
  "transient": {
    "plugins.security_analytics.correlation_time_window": "2m"
  }
}
```
{% include copy-curl.html %}


## What's next

After creating detectors and correlation rules, you can use the correlation graph to observe the correlations between findings from different log sources. For information about working with the correlation graph, see [Working with the correlation graph]({{site.url}}{{site.baseurl}}/security-analytics/usage/correlation-graph/). 
