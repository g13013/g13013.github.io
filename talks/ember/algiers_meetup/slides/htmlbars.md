###### HTMLBars

* Faster than Handlebars
* Virtual DOM
* Drop "Metamorph tags"
* Allows intuitive Handlebars syntax
    ```html.Handlebars
    <!-- before -->
    <img {{bind-attr src=image class=imageClassName}}>

    <!-- after -->
    <img src="http://url/to/{{image}}" class="a-class {{imageClassName}}">

    <!-- in the future -->
    <component-name prop=value>
    <!-- in place of -->
    {{component-name prop=value}}

    ```
