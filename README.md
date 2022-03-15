Feature flags in Angular using Azure App Configuration – What, Why & How
How can we implement feature flag in an Angular application using Azure App configuration feature management
In this section, we will implement an end to end implementation of feature flag in an Angular Application using Azure App configuration
Azure App configuration
1.	In the Azure portal, go to All Services -> Integration -> App Configuration
2.	Create an App configuration resource to hold all the feature flags. 
3.	Once resource is created go to the resource -> Operations -> Feature manager 
4.	Add a flag as testFeature
5.	Add two more flags as feature1 and feature2
 
After performing, all above steps we are done with creating a feature flag which can we enabled or disabled from Azure Portal.
Next, we will add an event subscription for tracking the changes made on the flag. Here I will send all the changes to Service Bus Queue, so that later our Angular app (any client app) will subscribe to this Service Bus Queue and enable / disable the feature on UI side.
Service Bus Queue
1.	On the App configuration screen, click on Events
2.	Select service bus queue and fill all the details to create an Event Subscription
3.	Now test that event subscription is working as expected, for that open App Configuration in one window and click on enabled check box. In another window, open Service Bus -> your service bus -> Queues -> Service Bus explorer -> Receive
4.	Click on refresh, it should show 1 active message
5.	Click on receive, it should return 1 record as below
6.	Click on received message which will give detail of the message like below

We are done with all the steps on Azure side, now feature flag is ready to use by any client application and based on this flag we can enable/disable any functionality.

Angular App
Now feature flags can be implemented based on the requirement of the project. I am here implementing in 3 ways
1.	Using Service: By using services, we can enable/disable feature on very granule level
2.	Using Directives: By using directives, we can enable/disable features which may be under development feature over existing functionality
3.	Using Angular guards: By using guards, we can enable/disable a complete module’s navigation

For more information about feature flags, you can refer below documents

•	https://docs.microsoft.com/en-us/azure/azure-app-configuration/manage-feature-flags

•	https://docs.microsoft.com/en-us/azure/azure-app-configuration/howto-feature-filters-aspnet-core

