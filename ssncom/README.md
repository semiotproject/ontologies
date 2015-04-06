# Communication Ontology for SSN

Communication Ontology extends Semantic Sensor Network ([SSN](http://purl.oclc.org/NET/ssnx/ssn#)) Ontology to provide a vocabulary for describing communication endpoints that is used to access sensor's observations.

Prefix: ssncom

Ontology URI: http://purl.org/NET/ssnext/communication#

## Example

```
@prefix ssn: <http://purl.oclc.org/NET/ssnx/ssn#>
@prefix hmtr: <http://purl.org/NET/ssnext/heatmeters#>
@prefix ssncom: <http://purl.org/NET/ssnext/communication#>

<coap://localhost:3131> a hmtr:HeatMeter ;
    ssn:hasSubsystem <coap://localhost:3131/temperature> ;
	ssn:hasSubsystem <coap://localhost:3131/heat> .

<coap://localhost:3131/temperature> a ssn:Sensor ;
	ssn:observes hmtr:Temperature ;
	ssncom:hasCommunicationEndpoint <coap://localhost:3131/temperature/obs> ;
    ssncom:hasCommunicationEndpoint <ws://localhost/ws?topic=localhost.3131.temperature.obs> .

<coap://localhost:3131/heat> a ssn:Sensor ;
	ssn:observes hmtr:Heat ;
	ssncom:hasCommunicationEndpoint <coap://localhost:3131/heat/obs> ;
    ssncom:hasCommunicationEndpoint <ws://localhost/ws?topic=localhost.3131.heat.obs>.

<coap://localhost:3131/temperature/obs> a ssncom:CommunicationEndpoint ;
    ssncom:protocol "COAP" .
<coap://localhost:3131/heat/obs> a ssncom:CommunicationEndpoint ;
    ssncom:protocol "COAP" .
<ws://localhost/ws?topic=localhost.3131.temperature.obs> a ssncom:CommunicationEndpoint ;
	ssncom:protocol "WAMP" .
<ws://localhost/ws?topic=localhost.3131.heat.obs> a ssncom:CommunicationEndpoint ;
	ssncom:protocol "WAMP" .
```
