# Heat Meter Ontology

Heat Meter Ontology extends Semantic Sensor Network (SSN) Ontology to provide a vocabulary for describing [heat meters](https://en.wikipedia.org/wiki/Heat_meter), its observations, etc.

Prefix: `hmtr`

Ontology URI: http://purl.org/NET/ssnext/heatmeters#

# Examples

## A heat meter

```
@prefix ssn: <http://purl.oclc.org/NET/ssnx/ssn#> .
@prefix qudt-quantity: <http://qudt.org/vocab/quantity#> .
@prefix qudt-unit: <http://qudt.org/vocab/unit#> .
@prefix qudt: <http://www.qudt.org/qudt/owl/1.0.0/qudt/#> .
@prefix hmtr: <http://purl.org/NET/ssnext/heatmeters#> .
@prefix : <http://example.com/> .

:hmeter-0 a hmtr:HeatMeter ;
  ssn:hasSubSystem :hmeter-0-heat ;
  ssn:hasSubSystem :hmeter-0-temperature .
  
:hmeter-0-temperature a ssn:SensingDevice ;
  ssn:observes qudt-quantity:ThermodynamicTemperature ;
  ssn:hasMeasurementCapability [
    a ssn:MeasurementCapability ;
    ssn:forProperty qudt-quantity:ThermodynamicTemperature ;
    ssn:hasMeasurementProperty [
      a qudt:Unit ;
      ssn:hasValue [
        a qudt:Quantity ;
        ssn:hasValue qudt-unit:DegreeCelsius ;
      ] ; 
    ] ;
    ssn:hasMeasurementProperty [
      a ssn:Accuracy ;
      ssn:hasValue [
        a qudt:QuantityValue ;
        ssn:hasValue "1.0"^^xsd:double ;
      ] ;
    ] .
  ] .
  
:hmeter-0-heat a ssn:SensingDevice ;
  ssn:observes qudt-quantity:SpecificHeatCapacity ;
  ssn:hasMeasurementCapability [
    a ssn:MeasurementCapability ;
    ssn:forProperty qudt-quantity:SpecificHeatCapacity ;
    ssn:hasMeasurementProperty [
      a qudt:Unit ;
      ssn:hasValue [
        a qudt:Quantity ;
        ssn:hasValue qudt-unit:Kilocalorie ;
      ] ;
    ] ;
    ssn:hasMeasurementProperty [
      a ssn:Accuracy ;
      ssn:hasValue [
        a qudt:QuantityValue ;
        ssn:hasValue "1.0"^^xsd:double ;
      ] ;
    ] .
  ] .
```

## An observation

```
@prefix ssn: <http://purl.oclc.org/NET/ssnx/ssn#> .
@prefix qudt-quantity: <http://qudt.org/vocab/quantity#> .
@prefix qudt-unit: <http://qudt.org/vocab/unit#> .
@prefix qudt: <http://www.qudt.org/qudt/owl/1.0.0/qudt/#> .
@prefix hmtr: <http://purl.org/NET/ssnext/heatmeters#> .
@prefix : <http://example.com/> .

:hmeter-0-heat-${TIMESTAMP} a ssn:Observation ;
  ssn:observedProperty qudt-quantity:SpecificHeatCapacity ;
  ssn:observedBy :hmeter-0-heat ;
  ssn:observationResultTime "${DATETIME}"^^xsd:dateTime;
  ssn:observationResult [ 
    a ssn:SensorOutput ;
    ssn:hasValue [
      a qudt:QuantityValue ;
      qudt:quantityValue "0.0"^^xsd:double .
    ] . 
  ] .

:hmeter-0-temperature-${TIMESTAMP} a ssn:Observation ;
  ssn:observedProperty qudt-quantity:ThermodynamicTemperature ;
  ssn:observedBy :hmeter-0-temperature ;
  ssn:observationResultTime "${DATETIME}"^^xsd:dateTime;
  ssn:observationResult [ 
    a ssn:SensorOutput ;
    ssn:hasValue [
      a qudt:QuantityValue ;
      qudt:quantityValue "0.0"^^xsd:double .
    ] . 
  ] .
```
