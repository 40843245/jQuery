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
  
Here are common query selector that be used in jQuery.

| query selector's type | format | meaning | description | NOTE | example | example explanation |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| `ID Selector` | `$("#<id>")` | id | select the first element by id | see below | `$("#nico")` | select the first element whose id="nico" |
| `Class Selector` | `$(".<class>")`| class | select the first element by class name | | `$(".lovelive")` | select all elements whose class contains "lovelive" | 
| `Element Selector` | `$("<tag-name>")` | tag name | select all elements by tag name `<tag-name>` | | `$("p")`| select all elements whose tag name is `<p>` |
| `Universal Selector` | `$("*")` | all elements | select all elements in the document | | | |
| `Multiple Selector` | `$("<sub-query-selector1>,<sub-query-selector2>")` and more | an array of sub-query selector | select all elements that<br>satisfies one of `<sub-query-selector1>` and `<sub-query-selector2>` | the return value of `$("<sub-query-selector1>,<sub-query-selector2>")` is equivalent to the result of combining the return value of `$("<sub-query-selector1>")` and $("<sub-query-selector2>")  | `$("h1,p, .footer")`| select all elements whose tag is one of `<h1>`, `<p>` |
| ` Selector` | `$("*")` | all elements | select all elements in the document | | | | 
| `Descendant Selector` | `$("<sub-query-selector1> <sub-query-selector2>")` and more | | select all elements that satisfies `<sub-query-selector1>`.<br>In these element select all elements that satisfies `<sub-query-selector2>` | | `$("#animation .Japanese .spyXfamily")` | select all elements by id `animation`. In these elements, select all elements by class containing `Japanese`. Then select all elements by class containing `spyXfamily`  | 

## reference

