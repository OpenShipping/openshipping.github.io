---
title: Openshipping workshop - October 2018 - Marseille
---

Associated documents :
- Workkshop API status_Traxens_20181008.pptx
- BRS_SCRDM_v1.0.0.2.pdf

## Minutes of workshop - message sent on 10/18/2018

Dear all,
firstly, I would like to thank you once again for your participation to the workshops. I’m sure we all wish it could go faster, but I’m proud to say that we’re making progress, and I do remain confident that we are still heading toward the right direction !
I hope you feel the same way. Please find below the MoM of our different discussions, and feel free to share your feedback and complete with your notes.

@Kai, @Nis, please read carefully, you might have some specific actions if you agree.

Looking forward to the next sessions, 

Best Regards,

Romain
-------------------------------------------------------------------------------------------------------------------------

Participants: 
-	Marie Roubinet, Traxens 
-	Sebastien Marin, Traxens 
-	Morgan Ventimila, Traxens 
-	Alejandro Amado, Navis
-	Eoin ONeill, DHL Supply Chain (DSC)
-	Geoff Smalling, Flexport
-	Peter Spellman, Inttra
-	Ed Ordway - Inttra 
-	Kai Heinrich, Hapag Lloyd 
-	Uwe Rieksmeier, Hapag Lloyd
-	Nis Jespersen, TradeLens Architect
-	Stanley Canepa – ports america
-	Rabab Hayek, CMA CGM
-	Cedric Barbut, CMA CGM 
-	Nicolas de Dreuille, CMA CGM
-	Romain Genoulaz, CMA CGM
-	Romaric Bonny, CMA CGM
-	Emmanuel Bourdon, CMA CGM
-	Maxime Frachon, CMA CGM

Session 1 - Moves (Traxens):
Traxens presented their current work on the definition of Move “Types” and the pattern that allows to describe each of them.
This work aims to cover the physical container movements, as well as other status changes that might occur while the container is not physically moving (stuffing, unstuffing, Refeer Power, etc.) 
Thus, very early, the need to use another generic term than “Moves” has been highlighted -> The use of “Status“ has been proposed and agreed.

- “Physical movements”: The structure of this type has been discussed (cf. slide §8 in “Workkshop API status_Traxens_20181008.pptx”).
- “other status”: based on the first Traxens’s proposal, we target to identify a first list and define the corresponding pattern.

Next Action : share Traxen’s excel file (-> Marie) and work offline on status list completion and attributes definitions.
->	Timeline 3 weeks, please come back to us if you want to participate.

Sessions 2&3 - Tracking (Maersk/TradeLens):
The discussions around Tracking were based on Nis’s proposal.

### 1.	API resource hierarchy: 
For this, it has been proposed to rely on UN/CEFACT model (cf. “BRS_SCRDM_v1.0.0.2.pdf”).
This model could fit to carrier’s shipping world, however, a deeper reflection has to be done to see how it could fit other spaces like LCL, freight forwarding, SCM,…
The complexity resides mainly in the ‘many to many’ relationships that could link Trade, Consignment, and Transport entities.

For instance, how to deal with a Purchase Order & subcontracting ?
The extension/review of CEFACT model is quite related to the ID discussion we had (consignment reference, equipment reference, … ?)

Next Actions:
- Provide feedback on CEFACT model extension (-> all)  @Nis would you mind taking the lead on this action and organize few workshops to tackle it ? I had the feeling your knowledge of CEFACT was beyond most of us (no offense for other stakeholders 😉) 

### 2.	API – Post Event Model: 
The shared swagger provides a first concrete model in a “containerized-context”.
Multiple endpoints allow to well define actor’s rights & responsibilities; per Leg type (e.g. Discharge, Arrival, ..), per Vehicule (Vessel, Rail, ..), and per ‘flavor’ (i.e. Planned, Estimated & Actual).

An additional endpoint has been added to cover actual “Position” tracking.

Next Actions:
- How to adapt this model to other contexts (-> all) 
  We propose to take in charge the follow-up and to organize next sessions. This point will certainly depend on the conclusions reached during next CEFACT workshops.
- How to deal with the “removes” from plan ref ? How to inform about a Planned Event in Plan A which is removed in the new revised Plan B (-> all) 
  We suggest to make a first proposal on our CMA CGM side.

- SMDG codification pattern (-> Expecting Hapag’s feedback 😊, @Kai are you OK with that ?).

### 3.	API – Querying model: 
How to answer the “where is my stuff” question of our clients.
This querying model should be addressed more in details in next sessions. Two main points have been already identified.

### Next Actions:
- Search parameters ? (linked to ID discussion)
- Security aspects to be clarified : 
Note that this two topics are no showstoppers, most likely they are to be managed by each API Provider, but a common frame can be considered and discussed

### Shared Repository:
Following our discussion, and thanks to Peter, we put all the shared document in a private OpenShipping GitHub branch.
We’ll shortly come back with more details on this repository. 
