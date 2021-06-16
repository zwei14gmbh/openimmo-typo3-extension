# Plugins

### List

Renders a paginated list of all property event entries

#### RouteEnhancer

```yaml
OpenimmoForTypo3RenderList:
  type: Extbase
  limitToPages:
    - xx
  extension: OpenimmoForTypo3
  plugin: RenderList
  routes:
    - routePath: /
      _controller: 'Render::list'
    - routePath: '/{page}'
      _controller: 'Render::list'
      _arguments:
        page: page
  defaultController: 'Render::list'
  defaults:
    page: '1'
  requirements:
    page: \d+
  aspects:
    page:
      type: StaticRangeMapper
      start: '1'
      end: '1000'
```

### ListRentLiving

Renders a paginated list of all property event entries for rent, living.

#### RouteEnhancer

```yaml
OpenimmoForTypo3RenderListRentLiving:
  type: Extbase
  limitToPages:
    - xx
  extension: OpenimmoForTypo3
  plugin: RenderListRentLiving
  routes:
    - routePath: /
      _controller: 'Render::listRentLiving'
    - routePath: '/{page}'
      _controller: 'Render::listRentLiving'
      _arguments:
        page: page
  defaultController: 'Render::listRentLiving'
  defaults:
    page: '1'
  requirements:
    page: \d+
  aspects:
    page:
      type: StaticRangeMapper
      start: '1'
      end: '1000'
```

### Notepad

The plugin can be triggered via forms to add or remove a property from the notepad \(`openimmofortypo3_notepad` cookie. The arguments `identifier` and `addOrRemove` must be set for the url `/{addOrRemove}/{identifier}` .

#### Add property

```markup
<f:form class="notepad notepad--add"
        pageType="214"
        action="notepad"
        pluginName="RenderNotepad"
        arguments="{identifier: propertyEvent.identifier, addOrRemove: 'add'}">
    <f:form.hidden name="headline" value="{oft3:openImmoChain(methodChain: 'getFreitexte()->getObjekttitel()', openImmoObject: propertyEvent.property)}" />
    <f:form.hidden name="subline" value="{oft3:openImmoChain(methodChain: 'getGeo()->getOrt()', openImmoObject: propertyEvent.property)}, {oft3:openImmoChain(methodChain: 'getGeo()->getStrasse()', openImmoObject: propertyEvent.property)} {oft3:openImmoChain(methodChain: 'getGeo()->getHausnummer()', openImmoObject: propertyEvent.property)}" />
    <f:form.hidden name="image" value="{image}" />
    <f:form.hidden name="provider_identifier" value="{propertyEvent.provider_identifier}" />
    <f:form.hidden name="target_software" value="{propertyEvent.sendersoftware}" />
    <f:form.hidden name="target_version" value="{propertyEvent.senderversion}" />
    <f:form.button class="link--heart-outline">Merken</f:form.button>
</f:form>
```

{% hint style="danger" %}
The hidden values in the example above are crucial for the **request** process. The cookie `openimmofortypo3_notepad` must contain all the information for the requested objects.

The example works with the **ImmoSolve\_CENTRAL 3.0** specific **FormFactory** and **Finisher**.
{% endhint %}

#### Remove property

```markup
<f:form class="notepad notepad--remove"
        pageType="214"
        action="notepad"
        pluginName="RenderNotepad"
        arguments="{identifier: propertyEvent.identifier, addOrRemove: 'remove'}">
    <f:form.button class="link--heart-outline active">Entfernen</f:form.button>
</f:form>
```

{% hint style="warning" %}
No hidden values required for removing a property from notepad.
{% endhint %}

#### Cookie

The `openimmofortypo3_notepad` cookie contains one or more entries as shown below.

```bash
<headline>__<subline>__<image>__<provider_identifier>__<target_software>__<target_version>;
```

#### RouteEnhancer

```yaml
OpenimmoForTypo3RenderNotepad:
  type: Extbase
  extension: OpenimmoForTypo3
  plugin: RenderNotepad
  routes:
    - routePath: '/{addOrRemove}/{identifier}'
      _controller: 'Render::notepad'
      _arguments:
        addOrRemove: addOrRemove
        identifier: identifier
  defaultController: 'Render::notepad'
  requirements:
    addOrRemove: (add|remove)
    identifier: '[0-9]{4}\.[0-9]{4}'
  aspects:
    addOrRemove:
      type: StaticValueMapper
      map:
        add: add
        remove: remove
    identifier:
      type: IdentifierMapper
      regex: '[0-9]{4}\.[0-9]{4}'
```

{% hint style="danger" %}
The regex must match the property identifiers in use. The regex must be defined without delimiters such as `/` or `#` .
{% endhint %}

### Request

Template

```markup
<formvh:render
    factoryClass="Zwei14\OpenimmoForTypo3\Domain\Factory\ImmoSolveCENTRAL\V30\Request\RequestFormFactory"
    overrideConfiguration="{requestForObjects: requestForObjects}"
/>
```

#### RouteEnhancer

```yaml
OpenimmoForTypo3RenderRequest:
  type: Extbase
  limitToPages:
    - 83
  extension: OpenimmoForTypo3
  plugin: RenderRequest
  routes:
    - routePath: /
      _controller: 'Render::request'
  defaultController: 'Render::request'
```

