# Applying semantic technologies in the context of Industry 4.0

This repository contains the solutions for **Portfolio Assignment 3** of the *Semantic Technologies* course at Universität Trier.

The assignment focuses on applying semantic technologies in the context of **Industry 4.0** using the Fischertechnik factory simulation model. The main topics include **Semantic Web Services**, **OWL ontology modelling**, **SOSA-based sensor data representation**, **SPARQL querying**, and **reasoning-based failure mode detection**.

## Repository Structure

```text
GROUP13_A3/
├── E5/
├── E6/
├── E7/
├── E8/
├── E9/
└── README.md
```

Each folder contains the solution files for the corresponding exercise.

## Technologies and Tools

* Protégé
* OWL
* RDF/XML
* RDF Schema
* SOSA / SSN Ontology
* SPARQL
* HermiT Reasoner
* Cellfie Plugin for Protégé
* Turtle
* JSOnto
* Microsoft Excel

## Exercise 5 — Semantic Web Services for Intelligent Control

Exercise 5 extends the provided Fischertechnik factory ontology with an additional postcondition for a semantic web service.

The modelled service represents the operation in which **VGR_1** picks up a red workpiece from **Sink_2** of the sorting system and transports it to the **waiting platform** of the high-bay warehouse.

The task focuses on modelling the postcondition:

```text
Postcondition_HBW_1_Status_Of_Light_Barrier_3_Interrupted_True
```

This postcondition states that light barrier 3 of the high-bay warehouse must be interrupted after the transport service has finished. The postcondition is linked to the corresponding transport service using the `has postcondition` object property and to the checking service using the `is checked by` object property.

### Contents

```text
E5/
├── *.owl
├── postcondition_individual_screenshot.png
└── service_with_postcondition_screenshot.png
```

## Exercise 6 — Modelling of Service Executions in OWL

Exercise 6 extends the ontology by modelling five executions of the service:

```text
Service_VGR_Pick_Up_And_Transport_With_Machine_VGR_1_With_Start_Sink_2_With_End_Waiting_Platform
```

Each service execution is represented with a start time and end time. Sensor data from the factory is imported and semantically annotated according to the **SOSA ontology**.

The imported sensor data includes:

* VGR pressure measurements,
* VGR acceleration measurements,
* high-bay warehouse waiting platform light barrier measurements.

The model connects the sensor observations to the corresponding service executions so that the data can later be used for failure detection and diagnosis.

### Contents

```text
E6/
├── concept_illustration.pdf
├── *.owl
├── *.json
├── cellfie.log
├── VGR1_pressure.xlsx
├── VGR1_BMX055_Acceleration.xlsx
└── HBW_WaitingPlatform_LB.xlsx
```

## Exercise 7 — SPARQL to Evaluate Postconditions

Exercise 7 defines a SPARQL query for detecting failed executions of the VGR transport service.

A service execution is considered failed if the required postcondition is not fulfilled. This is evaluated by checking the observations of the relevant light barrier. If the expected light barrier interruption is missing for a service execution, the execution is classified as failed.

The query returns:

* the failed service execution instance,
* its start time,
* its end time.

### Contents

```text
E7/
├── postcondition_failure_query.txt
├── sparql_results_screenshot.png
└── *.owl
```

## Exercise 8 — Reasoning for Knowledge-Based Failure Mode Detection

Exercise 8 extends the ontology with knowledge about failure modes for the VGR transport service.

The model supports reasoning-based classification of service executions into one of the following classes:

```text
ServiceExecution_VGR-PUT-VGR1-S2-WP_Successful
ServiceExecution_VGR-PUT-VGR1-S2-WP_FailureMode_VGR_Leakage
ServiceExecution_VGR-PUT-VGR1-S2-WP_FailureMode_VGR_Blocked
```

The classification is performed using the **HermiT Reasoner**.

The failure modes are based on sensor observations:

* A leakage is detected if the air pressure is below `0.002 bar`.
* A blockage is detected if the acceleration values on all axes are below `0.02 G`.
* A successful execution is detected if the postcondition assessment is fulfilled.

### Contents

```text
E8/
├── *.owl
├── successful_class_screenshot.png
├── leakage_class_screenshot.png
├── blocked_class_screenshot.png
└── reasoning_explanation_screenshots/
```

## Exercise 9 — Exploring Ontology Modelling Methods and Syntaxes

Exercise 9 compares different ontology modelling methods and serialization formats.

The ontology is extended using three different approaches:

1. **Protégé / RDF/XML**
2. **Turtle**
3. **JSOnto**

The modelling tasks include adding new classes, object properties, data properties, individuals, inverse properties, property characteristics, and annotation comments.

The exercise also includes a reflection on the experience of using Protégé, Turtle, and JSOnto for ontology modelling.

### Contents

```text
E9/
├── *.owl
├── *.ttl
└── jsonto/
    └── *.json
```

## Notes

* All OWL models are serialized in RDF/XML where required.
* The ontology models include comments explaining modelling decisions and assumptions.
* The models should be checked for consistency using the HermiT Reasoner.
* Screenshots are included where required by the assignment.
* Sensor data files and Cellfie import rules are included for reproducibility.




## Course

**Semantic Technologies**
Universität Trier
Portfolio Assignment 3
