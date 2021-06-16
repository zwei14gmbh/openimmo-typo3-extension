---
description: Custom FormFactory class
---

# RequestFormFactory

The FormFactory class defines a multi-step form for requesting a single or multiple properties \(`<immobilie>`\).

### Usage \(in Fluid\)

```markup
<formvh:render
    factoryClass="Zwei14\OpenimmoForTypo3\Domain\Factory\ImmoSolveCENTRAL\V30\Request\RequestFormFactory"
    overrideConfiguration="{requestForObjects: requestForObjects}"
/>
```

{% hint style="info" %}
**requestForObjects** must be set in the action and must contain one or more entries as shown below.

```bash
<headline>__<subline>__<image>__<provider_identifier>__<target_software>__<target_version>;
```
{% endhint %}



