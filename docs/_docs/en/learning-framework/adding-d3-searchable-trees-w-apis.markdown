---
title: Adding D3 Searchable Trees Using APIs
permalink: /en/learning-framework/adding-d3-searchable-trees-w-apis
features:
  - d3
  - select2
abstract: >- # this means to ignore newlines until "baseurl:"
  The hierarchy is a basic means of organizing and classifying items, many taxonomies are multi-tiered and dense. Too dense for professionals to either commit to memory or easily navigate. The interactive tree is a web page containing an interactive D3 expandable/collapsible tree representing the full hierarchy.  This document outlines how to use a D3 searchable tree that is populated by an API call instead of a static JSON structure.
---

<style>
/* Show the first tab by default */
#search-tree-basic {
    display: block;
}

/* Temporary */
.select2-container {
    width: 100% !important;
}

.select2-search-choice {
   border: 0px !important;
   margin-top: 8px !important;
   background-image: none !important;
   background-color: #c8e1ff !important;
   color: #444d56 !important;
}

</style>

<!-- could use modal-fullscreen or modal-xl -->
<div class="modal-overlay fade" id="id-info-modal" tabindex="-1" aria-labelledby="id-info-modalLabel" aria-hidden="true" style="display: none;">
        <div class="modal-content">
            <div class="modal-header">
                <h4 class="modal-title" id="id-info-modal-title">New message</h4>
                <button type="button" onclick="javasript:closeModal()" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body" id="id-info-modal-body"></div>
            <div class="modal-footer">
                <button type="button" onclick="javasript:closeModal()" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            </div>
        </div>
</div>

## Sourcing tree's JSON sturcture using APIs

The example below shows how to implement a WFM DMF D3 searchable tree using APIs.  This tree, in particular, is the Job Role Specialty taxonomy using the [WMF DMF Jrss API](https://ms-spring-server.dal1a.ciocloud.nonprod.intranet.ibm.com/api/v1/eds-ut-jrs-tax/jrss?includeParentage=true&includePit=false){:target="_blank"}.

<pre name="code" class="js">
api = "https://ms-spring-server.dal1a.ciocloud.nonprod.intranet.ibm.com/api/v1/eds-ut-jrs-tax/jrss?includeParentage=true&includePit=false"
d3.json(api,
    function (data) {
        d3.select("#jrss-tree").datum(data).call(jrssTree");
        ...
    });
</pre>

The above D3 code snippet performs the following actions:

1. `d3.json(api, function (data) { ... })`: This code uses D3's `json` method to make an asynchronous HTTP request to the specified API endpoint (`api`). The callback function `(function (data) { ... })` is executed once the JSON data is loaded. The retrieved JSON data is passed to this function as the `data` parameter.

2. `d3.select("#jrss-tree")`: This selects the HTML element with the ID "jrss-tree" using D3's `select` method.

3. `.datum(data)`: This sets the data associated with the selected element. The `datum` method binds the `data` obtained from the API response to the selected HTML element.

4. `.call(jrssTree")`: This calls the function `jrssTree"` and passes the selected element (with the associated data) as an argument to that function. The `call` method is used to invoke a function with a specific context, in this case, passing the data-bound element to the `jrssTree"` function.

In summary, this D3 code fetches JSON data from the specified API endpoint (`api`), associates that data with the HTML element with the ID "jrss-tree", and then calls the function `jrssTree"` with the data-bound element. Typically, `jrssTree"` would be a D3 tree layout or a function responsible for rendering a tree visualization based on the provided data.

As with the basic tree and since this document is using `select2`; the document must create an instance of `InteractiveD3TreeObj` and include a call to `initSelect2()`. The full code snippet is below.

<pre name="code" class="js">
treeHeight = 800
treeWidth = 2400
nodeSpacing = 300

jrssTree = new InteractiveD3TreeObj(treeHeight = treeHeight, treeWidth = treeWidth, nodeSpacing = nodeSpacing);

api = "https://ms-spring-server.dal1a.ciocloud.nonprod.intranet.ibm.com/api/v1/eds-ut-jrs-tax/jrss?includeParentage=true&includePit=false"
d3.json(api,
    function (data) {
        d3.select("#jrss-tree").datum(data).call(jrssTree);

        select2Tax = [ {"text":"Brands", "children":[]},
        {"text": "Growth Platforms", "children":[]},
        {"text": "Service Lines", "children":[]},
        {"text": "Practices", "children":[]},
        {"text": "Service Areas", "children":[]},
        {"text": "Job Role-Specialties", "children":[]}
        ];
        select2Id = "#searchName";

        jrssTree.initSelect2(select2Tax, select2Id, "d.description", "id-match-type");
});
</pre>

## JRS Navigator

The [JRS Navigator](https://wfm-wizard.dal1a.cirrus.ibm.com/#/jrs-navigator){:target="_blank"} tool is an IBM Consulting web application that enables users to identify valid Job Role Specialties (JRS). This tool provides both navigation and tree search capabilities and is a great resource to expolore the Job Role Specialty taxonomy.

## Database Schema

The diagram below shows the Job Role Specialty (JRS) taxonomy deployed within IBM Consulting.  Since the JRS taxonomy shares parents with the Offering taxonomy, both are shown in the diagram, with the JRS branch boxed in <span style="color:red">red</span>.

![JRS Taxonomy]({{ site.baseurl }}/assets/images/docs/unified-jrs-taxonomy-jrs.png){: class="center zoom"}

[![go-to]({{ site.baseurl }}/assets/images/go-to.svg){: style="height:24px;" } open full image]({{ site.baseurl }}/assets/images/docs/unified-jrs-taxonomy-jrs.png){: target="_blank"}


The database schema diagram is a visual representation or graphical illustration of the structure and relationships within a database. It depicts the tables, columns, data types, primary keys, foreign keys, and other database objects, as well as the connections or associations between them. The schema diagram provides a clear and concise overview of the database structure, aiding in understanding the data model and facilitating database design, development, and maintenance activities.

## Visualize

WFM has developed a D3 component that allows the [WFM Data Managment Framework](https://ms-spring-server.dal1a.ciocloud.nonprod.intranet.ibm.com/swagger-ui.html#/eds-dao-jrs-taxonomy-controller){:target="_blank"} taxonomy Apis, or any Api that returns a valid taxonomy, to display the results in a D3 tree.

The graph below is an interactive expandable/collapsible tree representing the full IBM Consulting Job Role - Specialty taxonomy
(Brand &rarr; Growth Platform &rarr; Service Line &rarr; Practice  &rarr; Service Area  &rarr; Job Role - Specialty) using the WFM Data Managment Framework's [JRSs API including parentage](https://ms-spring-server.dal1a.ciocloud.nonprod.intranet.ibm.com/api/v1/eds-ut-jrs-tax/jrss?includeParentage=true&includePit=false){:target="_blank"}.

The blue circles represent expandable nodes. The **search function** finds and highlights all areas of the tree where the key word is found. 

<p>Navigate the tree by selecting desired nodes or entering a key word in the <b>search field</b>. 		
     <a class="button" onclick="javascript:openModal()" aria-label="Tree search" data-bs-content="tree" style="cursor: pointer;">
        <i class="fa fa-info-circle fa-fw" style="color:blue;" title="Tree Search Help" aria-hidden="true"></i>
    </a>
</p>

<div class="tabs">
    <button class="tab-btn active" onclick="openTab('search-tree-basic')" id="search-tree-basic-btn">Basic</button>
    <button class="tab-btn" onclick="openTab('search-tree-advanced')" id="search-tree-advanced-btn">Advanced</button>
    <button class="tab-btn" onclick="openTab('search-tree-regex')" id="search-tree-regex-btn">Regular Expression</button>
</div>

<div id="search-tree-basic" class="tab-content" style="display: block;">
    <div class="form-group row">
        <label for="Search" class="col-sm-6 col-form-label"><b>Select or enter search criteria</b></label>
        <div class="col-sm-6">
            <div class="btn-group" id="id-basic-search-type" data-toggle="buttons" style="float: right;">
                <div class="form-check form-check-inline">
                    <input class="form-check-input" name="id-match-type" type="radio" value="pattern-match" id="id-match-pattern" checked="true">
                    <label class="form-check-label color-text-secondary f6" for="id-pattern-match">
                        Pattern Match
                    </label>
                   <input class="form-check-input" name="id-match-type" type="radio" value="exact-match" id="id-match-exact">
                    <label class="form-check-label color-text-secondary f6" for="id-exact-match">
                        Exact Match
                    </label>
                    &nbsp;|&nbsp;
                    <a class="button" onclick="javascript:openModal()" aria-label="Basic search" data-bs-content="basic" style="cursor: pointer;"><i class="fa fa-info-circle fa-fw" style="color:blue;" title="Basic Search Help" aria-hidden="true"></i></a>
                    &nbsp;|&nbsp;
                    <a class="button" onclick="jrssTree.resetTree()" aria-label="Reset tree" style="cursor: pointer;"><i class="fa fa-refresh fa-fw" style="color:blue;" title="Reset tree" aria-hidden="true"></i></a>
                </div>
            </div>
        </div>	
    </div>
    <div class="form-group row">
        <div class="col-sm-12">
<div id="searchName"></div>	
        </div>	
    </div>
</div>

<div id="search-tree-advanced" class="tab-content">
    <div class="form-group row">
        <label for="Search" class="col-sm-6 col-form-label"><b>Enter advanced search criteria</b></label>
        <div class="col-sm-6">
            <div class="btn-group" id="id-search-type" data-toggle="buttons" style="float: right;">
                <div class="form-check form-check-inline">
                    <input class="form-check-input" type="checkbox" value="" id="id-case-adv-sensitive">
                    <label class="form-check-label color-text-secondary f6" for="case-sensitive">
                        Case sensitive
                    </label>
                    &nbsp;|&nbsp;
                    <a class="button" onclick="javascript:openModal()" aria-label="Advanced search" data-bs-content="adv" style="cursor: pointer;"><i class="fa fa-info-circle fa-fw" style="color:blue;" title="Advanced Search Help" aria-hidden="true"></i></a>
                    &nbsp;|&nbsp;
                    <a class="button" onclick="jrssTree.resetTree()" aria-label="Reset tree" style="cursor: pointer;"><i class="fa fa-refresh fa-fw" style="color:blue;" title="Reset tree" aria-hidden="true"></i></a>
                </div>
            </div>
        </div>	
    </div>
    <div class="form-group row">
        <div class="col-sm-12">
            <div class="btn-group" id="id-advanced-search-type" data-toggle="buttons">
                <div class="form-check form-check-inline">
                    <input class="form-control" id="id-adv-criteria" type="text" placeholder="Enter advanced search criteria" style="width: 85%;" data-sb-validations="required">
                    <button class="btn btn-primary btn-lg" id="advanced-submit-button" type="button" onclick="javascript:advancedSearch()" style="float: right;">Submit</button>
                </div>
            </div>

        </div>	
    </div>
</div>

<div id="search-tree-regex" class="tab-content">
    <div class="form-group row">
        <label for="Search" class="col-sm-6 col-form-label"><b>Enter Regular Expression as search criteria</b></label>
        <div class="col-sm-6">
            <div class="btn-group" id="id-search-type" data-toggle="buttons" style="float: right;">
                <div class="form-check form-check-inline">
                    <input class="form-check-input" type="checkbox" value="" id="id-case-regex-sensitive">
                    <label class="form-check-label color-text-secondary f6" for="case-sensitive">
                        Case sensitive
                    </label>
                    &nbsp;|&nbsp;
                    <a class="button" onclick="javascript:openModal()" aria-label="Regular Expression (RegEx) search" data-bs-content="regex" style="cursor: pointer;"><i class="fa fa-info-circle fa-fw" style="color:blue;" title="Regular Expression (RegEx) Search Help" aria-hidden="true"></i></a>
                    &nbsp;|&nbsp;
                    <a class="button" onclick="jrssTree.resetTree()" aria-label="Reset tree" style="cursor: pointer;"><i class="fa fa-refresh fa-fw" style="color:blue;" title="Reset tree" aria-hidden="true"></i></a>
                </div>
            </div>
        </div>	
    </div>
    <div class="form-group row">
        <div class="col-sm-12">
            <div class="btn-group" id="id-regex-search-type" data-toggle="buttons">
                <div class="form-check form-check-inline">
                    <input class="form-control" id="id-regex-criteria" type="text" placeholder="Enter Regular Expression as search criteria" style="width: 85%;" data-sb-validations="required">
                    <button class="btn btn-primary btn-lg" id="regex-submit-button" type="button" onclick="javascript:regExSearch()" style="float: right;">Submit</button>
                </div>
            </div>

        </div>	
    </div>
</div>

<script>
function openTab(tabName) {
    // Hide all tab content
    var tabContents = document.getElementsByClassName('tab-content');
    for (var i = 0; i < tabContents.length; i++) {
        tabContents[i].style.display = 'none';
    }

    // Remove the 'active' class from all tab buttons
    var tabButtons = document.getElementsByClassName('tab-btn');
    for (var i = 0; i < tabButtons.length; i++) {
        tabButtons[i].classList.remove('active');
    }

    // Show the selected tab content
    document.getElementById(tabName).style.display = 'block';

    // Add the 'active' class to the clicked tab button
    document.getElementById(tabName + '-btn').classList.add('active');
}
</script>
<p style="display:block;" id="id-search-criteria-parsed-output"></p>
<button type="button" class="btn btn-primary" onclick="jrssTree.expandTree()">+ expand all</button>
<button type="button" class="btn btn-primary" onclick="jrssTree.collapseTree()">- collapse all</button>

<div>
    <p>&nbsp;</p>
</div>
<div id="tree-container">
    <div id="jrss-tree"></div>
</div>

<script>
    function evaluateBinaryExpression(obj) {
        evaluatedExpression+='(';
        evaluateTreeBasic(obj.left);
        if (obj.operator=='|') evaluatedExpression+=obj.operator
        evaluateTreeBasic(obj.right);
        evaluatedExpression+=')';
    }

    function evaluateLiteral(obj) {
        evaluatedExpression+= '(?=.*'+obj.value.replaceAll('~','\\b')+')';
    }

    function evaluateIdentifier(obj) {
        evaluatedExpression+= '(?=.*'+obj.name.replaceAll('~','\\b')+')';
    }

    function evaluateTreeBasic(obj) {
        if (obj.type == 'BinaryExpression') {
            evaluateBinaryExpression(obj);
        }
        else if (obj.type == 'Literal') {
            evaluateLiteral(obj);
        }
        else if (obj.type == 'Identifier')  {
            evaluateIdentifier(obj);
        }
        else {
            throw('Unknown token type: '+obj.type);
            console.log('xUnknown token type: '+obj.type)
        }

    };

    function basicSearch() {
        // Retrieve the text from the input field
        var searchCriteria = document.getElementById('basic-search-input').value;
        jrssTree.doSearch(searchCriteria,"d.description",0,'i')
    }

    function advancedSearch() {
        searchCriteriaParsedOutput = document.getElementById("id-search-criteria-parsed-output");
        //searchCriteriaParsedOutput = $("#id-search-criteria-parsed-output"); (requires JQuery)
        let  searchCriteriaElement = document.getElementById('id-adv-criteria');
        let expr = searchCriteriaElement.value;

        if (expr=="") {
            searchCriteriaParsedOutput.text("");
            resetTree();
            return;
        }
        var tree = false;
        try {
            tree = jsep(expr);
            //searchCriteriaParsedOutput.removeClass("text-danger");
            searchCriteriaParsedOutput.classList.remove('text-danger');
            
            evaluatedExpression="";
            evaluateTreeBasic(tree);
            searchCriteriaParsedOutput.textContent='Compiled RegEx expression: '+evaluatedExpression;
            console.log('Compiled RegEx expression: '+evaluatedExpression);
            
            caseSensitiveEl = document.getElementById('id-case-adv-sensitive');
            regexFlags='i'
            if (caseSensitiveEl && caseSensitiveEl.checked) regexFlags='';
            
            //doSearch(evaluatedExpression);
            jrssTree.doSearch(evaluatedExpression,"d.description",0,regexFlags)
            
        } catch(e) {
            console.log(e.message);
            //searchCriteriaParsedOutput.addClass("text-danger");
            searchCriteriaParsedOutput.classList.add('text-danger');
            searchCriteriaParsedOutput.textContent=e.message;
        }
    }

    /**=========================================================================
     * function invoked when the submit button clicked from the Regular Expression Tab. 
     * If... TO-DO complete
     * 
     * @author  Steven J. Ponessa
     * @parm    event
     * @returns void
     */
    function regExSearch() {
        let  searchCriteriaElement = document.getElementById('id-regex-criteria');
        let searchCriteria = searchCriteriaElement.value;
        
        caseSensitiveEl = document.getElementById('id-case-regex-sensitive');
        let matchType = 0;
        let regexFlags = 'i';
        if (caseSensitiveEl && caseSensitiveEl.checked) regexFlags='';
        
         jrssTree.doSearch(searchCriteria,"d.description",matchType, regexFlags)
    }

    treeHeight = 800
    treeWidth = 2400
    nodeSpacing = 300

    jrssTree = new InteractiveD3TreeObj(treeHeight = treeHeight, treeWidth = treeWidth, nodeSpacing = nodeSpacing);

    api = "https://ms-spring-server.dal1a.ciocloud.nonprod.intranet.ibm.com/api/v1/eds-ut-jrs-tax/jrss?includeParentage=true&includePit=false"
    d3.json(api,
        function (data) {
            d3.select("#jrss-tree").datum(data).call(jrssTree);

            select2Tax = [ {"text":"Brands", "children":[]},
            {"text": "Growth Platforms", "children":[]},
            {"text": "Service Lines", "children":[]},
            {"text": "Practices", "children":[]},
            {"text": "Service Areas", "children":[]},
            {"text": "Job Role-Specialties", "children":[]}
            ];
            select2Id = "#searchName";

            jrssTree.initSelect2(select2Tax, select2Id, "d.description", "id-match-type");
    });
 
//d3.select("#jrss-tree").datum(jrssJson).call(jrssTree);

let helpStructure;
d3.json("../../assets/data/helpContent.json", function(error, helpText) {
	helpStructure = helpText;
});



// Function to open the modal
function openModal() {
    var informationModal = document.getElementById('id-info-modal')
    // Button that triggered the modal
    var button = event.currentTarget
    // Extract info from data-bs-* attributes
    var contentId = button.getAttribute('data-bs-content')

    for (help of helpStructure) {
        if (help.id==contentId) break;
    }

    var modalTitle = informationModal.querySelector('.modal-title')
    let bodyDiv = document.getElementById('id-info-modal-body')

    modalTitle.textContent = help.title
    bodyDiv.innerHTML = '<div w3-include-html="'+help.context+'"></div>';
    /*make an HTTP request using the attribute value as the file name:*/
    xhttp = new XMLHttpRequest();
    xhttp.onreadystatechange = function() {
        if (this.readyState == 4) {
            if (this.status == 200) {bodyDiv.innerHTML = this.responseText;}
            if (this.status == 404) {bodyDiv.innerHTML = "Page not found.";}
        }
    }      
    xhttp.open("GET", window.location.protocol+"//"+window.location.host+help.context, true);
    xhttp.send();

    informationModal.style.display = 'flex';
}

// Function to close the modal
function closeModal() {
    var informationModal = document.getElementById('id-info-modal')
    informationModal.style.display = 'none';
}

/*
select2Tax = [ {"text":"Brands", "children":[]},
  {"text": "Growth Platforms", "children":[]},
  {"text": "Service Lines", "children":[]},
  {"text": "Practices", "children":[]},
  {"text": "Service Areas", "children":[]},
  {"text": "Job Role-Specialties", "children":[]}
];
select2Id = "#searchName";

jrssTree.initSelect2(select2Tax, select2Id, "d.description", "id-match-type");
*/

var tab = document.getElementById("search-tree-basic-btn")
tab.addEventListener('click', function() {
        //console.log("search-tree-basic-btn selected.")
        searchCriteriaParsedOutput = document.getElementById("id-search-criteria-parsed-output");
        searchCriteriaParsedOutput.textContent = "";
        searchCriteriaParsedOutput.classList.remove('text-danger');

        $('#searchName').val(null).trigger('change');
        jrssTree.resetTree();
    }
)

tab = document.getElementById("search-tree-advanced-btn")
tab.addEventListener('click', function() {
        //console.log("search-tree-advanced-btn selected.")
        searchCriteriaParsedOutput = document.getElementById("id-search-criteria-parsed-output");
        searchCriteriaParsedOutput.textContent = "";
        searchCriteriaParsedOutput.classList.remove('text-danger');

        searchCriteria = document.getElementById("id-adv-criteria")
        searchCriteria.value = ""
        jrssTree.resetTree();
    }
)

tab = document.getElementById("search-tree-regex-btn")
tab.addEventListener('click', function() {
        //console.log("search-tree-regex-btn selected.")
        searchCriteriaParsedOutput = document.getElementById("id-search-criteria-parsed-output");
        searchCriteriaParsedOutput.textContent = "";
        searchCriteriaParsedOutput.classList.remove('text-danger');

        searchCriteria = document.getElementById("id-regex-criteria")
        searchCriteria.value = ""   

        jrssTree.resetTree();
    }
)

</script>