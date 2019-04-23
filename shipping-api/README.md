# OpenShipping.org API for Event Publishing and Tracking

This API deals with data sharing among shipping organizations. Data providers include any organization which takes an active part in the movement of containers, while data consumers can be anyone interested in these movements. The API has been separated into two parts, specifically targeted these two groups of personas.

The *Event API* is designed specifically for stateless fire-and-forget event posting, with emphasis on simple mapping especially from carriers' back-end systems. The OpenShipping.org Event API is fully documented [here](event-api.md).
OpenAPI .yaml file for the Event API is [here](swagger/event-api.yaml) as well as on SwaggerHub [here](https://app.swaggerhub.com/apis/OpenShippingDotOrg/OpenShipping-EventAPI). 

The *Tracking API* provides querying functionality for getting shipping status, targeted answering common industry tracking requests. The OpenShipping.org Tracking API is documented [here](tracking-api.md). 
OpenAPI .yaml file for the Tracking API is [here](swagger/tracking-api.yaml) as well as on SwaggerHub [here](https://app.swaggerhub.com/apis/OpenShippingDotOrg/OpenShipping-TrackingAPI).

While event publishing and tracking are individual use cases (and technically essentially segregates the POST and the GET endpoints), they largely deal with the same data, and are based on a common logical data model.

## Logical Data Model
![Class Overview](images/class-overview.png)

The above diagram illustrates the fundamental classes of the API. The main resources involved are Consignments and Transport Equipment. 

A *Consignment* represents the contracted movement of goods. In this containerized context, the Consignment defines a bunch of containers to be moved.
Please note that Consignment is to be distinguished from "shipment", which refers to the traded goods. These semantics are often a bit blurry, carriers traditionally have not have a reason to distinguish. Throughout the API semantics are adopted directly from the UN/CEFACT SCRDM Buy-Ship-Pay model, emphasizing this distinction.

*Transport Equipment* in our context can be considered a container. It's worth pointing out the importance of its relation to a Consignment: since the same physical container is reused over and over, it is the Transport Equipment within a Consignment which is relevant to a given set of shipping parties. 

Next up are the various kinds of events, which come in three flavors: planned, estimated and actual. 

By and large, the industry plans at the Consignment level (meaning the plan is the same for all containers), and very often the individual container cannot be identified until a while after the plan is issued. This is represented by *Planned Events*, which are bundled into a full Consignment transport plan. 

By contrast, *Actual Events* are physical occurrences of the individual, identified containers. A container is gated in, not a Consignment. Thus, Actual Events relate to Transport Equipment. 

The same is the case for *Estimated Events*, which are operational expected occurrences such as ETAs and ETDs. This is different from a plan: a delay may render a plan invalid, but it doesn't automatically update that plan to a new one. 
