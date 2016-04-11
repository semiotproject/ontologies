## Examples

```
...
{
  "@id": "apidoc:observations",
  "@type": "hydra:Link",
  
  "rdfs:domain": "ssn:System",
  "rdfs:range": "hydra:Collection",

  "hydra:supportedOperation": [
    {
      "@type": "hydra:Operation",
      "hydra:method": "GET",
      "hydra:returns": {
        "@type": ["sh:Shape", "hydra:Collection"],
        "sh:property": {
          "sh:predicate": "hydra:member",
          "sh:class": "ssn:Observation"
        }
      }
    },
    {
      "@type": "hydra-pubsub:SubscribeOperation",
      "hydra-pubsub:publishes": "ssn:Observation",
      "hydra-pubsub:endpoint": "ws://localhost:8080/ws"^^xsd:anyURI,
      "hydra-pubsub:protocol": "hydra-pubsub:WAMP",
      "hydra-pubsub:parameterMapping": [
        {
          "@type": "hydra-pubsub:PropertyToPropertyMapping",
          "hydra-pubsub:toProperty": "hydra-pubsub:topic",
          "hydra-pubsub:fromProperty": "dcterms:identifier"
        }
      ]
    }
  ]
}
...
```
