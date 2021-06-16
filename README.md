# Structure / Flowchart

The extbase extension comes with several controller actions and corresponding plugins. The **list-**, **listRentLiving-**, **detail-**, **request-** and **notepadAction\(\)** and **plugins** are currently implemented. Actions for the other list endpoints of the API are currently not fully implemented. 

List, listRentLiving and detailAction render **fluid templates** \(some of which are divided into small **partials**\).

The **OpenImmoChainViewHelper** Class can be used to output the values ​​of any OpenImmo object \(`property`, `geo`, `preise`, etc.\) in Fluid via their getter functions.

The **notepadAction\(\)** can be called via **PageType 214** so that a property \(`<Immobilie>`\) can be added to or removed from the notepad. The action sets the appropriate cookie and then redirects to the page from which the action was initiated.

The **requestAction\(\)** is an exception insofar as a TYPO3 form is integrated in the template via the **formvh:render ViewHelper** via a **FormFactory**. The factory class defines a multi-step form that can be used to make inquiries for one or more properties \(`<Immobilie>`\). A finisher uses the user input and the information on one or more properties stored in the cookie described above to generate a corresponding request and sends it to the relevant endpoint of the API.

The **IdentifierMapper** class is used to generate the URLs of individual properties.

![Structure / Flowchart](.gitbook/assets/structure%20%283%29.png)





