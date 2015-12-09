# Electric Meter Ontology

Electric Meter Ontology extends Semantic Sensor Network ([SSN](http://purl.oclc.org/NET/ssnx/ssn#)) Ontology to provide a vocabulary for describing electric meters, its observations, etc.

Prefix: `emtr`

Ontology URI: http://purl.org/NET/ssnext/electricmeters#

# Examples

## An electric meter

```
@prefix ssn: <http://purl.oclc.org/NET/ssnx/ssn#> .
@prefix qudt-quantity: <http://qudt.org/vocab/quantity#> .
@prefix qudt-unit: <http://qudt.org/vocab/unit#> .
@prefix qudt: <http://qudt.org/schema/qudt#> .
@prefix emtr: <http://purl.org/NET/ssnext/electricmeters#> .
@prefix : <http://example.com/> .

:emeter-0 a emtr:HeatMeter ;
  ssn:hasSubSystem :emeter-0-ampere ;
  ssn:hasSubSystem :emeter-0-voltage ;
  ssh:hasSubSystem :emeter-0-power .

:emeter-0-ampere a ssn:SensingDevice ;
  ssn:observes qudt-quantity:Ampere ;
  ssn:hasMeasurementCapability [
    a ssn:MeasurementCapability ;
    ssn:forProperty qudt-quantity:Ampere ;
    ssn:hasMeasurementProperty [
      a qudt:Unit ;
      ssn:hasValue [
        a qudt:Quantity ;
        ssn:hasValue qudt-unit:Ampere ;
      ] ;
    ] ;
  ] .

:emeter-0-voltage a ssn:SensingDevice ;
  ssn:observes qudt-quantity:ElectromotiveForce ;
  ssn:hasMeasurementCapability [
    a ssn:MeasurementCapability ;
    ssn:forProperty qudt-quantity:ElectromotiveForce ;
    ssn:hasMeasurementProperty [
      a qudt:Unit ;
      ssn:hasValue [ 
        a qudt:Quantity ;
        ssn:hasValue qudt-unit:Volt ;
      ] ;
    ] ;
  ] .
  
:emeter-0-power a ssn:SensingDevice ;
  ssn:observes qudt-quantity:ElectricPower ;
  ssn:hasMeasurementCapability [
    a ssn:MeasurementCapability ;
    ssn:forProperty qudt-quantity:ElectricPower ;
    ssn:hasMeasurementProperty [
      a qudt:Unit ;
      ssn:hasValue qudt-unit:Watt .
    ] .
  ] .
```

## Observations

```
prefix ssn: <http://purl.oclc.org/NET/ssnx/ssn#> .
@prefix qudt-quantity: <http://qudt.org/vocab/quantity#> .
@prefix qudt-unit: <http://qudt.org/vocab/unit#> .
@prefix qudt: <http://qudt.org/schema/qudt#> .
@prefix hmtr: <http://purl.org/NET/ssnext/heatmeters#> .
@prefix : <http://example.com/> .

:emeter-0-ampere-${TIMESTAMP} a ssn:Observation ;
  ssn:observedProperty qudt-quantity:Ampere ;
  ssn:observedBy :emeter-0-ampere ;
  ssn:observationResultTime "${DATETIME}"^^xsd:dateTime;
  ssn:observationResult [ 
    a ssn:SensorOutput ;
    ssn:hasValue [
      a qudt:QuantityValue ;
      qudt:quantityValue "0.0"^^xsd:double .
    ] . 
  ] .

:emeter-0-voltage-${TIMESTAMP} a ssn:Observation ;
  ssn:observedProperty qudt-quantity:ElectromotiveForce ;
  ssn:observedBy :emeter-0-voltage ;
  ssn:observationResultTime "${DATETIME}"^^xsd:dateTime;
  ssn:observationResult [ 
    a ssn:SensorOutput ;
    ssn:hasValue [
      a qudt:QuantityValue ;
      qudt:quantityValue "0.0"^^xsd:double .
    ] . 
  ] .
  
:emeter-0-power-${TIMESTAMP} a ssn:Observation ;
  ssn:observedProperty qudt-quantity:ElectricPower ;
  ssn:observedBy :emeter-0-power ;
  ssn:observationResultTime "${DATETIME}"^^xsd:dateTime;
  ssn:observationResult [ 
    a ssn:SensorOutput ;
    ssn:hasValue [
      a qudt:QuantityValue ;
      qudt:quantityValue "0.0"^^xsd:double .
    ] . 
  ] .
```
