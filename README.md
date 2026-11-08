# Product ontology

A product repository uses this dependency to describe the experience it promises and the conditions under which its operator can provide it. People can read the intent of each declaration in a sentence. Agents can resolve its owner, metric, comparison and evidence through named fields.

Start with [the product example](examples/product.yaml). It inherits [an organization profile](examples/organization.yaml) and adds one participant, an action, an experience guarantee and two observable scenarios. The names, thresholds and organization in these examples belong to the examples. A product can declare several organizations, machine participants or other stakeholders.

## Use in a product repository

Pin this Git dependency to an immutable commit and keep a product module in the consuming repository. Read the dependency's [manifest](ontology.yaml), then validate each module against its [schema](module.schema.json). The module's ontology version must match the pinned dependency. The module version identifies the particular product or profile. Both are exact versions. Example imports resolve relative to the importing file.

## Meaning of a module

Use plain UTF-8 YAML with string keys, unique keys and JSON-compatible values. Identifiers use lowercase letters, digits and underscores, starting with a letter. Give each distinct concept a stable identifier and put its explanation in the corresponding meaning or intent field.

1. Load imports recursively. Each imported file must declare the requested module and version. Reject cycles, conflicting versions and declarations with the same identifier. A shared transitive dependency contributes its declarations once.
2. Combine inherited and local declarations by union. A local module can add a tighter requirement. Both requirements then apply. Changing an inherited declaration requires a new version of its source module.
3. Resolve references by kind. A relation connects two actors or entities. An action names an actor and an entity. A scenario names an action and one of its declared outcomes. An owner or attesting authority names an actor. A metric check or objective names a metric. Report every unresolved or ambiguous reference.
4. Evaluate each mandatory requirement within its metric's declared population, unit and window. The two numeric comparisons include equality. An empty population, incomplete window or missing evidence produces an unknown result. An attestation check requires evidence from its named authority covering the declared claim and scope. A declaration of a claim alone supplies no evidence.
5. Report satisfied, violated or unknown for each requirement. Only candidates with evidence of satisfying every applicable requirement qualify at the assessed boundary. Record whether evidence comes from a test, a projection or an operational observation. Claims about a completed operating period require evidence for that period.
6. Compare qualifying candidates by the entry module's priority list, highest priority first. The entry module must name every effective objective exactly once if it declares a ranking. Without a ranking, preserve the individual objective results. Missing measurements leave a comparison unresolved.
7. Use scenarios as observable examples. Their expected outcomes are machine-resolvable names. Their setup and trigger are natural language and still require a binding to a product-specific test or evaluation.

## Evolve the dependency

For a proposed change, keep the sample modules and evaluation inputs fixed, record the agent and ontology versions, and compare resolved requirements, outcomes, conflicts and requests for clarification. Repeat with independently authored profiles from different product types. Include a negative case such as an unresolved metric or an attempt to weaken an inherited limit. Publish changes to field meanings or evaluation rules under a new ontology version. A consuming repository reviews the effects on its own spec when it changes its pin.

This draft defines module composition, numeric bounds, attestations and ordered objectives. The schema checks document structure. Reference resolution, evidence collection and product conformance belong to the consuming factory. Future versions can introduce precise temporal and transition rules as evaluation cases establish the need.
