# CH4 -- add event to listener
## objectives
You will learn how to

+ add event to listener

## CH4.1 -- add event to listener
### `on` function

#### Basic structure

+ newer version (highly recommended)

```
$("<query-selector>").on("<event-name-without-prefix-on>",<event-callback>);
```

+ older version (**depreciated**, **discouraged** in Official docs)

```
$("<query-selector>").<event-name>(<event-callback>);
```

It will invoke `<event-callback>` event callback 

(to all elements satisfying `<query-selector>`) 

when `on<event-name-without-prefix-on>` event was triggered.

#### Sematically Equivalent

```
$("<query-selector>").on("<event-name-without-prefix-on>",<event-callback>);
```

is sematically equivalent to

```
document.querySelector("<query-selector>").on<event-name-without-prefix-on> = <event-callback>;
```

and (in older version, **depreciated**)

```
$("<query-selector>").<event-name>(<event-callback>);
```

## examples
### example 1
At startup, when one try to click all red things (which marked as `red` class) and alert `I found it`. 

One can use it in native html.

```
<script type="text/javascript">
document.getElementByClass("red").onclick = function(eventArgs){
    alert("I found it");
}
</script>
```

or one can use query selector in native html.

```
<script type="text/javascript">
document.querySelector(".red").onclick = function(eventArgs){
    alert("I found it");
}
</script>
```

or shorten with query selector in jQuery

```
<script type="text/javascript">
$(".red").on("click", function(eventArgs){
    alert("I found it");
})
</script>
```

### example 2
Image that 

one visits a book store.

one wants to find an Japanese Animation -- `SpyXFamily` from a table and 

redirects its official website `https:\\localhost\japanese\animation\SpyXFamily`

when one clicks `SpyXFamily`.

As following DOM tree.

```
<document>
    <div id="container">
        <table>
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Category</th>
                    <th>Author</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <th>SpyXFamily</th>
                    <th>Japanese Animation</th>
                    <th>Unknown</th>
                </tr>
            </tbody>
        </table>
    </div>
</document>
```

One can use 

```
<script type="text/javascript">
let allTrElements = document.querySelector("th");
let someTrElements = allTrElements.map(
    (element) => element.innerHTML == "SpyXFamily"
);
someTrElements.onclick = function(eventArgs){
    window.location.href = "https:\\localhost\japanese\animation\SpyXFamily";
}
</script>
```

or 

```
<script type="text/javascript">
let someTrElements = $("th").filter(function(){
    return $(this).innerHTML == "SpyXFamily"
}); 

someTrElements.on("click",function(eventArgs){
    window.location.href = "https:\\localhost\japanese\animation\SpyXFamily";
}
```

## reference
### Official docs
+ [`.on`](https://api.jquery.com/on/#on-events-selector-data-handler)