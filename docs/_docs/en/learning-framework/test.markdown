---
title: Test
permalink: /en/learning-framework/test
features:
  - mermaid
  - d3
abstract: >- # this means to ignore newlines until "baseurl:"
  Mermaid is a JavaScript-based diagramming and charting tool that uses Markdown-inspired text definitions and a renderer to create and modify complex diagrams. 
---



Diagramming and documentation costs precious developer time and gets outdated quickly. But not having diagrams or docs ruins productivity and hurts organizational learning. [Mermaid](https://mermaid.js.org/){: target="_blank"} addresses this problem by enabling users to create easily modifiable diagrams. It can also be made part of production scripts (and other pieces of code).

## Sequence Diagram
A Sequence diagram is an interaction diagram that shows how processes operate with one another and in what order. See [Mermaid sequence diagrams](https://mermaid.js.org/syntax/sequenceDiagram.html){: target="_blank"} for additional details.

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
     INT PublisherId PK "Uniquly identifies publisher"
     VARCHA(255) Name
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
     VARCHA(255) Name
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

## Gantt chart

A Gantt chart is a type of bar chart, first developed by Karol Adamiecki in 1896, and independently by Henry Gantt in the 1910s, that illustrates a project schedule and the amount of time it would take for any one project to finish. Gantt charts illustrate number of days between the start and finish dates of the terminal elements and summary elements of a project.  See [Mermaid gantt chart](https://mermaid.js.org/syntax/gantt.html){: target="_blank"} for additional details.

<pre class="mermaid">
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

**Code**
```
<pre class="mermaid">
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

## Adding a huge diagram

<pre class="mermaid">
classDiagram
class KyndrylDaoService {
  -Class t
  -String tableNm
  -String scdTableNm
  -BridgeDatasourceProperties bridgeProp
  +Connection getConnection()
}
KyndrylDaoService --|> AbstractDaoService: inherits
class DaoArtifactGeneratorService {
  -FileStorageProperties fileStorageProperties
  +Connection getConnection()
  +List generateArtifcat(int, java.lang.String, java.lang.String, java.lang.String)
}
</pre>


<pre class="mermaid">
classDiagram
class KyndrylDaoService {
  -Class t
  -String tableNm
  -String scdTableNm
  -BridgeDatasourceProperties bridgeProp
  +Connection getConnection()
}
KyndrylDaoService --|> AbstractDaoService: inherits
class DaoArtifactGeneratorService {
  -FileStorageProperties fileStorageProperties
  +Connection getConnection()
  +List generateArtifcat(int, java.lang.String, java.lang.String, java.lang.String)
}
DaoArtifactGeneratorService --|> AbstractDaoService: inherits
class DynamicSqlService {
  -Class t
  -String tableNm
  -String scdTableNm
  -BridgeDatasourceProperties bridgeProp
  +Connection getConnection()
}
DynamicSqlService --|> AbstractDaoService: inherits
class EdsDaoService {
  -Class t
  -String tableNm
  -String scdTableNm
  -BridgeDatasourceProperties bridgeProp
  +Connection getConnection()
}
EdsDaoService --|> AbstractDaoService: inherits
class FileSortService {
  +String sort(java.lang.String)
  +String sort(java.lang.String, java.lang.String)
}
class DaoInterface {
&lt;&lt;interface&gt;&gt;
&lt;&lt;abstract&gt;&gt;
  +Connection getConnection()
}
class ShortListDaoService {
  -Class t
  -String tableNm
  -String scdTableNm
  -BridgeDatasourceProperties bridgeProp
  +Connection getConnection()
  +List getShortListFromExcel(java.lang.String, java.lang.String)
}
ShortListDaoService --|> AbstractDaoService: inherits
class FileStorageService {
  -Path fileStorageLocation
  +Resource loadFileAsResource(java.lang.String)
  +String storeFile(org.springframework.web.multipart.MultipartFile)
}
class RahEtlDaoService {
  -Class t
  -String tableNm
  -String scdTableNm
  -RahEtlDatasourceProperties rahProp
  -FileStorageProperties fileStorageProperties
  +Connection getConnection()
}
RahEtlDaoService --|> AbstractDaoService: inherits
class ErdmDaoService {
  -Class t
  -String tableNm
  -String scdTableNm
  -ErdmDatasourceProperties erdmProp
  +Connection getConnection()
}
ErdmDaoService --|> AbstractDaoService: inherits
class CertificationDaoService {
  -Wf360DatasourceProperties wf360Prop
  -BridgeDatasourceProperties bridgeProp
  +List findAll()
  +int insertAll(java.util.List)
  +int deleteAll()
}
class JrsMapperService {
  -int PRACTICE_LVL$
  -int SERVICE_AREA_LVL$
  -int JRS_LVL$
  -int PRACTICE_NM$
  -int SERVICE_AREA_NM$
  -int JRS_NM$
  -int ID_NAME$
  -int ID_CNUM$
  -int ID_JOB_ROLE_SPECIALTY$
  -int ID_LABOR_GROUP$
  -int ID_GEOGRAPHY_TYPE$
  -int ID_GEOGRAPHY$
  -int ID_MARKET$
  -int ID_MARKET_REGION$
  -int ID_COUNTRY$
  -int ID_COMPANY$
  -int ID_BMDIV$
  -int ID_DIVISION$
  -int ID_CIC_CENTER_GROUP$
  -int ID_CIC_CENTER$
  -int ID_GROWTH_PLATFORM$
  -int ID_SERVICE$
  -int ID_PRACTICE$
  -int ID_SERVICE_AREA$
  -int ID_SECTOR$
  -int ID_INDUSTRY$
  -int ID_EBU_CODE$
  -int ID_FIN_DEPT_ID$
  -int ID_DEPT_CAT_CODE$
  -int ID_HR_ORG_CODE$
  -int ID_HR_DEPT$
  -int ID_DEPARTMENT_NAME$
  -int ID_EMF_STATUS$
  -int ID_BAND$
  -int ID_BILLABLE$
  -int ID_JR_S_SERVICE$
  -int ID_JR_S_PRACTICE$
  -int ID_JR_S_SERVICE_AREA$
  -int ID_CAPACITY_GROUP$
  -int ID_ISO_CTRY_CD$
  -int ID_LOB_CD$
  -int ID_FA_CD$
  -int ID_CHRG_GRP_CD$
  -int ID_DPT_MAJR_CD$
  -int ID_LCL_DPT_GRP_1_NM$
  -int ID_LCL_DPT_GRP_2_NM$
  -int ID_LCL_DPT_GRP_3_NM$
  -int ID_MGR_INET_EMAIL_ID$
  -int ID_MGR_LVL2_INET_EMAIL_ID$
  -int ID_MGR_LVL3_INET_EMAIL_ID$
  -int ID_MGR_NOTES_EMAIL_ID$
  -int ID_MGR_LVL2_NOTES_EMAIL_ID$
  -int ID_MGR_LVL3_NOTES_EMAIL_ID$
  -int ID_MGR_FLG$
  -int ID_RSA_NOTES_EMAIL_ID$
  -int ID_LBR_POOL_LVL_1_NM$
  -int ID_LBR_POOL_LVL_2_NM$
  -int ID_BMS_CTRY_CD$
  -int ID_INET_EMAIL_ID$
  -int ID_CTRY_CMPNY_NM$
  -ArrayList emeaMarketList$
  -boolean debug$
  -boolean addLi$
  -List jrss
  +void main([Ljava.lang.String;)$
  -JrsMapperResponse map(java.lang.String, java.lang.String, java.util.ArrayList, java.util.ArrayList, [I, [I, java.lang.String)
  +ArrayList buildServiceAreaMapFromFile(java.lang.String, java.lang.String)
  +String toStringDetailServiceAreaMatch(int, [Ljava.lang.String;, [I, com.ibm.wfm.beans.ServiceAreaMapNode, java.util.ArrayList, int, boolean)
  +String toStringDetailPracticeMatch(int, [Ljava.lang.String;, [I, com.ibm.wfm.beans.ServiceAreaMapNode, java.util.ArrayList, int, boolean)
  +int[] parseIntegerList(java.lang.String)$
  +JrsMapperResponse mapFromFile(java.lang.String, java.lang.String, java.lang.String, java.lang.String, [I, [I, java.lang.String)
  +ArrayList buildJrsMapFromFile(java.lang.String, java.lang.String)
  +String toStringHeader([Ljava.lang.String;, [I)
  +String[] getBranchKeys([Ljava.lang.String;, [I)
  +JrsMapNode findFullKey([Ljava.lang.String;, java.util.ArrayList)
  +String getStatusDescription(int)
  +String toStringDetailJrsMatch([Ljava.lang.String;, [I, com.ibm.wfm.beans.JrsMapNode, int, boolean)
  +ServiceAreaMapNode findServiceArea(java.lang.String, java.util.ArrayList)
  +ServiceAreaMapNode findPractice(java.lang.String, java.util.ArrayList)
  +String toStringDetailNoMatch(int, [Ljava.lang.String;, [I, int, boolean)
  +boolean isLevelValid(int, int)
  +String toStringDataDetail([Ljava.lang.String;, [I)
  +String getResolutionMapping(int, int, boolean)
  +String getCompensation(java.lang.String)
  +JrsMapNode findSaJrs([Ljava.lang.String;, java.util.ArrayList)
  +JrsMapNode findJrs(java.lang.String, java.util.ArrayList)
  +ServiceAreaMapNode findPSa([Ljava.lang.String;, java.util.ArrayList)
  +boolean burst(java.lang.String)
  +int getBurstId([Ljava.lang.String;)
}
class UserDaoService {
  -List users$
  -int userCount$
  +User save(com.ibm.wfm.beans.User)
  +List findAll()
  +User findOne(int)
  +User deleteOne(int)
}
class TaxonomyEvaluatorService {
  -NaryTree naTree
  -boolean useFullkey
  -Logger l$
  -FileStorageProperties fileStorageProperties
  +void main([Ljava.lang.String;)$
  +String[] getBranchKeys([Ljava.lang.String;, [I)
  +TaxonomyEvaluationResponse evaluateTaxonomy(java.lang.String, java.lang.String, java.lang.String, boolean, [I, java.lang.String, boolean, [I)
  +TaxonomyEvaluationResponse evaluateTaxonomy(com.ibm.wfm.beans.NaryTreeNode, java.lang.String, java.lang.String, boolean, [I, java.lang.String, boolean, [I)
  +NaryTreeNode populateTaxonomyFromCsv(java.lang.String, java.lang.String, boolean)
  +boolean isUseFullkey()
  +void setUseFullkey(boolean)
  +ArrayList evaluate(java.lang.String, java.lang.String, java.lang.String, boolean, [I, [I)
  +ArrayList evaluate(java.lang.String, java.lang.String, java.lang.String, boolean, [I)
  +ArrayList evaluate(com.ibm.wfm.beans.NaryTreeNode, java.lang.String, java.lang.String, boolean, [I, [I)
  +NaryTree getNaTree()
  +void setNaTree(com.ibm.wfm.utils.NaryTree)
}
class Wf360FutureSkillDaoService {
  -Class t
  -String tableNm
  -String scdTableNm
  -Wf360DatasourceProperties wf360Prop
  +Connection getConnection()
}
Wf360FutureSkillDaoService --|> AbstractDaoService: inherits
class FbsFootballDaoService {
  -Class t
  -String tableNm
  -String scdTableNm
  -BridgeDatasourceProperties bridgeProp
  +Connection getConnection()
}
FbsFootballDaoService --|> AbstractDaoService: inherits
class SourcingStrategyValidationService {
  -SourcingStrategyValidationService instance$
  -LocalDateTime cacheUpdateTime$
  -List countries
  -List cicDomCntrs
  -List cicGblCntrs
  -String SS01_AFFILIATE$
  -String SS02_CIC_DOMESTIC_CENTER$
  -String SS03_CIC_DOMESTIC_CENTER_CONTRACTOR$
  -String SS04_CIC_DOMESTIC_CENTER_EPH$
  -String SS05_CIC_GLOBAL$
  -String SS06_CIC_GLOBAL_AFFILIATE_ON_CLIENT_SITE$
  -String SS07_CIC_GLOBAL_OR_AFFILIATE$
  -String SS08_CIC_GLOBAL_OR_CIC_DOMESTIC_CENTER$
  -String SS09_CIC_GLOBAL_OR_CONTRACTOR_DOMESTIC$
  -String SS10_CIC_GLOBAL_OR_GEO_REGULARS_DOMESTIC$
  -String SS11_CIC_GLOBAL_OR_GEO_REGULARS_DOMESTIC_B8P_AFFILIATE_LE_B7$
  -String SS12_CIC_GLOBAL_OR_GEO_REGULARS_DOMESTIC_B9P_AFFILIATE_LE_B8$
  -String SS13_CONTRACTOR__DOMESTIC$
  -String SS14_GEO_REGULARS__DOMESTIC$
  -String SS15_GEO_REGULARS_DOMESTIC_EPH$
  -String SS16_GEO_REGULARS_DOMESTIC_B8_CIC_DOMESTIC_CENTER_LE_B7$
  -String SS17_GEO_REGULARS_DOMESTI_B8P_CIC_GLOBAL_LE_B7$
  -String SS18_INDIRECT$
  -String SS19_OTHER$
  -String SS20_CIC_GLOBAL_DOMESTIC_AFFILIATE$
  -String SS21_CIC_GLOBAL_DOMESTIC_B8P_DOM_CENTER$
  -String SS22_CIC_GLOBAL_DOMESTIC_B8P_DOM_CENTER$
  -String SS90_OTHER_CIC_DOMESTIC_CENTER$
  -String SS91_OTHER_GEO_REGULARS_DOMESTIC$
  +SourcingStrategyValidationBean validate(java.lang.String, java.util.Map, java.util.Map)
  +SourcingStrategyValidationService getInstance()$
  +SourcingStrategyValidationBean cicDomesticCenterRuleContractor(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean cicDomesticAffiliateOnClientSiteRule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean cicGlobalOrContractorDomesticRule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean cicGlobalOrGeoRegularDomesticRule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean cicGlobalOrDomesticB8pDomCenterRule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean cicGlobalOrDomesticB9pDomCenterRule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean otherCicGlobalOrCicDomesticCenter(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean otherCicGlobalOrGeoRegularsDomestic(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean validateTest(java.lang.String, java.util.Map, java.util.Map)
  +SourcingStrategyValidationBean affiliateRule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean cicDomesticCenterRule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean cicDomesticCenterRuleEph(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean cicGlobalRule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean cicGlobalAffiliateRule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean cicGlobalOrCiCDomesticRule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean contractorDomesticRule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean geoRegularDomesticRule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean geoRegularDomesticEphRule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean setValidity(java.lang.String, com.ibm.wfm.beans.SourcingStrategyValidationBean)
  -boolean lambda$0(java.util.Map, com.ibm.wfm.beans.BmsCountryDim)$
  -boolean lambda$1(java.util.Map, com.ibm.wfm.beans.BmsCountryDim)$
  +SourcingStrategyValidationBean geoRegularDomesticB8PlusOrCicDomesticLtB7Rule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean cicGlobalOrGeoRegularDomesticB9PlusOrAffiliateLtB8Rule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean geoRegularDomesticB8PlusOrCicGlobalLtB7Rule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean cicGlobalOrGeoRegularDomesticB8PlusOrAffiliateLtB7Rule(java.lang.String, java.util.Map)
  +SourcingStrategyValidationBean cicGlobalOrDomesticAffiliateOnClientSiteRule(java.lang.String, java.util.Map)
}
class UtAccessService {
  -RestTemplate restTemplate
  -String FILTERS$
  +void main([Ljava.lang.String;)$
  +List findAllEdsUt(java.lang.String, java.lang.String, java.lang.String)
  +List findEdsUt(java.lang.String, java.lang.String, java.lang.String, java.lang.String, java.lang.String, java.lang.String, java.lang.String, java.lang.String, java.lang.String)
}
class AbstractDaoService {
&lt;&lt;abstract&gt;&gt;
  -Class t
  -String baseTableNm
  -String tableNm
  -String scdTableNm
  -String forceTableNm
  -FileStorageService fileStorageService
  -FileStorageProperties fileStorageProperties
  +ResponseEntity insert(java.lang.Object)
  +ResponseEntity find(java.lang.Class, java.util.Map, java.lang.String, java.lang.String, boolean, java.lang.String, boolean, boolean, java.lang.String, java.lang.String, javax.servlet.http.HttpServletRequest)
  +ResponseEntity find(java.lang.Class, java.util.Map, java.lang.String, java.lang.String, boolean, boolean, java.lang.String, boolean, boolean, java.lang.String, boolean, int, java.lang.String, javax.servlet.http.HttpServletRequest)
  +ResponseEntity find(java.lang.Class, java.util.Map, java.lang.String, java.lang.String, boolean, java.lang.String, boolean, boolean, java.lang.String, boolean, java.lang.String, javax.servlet.http.HttpServletRequest)
  +ResponseEntity find(java.lang.Class, java.util.Map, java.lang.String, java.lang.String, boolean, java.lang.String, boolean, boolean, java.lang.String, int, java.lang.String, javax.servlet.http.HttpServletRequest)
  +ResponseEntity delete(java.lang.Class, java.lang.Object)
  +int delete(java.util.List)
  +List findAll(java.lang.String, java.lang.String, int, java.lang.String)
  +List findAll()
  +List findAll(java.lang.String, java.lang.String, int, int, java.lang.String)
  +List findAll(java.util.Map, java.lang.String, boolean, java.lang.String, int, int, java.lang.String, boolean)
  +List findAll(java.lang.String, int)
  +List findAll(java.lang.String, int, int)
  +List findAll(java.lang.String, java.lang.String, int)
  +List findAll(java.lang.String, java.lang.String, int, int)
  +List findAll(java.lang.String, java.lang.String, int, boolean)
  +List findAll(java.lang.String, java.lang.String, int, int, boolean)
  +List findAll(java.lang.String, java.lang.String)
  +List findAll(java.lang.String)
  +void setScdTableNm(java.lang.String)
  +String getForceTableNm()
  +void setForceTableNm(java.lang.String)
  +ResponseEntity returnTax2Csv(java.util.List, java.lang.String, javax.servlet.http.HttpServletRequest)
  +ResponseEntity returnTax2CsvObject(java.util.List, java.lang.String, javax.servlet.http.HttpServletRequest)
  +ResponseEntity returnTax3CsvObject(java.util.List, java.lang.String, javax.servlet.http.HttpServletRequest)
  +ResponseEntity returnCsvObject(java.util.List, java.lang.String, javax.servlet.http.HttpServletRequest)
  +ResponseEntity connectToDatasource(java.lang.String)
  +ResponseEntity runDynamicSql(java.lang.String, java.lang.String, javax.servlet.http.HttpServletRequest, boolean)
  +ResponseEntity runDynamicSql(java.lang.String, java.lang.String, javax.servlet.http.HttpServletRequest)
  +ResponseEntity runDynamicSql(java.lang.String, java.lang.String, [Ljava.lang.String;, javax.servlet.http.HttpServletRequest, boolean, int, int)
  +ResponseEntity runDynamicSql(java.lang.String, java.lang.String, javax.servlet.http.HttpServletRequest, int, int)
  +List getListForSql(java.lang.Class, java.sql.Connection, java.lang.String)
  +ResponseEntity findWithInheritence(java.lang.Class, java.util.Map, java.lang.String, java.lang.String, boolean, boolean, java.lang.String, boolean, java.lang.String, javax.servlet.http.HttpServletRequest)
  +List findAllWithInheritence(java.util.Map, java.lang.String, boolean, java.lang.String, int, java.lang.String, boolean)
  +List getObjectListFromExcel(java.lang.String, java.lang.String)
  +String getScdTableNm()
  +String getBaseTableNm()
  +void setBaseTableNm(java.lang.String)
  +void setT(java.lang.Class)
  +void setTableNm(java.lang.String)
  +ResponseEntity returnCsv(java.util.List, java.lang.String, javax.servlet.http.HttpServletRequest)
  +String getForSql(com.ibm.wfm.beans.DataSourceDim, java.lang.String)
  +String getForSql(java.sql.Connection, java.lang.String, [Ljava.lang.String;)
  +String getForSql(java.sql.Connection, java.lang.String)
  +String getForSql(com.ibm.wfm.beans.DataSourceDim, java.lang.String, [Ljava.lang.String;)
  +List findAllTax(java.lang.String, java.lang.String, int, boolean, java.lang.String)
  +List findAllTax(java.util.Map, java.lang.String, boolean, java.lang.String, int, boolean, java.lang.String)
  +List findAllTax(java.lang.String, java.lang.String, int, java.lang.String)
  +int insertAll(java.util.List)
  +int deleteAll(java.lang.String)
  +int deleteAll()
  +EtlResponse etl(java.lang.String, java.lang.String, int, java.lang.String)
  +ResponseEntity etl(java.lang.Class, org.springframework.web.multipart.MultipartFile, org.springframework.web.multipart.MultipartFile, int, java.lang.String)
  +int updateAll(java.util.List)
  +ResponseEntity countAll(java.lang.Class, java.util.Map, java.lang.String, boolean, java.lang.String, boolean)
  +Class getT()
  +String getTableNm()
  -Object lambda$1(java.util.Map$Entry)$
  -void lambda$2(com.fasterxml.jackson.dataformat.csv.CsvSchema$Builder, java.lang.String)$
}
AbstractDaoService --|> DaoInterface: implements
class SourcingStrategyDaoService {
  -Class t
  -String tableNm
  -String scdTableNm
  -BridgeDatasourceProperties bridgeProp
  +Connection getConnection()
}
SourcingStrategyDaoService --|> AbstractDaoService: inherits
class LadderComparatorService {
  +void main([Ljava.lang.String;)$
  +boolean process(java.lang.String, java.lang.String, int, java.lang.String)$
  +boolean processDemographicMovementCsv(java.lang.String, java.lang.String, int, java.lang.String)$
  +int compareArrays([Ljava.lang.String;, [Ljava.lang.String;, int)$
  +int compareArraysX([Ljava.lang.String;, [Ljava.lang.String;, int)$
  +boolean processCsv(java.lang.String, java.lang.String, int, java.lang.String)$
}
class DbmsConnectionServices {
  -BridgeDatasourceProperties bridgeProp
  -String DBMS_WFM_EDS$
  +Connection getConnectionForDbms(java.lang.String)
}
class RahDaoService {
  -Class t
  -String tableNm
  -String scdTableNm
  -RahDatasourceProperties rahProp
  -FileStorageProperties fileStorageProperties
  +Connection getConnection()
}
RahDaoService --|> AbstractDaoService: inherits
class T2gDemographicAnalysisService {
  -int GROWTH_PLATFORM_LVL$
  -int SERVICE_LINE_LVL$
  -int PRACTICE_LVL$
  +int PRACTICE_NM$
  +int SERVICE_LINE_NM$
  +int GROWTH_PLATFORM_NM$
  +String[] practiceMovementExceptions$
  +void main([Ljava.lang.String;)$
  +boolean isPracticeMovementException(java.lang.String, java.lang.String)$
}
class SkillDaoService {
  -Class t
  -String tableNm
  -String scdTableNm
  -BridgeDatasourceProperties bridgeProp
  +Connection getConnection()
}
SkillDaoService --|> AbstractDaoService: inherits
class FileBurstService {
  +void main([Ljava.lang.String;)$
  +boolean burst(java.lang.String, java.lang.String, [Ljava.lang.String;, java.lang.String, boolean)
}
</pre>

<button type="button" class="btn btn-primary" onclick="initZoom()">initZoom()</button>

<script>
    function handleZoom(e) {
        console.log("handleZoom e="+e)
        d3.select('svg g').attr('transform',e.transform);
    }
    let zoom = d3.zoom().on('zoom',handleZoom);
    function initZoom() {
        alert("initZoom()");
        d3.select('svg').call(zoom);
    }
    
</script>
