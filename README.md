# Product ontology

[Read the authoritative specification](ontology.json). It defines the common vocabulary, how modules inherit requirements, what references mean, which evidence satisfies a requirement and how objectives rank eligible designs. The accompanying [module schema](module.schema.json) defines the fields and types a consuming repository can declare.

## Adopt the dependency

Pin this repository to a Git commit. In the consuming repository, create a JSON module whose ontology version matches the dependency. Declare the participants, behavior, experience guarantees, business limits and objectives of that particular product. An organization can distribute a module of shared policies, which products import by exact version. All inherited requirements continue to apply.

## Assess a declaration

Parse the JSON and reject duplicate keys. Apply the module schema to each document. Then resolve imports, check typed references and apply the evaluation rules in the ontology. Report a failed check with its module, declaration, rule and supporting evidence. A schema validator can detect a missing threshold. Checking that a named metric exists requires reference resolution. Deciding whether the product actually meets that threshold requires measurement.

The [product fixture](examples/product.json) and [organization fixture](examples/organization.json) illustrate composition. Their names and numeric targets apply only to those fixtures.

## Scope of this version

This release specifies numeric bounds, attestations, observable action outcomes and ordered objectives. Metric evidence sources, scenario setup and triggers include prose. Automated assessment requires corresponding observations or test bindings. The repository contains the declarative specification and schema. Factory execution and evidence collection are separate.
