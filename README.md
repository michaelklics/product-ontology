# Product ontology

[Read the authoritative specification](ontology.json). It defines the common vocabulary, how modules inherit requirements, what references mean, which evidence satisfies a requirement and how objectives rank eligible designs. The accompanying [module schema](module.schema.json) defines the fields and types a consuming repository can declare.

## Adopt the dependency

Pin this repository to a Git commit. In the consuming repository, create a JSON module whose ontology version matches the dependency. Declare the participants, behavior, experience guarantees, organizational constraints and objectives of that particular product. An organization can distribute a module of shared policies, which products import by exact version. All inherited requirements continue to apply.

Declare a product's operating cost requirements and metrics in its product module. A software factory can declare its own resource and development cost requirements as a separate product. The ontology supplies the same metric and requirement vocabulary to both; it does not combine their accounting.

## Product governance

A product names its governing party with `governed_by`. The value resolves to one actor, locally or through an import. A collective can be that actor. In the product fixture, the council governs the product, the operator owns the cost requirement and a participant owns the experience objective. If legal ownership matters, declare it as a separate relation.

To migrate from 0.2.0, set the ontology version to 0.3.0 and give each module a `kind` of `product` or `profile`. Each product declares its governing party. Shared profiles contribute actors and policies. Replace the `business` perspective with `organizational` on requirements and objectives, version the changed modules and update import pins.

## Assess a declaration

Parse the JSON and reject duplicate keys. Apply the module schema to each document. Then resolve imports, check typed references and apply the evaluation rules in the ontology. Report a failed check with its module, declaration, rule and supporting evidence. A schema validator can detect a missing threshold. Checking that a named metric exists requires reference resolution. Deciding whether the product actually meets that threshold requires measurement.

The [product fixture](examples/product.json) and [organization fixture](examples/organization.json) illustrate composition. Their names and numeric targets apply only to those fixtures.

## Scope of this version

This release specifies numeric bounds, attestations, observable action outcomes and ordered objectives. Metric evidence sources, scenario setup and triggers include prose. Automated assessment requires corresponding observations or test bindings. The repository contains the declarative specification and schema. Factory execution and evidence collection are separate.

## License

This project is available under the [MIT License](LICENSE).
