# Policy Store

This interface supports policy language used for making call routing decisions.

A policy document is a JWS; the payload is a JSON object conformant to the "Policy" type with rules conforming to the "Rule" object. Policy documents are carried using the MIME type of Application/EmergencyCallData.auth-policy+json. A policy document is composed of a set of rules and an optional description. Each rule is a JSON object containing the following members:

*	“id” (REQUIRED): a string containing an ID for the rule; the value MUST be unique within the ruleset
*	“priority” (REQUIRED): an integer greater than or equal to zero that MUST be unique within the ruleset; this is the rule’s priority
*	“conditions” (OPTIONAL): an object that MAY contain one or more Condition objects 
*	“actions” (REQUIRED): an object that MUST contain one or more Action objects 
*	“description” (OPTIONAL): a string that describes the rule

Within a rule, the “Conditions” object evaluates to "true" or "false". If it evaluates to "true" then the “actions” part of the rule is eligible to be executed.

Because multiple rules might have “Condition” parts that evaluate to "true", each rule has an associated priority value. A higher (numerically greater) value takes precedence over a rule with a lower value. When more than one rule has a “Conditions” section that evaluates to "true", only the rule with the largest priority value has its actions section executed. Priority 0 is the lowest priority; a rule with priority 0 is only executed if no other rule’s “conditions” evaluate to "true". Each rule also has an ID, which is a string unique to the ruleset.

In a Route Policy, an omitted “Conditions” section evaluates to "true"; this permits constructing default or “catch-all” rules that are executed only if no other rule matches. Normally, such rules have an extremely low priority value, e.g., 0.

## Owner

The owner of this repository approves all changes to the repository. 

This repository is owned by the NENA Core Services Committee, i3 Architecture working group.

#### Rules:

Specification Required. 

#### Contact:

[https://www.nena.org/page/911CoreSvcs](https://www.nena.org/page/911CoreSvcs) 

## Version History

### Geocode Conversion Service v 1.0

Version 1 OpenAPI schema for this service was originally defined in NENA-STA-010.3.2021. See https://www.nena.org/page/i3_Stage
