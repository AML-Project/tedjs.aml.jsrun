# JsRun - Tedjs Library


### :: Name Space and ID
NameSpace | ID
--------- | ----------
JsRun | system.aml.jsrun

##

 ### .:: Language: **English**

Description:

jsRun is a plugin for Tedjs Framework. it help you to create a code editor in you site directly. you can define a file as an library and access to it from ajax with a file name , like a local file. it has JS,HTML and CSS with other external files that you can add to it.
each external file can be edited in editor or just be a external library.
editor has two color. dark and light.

### :: Element Details
* General Shape:
    ```html
    <jsrun></jsrun>
    ```
    the general element TagName is ``jsrun`` that get 3 attribute and some children elements.

    to include this library to your project after attaching [tedjs](https://tedjs.org) to your website , write this function down:
    ```javascript
    include("system.aml.jsrun");
    // OR
    ainclude("system.aml.jsrun");
    ```
    or your can download it and use it localy.

*  Attributes:

    * ``width`` : 

        to set the width of whole editor. accepts all css units. the default unit is ``px``
        ```html
        <jsrun width="50%"></jsrun>
        ```

    * ``height`` : 
    
        to set the height of whole editor. accepts all css units.the default unit is ``px``
        ```html
        <jsrun height="200px"></jsrun>
        ```
    * ``color`` :

        with this can set the color of your editor.``light`` and ``dark``
        ![Dark Theme](dark.png "Dark Theme")
        ```html
        <jsrun color="dark"></jsrun>
        ```
        OR
        ![Dark Theme](light.png "Dark Theme")
        ```html
        <jsrun color="light"></jsrun>
        ```
* Children ``Elements`` :

    * General ``Attributes`` :

        each child element has generals attributes.

        * ``type`` Attribute : **``Requeired``**

            ``type`` attribute will set the type of that element to parse the content type are ``html`` , ``js`` or ``javascript`` and ``css``
            ```html
            <element type="html"/>
            <element type="js"/>
            <element type="css"/>
            ```
        
        * ``url`` Attribute :

            if use this attribute , the inner content of element will not parse as a code inside the editor and the content of the url will be fetched.
            ```html
            <element url="/path/file.ext">
            <element url="http://doamin.tld/...">
            ```

        * ``preCompile`` Attribute :

            in some cases you want to use ``less`` instead of ``css`` . so you can load less as a library in your site and use the parse function as a pre parser for the codes to load them as ``css``.

            in attribute value must write down the name of parser function. like:
            ```html
            <element preCompile="less.parser">
            ```

    * ``lang`` Element

        the element ``lang`` will let you to insert any type of ``css`` , ``javascrip`` and ``html`` for one time. if there are more than one element from a same type , the first one will accepted.
        
        to define a ``lang`` element , you must do like this:
        ```html
        <lang type="[Types]"></lang>
        ```

        if you write codes inside the element block , it will parse the code , but if use the ``url`` attribute it will fetch the url data and parse this data.
        ```html
        <lang type="javascript">var a = 2;</lang>
        // OR
        <lang type="css" url="http://domain.com/file.css"></lang>
        ```

        and as on top explained you can use ``preCompile`` attribute too.

    * ``extfile`` Element :

        this element is an external file that you can load a url or inline code as a editable library in editor or not.

       it accept general attributes , also has some special attributes too.

       to define the element:
       ```html
       <extfile 
            name="library"
            path="lib.js"
            path-in="[Type | Types,...]"
       ></extfile>
       ```

       * ``extFile`` element attributes :
            * ``name`` Attribute :

                the value of this attribute is used to write in the top menu of editor to can be accessible to edit.
                
                if the name not defined , the name will be selectd automaticly.the name will be ``Extend[Number]`` like ``Extend0``.

            * ``path`` Attribute :

                if use this attribute , the system will show this as an editable library in editor. the value of this attribute is a file name with its extension name like ``app.js``.

                after adding this , you can access to this file via ajax with the defined file name. like it is a local file.

            * ``path-in`` Attribute :

                with this , you can tell element that the file name should be accessible within which files. ``html`` , ``css`` or ``javascript`` or multiple of them.
                ```html
                <extfile ... path-in="html"></extfile>
                ```
                OR
                ```html
                <extfile ... path-in="javascript,css"></extfile>
                ```
                OR ...



# Notice
    to write html code inside lang element , you must encode it first to not be parsed by Browser 

##

# Example :

the ``lang`` and ``extfile`` elements are optional. if don't write each one , will not shown on top menu.

```html
<jsrun color="light" width="800px" height="300px">

    <lang type="html">
        &lt;p&gt; Hello This is a Test &lt;/p&gt;
    </lang>
    
    <lang type="css">body{
        background:black;
        color:white;
    }</lang>

    <lang type="js">
        alert(a);
    </lang>

    <extfile type="js">
        var a = 2;
    </extfile>

    <extfile type="css" path="style.css" name="Style">
        body{color:red !important;}
    </extfile>

</jsrun>
```

##

## to highlighting the code , [ace editor](https://github.com/ajaxorg/ace) is used. 

# Author
this is created by [poryagrand](https://github.com/poryagrand) . power by [Tedjs](https://tedjs.org)