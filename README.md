# azure-monitor-integration
Azure Monitor provides an integrated monitoring solution for resources on Microsoft Azure cloud infrastructure. It allows you to monitor target resource, setup alert criteria and use action groups to perform actions as a result of the alert raised by the monitor. In this xM lab integration, we leverage action groups to create an xMatter event that notify target resources. 

---------

<kbd>
  <img src="https://github.com/xmatters/xMatters-Labs/raw/master/media/disclaimer.png">
</kbd>

---------

# Pre-Requisites
* Azure account (https://azure.microsoft.com/) or willingness to create a trial account
* xMatters account

# Files -- TO UPDATE
* [AzureMonitor.zip](AzureMonitor.zip) - The comm plan

# Installation

## xMatters set up

1. Load in the [AzureMonitor.zip](AzureMonitor.zip) Comm Plan
2. Review the Form's (Azure Monitor) configuration - add a default group or user in the recipients section
3. In the Integration Builder, look up the URL for the inbound integration "AzureUnifiedAlerts" and copy this for setting up a new Action Group in Azure

## Application (Azure Monitor) set up

1. Login in to Azure and use the left navigation to navigate to Monitor
1. On the dashboard page, click Create Alert 
1. Select a Target for the alert
1. Select a criteria for the target
1. Fill out the Alert details information
1. Create a new Action Group and fill oput the details, then create a new action. Use Webhook as the Action Type and paste in the URL copied from the Integration Builder
1. Save the new Alert
   
# Testing
To test, create an error situation that will trigger your monitor in the target based on the criteria defined. For example for a target of a Virtual Machine and the alert criteria is CPU over 20% over a period of time on average, use a tool in the target to generate the condition. When the condition is reached for a sustained amount of time to satisfy the monitoring alert criteria, you should see Azure displays the alert has been triggered. After a little while (up to 30 minutes), Azure should trigger the xMatters webhook URL you configured. A new xMatters event with the Azure Monitor information will be generated.

# Troubleshooting
If no event is created in xMatters, go to the inbound integration's Activity Stream and check that there was a recent request from Azure.

If the activity stream does not contain errors, check to see if an event was created and check the event log for more details.