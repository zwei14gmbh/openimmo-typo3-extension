# OpenImmoChain

The OpenImmoChainViewHelper class returns the value for a given OpenImmo object \(&lt;immobilie&gt;, &lt;geo&gt;, &lt;preise&gt;, etc.\) and a chain of getter methods.

#### Example

```markup
<html xmlns:f="http://typo3.org/ns/TYPO3/CMS/Fluid/ViewHelpers"
      xmlns:oft3="http://typo3.org/ns/Zwei14/OpenimmoForTypo3/ViewHelpers">
      
    <!-- methodChain: method chain for PLZ -->
    <!-- openImmoObject: property object -->
    <oft3:openImmoChain
        methodChain="getGeo()->getPlz()" 
        openImmoObject="{propertyEvent.property}" /> 
    
</html>
```

 

