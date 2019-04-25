# OpenShipping.org Tracking API

The *Tracking API* provides querying functionality for getting shipping status, targeted answering common industry tracking requests. Data publishers include carriers and other shipping actors, as well as data aggregation service providers. Data consumers are mainly beneficiary cargo owners, shippers, consignees and similar customers with a need to track cargo movements. 

OpenAPI .yaml file for the Tracking API can be found [here](tracking-api.yaml) and also on SwaggerHub [here](https://app.swaggerhub.com/apis/OpenShippingDotOrg/OpenShipping-TrackingAPI).

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
