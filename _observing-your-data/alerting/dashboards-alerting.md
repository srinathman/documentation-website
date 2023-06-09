---
layout: default
title: Integrating alerts with Dashboard 
parent: Alerting
nav_order: 50
---

# Integrating alerts with Dashboard
Introduced 2.8
{: .label .label-purple }

Create, manage, and take action on your alerts in a single, consolidated view and identify and resolve issues quickly. Use the **Dashboard** app to:

- Set up, add, and adjust rules and conditions that trigger alerts and notifications.
- Create graphs that show trends and patterns and build intuitive dashboards to stay on top of important metrics and data points in real time.
- Monitor your alerts in one place with at-a-glance views.

<img src="{{site.url}}{{site.baseurl}}/images/dashboards/alerting-viz.png" alt="Example alerting visualization" width="800" height="800">

## Getting started 

Before getting started, you must have:

- Installed OpenSearch and OpenSearch Dashboards version 2.8 or later. See [Installing OpenSearch]({{site.url}}{{site.baseurl}}/install-and-configure/install-opensearch/index/).
- Installed Alerting and Notifications Dashboards plugins. See [Managing OpenSearch Dashboards plugins]({{site.url}}{{site.baseurl}}/install-and-configure/install-dashboards/plugins/) to get started.

## Configuring admin settings

You can only access, create, or manage alerts for resources for which you have permissions. Access to alerting dashboards and visualizations is controlled by OpenSearch and OpenSearch Dashboards privileges, and you can manage the settings in **Stack Management**. Access is enabled by default and appears as a feature in the **Stack Management** > **Advanced Settings** > **Visualizations** window. If the setting is disabled, it does not appear in this window. The setting can be disabled at the cluster level through the `opensearch-dashboards.yml` file.

## General requirements for alerting visualizations

Alerting visualizations are displayed as time-series charts that give you a snapshot of the alert, alert status, last updated time, and reason for the alert. You can show up to 10 metrics on your chart, and each series can be shown as a line in the chart.

Keep in mind the following requirements when setting up or creating alerting visualizations:

- Must be a [Vizlib line chart](https://community.vizlib.com/support/solutions/articles/35000107262-vizlib-line-chart-introduction)
- Must contain one Y-axis metric aggregation
- Must not have non-Y-axis metric aggregation types
- Must use date histogram aggregation type for the X-axis bucket
- Must have X-axis on the bottom
- Must define one X-axis aggregation bucket
- Must have a valid time-based X-axis

## Creating alerting monitors with Dashboard

By default, when you begin to create the alert monitor workflow using the Dashboard app, you are presented with a menu-driven interface. This interface provides a range of options, displayed in full screen, pop-up, pull-down, or dropdown, to define the metrics to monitor, set thresholds, customize triggers that automate workflows, and generate actions when conditions are met. Currently, you can create [per query monitors]({{site.url}}{{site.baseurl}}/observing-your-data/alerting/monitors/#monitor-types) only.

#### To create an alerting monitor 

1. Choose **Dashboard** from the OpenSearch Dashboards main menu.
2. From the **Dashboards** window, select **Create** and then choose **Dashboard**.
3. Select **Add an existing**, then select the appropriate alerting visualization from the **Add panels** list. The visualization is added to the dashboard.
4. From the visualization panel, choose the ellipsis icon ({::nomarkdown}<img src="{{site.url}}{{site.baseurl}}/images/ellipsis-icon.png" class="inline-icon" alt="ellipsis icon"/>{:/}). 
5. From the **Options** menu, select **Add alerting monitor**.
6. Input information for **Monitor details** and **Triggers**  
7. Choose **Create monitor**. The monitor is added to the visualization.  

An example of the create monitor steps is shown in the following screenshot.

<img src="{{site.url}}{{site.baseurl}}/images/dashboards/create-monitor-menu.png" alt="Create monitor interface" width="400" height="400">

## Associating monitors

You can associate certain monitors (existing and with a with a visualization using the Dashboard app instead of the plugin page, giving you a single interface to add, view, and edit monitor data. 

#### To associate a monitor

Continuing with the alerting visualization and dashboard created in the preceding tutorial, associate an existing monitor with a visualization by following these steps. 

1. From the visualization panel, choose the ellipsis icon ({::nomarkdown}<img src="{{site.url}}{{site.baseurl}}/images/ellipsis-icon.png" class="inline-icon" alt="ellipsis icon"/>{:/}).
2. Select **Associated monitors**.
3. From the **Select monitor to associate** dropdown menu, select the monitor. Only eligible monitors are listed in the dropdown menu. 
4. View the monitor's basic information. To view comprehensive details, select **View monitor page** to open the Alerting plugin page.
5. Select **Associate monitor**. An existing monitor is associated to the visualization.

## Exploring alerting monitor details

Once you've created or associated alerting monitors, verify the monitor is generating the alerts and explore alert details by following these steps:

1. Open the alerting dashboard. Alerts are indicated on the visualization with a triangle icon ({::nomarkdown}<img src="{{site.url}}{{site.baseurl}}/images/dashboards/triangle-icon.png" class="inline-icon" alt="triangle icon"/>{:/}). 
2. Hover over a triangle to view high-level data, such as number of alerts. To investigate alert details, select the triangle icon ({::nomarkdown}<img src="{{site.url}}{{site.baseurl}}/images/dashboards/triangle-icon.png" class="inline-icon" alt="triangle icon"/>{:/}) to open a flyout with more detailed monitor information. Alternatively, select the ellipsis icon ({::nomarkdown}<img src="{{site.url}}{{site.baseurl}}/images/ellipsis-icon.png" class="inline-icon" alt="ellipsis icon"/>{:/}) in the visualization panel and choose **View events**.
3. Select the ellipsis icon ({::nomarkdown}<img src="{{site.url}}{{site.baseurl}}/images/ellipsis-icon.png" class="inline-icon" alt="ellipsis icon"/>{:/}), then **Alerting** > **Associated monitors**.
4. Choose an alerting monitor from the list. Information such as history, alerts, and associated visualizations are shown within the visualization panel.
5. Explore unlinking or editing a monitor. 
   1. Unlink a monitor from the visualization by selecting the link icon ({::nomarkdown}<img src="{{site.url}}{{site.baseurl}}/images/dashboards/link-icon.png" class="inline-icon" alt="link icon"/>{:/}) under **Actions**. This unlinks the monitor from the visualization only; it does not delete the monitor.
   2. Edit the monitor's metrics by selecting the edit icon ({::nomarkdown}<img src="{{site.url}}{{site.baseurl}}/images/dashboards/edit-icon.png" class="inline-icon" alt="edit icon"/>{:/}).

## Next steps

- [Learn more about Dashboard](https://opensearch.org/docs/latest/dashboards/dashboard/index/)
- [Learn more about alerting](https://opensearch.org/docs/latest/observing-your-data/alerting/index/)