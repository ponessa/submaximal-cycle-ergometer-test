---
title: Adding D3 Searchable Trees
permalink: /en/documentation-framework/adding-d3-searchable-trees
features:
  - mermaid
  - d3
  - select2
abstract: >- # this means to ignore newlines until "baseurl:"
  The hierarchy is a basic means of organizing and classifying items, many taxonomies are multi-tiered and dense. Too dense for professionals to either commit to memory or easily navigate. The interactive tree is a web page containing an interactive D3 expandable/collapsible tree representing the full hierarchy.
---

The `InteractiveD3TreeObj` object contains the functionality to draw, expand, collapse, show node details, search, and re-draw the D3 tree.  It exposes the functions:
1. `expandTree()`
1. `collapseTree()`
1. `resetTree()`
1. `doSearch(searchCriteria, searchField = "d.name", matchType=0, regexFlags="i")`
1. `initSelect2(select2Tax, select2Id = "#searchName", searchField = "d.name", idMatchType)`

This object and the exposed functions will be discussed in further details as we look at some usage scenarios.

## Adding D3 to a document's Front Matter
**D3**, short for **Data Driven Documents**, is a JavaScript-powered data visualization library that supports a myriad of features. The “Tree layout” is one type of D3’s family of hierarchical layouts. The tree layout produces a “node-link” diagram that lays out the connections among nodes in a way that displays the relationship of one node to another in a parent-child fashion.

As described in [Quickstart > Writing your document](../quickstart/writing-your-documents), all documents begin with Jekyll **Front Matter**.  In Jekyll, front matter refers to the metadata that is placed at the beginning of a document or a page. It is typically written in YAML (YAML Ain't Markup Language) format, but JSON and TOML are also supported. Front matter provides additional information about the content of the document, such as layout, title, date, and within the WFM documentation framework, it is used to add features to your document.

To include D3, add the YAML variable `features` and assign `- d3` to it.  E.g.,:
```
---
title: Adding D3 Searchable Trees
permalink: /en/learning-framework/adding-d3-searchable-trees
features:
  - d3
abstract: >- # this means to ignore newlines until "baseurl:"
  The hierarchy is a basic means of organizing and classifying .... 
---
```

## Simple Tree

To begin with we'll start with a basic tree that shows the (partial) hierarchy of teams in the NFL.  

<pre class="mermaid">
erDiagram

   League {
     league_code Char(3) PK
     name Varchar(255)
   }
   League ||--o{ Conference : contains
   Conference {
     conference_code Char(3) PK
     name Varchar(255)
     league_code Char(3) FK
  }
  Conference ||--o{ Division : contains
  Division {
    division_code Char(11) PK
    name Varchar(255)
    conference_code Char(3) FK
  }
  Division ||--o{ Team : contains
  Team {
    team_code Char(3) PK
    name Varchar(255)
    division_code Char(11) FK
  }

</pre>


After adding the `d3` feature in the document's front matter, you'll only need to:
1. Define a HTML division with an unique id to specify where to place the tree.
1. Define the JSON structure that holds the tree nodes
1. Instantiate the tree object (`InteractiveD3TreeObj`.
1. Pass the HTML division id, JSON tree structure, and instance of `InteractiveD3TreeObj` to D3.

<div id="nfl-tree"></div>
<button type="button" class="btn btn-primary" onclick="nflTree.expandTree()">+ Expand all</button>
<button type="button" class="btn btn-primary" onclick="nflTree.collapseTree()">- Collapse all</button>
<button type="button" class="btn btn-primary" onclick="nflTree.resetTree()">Resset tree</button>

<script>
    nflJson = [ {
        "code": "NFL",
        "name": "National Football League",
        "children": [
        {
            "code": "AFC",
            "name": "American Football Conference",
            "children": [
            {
                "code": "AFC_EAST",
                "name": "AFC East",
                "children": [
                {"code": "BUF", "name": "Buffalo Bills"},
                {"code": "MIA", "name": "Miami Dolphins"},
                {"code": "NE", "name": "New England Patriots"},
                {"code": "NYJ", "name": "New York Jets"}
                ]
            },
            {
                "code": "AFC_NORTH",
                "name": "AFC North",
                "children": [
                {"code": "BAL", "name": "Baltimore Ravens"},
                {"code": "CIN", "name": "Cincinnati Bengals"},
                {"code": "CLE", "name": "Cleveland Browns"},
                {"code": "PIT", "name": "Pittsburgh Steelers"}
                ]
            },
            // Add AFC South and AFC West as needed
            ]
        },
        {
            "code": "NFC",
            "name": "National Football Conference",
            "children": [
            {
                "code": "NFC_EAST",
                "name": "NFC East",
                "children": [
                {"code": "DAL", "name": "Dallas Cowboys"},
                {"code": "NYG", "name": "New York Giants"},
                {"code": "PHI", "name": "Philadelphia Eagles"},
                {"code": "WAS", "name": "Washington Commanders"}
                ]
            },
            {
                "code": "NFC_NORTH",
                "name": "NFC North",
                "children": [
                {"code": "CHI", "name": "Chicago Bears"},
                {"code": "DET", "name": "Detroit Lions"},
                {"code": "GB", "name": "Green Bay Packers"},
                {"code": "MIN", "name": "Minnesota Vikings"}
                ]
            },
            // Add NFC South and NFC West as needed
            ]
        }
        ]
    }
    ]
    nflJsonSearch = [ {
        "code": "NFL",
        "name": "National Football League",
        "children": [
        {
            "code": "AFC",
            "name": "American Football Conference",
            "children": [
            {
                "code": "AFC_EAST",
                "name": "AFC East",
                "children": [
                {"code": "BUF", "name": "Buffalo Bills"},
                {"code": "MIA", "name": "Miami Dolphins"},
                {"code": "NE", "name": "New England Patriots"},
                {"code": "NYJ", "name": "New York Jets"}
                ]
            },
            {
                "code": "AFC_NORTH",
                "name": "AFC North",
                "children": [
                {"code": "BAL", "name": "Baltimore Ravens"},
                {"code": "CIN", "name": "Cincinnati Bengals"},
                {"code": "CLE", "name": "Cleveland Browns"},
                {"code": "PIT", "name": "Pittsburgh Steelers"}
                ]
            },
            {
                "code": "AFC_SOUTH",
                "name": "AFC South",
                "children": [            
                    {"code": "HOU", "name": "Houston Texans"},
                    {"code": "IND", "name": "Indianapolis Colts"},
                    {"code": "JAX", "name": "Jacksonville Jaguars"},
                    {"code": "TEN", "name": "Tennessee Titans"}
                    ]
            },
            {
                "code": "AFC_WEST",
                "name": "AFC West",
                "children": [  
                    {"code": "DEN", "name": "Denver Broncos"},
                    {"code": "KC", "name": "Kansas City Chiefs"},
                    {"code": "LV", "name": "Las Vegas Raiders"},
                    {"code": "LAC", "name": "Los Angeles Chargers"}
                ]
            }
            ]
        },
        {
            "code": "NFC",
            "name": "National Football Conference",
            "children": [
            {
                "code": "NFC_EAST",
                "name": "NFC East",
                "children": [
                {"code": "DAL", "name": "Dallas Cowboys"},
                {"code": "NYG", "name": "New York Giants"},
                {"code": "PHI", "name": "Philadelphia Eagles"},
                {"code": "WAS", "name": "Washington Commanders"}
                ]
            },
            {
                "code": "NFC_NORTH",
                "name": "NFC North",
                "children": [
                {"code": "CHI", "name": "Chicago Bears"},
                {"code": "DET", "name": "Detroit Lions"},
                {"code": "GB", "name": "Green Bay Packers"},
                {"code": "MIN", "name": "Minnesota Vikings"}
                ]
            },
            {
                "code": "NFC_SOUTH",
                "name": "NFC South",
                "children": [            
                    {"code": "ATL", "name": "Atlanta Falcons"},
                    {"code": "CAR", "name": "Carolina Panthers"},
                    {"code": "NO", "name": "New Orleans Saints"},
                    {"code": "TB", "name": "Tampa Bay Buccaneers"}
                    ]
            },
            {
                "code": "NFC_WEST",
                "name": "NFC West",
                "children": [  
                    {"code": "ARI", "name": "Arizona Cardinals"},
                    {"code": "LAR", "name": "Los Angeles Rams"},
                    {"code": "SF", "name": "San Francisco 49ers"},
                    {"code": "SEA", "name": "Seattle Seahawks"}
                ]
            }
            ]
        }
        ]
    }
    ]    
    nflJsonSelect2 = [ {
        "code": "NFL",
        "name": "National Football League",
        "children": [
        {
            "code": "AFC",
            "name": "American Football Conference",
            "children": [
            {
                "code": "AFC_EAST",
                "name": "AFC East",
                "children": [
                {"code": "BUF", "name": "Buffalo Bills"},
                {"code": "MIA", "name": "Miami Dolphins"},
                {"code": "NE", "name": "New England Patriots"},
                {"code": "NYJ", "name": "New York Jets"}
                ]
            },
            {
                "code": "AFC_NORTH",
                "name": "AFC North",
                "children": [
                {"code": "BAL", "name": "Baltimore Ravens"},
                {"code": "CIN", "name": "Cincinnati Bengals"},
                {"code": "CLE", "name": "Cleveland Browns"},
                {"code": "PIT", "name": "Pittsburgh Steelers"}
                ]
            },
            {
                "code": "AFC_SOUTH",
                "name": "AFC South",
                "children": [            
                    {"code": "HOU", "name": "Houston Texans"},
                    {"code": "IND", "name": "Indianapolis Colts"},
                    {"code": "JAX", "name": "Jacksonville Jaguars"},
                    {"code": "TEN", "name": "Tennessee Titans"}
                    ]
            },
            {
                "code": "AFC_WEST",
                "name": "AFC West",
                "children": [  
                    {"code": "DEN", "name": "Denver Broncos"},
                    {"code": "KC", "name": "Kansas City Chiefs"},
                    {"code": "LV", "name": "Las Vegas Raiders"},
                    {"code": "LAC", "name": "Los Angeles Chargers"}
                ]
            }
            ]
        },
        {
            "code": "NFC",
            "name": "National Football Conference",
            "children": [
            {
                "code": "NFC_EAST",
                "name": "NFC East",
                "children": [
                {"code": "DAL", "name": "Dallas Cowboys"},
                {"code": "NYG", "name": "New York Giants"},
                {"code": "PHI", "name": "Philadelphia Eagles"},
                {"code": "WAS", "name": "Washington Commanders"}
                ]
            },
            {
                "code": "NFC_NORTH",
                "name": "NFC North",
                "children": [
                {"code": "CHI", "name": "Chicago Bears"},
                {"code": "DET", "name": "Detroit Lions"},
                {"code": "GB", "name": "Green Bay Packers"},
                {"code": "MIN", "name": "Minnesota Vikings"}
                ]
            },
            {
                "code": "NFC_SOUTH",
                "name": "NFC South",
                "children": [            
                    {"code": "ATL", "name": "Atlanta Falcons"},
                    {"code": "CAR", "name": "Carolina Panthers"},
                    {"code": "NO", "name": "New Orleans Saints"},
                    {"code": "TB", "name": "Tampa Bay Buccaneers"}
                    ]
            },
            {
                "code": "NFC_WEST",
                "name": "NFC West",
                "children": [  
                    {"code": "ARI", "name": "Arizona Cardinals"},
                    {"code": "LAR", "name": "Los Angeles Rams"},
                    {"code": "SF", "name": "San Francisco 49ers"},
                    {"code": "SEA", "name": "Seattle Seahawks"}
                ]
            }
            ]
        }
        ]
    }
    ]    
    treeHeight = 600
    treeWidth = 850
    nodeSpacing = 150

    nflTree = new InteractiveD3TreeObj(treeHeight = treeHeight, treeWidth = treeWidth, nodeSpacing = nodeSpacing);
     d3.select("#nfl-tree").datum(nflJson).call(nflTree);
</script>

To get this to work we only need to include one HTML element and two lines of JavaScript code inserted onto the document.  

### HTML element

The HTML element is an empty division with a unique `id`, this is where D3 will place the tree (e.g., `<div id="nfl-tree"></div>`).

### JSON Structure

The JSON tree structure represents a hierarchical organization of nodes, where each node can have various attributes. Follow the guidelines below to create a valid JSON tree:

1. Root Node:
   - The JSON tree must start with a root node.
   - The root node should be an object and contain the following attributes:
     - `code`: A unique identifier for the node.
     - Either `name` or `description`: A human-readable label or description for the node.

2. Child Nodes:
   - Each node can have an array of children represented by the attribute `children[]`.
   - The `children[]` attribute should contain an array of objects, each representing a child node.
   - Each child node follows the same structure as the root node, having at least a `code` attribute and either `name` or `description`.

3. Attributes:
   - Besides `code` and `name` or `description`, a node can have additional attributes based on the specific requirements.
   - Include any other relevant attributes for each node as needed.  These attributes will be shown in the scoll over dialog that is displayed when the user moves their cursor over the node.

### Instantiate the tree objct

Next, within a `<scipt>` element, you'll create an instance of `InteractiveD3TreeObject` and then pass this instance to D3 along with the name of the JSON object and the `id` from the HTML element.

The `InteractiveD3TreeObject` object contains the methods and attributes used to build the D3 tree, handle expanding and collapsing nodes, execute tree searches, and drawing the result tree.
The constructor has 3 **optional** parameters.

| **Parameter name** | **Default Value** | **Purpose** |
|----------------|---------------|---------|
| treeHeight     | 500 px        | Sets the height that the tree will be contained within. |
| treeWidth      | 1700 px       | Sets the width that the tree will be contained within.  |
| nodeSpacing    | 210 px        | Sets the distance between nodes at different levels.    |

### Pass the HTML division id, JSON tree structure, and trr object to D3.
In this D3 code snippet:

<pre name="code" class="js">
d3.select("#nfl-tree").datum(nflJson).call(nflTree);
</pre>

Here's a breakdown of what each part does:

1. `d3.select("#nfl-tree")`: This selects the HTML element with the ID "nfl-tree". It uses the D3.js library's `select` function to obtain a reference to the specified DOM element.

2. `.datum(nflJson)`: This sets the data associated with the selected element. The `datum` function binds the specified data (`nflJson` in this case) to the selected element.

3. `.call(nflTree)`: This invokes the function `nflTree` and passes the selected element (with the associated data) as an argument to that function. The `call` method is a convenient way to execute a function with a specific context (in this case, the selected element and its data).

This D3 code is setting the data for the selected HTML element with the ID "nfl-tree" to be `nflJson` and then calling the function `nflTree` with this data-bound element as an argument. This is a common pattern in D3 for binding data to DOM elements and then updating the visualization based on that data.

The code snippet below shows how this all works:
<pre name="code" class="html">
&lt;div id="nfl-tree"&gt;&lt;/div&gt;
</pre>

<pre name="code" class="js">
nflJson = [ {
    "code": "NFL",
    "name": "National Football League",
    "children": [
    {
        "code": "AFC",
        "name": "American Football Conference",
        "children": [
        {
            "code": "AFC_EAST",
            "name": "AFC East",
            "children": [
            {"code": "BUF", "name": "Buffalo Bills"},
            {"code": "MIA", "name": "Miami Dolphins"},
            {"code": "NE", "name": "New England Patriots"},
            {"code": "NYJ", "name": "New York Jets"}
            ]
        },
        ...

treeHeight = 600
treeWidth = 850
nodeSpacing = 150

nflTree = new InteractiveD3TreeObj(treeHeight = treeHeight, treeWidth = treeWidth, nodeSpacing = nodeSpacing);
d3.select("#nfl-tree").datum(nflJson).call(nflTree);
</pre>


### Expand, Collapse, and Reset Tree

The `InteractiveD3TreeObj` object provides this functionality using:
1. `expandTree()`
1. `collapseTree()`
1. `resetTree()`

Now that we have a basic tree, we can use the `InteractiveD3TreeObj` object's `expandTree()`, `collapseTree()`, and `resetTree()` functions.  We added 3 buttons to invoke "Expand all", "Collapse all", and "Reset tree".

<pre name="code" class="html">
&lt;button type="button" class="btn btn-primary" onclick="nflTree.expandTree()"&gt;+ Expand all&lt;/button&gt;
&lt;button type="button" class="btn btn-primary" onclick="nflTree.collapseTree()"&gt;- Collapse all&lt;/button&gt;
&lt;button type="button" class="btn btn-primary" onclick="nflTree.resetTree()"&gt;Resset tree&lt;/button&gt;
</pre>

### Search

The search function will search the entire tree and match nodes to the search criteria. The tree will then update and highlight the path to any and all nodes that match the search criteria.

The `InteractiveD3TreeObj` object provides this functionality using:
1. `doSearch(searchCriteria, searchField = "d.name", matchType=0, regexFlags="i")`

the function has 1 **required** and 3 **optional** parameters.

| **Parameter name** | **Default Value** | **Purpose** |
|------------------------|---------------|---------|
| **searchCriteria**     | None (required)      | Array of nodes or a valid **Regular Expression** (**RegEx**). <br> The nodes array should have the format: <br> `{"id": node-id, "text": node-text-value }` <br><br> A regular expression is a sequence of characters that forms a search pattern, used for pattern matching within strings. |
| searchField      |  "d.name"      | The name of the node (`d.`) attribute to be searched.  This attribute must exist in the tree structure used to build the tree. |
| matchType    | 0  | - **0** Pattern match (e.g., Man finds Man, Manual, Manufacturing) <br>- **1** Exact batch (e.g., Man finds Man) |
| regexFlags | "i" | Regular expression flags are optional parameters that modify the behavior of a regex pattern, influencing aspects such as case sensitivity, global matching, and multiline matching. They are appended to the end of a regex and alter how the pattern is applied to the target text. |

<div id="nfl-tree-search"></div>
<button type="button" class="btn btn-primary" onclick="nflTreeSearch.expandTree()">+ Expand all</button>
<button type="button" class="btn btn-primary" onclick="nflTreeSearch.collapseTree()">- Collapse all</button>
<button type="button" class="btn btn-primary" onclick="nflTreeSearch.resetTree()">Resset tree</button>


<script>
    nflTreeSearch = new InteractiveD3TreeObj(treeHeight = treeHeight, treeWidth = treeWidth, nodeSpacing = nodeSpacing);
    d3.select("#nfl-tree-search").datum(nflJsonSearch).call(nflTreeSearch);

    function runSearch() {
        searchCriteriaInput = document.getElementById("search-criteria-id").value
       
       let searchCriteria = ""

        if (searchCriteriaInput)
            // Check if the first character is '{' or '['
            if (searchCriteriaInput.startsWith('{') || searchCriteriaInput.startsWith('[')) {
            try {
                // Parse the string into a JSON object
                searchCriteria = JSON.parse(searchCriteriaInput);
            } catch (error) {
                console.error('Error parsing JSON:', error);
            }
            } else {
                searchCriteria = searchCriteriaInput;
            }


            nflTreeSearch.doSearch(searchCriteria)
    }
</script>

<input class="form-control" id="search-criteria-id" type="text" placeholder="Enter RegEx expression or valid JSON array string (see examples below)" style="width: 88%;" data-sb-validations="required">
<button class="btn btn-primary btn-lg" id="submitButton" type="button" onclick="javascript:runSearch()">Submit</button>

| **Type** | **Value**                           | **Finds** |
|----------|-------------------------------------|-----------|
| RegEx    | `((?=.*Bay)|(?=.*New))`             | Any name containing **bay** or **new** |
| RegEx    | `((?=.*Miami)|((?=.*New)(?=.*York)))` <br>or<br>`((?=.*Miami)|(?=.*New York))` | Any name containing **bay** or **new york** |
| RegEx    | `((?=.*Chi)|(?=.*New York)|(?=.*Los Angeles))` | Any name containing **chi** or **new york** or **los angeles** |
| JSON array | `[{"id":"NYJ", "text":"New York Jets"}, {"id":"NYG", "text":"New York Giants"}]` | Only name **new york jets** or **new york giants** |

## Adding Select2 drop down

**Select2** was designed to be a replacement for the standard `<select>` box that is displayed by the browser.  Specifically, the WFM Documenation Framework uses multi-value select boxes with pillboxes (to display what has already been selected).

For multi-select boxes, there is no distinct search control. To initiate a search, the user simply clicks into the control and a drop down is displayed by the different tiers of the taxonomy (e.g., League &rarr; Conference &rarr; Division &rarr; Team).

After a node is selected, the tree will update and highlight the path to the found node.  The `select2` control will also add a "pillbox" with the selected node.  To remove any specific selection the user can just the **x** to the right of the pillbox to remove the node from the search.

![select2 control]({{ site.baseurl }}/assets/images/docs/select2-control.png){: class="zoom" }

### Adding Select2 to a document's Front Matter

As described in [Quickstart > Writing your document](../quickstart/writing-your-documents), all documents begin with Jekyll **Front Matter**.  In Jekyll, front matter refers to the metadata that is placed at the beginning of a document or a page. It is typically written in YAML (YAML Ain't Markup Language) format, but JSON and TOML are also supported. Front matter provides additional information about the content of the document, such as layout, title, date, and within the WFM documentation framework, it is used to add features to your document.

To include D3, add the YAML variable `features` and assign `- d3` to it.  E.g.,:
```
---
title: Adding D3 Searchable Trees
permalink: /en/learning-framework/adding-d3-searchable-trees
features:
  - d3
  - select2
abstract: >- # this means to ignore newlines until "baseurl:"
  The hierarchy is a basic means of organizing and classifying .... 
---
```

### Adding Select2 to a document

1. Add an empty division HTML element with a unique `id`, this is where `select2` control will place the tree (e.g., `<div id="nfl-select2-id"></div>`).
    <pre name="code" class="html">
    &lt;div id="nfl-select2-id"&gt;&lt;/div&gt;
    </pre>
1. Define a JavaScript array that defines the different levels of the taxonomy
    <pre name="code" class="js">
    select2Tax = [ {"text":"League", "children":[]},
        {"text": "Conference", "children":[]},
        {"text": "Division", "children":[]},
        {"text": "Team", "children":[]}
    ];
    </pre>
1. Intialize the `select2` controll passing in
    - Taxonomy definition array (`select2Tax`)
    - HTML id to place the control (`#nfl-select2-id`)
    - The attribute name to be used for the search (`d.name`)
    - The match type (`0` for pattern, `1` for exact match)
    <pre name="code" class="js">
    nflTreeSelect2.initSelect2(select2Tax, select2Id, "d.name", 0);
    </pre>

<div id="nfl-tree-select2"></div>
<button type="button" class="btn btn-primary" onclick="nflTreeSelect2.expandTree()">+ Expand all</button>
<button type="button" class="btn btn-primary" onclick="nflTreeSelect2.collapseTree()">- Collapse all</button>
<button type="button" class="btn btn-primary" onclick="nflTreeSelect2.resetTree()">Resset tree</button>

<div class="form-group row">
    <div class="col-sm-12">
        <div id="nfl-select2-id"></div>	
    </div>	
</div>

<script>
    nflTreeSelect2 = new InteractiveD3TreeObj(treeHeight = treeHeight, treeWidth = treeWidth, nodeSpacing = nodeSpacing);
    d3.select("#nfl-tree-select2").datum(nflJsonSelect2).call(nflTreeSelect2);

    select2Tax = [ {"text":"League", "children":[]},
    {"text": "Conference", "children":[]},
    {"text": "Division", "children":[]},
    {"text": "Team", "children":[]}
    ];
    select2Id = "#nfl-select2-id";

    nflTreeSelect2.initSelect2(select2Tax, select2Id, "d.name", 0);
</script>