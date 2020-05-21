
# Create alerts to proactively monitor your data factory pipelines

Organizations can improve operational productivity by creating alerts on data integration events (success/failure) and proactively monitor with Azure Data Factory (ADF).

[This document from Microsoft](https://azure.microsoft.com/en-us/blog/create-alerts-to-proactively-monitor-your-data-factory-pipelines/) offers detailed instructions on how to enable monitoring within ADF.

But connecting ADF to Azure Monitor, you can:
* Archive logs to a storage account
* Stream to an event hub
* Send to Log Analytics

### Azure Monitor
ADF's monitoring solution is built on [Azure Monitor.](https://docs.microsoft.com/en-us/azure/azure-monitor/overview) Azure Monitor maximizes the availability and performance of your applications and services by delivering a comprehensive solution for collecting, analyzing, and acting on telemetry from your cloud and on-premises environments. 

It helps you understand how your applications are performing and proactively identifies issues affecting them and the resources they depend on.

### Configuring alerts

![image info](./img/1-criteria.png)

In ADF you can configure the alert logic. You can specify various filters such as activity name, pipeline name, activity type, and failure type for the raised alerts. You can also specify the alert logic conditions and the evaluation criteria.

![image info](./img/2-alert_logic.png)

### Notifications
Upon fulfillment of your parameters (Pass or Fail), an alert will be sent out. It takes ~2 minutes to reach my inbox. 

Different mechanisms such email, SMS, voice, and push notifications are supported.

![image info](./img/3-alert_email.png)

### Keeping Azure Data Factory data
Data Factory stores pipeline-run data for only 45 days. Use Monitor if you want to keep that data for a longer time. With Monitor, you can route diagnostic logs for analysis. You can also keep them in a storage account so that you have factory information for your chosen duration.

#### Diagnostic logs
* Save your diagnostic logs to a storage account for auditing or manual inspection. You can use the diagnostic settings to specify the retention time in days.
* Stream the logs to Azure Event Hubs. The logs become input to a partner service or to a custom analytics solution like Power BI.
* Analyze the logs with Log Analytics.

### Azure Monitor (cont'd)
The following diagram gives a high-level view of Azure Monitor. At the center of the diagram are the data stores for metrics and logs, which are the two fundamental types of data use by Azure Monitor. 

On the left are the sources of monitoring data that populate these data stores. 

On the right are the different functions that Azure Monitor performs with this collected data such as analysis, alerting, and streaming to external systems.
![image info](./img/4-az_monitor.png)

All data collected by Azure Monitor fits into one of two fundamental types, metrics and logs. Metrics are numerical values that describe some aspect of a system at a particular point in time. They are lightweight and capable of supporting near real-time scenarios.

 Logs contain different kinds of data organized into records with different sets of properties for each type. Telemetry such as events and traces are stored as logs in addition to performance data so that it can all be combined for analysis.

 #### Monitor Data Factory metrics with Azure Monitor
[This video from Scott Hanselman](https://docs.microsoft.com/en-us/azure/data-factory/monitor-using-azure-monitor#monitor-data-factory-metrics-with-azure-monitor) has step-by-step instructions on how to configure Azure Data Factory Analytics with Azure Monitor.

It will require the [Azure Data Factory Management Solution Service Pack](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/Microsoft.AzureDataFactoryAnalytics?src=azserv&tab=Overview).

![image info](./img/5-adf_mgmt_sol.png)

This will install the service pack to your data factory instance, where you can specify how you will store/stream your logs.

![image info](./img/6-adf_logging.png)

Once you configure your logging preferences, the Azure Data Factory Analytics workspace will appear in your Azure dashboard.

---------------
### Resources
* [Create alerts to proactively monitor your data factory pipelines](https://azure.microsoft.com/en-us/blog/create-alerts-to-proactively-monitor-your-data-factory-pipelines/)

* [Alert and monitor data factories by using Azure Monitor](https://docs.microsoft.com/en-us/azure/data-factory/monitor-using-azure-monitor#monitor-data-factory-metrics-with-azure-monitor)

* [Azure Monitor overview](https://docs.microsoft.com/en-us/azure/azure-monitor/overview)

* [Azure Data Factory Management Solution Service Pack](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/Microsoft.AzureDataFactoryAnalytics?src=azserv&tab=Overview)


-----------------
###### Prepared by [Dave Voyles](dvoyles@microsoft.com), Microsoft Corp | May 2020