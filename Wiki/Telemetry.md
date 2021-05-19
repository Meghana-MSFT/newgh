
# Telemetry

New employee onboarding app logs telemetry to [Azure Application Insights](https://azure.microsoft.com/en-us/services/monitor/). You can go to the Application Insights blade of the Azure App Service to view basic telemetry about your services, such as requests, failures, and dependency errors, custom events, traces.

App integrates with Application Insights to gather bot activity analytics, as described [here](https://blog.botframework.com/2019/03/21/bot-analytics-behind-the-scenes/).

App logs a few kinds of events:

`Events` logs keeps the track of application events and also logs the user activities like:

- Total and Unique Users per month.
- Number of introduction submitted per week/month.
- Number of introduction approved per week/month.
- Average number of introduction posted to Teams channel.
- Number of feedback shared per week/month.
- Number of learning plan notification card sent per week/month.
- Number of pair up notification card sent per week/month.
- Average Response Time

  Exceptions` logs keeps the records of exceptions tracked in the application.

  

*Application Insights queries:*

- This query gives total number of unique users of bot.
```
customEvents
| extend User = tostring(customDimensions.userId)
| summarize dcount(User)

- This query gives total number of introduction submitted per week/month.
```
customEvents
| project name, timestamp
| where name contains "Introduction submitted" and (timestamp >= datetime('<<Start date time>>') and timestamp <= datetime('<<End date time>>'))
| summarize count() by name

- This query gives total number of introduction approved per week/month.
```
customEvents
| project name, timestamp
| where name contains"Introduction approved by manager"and (timestamp >= datetime('<<Start date time>>') and timestamp <= datetime('<<End date time>>'))
| summarizecount() by name

- This query gives total number of introduction posted to Teams channel.
```
customEvents
| project name, timestamp
| where name contains "Introduction posted to Teams" and (timestamp >= datetime('<<Start date time>>') and timestamp <= datetime('<<End date time>>'))
| summarize count() by name

- This query gives total number of feedback shared per week/month.
```
customEvents
| project name, timestamp
| where name contains "Feedback submitted" and (timestamp >= datetime('<<Start date time>>') and timestamp <= datetime('<<End date time>>'))
| summarize count() by name

- This query gives total number of learning plan notification card sent per week/month.
```
customEvents
| project name, timestamp
| where name contains "Sending notification to the specified conversation id" and (timestamp >= datetime('<<Start date time>>') and timestamp <= datetime('<<End date time>>'))
| summarize count() by name

- This query gives total number of pair up notification card sent per week/month.
```
customEvents
| project name, timestamp
| where name contains "Pair-up notification sent" and (timestamp >= datetime('<<Start date time>>') and timestamp <= datetime('<<End date time>>'))
| summarize count() by name

- This query gives average response time of requests.
```
requests
| summarize avg(duration)

## Privacy and Telemetry Notice. 

Data Collection. The software may collect information about your use of the software and send it to Microsoft. Microsoft may use this information to provide services and improve our products and services. You may turn off the telemetry as described in the repository. There are also some features in the software that may enable you and Microsoft to collect data from users of your applications. If you use these features, you must comply with applicable law, including providing appropriate notices to users of your applications together with a copy of Microsoft's privacy statement. Our privacy statement is located at https://go.microsoft.com/fwlink/?LinkID=824704. You can learn more about data collection and use in the help documentation and our privacy statement. Your use of the software operates as your consent to these practices.