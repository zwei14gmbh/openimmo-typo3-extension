# IdentifierMapper

The **IdentifierMapper class** is used as aspect in **RouteEnhancers** \(e.g. list\) to check whether the identifier argument matches against a given regex.

#### Example

{% code title="ext\_localconf.php" %}
```php
$GLOBALS['TYPO3_CONF_VARS']['SYS']['routing']['aspects']['IdentifierMapper'] =
    Zwei14\OpenimmoForTypo3\Routing\Aspect\IdentifierMapper::class;
```
{% endcode %}

{% code title="config.yaml" %}
```yaml
aspects:
  identifier:
    type: IdentifierMapper
    regex: '[0-9]{4}\.[0-9]{4}'
```
{% endcode %}

