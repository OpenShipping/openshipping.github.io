---
title: Openshipping workshop - January 2019 - Marseille
---

Associated document :
- 2019-01_Marseille-OpenShipping-Workshops Jan19.pptx

## Minutes of workshop - message sent on 02/22/2019 


Dear all,
as you may have noticed, several initiatives around standardization (API, Data, Blockchain, EDI3, Terminals, etc.) have been created since we started Openshipping.org. However, considering that this collaborative work benefits from being shared anyway, I would like to update you with the last contents on which we’ve been working. We reduced the last workshop to fewer participants in order to focus on smart container events and only kept the most active ones* in order to ease the discussions and the delivery of a first version.
Thanks to Rabab’s work and synthesis, I’m glad to share with you the below inputs. 

Note that we can centralize comments and feedbacks in order to avoid spamming every one. 
Besides, we’ll schedule a new workshop in March. Please let us know if you want to participate !

### 1.	Standard Tracking API (https://app.swaggerhub.com/apis/API-Factory/Standard_Tracking_API/0.0.3):

Based on Nis’s proposal, we worked on this version focusing first on POSTING events.
As discussed, this API should include later the GET part (querying available tracking data), as well as data pipelines topics.
In this API, we manage the following entities:
•	Event : generic entity, containing the common event description seen together (e.g. location, date, position, vehicule, etc.)
•	Move : an event, with move information based mainly on EDI codification.
•	Smart Event : an event, with additional information including 
-	the new event codification to de defined
-	the metadata specific to new technologies like IoT (asset, device, transmission date, ..)
-	the event detail provides contextual data according to a customizable pattern. This pattern is to be defined for each smart event (cf. below).
Note: “Position” events will be handled finally as smart events. Thus, no need for a dedicated entity.

### 2.	Smart Event Catalog (https://app.swaggerhub.com/apis/API-Factory/Smart_Event_Catalog/0.0.3):

We propose to work, in parallel, on the catalog of smart events in order to identify the pattern describing each event “details”.
Please find here a first version, including pattern definition for Reefer measurements and Late events.
-> Please find attached some slides for a brief introduction of the two above swagger files.
Many thanks for your time and involvement !
Best regards,

* special thanks to Hanane, Nis, Kai, Marie, Mickael, Cédric, Nico, Zou, Coco, please forgive me if I’m forgetting someone.
