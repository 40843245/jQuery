# CH3 -- access elements in DOM tree
## objectives
You will learn how to

+ access elements in DOM tree

## CH3.1 -- access elements in DOM tree
Use `$("<query-selector>")`.

where 

`<query-selector>` is a query selector in JS.

> [!TIP]
> You can think of query selector as a filter to filter out DOM tree.

> [!CAUTION]
> Since `$()` only accepts one argument with string type,
>
> quotated the query selector with double quotation (i.e. `"`).

Here are type of query selector

+ directly children selector (basic selector):

it will search for its directly children (with depth 1), including   

    - `ID Selector`
    - `Class Selector`
    - `Element Selector`
    - `Universal Selector`
    - `Multiple Selector`
    
+ hierarchy selector
  
it will search for its sibling or parent, etc, including   

  - `Multiple Selector`
  - `Descendant Selector`
  - `Child Selector`
  - `Next Adjacent Selector`
  - `Sibling Selector`
  - `Content Filter Selectors`

+ Attribute Selectors

a selector that search for specified attribute(s).


+ Basic Filter Selectors:

It allows for more refined selection based on position or state.

Here are common query selector that be used in jQuery.

| query selector's type | format | meaning | description | NOTE | example | example explanation |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| `ID Selector` | `$("#<id>")` | id | select the first element by id | see below | `$("#nico")` | select the first element whose id="nico" |
| `Class Selector` | `$(".<class>")`| class | select all by class containing the **word** `<class>` | In this example, assume an element whose class=`ali _lovelive_`, there are NO element found since it needs to find all elements by class containg the **exactly word** `lovelive` (NOT `_lovelive_`) | `$(".lovelive")` | select all elements by class containing the **word** `lovelive` | 
| `Element Selector` | `$("<tag-name>")` | tag name | select all elements by tag name `<tag-name>` | | `$("p")`| select all elements whose tag name is `<p>` |
| `Universal Selector` | `$("<sub-query-selector> *")` | all descendants | select all elements satisfying `<sub-query-selector>` and they're descendants. | | `$(".p *")` | select all `<p>` elements and they're descendants |
| `Multiple Selector` | `$("<sub-query-selector1>,<sub-query-selector2>")` and more | an array of sub-query selector | select all elements that<br>satisfies one of `<sub-query-selector1>` and `<sub-query-selector2>` | the return value of `$("<sub-query-selector1>,<sub-query-selector2>")` is equivalent to the result of combining the return value of `$("<sub-query-selector1>")` and $("<sub-query-selector2>")  | `$("h1,p, .footer")`| select all elements whose tag is one of `<h1>`, `<p>` |
| `Child Selector`| `$("<sub-query-selector1> > <sub-query-selector2>")` and more | | select all elements that satisfies `<sub-query-selector1>`.<br>In these elements, select all direcly children elements that satisfies `<sub-query-selector2>` | `$("#animation .Japanese")` | select all elements by id `animation`. In these elements, select all descendant elements by class containing `Japanese`. | 
| `Descendant Selector` | `$("<sub-query-selector1> <sub-query-selector2>")` and more | | select all elements that satisfies `<sub-query-selector1>`.<br>In these elements, select all descendant elements that satisfies `<sub-query-selector2>` | | `$("#animation .Japanese .spyXfamily")` | select all elements by id `animation`. In these elements, select all descendant elements by class containing `Japanese`. Then select all descendant elements by class containing `spyXfamily` | 
| `Next Adjacent Selector` | `$("`<sub-query-selector1>` + `<sub-query-selector2>`")` | | select first element satsifing `<sub-query-selector1>` that is immediately after the element satisfying `<sub-query-selector2>` | `$(".red + p")` | select the first element by class containing `red` and is immediately after the `<p>` element |
| `Sibling Selector` | `$("<sub-query-selector1> ~ <sub-query-selector2>")` and more | | select all elements satisfying `<sub-query-selector1>`<br>which is sibling of all elements satisfying `<sub-query-selector2>`<br>and comes after all elements satisfying `<sub-query-selector2>` | `$(".red ~ p")` | select all elements by class containing `red`<br>which is sibling of all `<p>` elements<br>and comes after all `<p>` elements | 
| `Attribute Selectors` | `$("[<attribute>]")` | | select all elements that has `<attribute>` attribute | | `$("[href]")` | select all elements that has `href` attribute |
| `Attribute Selectors` | `$("[<attribute>='<value>']")` | | select all elements that has `<attribute>` attribute and its value equals to `<value>` | | `$("[type='text']")` | select all elements that has `type` attributes and its value equals to `text` |
| `Attribute Selectors` | `$("[<attribute>^='<value>']")` | | select all elements that has `<attribute>` attribute and its value starts with `<value>` | | `$("[href^='http']")` | select all elements that has `href` attribute and its value starts with `http` |
| `Attribute Selectors` | `$("[<attribute>$='<value>']")` | | select all elements that has `<attribute>` attribute and its value ends with `<value>` | | `$("[img$='.jpg']")` | select all elements that has `img` attribute and its value ends with `.jpg` |
| `Attribute Selectors` | `$("[<attribute>*='<value>']")` | | select all elements that has `<attribute>` attribute that its value containing `<value>` | In this example, assume that class="reddit", then the element will be found.  | `$("[class*='red']")` | select all elements whose class containing `red` **(NOT NECESSARY be a word)** |
| `Attribute Selectors` | `$("[<attribute>!='<value>']")` | | select all elements that has `<attribute>` attribute and<br>satisfying one of requirements:<ol><li>the attribute has no value specified</li><li>the attribute's value is NOT same as `<value>`</li></ol> | | `$("[href!='https://www.youtube.com/']")` | select all elements has the `href` attribute and its value is NOT equal to `https://www.youtube.com/` or is missing |
| `Basic Filter Selectors` | `$("<sub-query-selector>:first")` | | select first element satisfying `<sub-query-selector>` | | `$(".Japanese:first")` | select first element by class containing **exactly word** `Japanese` |
| `Basic Filter Selectors` | `$("<sub-query-selector>:last")` | | select last element satisfying `<sub-query-selector>` | | `$(".Japanese:last")` | select last element by class containing **exactly word** `Japanese` |
| `Basic Filter Selectors` | `$("<sub-query-selector>:even")` | | select even-index **(zero-based)** elements satisfying `<sub-query-selector>` | | `$(".Japanese:even")` | select the 0th, 2th, 4th etc elements by class containing **exactly word** `Japanese` |
| `Basic Filter Selectors` | `$("<sub-query-selector>:odd")` | | select odd-index **(zero-based)** elements satisfying `<sub-query-selector>` | | `$(".Japanese:odd")` | select the 1th, 3th, 5th etc elements by class containing **exactly word** `Japanese` |
| `Basic Filter Selectors` | `$("<sub-query-selector>:eq(<n>)")` | | select `<n>`-index **(zero-based)** elements satisfying `<sub-query-selector>` | | `$(".Japanese:eq(5)")` | select the 5th, element by class containing **exactly word** `Japanese` |
| `Basic Filter Selectors` | `$("<sub-query-selector>:gt(<n>)")` | | select all elements (which index is greater than `<n>` **(zero-based)**) satisfying `<sub-query-selector>` | |
 `$(".Japanese:gt(5)")` | select all elements which index is greater than 5 (i.e. 5th,6th,7th,...) by class containing **exactly word** `Japanese` |
| `Basic Filter Selectors` | `$("<sub-query-selector>:lt(<n>)")` | | select all elements (which index is less than `<n>` **(zero-based)**) satisfying `<sub-query-selector>` | | `$(".Japanese:lt(5)")` | select all elements which index is less than 5 (i.e. 0th,1th,2th,3th,4th) by class containing **exactly word** `Japanese` |
| `Basic Filter Selectors` | `$("<sub-query-selector>:not(<excluded-sub-query-selector>)")` | | select all elements satisfying `<sub-query-selector>` but NOT satisifying `<excluded-sub-query-selector>` | | `$("p:not(.Japanese)")` | select all `<p>` elements but exclude the class containing **exactly word** `Japanese` |
| `Basic Filter Selectors` | `$("<sub-query-selector>:header)")` | | select all elements satisfying `<sub-query-selector>` and it's a heading `<h1>` to `<h6>` | | `$(".Japanese:hear")` | select all `<h1>` to `<h6>` elements and its class containing **exactly word** `Japanese` |
| `Basic Filter Selectors` | `$("<sub-query-selector>:animated)")` | | select all elements satisfying `<sub-query-selector>` that are currently being animated | | `$(".Japanese:animated")` | select all elements whose class containing **exactly word** `Japanese` and the elements are currently being animated.  |
| `Content Filter Selectors` | `$("<sub-query-selector>:contains(<text>))")` | | select all elements satisfying `<sub-query-selector>` whose `innerHTML` contains `<text>` | | `$("p:contains("AI")")` | select all `<p>` elements satisfying whose `innerHTML` contains `AI` |




## reference

