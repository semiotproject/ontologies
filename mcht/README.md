# Machine Tools Ontology

Machine Tools Ontology extends Semantic Sensor Network (SSN) Ontology to provide a vocabulary for describing [machine tools](https://en.wikipedia.org/wiki/Machine_tool), its observations, etc.

Prefix: `mcht`
Ontology URI: http://purl.org/NET/ssnext/machinetools#

# Examples

## A machine tool

```
@prefix ssn: <http://purl.oclc.org/NET/ssnx/ssn#> .
@prefix mcht: <http://purl.org/NET/ssnext/machinetools#> .
@prefix : <http://example.com/> .

:mt-0 a mcht:MachineTool ;
  ssn:hasSubSystem :mt-0-state .
  
:mt-0-st a ssn:SensingDevice ;
  ssn:observes mcht:MachineToolWorkingState .
```

## An observation

```
@prefix ssn: <http://purl.oclc.org/NET/ssnx/ssn#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix mcht: <http://purl.org/NET/ssnext/machinetools#> .
@prefix : <http://example.com/> .

:mt-0-${TIMESTAMP} a ssn:Observation ;
  ssn:observedProperty mcht:MachineToolWorkingState ;
  ssn:observedBy :mt-0-st ;
  ssn:observationResultTime "${DATETIME}"^^xsd:dateTime;
  ssn:observationResult [ 
    a ssn:SensorOutput ;
    ssn:hasValue [
      a qudt:Enumeration ;
      ssn:hasValue mcht:IsInExecutionOfTask .
    ] . 
  ] .
```
