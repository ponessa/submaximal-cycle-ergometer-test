---
title: Adding Diagrams With Mermaid
permalink: /en/learning-framework/adding-diagrams-with-mermaid
features:
  - mermaid
  - d3
  - zoom
abstract: >- # this means to ignore newlines until "baseurl:"
  Mermaid is a JavaScript-based diagramming and charting tool that uses Markdown-inspired text definitions and a renderer to create and modify complex diagrams. 
---

Diagramming and documentation costs precious developer time and gets outdated quickly. But not having diagrams or docs ruins productivity and hurts organizational learning. [Mermaid](https://mermaid.js.org/){: target="_blank"} addresses this problem by enabling users to create easily modifiable diagrams. It can also be made part of production scripts (and other pieces of code).

Note: for a online, visual editor, see [Mermaid Chart](https://www.mermaidchart.com/app/dashboard){:target="_blank"}

## Adding mermaid to a document's Front Matter
As described in [Quickstart > Writing your document](../quickstart/writing-your-documents), all documents begin with Jekyll **Front Matter**.  In Jekyll, front matter refers to the metadata that is placed at the beginning of a document or a page. It is typically written in YAML (YAML Ain't Markup Language) format, but JSON and TOML are also supported. Front matter provides additional information about the content of the document, such as layout, title, date, and within the WFM documentation framework, it is used to add features to your document.

To include Mermaid, add the YAML variable `features` and assign `- mermaid` and `- d3` to it.  E.g.,:
```
---
title: Adding Diagrams With Mermaid
permalink: /en/learning-framework/adding-diagrams-with-mermaid
features:
  - mermaid
  - d3
abstract: >- # this means to ignore newlines until "baseurl:"
  Mermaid is a JavaScript-based diagramming and charting tool .... 
---
```


## Sequence Diagram
A Sequence diagram is an interaction diagram that shows how processes operate with one another and in what order. See [Mermaid sequence diagrams](https://mermaid.js.org/syntax/sequenceDiagram.html){: target="_blank"} for additional details.

<pre class="mermaid" id="image-1">
sequenceDiagram
    Browser->>AuthenticationFilter: doFilter()
    activate AuthenticationFilter
        AuthenticationFilter->>Helpers: readServletCookie(HttpServletRequest,"wfm-dmf-user")
        activate Helpers
        Helpers-->>AuthenticationFilter: null
        deactivate Helpers
        AuthenticationFilter->>IBM SSO: sendRedirect()
    deactivate AuthenticationFilter
</pre>

**Code**
```
<pre class="mermaid">
sequenceDiagram
    Browser->>AuthenticationFilter: doFilter()
    activate AuthenticationFilter
        AuthenticationFilter->>Helpers: readServletCookie(HttpServletRequest,"wfm-dmf-user")
        activate Helpers
            Helpers-->>AuthenticationFilter: null
        deactivate Helpers
        AuthenticationFilter->>IBM SSO: sendRedirect()
    deactivate AuthenticationFilter
</pre>
```

### Activations
It is possible to activate and deactivate an actor and (de)activation can be dedicated declarations. Put a plus (`+`) before the actor to activate and a minus (`-`) upon the return.
```
<pre class="mermaid">
sequenceDiagram
    Browser->>+AuthenticationFilter: doFilter()
    AuthenticationFilter->>+Helpers: readServletCookie(HttpServletRequest,"wfm-dmf-user")
    Helpers-->>-AuthenticationFilter: null
    AuthenticationFilter->>-IBM SSO: sendRedirect()
</pre>
``` 

### Messages
Messages can be of two displayed either solid or with a dotted line.

`[Actor][Arrow][Actor]:Message text`

There are six types of arrows currently supported:

| **Type** | **Description** |
|:--------:|------  ---------|
| `->`     | Solid line without arrow |
| `-->`    | Dotted line without arrow |
| `->>`    | Solid line with arrowhead |
| `-->>`   | Dotted line with arrowhead |
| `-x`     | Solid line with a cross at the end |
| `--x`    | Dotted line with a cross at the end. |
| `-)`     | Solid line with an open arrow at the end (async) |
| `--)`    | Dotted line with a open arrow at the end (async) |



## Class Diagram

The class diagram is the main building block of object-oriented modeling. It is used for general conceptual modeling of the structure of the application, and for detailed modeling to translate the models into programming code. See [Mermaid class diagrams](https://mermaid.js.org/syntax/classDiagram.html){: target="_blank"} for additional details.

<pre class="mermaid">
classDiagram
class BankAccount{
    -int id
    -String owner
    -Double balance
    +getOwner() String
    +setOwner(name) void
    +getBalance() Double
    +setBalance(amount) void

    +deposit(amount) bool
    +withdrawal(amount) int
    ~applyInterest() void
}

class SavingsAccount {
    - double interestRate
    +SavingsAccount(int, String, double, double)
    +applyInterest()  void
}

class CheckingAccount {
    - overdraftLimit
    - double interestRate
    +CheckingAccount(int, String, double, double, double)
    +applyInterest()  void
}

BankAccount <|-- SavingsAccount : Is-a
BankAccount <|-- CheckingAccount : Is-a
</pre>

**Code**
```
<pre class="mermaid">
classDiagram
class BankAccount{
    -int id
    -String owner
    -Double balance
    +getOwner() String
    +setOwner(name) void
    +getBalance() Double
    +setBalance(amount) void

    +deposit(amount) bool
    +withdrawal(amount) int
    ~applyInterest() void
}

class SavingsAccount {
    - double interestRate
    +SavingsAccount(int, String, double, double)
    +applyInterest()  void
}

class CheckingAccount {
    - overdraftLimit
    - double interestRate
    +CheckingAccount(int, String, double, double, double)
    +applyInterest()  void
}

BankAccount <|-- SavingsAccount : Is-a
BankAccount <|-- CheckingAccount : Is-a

</pre>
```

### Visibility
To describe the visibility (or encapsulation) of an attribute or method/function that is a part of a class (i.e. a class member), optional notation may be placed before that members' name:

- `+` Public
- `-` Private
- `#` Protected
- `~` Package/Internal

> note you can also include additional classifiers to a method definition by adding the following notation to the end of the method, i.e.,: after the `()` or after the return type:

- `*` Abstract e.g.: `someAbstractMethod()*` or `someAbstractMethod() int*`
- `$` Static e.g.: `someStaticMethod()$` or `someStaticMethod() String$`

> note you can also include additional classifiers to a field definition by adding the following notation to the very end:

- `$` Static e.g.: `String someField$`

### Defining Relationship
A relationship is a general term covering the specific types of logical connections found on class and object diagrams.

`[classA][Arrow][ClassB]:LabelText` where `:LabelText` is optional.

There are eight different types of relations defined for classes under UML which are currently supported:

| **Type** | **Description** |
|:--------:|------  ---------|
| `<|--`   | Inheritance     |
| `*--`    | Composition     |
| `o--`    | Aggregation     |
| `-->`    | Association     |
| `--`     | Link (Solid)    |
| `..>`    | Dependency      | 
| `..|>`   | Realization     |
| `..`    | Link (Dashed)    |

<pre class="mermaid">
classDiagram
classA <|-- classB: Is-a
classC *-- classD: Composition
classE o-- classF: Aggregation
classG <-- classH: Association
classI -- classJ: (solid line)
classK <.. classL
classM <|.. classN
classO .. classP: (dashed line)
classA
classB
classC
classD
classE
classF
classG
classH
classI
classJ
</pre>

**Code:**
```
<pre class="mermaid">
classDiagram
classA <|-- classB: Is-a
classC *-- classD: Composition
classE o-- classF: Aggregation
classG <-- classH: Association
classI -- classJ: (solid line)
classK <.. classL
classM <|.. classN
classO .. classP: (dashed line)
classA
classB
classC
classD
classE
classF
classG
classH
classI
classJ
</pre>
```

## ER Diagram
An Entity-Relationship Diagram (ERD), is a visual representation used to describe the structure of a database. It is a conceptual tool used in database design to model the entities (objects, concepts, things) in a system and the relationships between them. The primary components of an ERM include:

1. **Entity:** An entity represents a real-world object, concept, or thing that can be uniquely identified. In a database context, entities typically correspond to tables. Each entity has attributes that describe the properties or characteristics of that entity. For example, in a database for a library, "Book," "Author," and "Library Member" could be entities.

2. **Attributes:** Attributes are the properties or characteristics of an entity. They describe what kind of data is associated with an entity. For a "Book" entity, attributes might include "Title," "Author," "ISBN," and "Publication Year."

3. **Relationships:** Relationships describe how entities are related to one another. They illustrate the associations between entities. For example, in a library database, a relationship might exist between "Library Member" and "Borrowed Book," indicating that a library member has borrowed a book.

4. **Cardinality:** Cardinality defines the number of instances of one entity that can be related to the number of instances of another entity through a particular relationship. Common cardinality notations include one-to-one (1:1), one-to-many (1:N), and many-to-many (N:M).

5. **Keys:** Keys are attributes or combinations of attributes that uniquely identify each instance of an entity. A primary key is the attribute or set of attributes that uniquely identifies an entity within a table.

See [Mermaid entity-relationshi diagrams](https://mermaid.js.org/syntax/entityRelationshipDiagram.html){: target="_blank"} for additional details.

<pre class="mermaid">
erDiagram

   PUBLISHER {
     PublisherId INT PK "Uniquly identifies publisher"
     Name VARCHAR(255)
   }
   PUBLISHER ||--o{ BOOK : publishes
   BOOK {
    VARCHAR(13) IsbnNumber PK "ISBN Number"
    VARCHAR(255) Title "Book title"
    VARCHAR(255) Author 
    INT PublicationYear 
    INT PublisherId FK
  }
  LIBRARY_MEMBER {
    INT MemberID PK
    VARCHAR(255) FirstName 
    VARCHAR(255) LastName
    VARCHAR(100) Email
  }
  BOOK |o--o{ BORROWED_BOOK : "is borrowed"
  LIBRARY_MEMBER |o--o{ BORROWED_BOOK : "is borrowed by"
  BORROWED_BOOK {
    INT BorrowedBookId PK
    VARCHAR(13) IsbnNumber FK "ISBN Number"
    INT MemberID FK
    DATE BorrowDate 
    DATE DueDate 
    DATE ReturnDate 
  }

</pre>

**Code**

```
<pre class="mermaid">
erDiagram

   PUBLISHER {
     INT PublisherId PK "Uniquly identifies publisher"
     VARCHAR(255) Name
   }
   PUBLISHER ||--o{ BOOK : publishes
   BOOK {
    VARCHAR(13) IsbnNumber PK "ISBN Number"
    VARCHAR(255) Title "Book title"
    VARCHAR(255) Author 
    INT PublicationYear 
    INT PublisherId FK
  }
  LIBRARY_MEMBER {
    INT MemberID PK
    VARCHAR(255) FirstName 
    VARCHAR(255) LastName
    VARCHAR(100) Email
  }
  BOOK |o--o{ BORROWED_BOOK : "is borrowed"
  LIBRARY_MEMBER |o--o{ BORROWED_BOOK : "is borrowed by"
  BORROWED_BOOK {
    INT BorrowedBookId PK
    VARCHAR(13) IsbnNumber FK "ISBN Number"
    INT MemberID FK
    DATE BorrowDate 
    DATE DueDate 
    DATE ReturnDate 
  }

</pre>
```

### Entities and Relationships

Each relationship statement consists of the following parts:

```
    <first-entity> [<relationship> <second-entity> : <relationship-label>]
```

Where:

- `first-entity` is the name of an entity. Names must begin with an alphabetic character or an underscore (from v10.5.0+), and may also contain digits and hyphens.
- `relationship` describes the way that both entities inter-relate. See below.
- `second-entity` is the name of the other entity.
- `relationship-label` describes the relationship from the perspective of the first entity.

For example:

```
    PROPERTY ||--|{ ROOM : contains
```

<pre class="mermaid">
erDiagram

  PROPERTY ||--|{ ROOM : contains
</pre>  


This statement can be read as _a property contains one or more rooms, and a room is part of one and only one property_. You can see that the label here is from the first entity's perspective: a property contains a room, but a room does not contain a property. When considered from the perspective of the second entity, the equivalent label is usually very easy to infer. 

Only the `first-entity` part of a statement is mandatory. This makes it possible to show an entity with no relationships, which can be useful during iterative construction of diagrams. If any other parts of a statement are specified, then all parts are mandatory.

### Relationship Syntax

The `relationship` part of each statement can be broken down into three sub-components:

- the cardinality of the first entity with respect to the second,
- whether the relationship confers identity on a 'child' entity
- the cardinality of the second entity with respect to the first

Cardinality is a property that describes how many elements of another entity can be related to the entity in question. In the above example a `PROPERTY` can have one or more `ROOM` instances associated to it, whereas a `ROOM` can only be associated with one `PROPERTY`. In each cardinality marker there are two characters. The outermost character represents a maximum value, and the innermost character represents a minimum value. The table below summarises possible cardinalities.

| Value (left) | Value (right) | Meaning                       |
| :----------: | :-----------: | ----------------------------- |
|    `|o`      |     `o|`      | Zero or one                   |
|    `||`      |     `||`      | Exactly one                   |
|    `}o`      |     `o{`      | Zero or more (no upper limit) |
|    `}|`      |     `|{`      | One or more (no upper limit)  |

<pre class="mermaid">
erDiagram
  EMPLOYEE ||--o| BADGE : "Exactly one to Zero or one"
  GROWTH_PLATFORM ||--|{ SERVICE_LINE : "1 to many"
  BOOK }|--|{ AUTHOR : "many to many"
</pre>


## State diagram
A state diagram is a type of diagram used in computer science and related fields to describe the behavior of systems. State diagrams require that the system described is composed of a finite number of states; sometimes, this is indeed the case, while at other times this is a reasonable abstraction.  See [Mermaid state diagram](https://mermaid.js.org/syntax/stateDiagram.html){: target="_blank"} for additional details.
<pre class="mermaid">
stateDiagram-v2
    [*] --> Active

    state Active {
        [*] --> NumLockOff
        NumLockOff --> NumLockOn : EvNumLockPressed
        NumLockOn --> NumLockOff : EvNumLockPressed
        --
        [*] --> CapsLockOff
        CapsLockOff --> CapsLockOn : EvCapsLockPressed
        CapsLockOn --> CapsLockOff : EvCapsLockPressed
        --
        [*] --> ScrollLockOff
        ScrollLockOff --> ScrollLockOn : EvScrollLockPressed
        ScrollLockOn --> ScrollLockOff : EvScrollLockPressed
    }
</pre>

**Code**
```
<pre class="mermaid">
stateDiagram-v2
    [*] --> Active

    state Active {
        [*] --> NumLockOff
        NumLockOff --> NumLockOn : EvNumLockPressed
        NumLockOn --> NumLockOff : EvNumLockPressed
        --
        [*] --> CapsLockOff
        CapsLockOff --> CapsLockOn : EvCapsLockPressed
        CapsLockOn --> CapsLockOff : EvCapsLockPressed
        --
        [*] --> ScrollLockOff
        ScrollLockOff --> ScrollLockOn : EvScrollLockPressed
        ScrollLockOn --> ScrollLockOff : EvScrollLockPressed
    }
</pre>
```

## Flowchart
Flowcharts are composed of nodes (geometric shapes) and edges (arrows or lines). The Mermaid code defines how nodes and edges are made and accommodates different arrow types, multi-directional arrows, and any linking to and from subgraphs. See [Mermaid flowchart diagrams](https://mermaid.js.org/syntax/flowchart.html){: target="_blank"} for additional details.

<pre class="mermaid">
flowchart LR
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}
    C -->|Yes| D[Result yes]
    C -->|No| E[Result no]
    click D href "https://www.github.com" _blank
</pre>

>Note: click on the "Result yes" node.

**Code**
```
<pre class="mermaid">
flowchart LR
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}
    C -->|Yes| D[Result yes]
    C -->|No| E[Result no]
    click D href "https://www.github.com" _blank
</pre>
```
**Other node types**
<pre class="mermaid">
%%{init: {"flowchart": {"htmlLabels": false}} }%%
flowchart LR
    markdown["`This **is** _Markdown_`"]
    newLines["`Line1
    Line 2
    Line 3`"]
    markdown --> newLines

    id1(text in box)
    id2a([text in rounded box])
    id2b[["`text in **subroutine** box`"]]
    id1 --> id2a
    id1 --> id2b

    id3[(Database)]
    id4((Circle))
    id5>asymmetric shape]
    id6{"`rhombus (**decision**)`"}
    id3 ==> id4 -.-> id5 -..-> id6

    node1{{Hexagon}}
    node2[/Parallelogram/]
    node3[\Parallelogram alt\]
    node4[/Trapazoid\]
    node5[\Trapazoid alt/]
    node1-->node2 & node3-->node4
    node4 --> node5
</pre>

**Code for other node types**
```
<pre class="mermaid">
%%{init: {"flowchart": {"htmlLabels": false}} }%%
flowchart LR
    markdown["`This **is** _Markdown_`"]
    newLines["`Line1
    Line 2
    Line 3`"]
    markdown --> newLines

    id1(text in box)
    id2a([text in rounded box])
    id2b[["`text in **subroutine** box`"]]
    id1 --> id2a
    id1 --> id2b

    id3[(Database)]
    id4((Circle))
    id5>asymmetric shape]
    id6{"`rhombus (**decision**)`"}
    id3 ==> id4 -.-> id5 -..-> id6

    node1{{Hexagon}}
    node2[/Parallelogram/]
    node3[\Parallelogram alt\]
    node4[/Trapazoid\]
    node5[\Trapazoid alt/]
    node1-->node2 & node3-->node4
    node4 --> node5
</pre>
```

## Gantt chart

A Gantt chart is a type of bar chart, first developed by Karol Adamiecki in 1896, and independently by Henry Gantt in the 1910s, that illustrates a project schedule and the amount of time it would take for any one project to finish. Gantt charts illustrate number of days between the start and finish dates of the terminal elements and summary elements of a project.  See [Mermaid gantt chart](https://mermaid.js.org/syntax/gantt.html){: target="_blank"} for additional details.

> Note: this diagram has zooming an panning enabled (covered later) for readability.

<div style="width: 100%; overflow-x: auto;">
    <pre class="mermaid svg-zoomable-content" id="gant-chart" style="width:  150%;">
    gantt
        dateFormat  YYYY-MM-DD
        title       Adding GANTT diagram functionality to mermaid
        excludes    weekends
        %% (`excludes` accepts specific dates in YYYY-MM-DD format, days of the week ("sunday") or "weekends", but not the word "weekdays".)

        section A section
        Completed task            :done,    des1, 2014-01-06,2014-01-08
        Active task               :active,  des2, 2014-01-09, 3d
        Future task               :         des3, after des2, 5d
        Future task2              :         des4, after des3, 5d

        section Critical tasks
        Completed task in the critical line :crit, done, 2014-01-06,24h
        Implement parser and jison          :crit, done, after des1, 2d
        Create tests for parser             :crit, active, 3d
        Future task in critical line        :crit, 5d
        Create tests for renderer           :2d
        Add to mermaid                      :1d
        Functionality added                 :milestone, 2014-01-25, 0d

        section Documentation
        Describe gantt syntax               :active, a1, after des1, 3d
        Add gantt diagram to demo page      :after a1  , 20h
        Add another diagram to demo page    :doc1, after a1  , 48h

        section Last section
        Describe gantt syntax               :after doc1, 3d
        Add gantt diagram to demo page      :20h
        Add another diagram to demo page    :48h
    </pre>
</div>
<button type="button" class="btn btn-primary" onclick="restoreSvg('gant-chart')">Reset zoom</button>
<button type="button" class="btn btn-primary" onclick="downloadSvg('gant-chart')">Download</button>
<button type="button" class="btn btn-primary" onclick="openSvg('gant-chart')">Open</button>

**Code**
```
<div style="width: 100%; overflow-x: auto;">
    <pre class="mermaid svg-zoomable-content" id="gant-chart" style="width:  150%;">
    gantt
        dateFormat  YYYY-MM-DD
        title       Adding GANTT diagram functionality to mermaid
        excludes    weekends
        %% (`excludes` accepts specific dates in YYYY-MM-DD format, days of the week ("sunday") or "weekends", but not the word "weekdays".)

        section A section
        Completed task            :done,    des1, 2014-01-06,2014-01-08
        Active task               :active,  des2, 2014-01-09, 3d
        Future task               :         des3, after des2, 5d
        Future task2              :         des4, after des3, 5d

        section Critical tasks
        Completed task in the critical line :crit, done, 2014-01-06,24h
        Implement parser and jison          :crit, done, after des1, 2d
        Create tests for parser             :crit, active, 3d
        Future task in critical line        :crit, 5d
        Create tests for renderer           :2d
        Add to mermaid                      :1d
        Functionality added                 :milestone, 2014-01-25, 0d

        section Documentation
        Describe gantt syntax               :active, a1, after des1, 3d
        Add gantt diagram to demo page      :after a1  , 20h
        Add another diagram to demo page    :doc1, after a1  , 48h

        section Last section
        Describe gantt syntax               :after doc1, 3d
        Add gantt diagram to demo page      :20h
        Add another diagram to demo page    :48h
    </pre>
</div>
```

## Quadrant chart

A quadrant chart is a visual representation of data that is divided into four quadrants. It is used to plot data points on a two-dimensional grid, with one variable represented on the x-axis and another variable represented on the y-axis. The quadrants are determined by dividing the chart into four equal parts based on a set of criteria that is specific to the data being analyzed. Quadrant charts are often used to identify patterns and trends in data, and to prioritize actions based on the position of data points within the chart. They are commonly used in business, marketing, and risk management, among other fields.  See [Mermaid quadrant chart](https://mermaid.js.org/syntax/quadrantChart.html){: target="_blank"} for additional details.

<pre class="mermaid">
quadrantChart
    title Reach and engagement of campaigns
    x-axis Low Reach --> High Reach
    y-axis Low Engagement --> High Engagement
    quadrant-1 We should expand
    quadrant-2 Need to promote
    quadrant-3 Re-evaluate
    quadrant-4 May be improved
    Campaign A: [0.3, 0.6]
    Campaign B: [0.45, 0.23]
    Campaign C: [0.57, 0.69]
    Campaign D: [0.78, 0.34]
    Campaign E: [0.40, 0.34]
    Campaign F: [0.35, 0.78]
</pre>

**Code**
```
<pre class="mermaid">
quadrantChart
    title Reach and engagement of campaigns
    x-axis Low Reach --> High Reach
    y-axis Low Engagement --> High Engagement
    quadrant-1 We should expand
    quadrant-2 Need to promote
    quadrant-3 Re-evaluate
    quadrant-4 May be improved
    Campaign A: [0.3, 0.6]
    Campaign B: [0.45, 0.23]
    Campaign C: [0.57, 0.69]
    Campaign D: [0.78, 0.34]
    Campaign E: [0.40, 0.34]
    Campaign F: [0.35, 0.78]
</pre>
```

## Pie chart
A pie chart (or a circle chart) is a circular statistical graphic, which is divided into slices to illustrate numerical proportion. In a pie chart, the arc length of each slice (and consequently its central angle and area), is proportional to the quantity it represents. While it is named for its resemblance to a pie which has been sliced, there are variations on the way it can be presented.  See [Mermaid pie chart](https://mermaid.js.org/syntax/pie.html){: target="_blank"} for additional details.

<pre class="mermaid">
%%{init: {"pie": {"textPosition": 0.5}, "themeVariables": {"pieOuterStrokeWidth": "5px"}} }%%
pie showData
    title Key elements in Product X
    "Calcium" : 42.96
    "Potassium" : 50.05
    "Magnesium" : 10.01
    "Iron" :  5
</pre>

**Code**
```
<pre class="mermaid">
%%{init: {"pie": {"textPosition": 0.5}, "themeVariables": {"pieOuterStrokeWidth": "5px"}} }%%
pie showData
    title Key elements in Product X
    "Calcium" : 42.96
    "Potassium" : 50.05
    "Magnesium" : 10.01
    "Iron" :  5
```

## Regular zoom

To enable a zoom effect on images within your markup when hovering over them, specify the `zoom` class.  For example,
```
<pre class="mermaid zoom">
   ...
```
<pre class="mermaid zoom">
%%{init: {"pie": {"textPosition": 0.5}, "themeVariables": {"pieOuterStrokeWidth": "5px"}} }%%
pie showData
    title Key elements in Product X
    "Calcium" : 42.96
    "Potassium" : 50.05
    "Magnesium" : 10.01
    "Iron" :  5
</pre>

For non-mermaid images, add `{: class="zoom"}` after specifying the image name.
```
![The San Juan Mountains are beautiful!]
    ({{ site.baseurl }}/assets/images/san-juan-mountains.jpg){: class="zoom"}
```
![The San Juan Mountains are beautiful!]({{ site.baseurl }}/assets/images/san-juan-mountains.jpg){: class="zoom"}



## Panning and zooming
Panning and zooming are popular interaction techniques which let the user focus on a region of interest by restricting the view. It is easy to use due to direct manipulation: click-and-drag to pan (translate), spin the wheel to zoom (scale), or use touch. 

Mermaid.js library itself doesn't provide built-in zoom or pan functionality for the diagrams it generates. Mermaid.js is primarily focused on creating static diagrams for visualization and documentation.  To implement zoom and pan functionality for Mermaid diagrams, the WFM documentation tool uses [**D3.js**](https://d3js.org/){:target="_blank"} to handle the zoom and pan features with the Mermaid-generated SVG.  D3 provides a module `d3.zoom` is a flexible abstraction that adds zoom and pan behaviour to an HTML or SVG element. 


### Setting an diagram to zoom and pan

To enable a diagram to be able to zoom and pan add the following attributes to the `<pre>` tag:
1. `class="svg-zoomable-content"`
1. `id` with a unique value

For example, adding the `svg-zoomable-content` class and providing a unique id for the `<pre>` element, the reader can zoom in or out or move/pan the generated diagram.

```
<pre class="mermaid svg-zoomable-content" id="e-r-diagram">
classDiagram
class BankAccount{
    -int id
    -String owner
    -Double balance
    +getOwner() String
    +setOwner(name) void
    +getBalance() Double
    +setBalance(amount) void

    +deposit(amount) bool
    +withdrawal(amount) int
    ~applyInterest() void
}

class SavingsAccount {
    - double interestRate
    +SavingsAccount(int, String, double, double)
    +applyInterest()  void
}

class CheckingAccount {
    - overdraftLimit
    - double interestRate
    +CheckingAccount(int, String, double, double, double)
    +applyInterest()  void
}

BankAccount <|-- SavingsAccount : Is-a
BankAccount <|-- CheckingAccount : Is-a
</pre>
```

Try zooming and moving the diagram below.

<pre class="mermaid svg-zoomable-content" id="e-r-diagram">
classDiagram
class BankAccount{
    -int id
    -String owner
    -Double balance
    +getOwner() String
    +setOwner(name) void
    +getBalance() Double
    +setBalance(amount) void

    +deposit(amount) bool
    +withdrawal(amount) int
    ~applyInterest() void
}

class SavingsAccount {
    - double interestRate
    +SavingsAccount(int, String, double, double)
    +applyInterest()  void
}

class CheckingAccount {
    - overdraftLimit
    - double interestRate
    +CheckingAccount(int, String, double, double, double)
    +applyInterest()  void
}

BankAccount <|-- SavingsAccount : Is-a
BankAccount <|-- CheckingAccount : Is-a
</pre>
<button type="button" class="btn btn-primary" onclick="restoreSvg('e-r-diagram')">Reset zoom</button>
<button type="button" class="btn btn-primary" onclick="downloadSvg('e-r-diagram')">Download</button>
<button type="button" class="btn btn-primary" onclick="openSvg('e-r-diagram')">Open</button>

### Exposed functions

The framework exposes some functions that can be accessed programmatically.

| **#**  | **Function**   | **Parameters**    | **Description** |
|-------:|----------------|-------------------|-----------------|
|     1. | restoreSvg     | image id assigned | Restores the image size and position to their original value |
|     2. | downloadSvg    | image id assigned | Downloads the image/svg with the file name <image-id>.svg.   |
|     3. | openSvg        | image id assigned | Opens the image in its own stand-alnoe page.   |

For example you'll notice the **Reset zoom**, **Download**, and **Open** buttons. These buttons were added with the following code:

<pre name="code" class="javascript">
<button type="button" class="btn btn-primary" onclick="restoreSvg('e-r-diagram')">Reset zoom</button>
<button type="button" class="btn btn-primary" onclick="downloadSvg('e-r-diagram')">Download</button>
<button type="button" class="btn btn-primary" onclick="openSvg('e-r-diagram')">Open</button>
</pre>
### Container and image/svg size

By default, the image is scaled to fit 100% of the width of its container. The height is then scaled accordingly. For example, below is ER Diagram for the product (Unified Taxonomy (UT)) and skills (Job Role Specialty (JRS)) taxonomies. You can see that the width of the image is scaled down to fit the container it is being displayed in, but the height expands down the page.

<pre class="mermaid svg-zoomable-content" id="ut-jrs-taxonomy">
erDiagram
  BRAND_DIM {
     BRAND_ID	INTEGER 	PK	"Surrogate key for REFT.BRAND_DIM." 
     BRAND_CD	CHAR(8) "Brand code." 
     BRAND_NM	VARCHAR(255) "Brand name (short description)."
     BRAND_DESC	VARCHAR(255) "Brand description."
  }
  GROWTH_PLATFORM_DIM {
     GROWTH_PLATFORM_ID	INTEGER 	PK	"Surrogate key for REFT.GROWTH_PLATFORM_DIM." 
     GROWTH_PLATFORM_CD	CHAR(8) "Growth Platform code."
     GROWTH_PLATFORM_NM	VARCHAR(255) "Growth Platform name (short description)." 
     GROWTH_PLATFORM_DESC	VARCHAR(255) "Growth Platform long description." 
     BRAND_CD	CHAR(8) FK  "Brand code, Foreign Key." 
  }
  BRAND_DIM ||--|{ GROWTH_PLATFORM_DIM : contains
  SERVICE_LINE_DIM {
     SERVICE_LINE_ID	INTEGER 	PK	"Surrogate key for REFT.SERVICE_LINE_DIM." 
     SERVICE_LINE_CD	CHAR(8) "Service Line code." 
     SERVICE_LINE_NM	VARCHAR(255) "Service Line name (short description)." 
     SERVICE_LINE_DESC	VARCHAR(255) "Service Line long description." 
     GROWTH_PLATFORM_CD	CHAR(8) FK "Growth Platform code, Foreign Key." 
  }
  GROWTH_PLATFORM_DIM ||--|{ SERVICE_LINE_DIM : contains
  PRACTICE_DIM {
     PRACTICE_ID	INTEGER 	PK	"Surrogate key for REFT.PRACTICE_DIM." 
     PRACTICE_CD	CHAR(8) "Practice code." 
     PRACTICE_NM	VARCHAR(255) "Practice name (short description)." 
     PRACTICE_DESC	VARCHAR(255) "Practice long description." 
     ECONOMIC_MODEL_CD	CHAR(2) "Economic Model Code." 
     ACCEL_PRACTICE_IND	CHAR(1) "Accelerated Practice Indicator." 
     SERVICE_LINE_CD	CHAR(8) FK "Service Line code, Foreign Key." 
  }
  SERVICE_LINE_DIM ||--|{ PRACTICE_DIM : contains
  OFFERING_PORTFOLIO_DIM {
     OFFERING_PORTFOLIO_ID	INTEGER 	PK	"Surrogate key for REFT.OFFERING_PORTFOLIO_DIM." 
     OFFERING_PORTFOLIO_CD	CHAR(8) "Offering Portfolio code (UTL20 Code)." 
     OFFERING_PORTFOLIO_NM	VARCHAR(255) "Offering Portfolio name (short description)." 
     OFFERING_PORTFOLIO_DESC	VARCHAR(255) "Offering Portfolio long description." 
     SERVICE_LINE_CD	CHAR(8) FK "Service Line code, Foreign Key."
  }
  SERVICE_LINE_DIM ||--|{ OFFERING_PORTFOLIO_DIM : contains
  OFFERING_DIM {
     OFFERING_ID	INTEGER 	PK	"Surrogate key for REFT.OFFERING_DIM." 
     OFFERING_CD	CHAR(8) "Offering code (UTL30 Code)." 
     OFFERING_NM	VARCHAR(255) "Offering name (short description)." 
     OFFERING_DESC	VARCHAR(255) "Offering long description." 
     LEAD_PRACTICE_CD	CHAR(8) 
     LEAD_PRACTICE_NM	VARCHAR(255)
     FINANCIAL_OFFERING_ATTRIBUTE_NM	VARCHAR(255)
     OFFERING_PORTFOLIO_CD	CHAR(8) FK "Offering Portfolio code, Foreign Key."
  }
  OFFERING_PORTFOLIO_DIM ||--|{ OFFERING_DIM  : contains
  SERVICE_AREA_DIM {
     SERVICE_AREA_ID	INTEGER 	PK	"Surrogate key for REFT.SERVICE_AREA_DIM." 
     SERVICE_AREA_CD	CHAR(8) "Service Area code." 
     SERVICE_AREA_NM	VARCHAR(255) "Service Area name (short description)." 
     SERVICE_AREA_DESC	VARCHAR(255) "Service Area description." 
     PRACTICE_CD	CHAR(8) FK "Practice code, Foreign Key." 
  }
  PRACTICE_DIM ||--|{ SERVICE_AREA_DIM : contains
  JRS_DIM {
     JRS_ID	INTEGER 	PK	"Surrogate key for REFT.JRS_DIM." 
     JRS_CD	CHAR(17) "Job Role code." 
     JRS_NM	VARCHAR(255) "Job Role name (short description)." 
     JRS_DESC	VARCHAR(255) "Job Role name (short description)." 
     JOB_ROLE_CD	CHAR(8) "Job Role code." 
     JOB_ROLE_NM	VARCHAR(255) "Job Role name (short description)." 
     SPECIALTY_CD	CHAR(8) "Specialty code."
     SPECIALTY_NM	VARCHAR(255) "Specialty  name (short description)." 
     SERVICE_AREA_CD	CHAR(8) "Service Area code, Foreign Key." 
     CMPNSTN_GRD_LST	VARCHAR(64) "Compensation Grade List." 
     INCENTIVE_FLG	CHAR(1) 
  }
  SERVICE_AREA_DIM ||--|{ JRS_DIM : contains
  PRACTICE_DIM ||--|{ OFFERING_DIM : has
</pre>  
<button type="button" class="btn btn-primary" onclick="restoreSvg('ut-jrs-taxonomy')">Reset zoom</button>
<button type="button" class="btn btn-primary" onclick="downloadSvg('ut-jrs-taxonomy')">Download</button>
<button type="button" class="btn btn-primary" onclick="openSvg('ut-jrs-taxonomy')">Open</button>

Below is a sequence diagram for `git fetch`. Note that all requests pass through `NGINX`, `Workhorse` (a reverse proxy used by GitLab to offload some of the heavy work), and `Gitaly` (Git RPC (Remote Procedure Call) service that separates the Git operations from the main application server). The diagram is an example of a wide diagram being displayed within a limited area:

<pre class="mermaid svg-zoomable-content" id="sequence-diagram-1" >
  sequenceDiagram
      participant Git on client
      participant NGINX
      participant Workhorse
      participant Rails
      participant Gitaly
      participant Git on server

      Note left of Git on client: git fetch<br/>info-refs
      Git on client->>+Workhorse: GET /info/refs?service=git-upload-pack
      Workhorse->>+Rails: GET /info/refs?service=git-upload-pack
      Note right of Rails: Auth check
      Rails-->>-Workhorse: Gitlab::Workhorse.git_http_ok
      Workhorse->>+Gitaly: SmartHTTPService.InfoRefsUploadPack request
      Gitaly->>+Git on server: git upload-pack --stateless-rpc --advertise-refs
      Git on server-->>-Gitaly: git upload-pack response
      Gitaly-->>-Workhorse: SmartHTTPService.InfoRefsUploadPack response
      Workhorse-->>-Git on client: 200 OK

      Note left of Git on client: git fetch<br/>fetch-pack
      Git on client->>+Workhorse: POST /git-upload-pack
      Workhorse->>+Rails: POST /git-upload-pack
      Note right of Rails: Auth check
      Rails-->>-Workhorse: Gitlab::Workhorse.git_http_ok
      Workhorse->>+Gitaly: SmartHTTPService.PostUploadPack request
      Gitaly->>+Git on server: git upload-pack --stateless-rpc
      Git on server-->>-Gitaly: git upload-pack response
      Gitaly-->>-Workhorse: SmartHTTPService.PostUploadPack response
      Workhorse-->>-Git on client: 200 OK
</pre>
<button type="button" class="btn btn-primary" onclick="restoreSvg('sequence-diagram-1')">Reset zoom</button>
<button type="button" class="btn btn-primary" onclick="downloadSvg('sequence-diagram-1')">Download</button>
<button type="button" class="btn btn-primary" onclick="openSvg('sequence-diagram-1')">Open</button>

Of course the reader can zoom, pan, and/or open the image in its own window, but the author has other options.

Unfortunately the Mermaid library does not inherently provide an option to generate diagrams larger than the container size. Mermaid renders diagrams within the constraints of the container in which it is placed.  However, you can achieve a larger diagram by adjusting the container size or applying custom styles to the generated SVG. 

For example, you could adjust the width of the container. For example adding `style="width:150%"` to the `<pre>` HTML element, appllies an inline style that sets the width of the element to be 150% of its containing element's width. This expands to image but will overflow into the next adjacent area of the page. 
```
<pre class="mermaid svg-zoomable-content" id="sequence-diagram-2" style="width:150%" >
```
Results in:
<pre class="mermaid svg-zoomable-content" id="sequence-diagram-2" style="width:150%" >
  sequenceDiagram
      participant Git on client
      participant NGINX
      participant Workhorse
      participant Rails
      participant Gitaly
      participant Git on server

      Note left of Git on client: git fetch<br/>info-refs
      Git on client->>+Workhorse: GET /info/refs?service=git-upload-pack
      Workhorse->>+Rails: GET /info/refs?service=git-upload-pack
      Note right of Rails: Auth check
      Rails-->>-Workhorse: Gitlab::Workhorse.git_http_ok
      Workhorse->>+Gitaly: SmartHTTPService.InfoRefsUploadPack request
      Gitaly->>+Git on server: git upload-pack --stateless-rpc --advertise-refs
      Git on server-->>-Gitaly: git upload-pack response
      Gitaly-->>-Workhorse: SmartHTTPService.InfoRefsUploadPack response
      Workhorse-->>-Git on client: 200 OK

      Note left of Git on client: git fetch<br/>fetch-pack
      Git on client->>+Workhorse: POST /git-upload-pack
      Workhorse->>+Rails: POST /git-upload-pack
      Note right of Rails: Auth check
      Rails-->>-Workhorse: Gitlab::Workhorse.git_http_ok
      Workhorse->>+Gitaly: SmartHTTPService.PostUploadPack request
      Gitaly->>+Git on server: git upload-pack --stateless-rpc
      Git on server-->>-Gitaly: git upload-pack response
      Gitaly-->>-Workhorse: SmartHTTPService.PostUploadPack response
      Workhorse-->>-Git on client: 200 OK
</pre>

<button type="button" class="btn btn-primary" onclick="restoreSvg('sequence-diagram-2')">Reset zoom</button>
<button type="button" class="btn btn-primary" onclick="downloadSvg('sequence-diagram-2')">Download</button>
<button type="button" class="btn btn-primary" onclick="openSvg('sequence-diagram-2')">Open</button>

To prevent the overflow you can wrap the `<pre>` element (the Mermaid diagram) within a `<div>` with the style `width: 100%; overflow-x: auto;`
```
<div style="width: 100%; overflow-x: auto;">
    <pre class="mermaid svg-zoomable-content" id="sequence-diagram-3" style="width: 150%;">
       .. Mermaid diagram ...
    </pre>
</div>
```
This would have the following implications:

1. **`width: 100%;`:** The `<div>` will take up 100% of the width of its containing element. If there's no explicit width set on the parent element, it will take up 100% of the available width.

2. **`overflow-x: auto;`:** This CSS property specifies how the content should behave when it overflows the content box horizontally. In this case, when the content inside the `<div>` exceeds its specified width, a horizontal scrollbar will appear, allowing the user to scroll horizontally to see the hidden content.

For example:

<div style="width: 100%; overflow-x: auto;">
    <pre class="mermaid svg-zoomable-content" id="sequence-diagram-3" style="width: 150%;">
      sequenceDiagram
          participant Git on client
          participant NGINX
          participant Workhorse
          participant Rails
          participant Gitaly
          participant Git on server

          Note left of Git on client: git fetch<br/>info-refs
          Git on client->>+Workhorse: GET /info/refs?service=git-upload-pack
          Workhorse->>+Rails: GET /info/refs?service=git-upload-pack
          Note right of Rails: Auth check
          Rails-->>-Workhorse: Gitlab::Workhorse.git_http_ok
          Workhorse->>+Gitaly: SmartHTTPService.InfoRefsUploadPack request
          Gitaly->>+Git on server: git upload-pack --stateless-rpc --advertise-refs
          Git on server-->>-Gitaly: git upload-pack response
          Gitaly-->>-Workhorse: SmartHTTPService.InfoRefsUploadPack response
          Workhorse-->>-Git on client: 200 OK

          Note left of Git on client: git fetch<br/>fetch-pack
          Git on client->>+Workhorse: POST /git-upload-pack
          Workhorse->>+Rails: POST /git-upload-pack
          Note right of Rails: Auth check
          Rails-->>-Workhorse: Gitlab::Workhorse.git_http_ok
          Workhorse->>+Gitaly: SmartHTTPService.PostUploadPack request
          Gitaly->>+Git on server: git upload-pack --stateless-rpc
          Git on server-->>-Gitaly: git upload-pack response
          Gitaly-->>-Workhorse: SmartHTTPService.PostUploadPack response
          Workhorse-->>-Git on client: 200 OK
    </pre>
</div>
<button type="button" class="btn btn-primary" onclick="restoreSvg('sequence-diagram-3')">Reset zoom</button>
<button type="button" class="btn btn-primary" onclick="downloadSvg('sequence-diagram-3')">Download</button>
<button type="button" class="btn btn-primary" onclick="openSvg('sequence-diagram-3')">Open</button>

## Other Diagrams

=== "Environments"

<div style="width: 100%; overflow-x: auto;">
    <pre class="mermaid svg-zoomable-content" id="graph-td" style="width: 150%;">
graph TD
subgraph Environments
    subgraph Development [Development: <a href='https://github.ibm.com/consulting-sidekick/scribeflow'>main</a> - dev use only]
        subgraph DEV[CIRRUS GHE <a href='https://cirrus.ibm.com/projects/d17ccc00-7058-4853-a48e-7faaf32c44e3/pipelines'>Pipelines</a>, autodeploy from main]
            scribeflow --> weaviate[(Weaviate<br/>1 vCPU, 1GB)]
            weaviate --> weaviate-storage(weaviate-storage<br/>OCS 5GB)
            scribeflow([<a href='https://scribeflow-dev.wdc1a.ciocloud.nonprod.intranet.ibm.com'>ScribeFlow Dev</a><br/> Retrieval Augmented Generation<br/> 1 x 2vCPU, 4GB]) --> mongo[(MongoDB<br/> 0.5 vCPU, 0.5GB)]
            mongo --> mongo-storage(mongo-storage<br/>OCS 5GB)
            thumbsup([<a href='https://thumbsup.wdc1a.ciocloud.nonprod.intranet.ibm.com'>ThumbsUp Dev</a><br/>Model Testing<br/> 0.5vCPU, 0.5GB]) --> postgres[(PostgreSQL<br/> 0.5 vCPU, 0.5GB)]
            postgres --> postgres-storage(postgres-storage<br/>OCS 5GB)
        end

    end

    subgraph Testing [Testing: <a href='https://github.ibm.com/consulting-sidekick/scribeflow/tree/stable'>stable</a> - Shared with testers]
        subgraph TEST[CIRRUS deploy from stable, at end of sprint]
            scribeflow-test([<a href='https://sidekick-api-test.wdc1a.ciocloud.nonprod.intranet.ibm.com/apidocs/#/'>ScribeFlow Test</a><br/> Retrieval Augmented Generation<br/>4 x 2vCPU, 3GB]) --> weaviate-test[(Weaviate on IBM Cloud from Luis <br/>)]
        end
    end

    subgraph Production [Production: <a href='https://github.ibm.com/consulting-sidekick/scribeflow/tags'>release</a> - Sidekick only]
        PROD(Production - Manualy Deployment, release branch)
    end
end
</pre>
</div>
<button type="button" class="btn btn-primary" onclick="restoreSvg('graph-td')">Reset zoom</button>
<button type="button" class="btn btn-primary" onclick="downloadSvg('graph-td')">Download</button>
<button type="button" class="btn btn-primary" onclick="openSvg('graph-td')">Open</button>

== Top Down (TD) vs Left Right (LR)
<pre class='mermaid'>
graph TD;
        subgraph DEV[CIRRUS GHE <a href='https://cirrus.ibm.com/projects/d17ccc00-7058-4853-a48e-7faaf32c44e3/pipelines'>Pipelines</a>, autodeploy from main]
            scribeflow --> weaviate[(Weaviate<br/>1 vCPU, 1GB)]
            weaviate --> weaviate-storage(weaviate-storage<br/>OCS 5GB)
            scribeflow([<a href='https://scribeflow-dev.wdc1a.ciocloud.nonprod.intranet.ibm.com'>ScribeFlow Dev</a><br/> Retrieval Augmented Generation<br/> 1 x 2vCPU, 4GB]) --> mongo[(MongoDB<br/> 0.5 vCPU, 0.5GB)]
            mongo --> mongo-storage(mongo-storage<br/>OCS 5GB)
            thumbsup([<a href='https://thumbsup.wdc1a.ciocloud.nonprod.intranet.ibm.com'>ThumbsUp Dev</a><br/>Model Testing<br/> 0.5vCPU, 0.5GB]) --> postgres[(PostgreSQL<br/> 0.5 vCPU, 0.5GB)]
            postgres --> postgres-storage(postgres-storage<br/>OCS 5GB)
        end

            subgraph TEST[CIRRUS deploy from stable, at end of sprint]
                scribeflow-test([<a href='https://sidekick-api-test.wdc1a.ciocloud.nonprod.intranet.ibm.com/apidocs/#/'>ScribeFlow Test</a><br/> Retrieval Augmented Generation<br/>4 x 2vCPU, 3GB]) --> weaviate-test[(Weaviate on IBM Cloud from Luis <br/>)]
            end

</pre>

<pre class='mermaid'>
graph TD;
subgraph My Subgraph
    A-->B;
    A-->C;
    B-->D;
    C-->D;
end
subgraph My Sub-Subgraph
    E-->F;
    E-->G;
    F-->H;
    G-->H;
end
</pre>

=== "Development and Test Architecture"

<pre class='mermaid'>
flowchart TB
    style IBMUser fill:blue,stroke-width:4px
    style Slack fill:blue,stroke-width:4px
    style scribeflow fill:darkred,stroke-width:4px
    style scribeflow-load fill:darkred,stroke-width:4px
    style scribeflow-ui fill:darkred,stroke-width:4px
    style scribeflow-cli fill:darkred,stroke-width:4px
    style weaviate fill:teal,stroke-width:4px
    style weaviate fill:teal,stroke-width:4px
    style bam fill:darkblue,stroke-width:4px
    style Sidekick fill:green,stroke:#333,stroke-width:4px


    subgraph corpus
        IBV
        Bluebook
        Archetypes
        Lighthouse
        Assets
        Journeys
        Trainings
    end
    corpus -.-> scribeflow-load

    subgraph clients[<font size=3>End-User Applications]
        scribeflow-cli[scribeflow\nCLI]
        IBMUser((IBM User\nBrowser))
        Slack((Slack Bot))
    end

    subgraph cicd [CICD]
        jenkins
        travis[TravisCI\npytest coverage\ndoc build]-->github-pages[GitHub Pages\nDocumentation\nTest Coverage]
        github-->travis
        github[github.ibm.com\nconsulting-sidekick/scribeflow]<-->jenkins
    end

    subgraph ocp [IKS MZR]
        Slack((Slack Bot))-->|https|istio
        IBMUser((IBM User\nBrowser))-->|https|istio
        istio-->|https|gateway
        gateway<-->|ID token|keycloak[(Keycloak\nIdentity Management)]
        scribeflow-cli[scribeflow\nCLI]-->istio
        gateway-->scribeflow-ui[Development\n& Management UI]
        gateway-->scribeflow
        gateway-->scribeflow-load
        keycloak
        scribeflow-ui-->|REST|scribeflow{{<a href='https://scribeflow-dev.wdc1a.ciocloud.nonprod.intranet.ibm.com/apidocs/'>scribeflow</a>\nquery,schema}}
        scribeflow-ui-->|REST|scribeflow-load{{scribeflow\nconvert\ningest}}
        scribeflow-->|REST|weaviate[(Weaviate\n Vector Store\nDatabase\nDEV: 1 node\nPROD: 3 Replicas + 3 Shards)]
        scribeflow-load-->weaviate
    end

    scribeflow-load-..-sources
    subgraph ibm [IBM Consumer Applications]
        FASTEN[[Fast AI Solutioning\ncurrently an POC]]-->|REST|istio
        Sidekick><b><a href='https://ocp2.cloud.boomerangplatform.net/qa/curatorai/apps/ui'>IBM Consulting Sidekick AI</a>\nIntegrated in Dev</b>]-->|REST|istio
        scribeflow-cli[scribeflow\nCLI]-.->|bulk load|weaviate
    end

    subgraph sources [IBM Systems]
        scribeflow-->bam[watsonx.ai\nbam.res.ibm.com]
        LighthouseAPI[Lighthouse API]
        Box
    end

    subgraph ibmcloud [IBM Cloud VPC]
        secrets[Secrets Manager]
        ocp-->secrets
        weaviate-->secrets
        database[(Data Lakehouse\nJSON Documents)] --Spark-->weaviate
        ocp --> iccr[(ICCR Registry)]
        weaviate-->COS[(COS backup)]
        weaviate-->File[(File Storage)]
        jenkins[Jenkins\npytest\npodman build, skopeo]-->iccr
    end
</pre>