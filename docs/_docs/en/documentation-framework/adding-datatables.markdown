---
title: Adding Datatables
permalink: /en/documentation-framework/adding-datatables
features:
  - select2
  - datatables
abstract: >- # this means to ignore newlines until "baseurl:"
  A data table is an organized collection of information presented in rows and columns, allowing for efficient data management, analysis, and interaction through features like sorting, filtering, and pagination.
---

# Introduction

The WFM web publishing framework, has introduced support for tabular data visualization using [DataTables.js](https://datatables.net/){:target="_blank"}. This powerful plugin enhances the way data tables are displayed and interacted with on your web pages. With features like pagination, sorting, filtering, and various export options, managing and presenting large datasets is easy. This section will walk you through the key functionalities and show you how to make the most of these new capabilities.

# Key Features

1. **Pagination**: Seamlessly navigate through large datasets with efficient pagination controls.
2. **Sorting**: Easily sort columns in ascending or descending order to find the information you need quickly.
3. **Filtering**: Apply filters to columns to narrow down the data displayed based on specific criteria.
4. **Copying**: Copy table data to the clipboard for quick use in other applications.
5. **Exporting**: Export your data to various formats, including CSV, Excel, and PDF, for offline analysis or sharing.
6. **Printing**: Print the table directly from the browser for physical records or reports.
7. **Column Visibility**: Toggle the visibility of columns to customize the data view according to your needs.
8. **Page Length Control**: Adjust the number of rows displayed per page to suit your preference.

# Detailed Functionality

## Pagination
DataTables.js provides intuitive pagination controls at the bottom of the table. Users can navigate through different pages of data using these controls, ensuring that even large datasets are manageable and easy to browse.

## Sorting
Each column header in the table is clickable, allowing users to sort the data in that column either in ascending or descending order. This is especially useful for organizing data in a meaningful way, such as sorting a list of names alphabetically or ordering numerical data from highest to lowest.

## Filtering
Above each column, there is a filter input box where users can type in criteria to filter the data. This dynamic filtering updates the table in real-time, displaying only the rows that match the filter criteria. This feature is ideal for quickly finding specific entries within large datasets.

## Copying
With a single click, users can copy the table data to their clipboard. This functionality is especially useful for quickly transferring data to other applications without the need for complex export processes.

## Exporting
DataTables.js supports exporting table data to multiple formats:
- **CSV**: Export data to a CSV file for use in spreadsheet applications.
- **Excel**: Export data to an Excel file for advanced data manipulation and analysis.
- **PDF**: Export data to a PDF file for sharing and printing.
- **Print**: Directly print the table from the browser for physical copies.

## Column Visibility
Users can control the visibility of each column through a built-in column visibility menu. This allows for a customized view of the data, showing only the columns that are relevant to the current task.

## Page Length Control
The page length control feature allows users to select the number of rows displayed per page. Options typically range from 10 to 100 rows per page, giving users the flexibility to view as much or as little data as they need at a time.

# Getting Started

To enable these features in your web application, simply include DataTables.js in your project and initialize it with your table. You only need to add the `datatables` (and select2) features to the **front matter** of your document and link it to your table using an **id** and the **class** `display`.  

> **Note:** Currently `select2` is required to pull in `jquery.js` which is used by DataTable.  As the framework matures we'll add dependency logic so that the build process understands and includes required dependencies automatically.

Below is an example of how to set it up using a static table:

<pre name="code" class="html">
---
title: Adding Datatables
permalink: /en/learning-framework/adding-datatables
features:
  - select2
  - datatables
abstract: >- # this means to ignore newlines until "baseurl:"
  A data table is an ....
---
...
&lt;table id="id-datatable-fbsfootball-sec" class="display" style="width:100%"&gt;
   &lt;thead&gt;
      &lt;tr&gt;
         &lt;th&gt;TEAM_CD&lt;/th&gt;
         &lt;th&gt;NICKNAME&lt;/th&gt;
         &lt;th&gt;INSTITUTION_NM&lt;/th&gt;
         &lt;th&gt;FOUNDED_YR&lt;/th&gt;
         &lt;th&gt;JOINED_DT&lt;/th&gt;
         &lt;th&gt;ENROLLMENT_CNT&lt;/th&gt;
         &lt;th&gt;ENDOWMENT_AMT&lt;/th&gt;
         &lt;th&gt;CONF_CD&lt;/th&gt;
         &lt;th&gt;DIV_CD&lt;/th&gt;
      &lt;/tr&gt;
   &lt;/thead&gt;
   &lt;tbody&gt;
      &lt;tr&gt;
         &lt;td&gt;FLA &lt;/td&gt;
         &lt;td&gt;Gators&lt;/td&gt;
         &lt;td&gt;University of Florida&lt;/td&gt;
         &lt;td&gt;1853&lt;/td&gt;
         &lt;td&gt;11689&lt;/td&gt;
         &lt;td&gt;52218&lt;/td&gt;
         &lt;td&gt;1850&lt;/td&gt;
         &lt;td&gt;SEC&lt;/td&gt;
         &lt;td&gt;EA&lt;/td&gt;
      &lt;/tr&gt;
      &lt;tr&gt;
         &lt;td&gt;MIZZ&lt;/td&gt;
         &lt;td&gt;Tigers&lt;/td&gt;
         &lt;td&gt;University of Missouri&lt;/td&gt;
         &lt;td&gt;1839&lt;/td&gt;
         &lt;td&gt;41032&lt;/td&gt;
         &lt;td&gt;29866&lt;/td&gt;
         &lt;td&gt;1740&lt;/td&gt;
         &lt;td&gt;SEC&lt;/td&gt;
         &lt;td&gt;EA&lt;/td&gt;
      &lt;/tr&gt;
      ...
    &lt;/tbody&gt;
&lt;/table&gt;
...
<script>
$('#id-datatable-fbsfootball-sec').DataTable({
    dom: 'Bfrtip',
    buttons: [
        'copy', 'csv', 'excel', 'pdf', 'print', 'colvis', 'pageLength'
    ],
    scrollX: true,
    columnDefs: [
            {
                "targets": [2], // Indices of columns with long content
                "createdCell": function (td, cellData, rowData, row, col) {
                    $(td).addClass('min-width-200');
                }
            },
            {
                targets: [4], // The index of the column that contains the date
                render: function(data, type, row) {
                    if (type === 'display' || type === 'filter') {
                        // Excel's epoch starts at 1899-12-30
                        var epoch = new Date(1899, 11, 30); // December 30, 1899
                        var date = new Date(epoch.getTime() + data * 24 * 60 * 60 * 1000);
                        var year = date.getFullYear();
                        var month = ('0' + (date.getMonth() + 1)).slice(-2);
                        var day = ('0' + date.getDate()).slice(-2);
                        return year + '-' + month + '-' + day;
                    }
                    return data;
                }
            },
            {
                "targets": [5],
                "className": "align-right",
                "render": function ( data, type, row ) {
                    return new Intl.NumberFormat('en-US', { 
                        minimumFractionDigits: 0, 
                        maximumFractionDigits: 0 
                    }).format(data);
                }
            },
            {
                "targets": [6],
                "className": "align-right",
                "render": function ( data, type, row ) {
                    return new Intl.NumberFormat('en-US', { 
                        minimumFractionDigits: 2, 
                        maximumFractionDigits: 2 
                    }).format(data);
                }
            }
    ]
});

</script>

</pre>

This will generate a data table containing the FBS Football SEC teams.

<table id="id-datatable-fbsfootball-sec" class="display" style="width:100%">
   <thead>
      <tr>
         <th>Code</th>
         <th>Name</th>
         <th>Institution</th>
         <th>Founded Year</th>
         <th>Joined Date</th>
         <th>Enrollment</th>
         <th>Endowment</th>
         <th>Conf Cd</th>
         <th>Div Cd</th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td>FLA </td>
         <td>Gators</td>
         <td>University of Florida</td>
         <td>1853</td>
         <td>11689</td>
         <td>52218</td>
         <td>1850</td>
         <td>SEC</td>
         <td>EA</td>
      </tr>
      <tr>
         <td>MIZZ</td>
         <td>Tigers</td>
         <td>University of Missouri</td>
         <td>1839</td>
         <td>41032</td>
         <td>29866</td>
         <td>1740</td>
         <td>SEC</td>
         <td>EA</td>
      </tr>
      <tr>
         <td>SC  </td>
         <td>Gamecocks</td>
         <td>University of South Carolina</td>
         <td>1801</td>
         <td>33475</td>
         <td>35365</td>
         <td>788.3</td>
         <td>SEC</td>
         <td>EA</td>
      </tr>
      <tr>
         <td>TENN</td>
         <td>Volunteers</td>
         <td>University of Tennessee</td>
         <td>1794</td>
         <td>12239</td>
         <td>28900</td>
         <td>1355</td>
         <td>SEC</td>
         <td>EA</td>
      </tr>
      <tr>
         <td>UGA </td>
         <td>Bulldogs</td>
         <td>University of Georgia</td>
         <td>1785</td>
         <td>11689</td>
         <td>38652</td>
         <td>1344</td>
         <td>SEC</td>
         <td>EA</td>
      </tr>
      <tr>
         <td>UK  </td>
         <td>Wildcats</td>
         <td>University of Kentucky</td>
         <td>1865</td>
         <td>11689</td>
         <td>29182</td>
         <td>1407</td>
         <td>SEC</td>
         <td>EA</td>
      </tr>
      <tr>
         <td>VAN </td>
         <td>Commodores</td>
         <td>Vanderbilt University</td>
         <td>1873</td>
         <td>11689</td>
         <td>13537</td>
         <td>6900</td>
         <td>SEC</td>
         <td>EA</td>
      </tr>
      <tr>
         <td>ALA </td>
         <td>Crimson Tide</td>
         <td>University of Alabama</td>
         <td>1831</td>
         <td>11689</td>
         <td>38563</td>
         <td>832.8</td>
         <td>SEC</td>
         <td>WE</td>
      </tr>
      <tr>
         <td>ARK </td>
         <td>Razorbacks</td>
         <td>University of Arkansas</td>
         <td>1871</td>
         <td>33473</td>
         <td>27778</td>
         <td>1220</td>
         <td>SEC</td>
         <td>WE</td>
      </tr>
      <tr>
         <td>LSU </td>
         <td>Tigers</td>
         <td>Louisiana State University</td>
         <td>1860</td>
         <td>11689</td>
         <td>30985</td>
         <td>521.8</td>
         <td>SEC</td>
         <td>WE</td>
      </tr>
      <tr>
         <td>MISS</td>
         <td>Rebels</td>
         <td>University of Mississippi</td>
         <td>1848</td>
         <td>11689</td>
         <td>22456</td>
         <td>736.3</td>
         <td>SEC</td>
         <td>WE</td>
      </tr>
      <tr>
         <td>MSST</td>
         <td>Bulldogs</td>
         <td>Mississippi State University</td>
         <td>1878</td>
         <td>11689</td>
         <td>21974</td>
         <td>528.7</td>
         <td>SEC</td>
         <td>WE</td>
      </tr>
      <tr>
         <td>TA&M</td>
         <td>Aggies</td>
         <td>Texas A&M University</td>
         <td>1886</td>
         <td>37867</td>
         <td>80522</td>
         <td>82348</td>
         <td>SEC</td>
         <td>WE</td>
      </tr>
   </tbody>
</table>

<script>
$('#id-datatable-fbsfootball-sec').DataTable({
    dom: 'Bfrtip',
    buttons: [
        'copy', 'csv', 'excel', 'pdf', 'print', 'colvis', 'pageLength'
    ],
    scrollX: true,
    columnDefs: [
        {
            "targets": [2], // Indices of columns with long content
            "createdCell": function (td, cellData, rowData, row, col) {
                $(td).addClass('min-width-200');
            }
        },
        {
            targets: [4], // The index of the column that contains the date
            render: function(data, type, row) {
                if (type === 'display' || type === 'filter') {
                    // Excel's epoch starts at 1899-12-30
                    var epoch = new Date(1899, 11, 30); // December 30, 1899
                    var date = new Date(epoch.getTime() + data * 24 * 60 * 60 * 1000);
                    var year = date.getFullYear();
                    var month = ('0' + (date.getMonth() + 1)).slice(-2);
                    var day = ('0' + date.getDate()).slice(-2);
                    return year + '-' + month + '-' + day;
                }
                return data;
            }
        },
        {
            "targets": [5],
            "className": "align-right",
            "render": function ( data, type, row ) {
                return new Intl.NumberFormat('en-US', { 
                    minimumFractionDigits: 0, 
                    maximumFractionDigits: 0 
                }).format(data);
            }
        },
        {
            "targets": [6],
            "className": "align-right",
            "render": function ( data, type, row ) {
                return new Intl.NumberFormat('en-US', { 
                    minimumFractionDigits: 2, 
                    maximumFractionDigits: 2 
                }).format(data);
            }
        }
    ]
});
</script>

<br/>

## Explanation of Parameters and Options

### `dom`
The `dom` parameter defines the structure of the table control elements. In this case:
- `B`: Buttons extension, providing the buttons defined in the `buttons` array.
- `f`: Filtering input.
- `r`: Processing indicator.
- `t`: The table itself.
- `i`: Table information summary.
- `p`: Pagination control.

### `buttons`
The `buttons` array includes options for exporting and interacting with the table data:
- `copy`: Copies the table data to the clipboard.
- `csv`: Exports the table data to a CSV file.
- `excel`: Exports the table data to an Excel file.
- `pdf`: Exports the table data to a PDF file.
- `print`: Prints the table data.
- `colvis`: Allows users to control column visibility.
- `pageLength`: Allows users to control the number of rows displayed per page.

### `scrollX`
The `scrollX` parameter enables horizontal scrolling for the table. This is useful for tables with many columns that might not fit within the viewport.

### `columnDefs`
The `columnDefs` array is used to define specific options for individual columns.

1. **First `columnDefs` Entry**
   <pre name="code" class="js">
   {
       "targets": [2],
       "createdCell": function (td, cellData, rowData, row, col) {
           $(td).addClass('min-width-200');
       }
   }
   </pre>
   - `targets`: Specifies the columns to which the definition applies. `[2]` targets the third column, INSTITUTION_NM (index starts from 0).
   - `createdCell`: A function called whenever a cell is created. Here, it adds the class `min-width-200` to cells in the specified column to ensure a minimum width of 200 pixels.

2. **Second `columnDefs` Entry**
   <pre name="code" class="js">
   {
       targets: [4],
       render: function(data, type, row) {
           if (type === 'display' || type === 'filter') {
               var epoch = new Date(1899, 11, 30);
               var date = new Date(epoch.getTime() + data * 24 * 60 * 60 * 1000);
               var year = date.getFullYear();
               var month = ('0' + (date.getMonth() + 1)).slice(-2);
               var day = ('0' + date.getDate()).slice(-2);
               return year + '-' + month + '-' + day;
           }
           return data;
       }
   }
   </pre>
   - `targets`: Specifies the columns to which the definition applies. `[4]` targets the fifth column, JOINED_DT.
   - `render`: A function that converts the integer date value into a formatted date string in the `yyyy-MM-dd` format. The function calculates the date by adding the integer value (days) to the **epoch date** (December 30, 1899).

       An epoch date is a reference point from which time is measured. It is a specific date and time used as the starting point in a system for measuring dates. The value of a date-time variable in many systems is often the number of seconds, milliseconds, or days elapsed since the epoch date. The **Excel Epoch** is December 30, 1899. Other Epochs include
        - **Unix Epoch**: January 1, 1970 (midnight UTC/GMT)
        - **JavaScript Epoch**: January 1, 1970 (midnight UTC/GMT)
        - **Global Positioning System (GPS) Epoch**: January 6, 1980

3. **Third `columnDefs` Entry**
   <pre name="code" class="js">
   {
       "targets": [5],
       "className": "align-right",
       "render": function (data, type, row) {
           return new Intl.NumberFormat('en-US', { 
               minimumFractionDigits: 0, 
               maximumFractionDigits: 0 
           }).format(data);
       }
   }
   </pre>
   - `targets`: Specifies the columns to which the definition applies. `[5]` targets the sixth column.
   - `className`: Adds the class `align-right` to the cells in the specified column to align text to the right.
   - `render`: A function that formats the numerical data in the specified column using the `Intl.NumberFormat` object, ensuring zero decimal places.

4. **Fourth `columnDefs` Entry**
   <pre name="code" class="js">
   {
       "targets": [6],
       "className": "align-right",
       "render": function (data, type, row) {
           return new Intl.NumberFormat('en-US', { 
               minimumFractionDigits: 2, 
               maximumFractionDigits: 2 
           }).format(data);
       }
   }
   </pre>

   - `targets`: Specifies the columns to which the definition applies. `[6]` targets the seventh column.
   - `className`: Adds the class `align-right` to the cells in the specified column to align text to the right.
   - `render`: A function that formats the numerical data in the specified column using the `Intl.NumberFormat` object, ensuring two decimal places.

These configurations allow for a flexible and user-friendly table with features for exporting, filtering, and custom formatting.

This example demonstrates a basic setup with all the new functionalities included. By following this template, you can quickly implement a powerful, interactive data table in your web application.

# Dynamic Tables

Data Tables may also dynamically retrieve data from an API call.  Consider the same data that is retrieved by the following [API - https://ms-spring-server.dal1a.ciocloud.nonprod.intranet.ibm.com/api/v1/fbs-football/teams?filters=CONF_CD%3D'SEC'](https://ms-spring-server.dal1a.ciocloud.nonprod.intranet.ibm.com/api/v1/fbs-football/teams?filters=CONF_CD%3D'SEC'){:target="_blank"}.

## Example JSON Response
Here’s an example of a JSON response.

<pre name="code" class="js">
[
  {
    "code": "ALA",
    "fullKey": null,
    "description": "Crimson Tide",
    "level": 2,
    "children": null,
    "teamId": 23,
    "id": 23,
    "teamCd": "ALA",
    "nickname": "Crimson Tide",
    "institutionNm": "University of Alabama",
    "locationNm": "Tuscaloosa, Alabama",
    "foundedYr": 1831,
    "joinedDt": "1932-01-01",
    "enrollmentCnt": 38563,
    "endowmentAmt": 832.8,
    "onCampusStadiumInd": "Y",
    "confCd": "SEC",
    "divCd": "WE",
    "effTms": null,
    "expirTms": null,
    "rowStatusCd": null
  },
  {
    "code": "ARK",
    "fullKey": null,
    "description": "Razorbacks",
    "level": 2,
    "children": null,
    "teamId": 43,
    "id": 43,
    "teamCd": "ARK",
    "nickname": "Razorbacks",
    "institutionNm": "University of Arkansas",
    "locationNm": "Fayetteville, Arkansas",
    "foundedYr": 1871,
    "joinedDt": "1991-08-23",
    "enrollmentCnt": 27778,
    "endowmentAmt": 1220,
    "onCampusStadiumInd": "Y",
    "confCd": "SEC",
    "divCd": "WE",
    "effTms": null,
    "expirTms": null,
    "rowStatusCd": null
  },
  ...
</pre>

Note that the returned JSON can contain other meta-data, for example:

<pre name="code" class="js">
{
    "status": "success",
    "results": [
        {
            "code": "ALA",
            "fullKey": null,
            "description": "Crimson Tide",
            "level": 2,
            "children": null,
            "teamId": 23,
            "id": 23,
            "teamCd": "ALA",
            "nickname": "Crimson Tide",
            ...
        },
        // More team data...
    ]
}
</pre>

In this case you matches the `dataSrc` value specified in the `ajax` object.

## Explanation of `ajax` and `columns` Objects and their Properties

<pre name="code" class="js">
{
    ...
    ajax: {
        url: "https://ms-spring-server.dal1a.ciocloud.nonprod.intranet.ibm.com/api/v1/fbs-football/teams?filters=CONF_CD%3D'SEC'", // URL to fetch JSON data
        dataSrc: ''
    },
    columns: [
        { "data": "ORIG_COUNTRY_CD" },
        { "data": "ORIG_COMPANY_CD" },
        { "data": "CHRG_GROUP_CD" },
        { "data": "CHRG_GROUP_DESC" },
        { "data": "CNT" }
    ]
    ...
}
</pre>

### `ajax`
The `ajax` object is used to specify the URL from which DataTables should fetch JSON data and to define the property in the JSON response that contains the data array. This allows DataTables to dynamically populate the table with data from an API.

#### `url`
- **Description**: The `url` property specifies the endpoint of the API from which the table data will be fetched. This should be a string containing the full URL to the API endpoint.
- **Usage**: DataTables will send an HTTP request to this URL to retrieve data in JSON format.
- **Example**: `https://ms-spring-server.dal1a.ciocloud.nonprod.intranet.ibm.com/api/v1/fbs-football/teams?filters=CONF_CD%3D'SEC'`

#### `dataSrc`
- **Description**: The `dataSrc` property specifies the property in the JSON response that contains the data array. This is typically used when the JSON response contains additional metadata along with the actual data.
- **Usage**: DataTables will look for the specified property in the JSON response and use its value (which should be an array) to populate the table.
- **Example**: _blank_

### `columns`
The `columns` array defines the columns of the DataTable and specifies which property from the data source should be used to populate each column. Each object within the `columns` array corresponds to a column in the DataTable.

Each object in the `columns` array has the following property:

#### `data`
- **Description**: The `data` property specifies the property name in the data source (JSON response) that should be used to populate the corresponding column in the DataTable. This should match the key in the objects within the array from the JSON response.
- **Usage**: DataTables will look for the specified property in each object within the array and use its value to populate the cells in the corresponding column.
- **Example**: `{ "data": "teamCd" }` will populate the column with the `teamCd` property from each object in the array.



### Detailed Explanation
1. **Fetching Data**:
    - When the table is initialized, DataTables will make an HTTP GET request to the specified URL (`https://ms-spring-server.dal1a.ciocloud.nonprod.intranet.ibm.com/api/v1/fbs-football/teams?filters=CONF_CD%3D'SEC'`).

2. **Handling the Response**:
    - The JSON response from the API will be parsed.
    - DataTables will look for the property in the parsed JSON object specified by the `dataSrc` attribute (blank in this example).
    - The value should be an array containing the actual data to be displayed in the table.

3. **Populating the Table**:
    - The data within the array will be used to populate the rows of the DataTable.
    - Each object within the `results` array represents a row, and each property of the object corresponds to a column.

## Integration with Other DataTables Options
The `ajax` object can be used alongside other DataTables options, such as `columnDefs`, `buttons`, and `scrollX`, to create a fully-featured table. Here’s an example integrating the `ajax` object with other options:

<table id="id-datatable-dynamic-fbsfootball-sec" class="display" style="width:100%">
   <thead>
      <tr>
         <th>Code</th>
         <th>Name</th>
         <th>Institution</th>
         <th>Founded Year</th>
         <th>Joined Date</th>
         <th>Enrollment</th>
         <th>Endowment</th>
         <th>Conf Cd</th>
         <th>Div Cd</th>
      </tr>
   </thead>
</table>

<script>
$('#id-datatable-dynamic-fbsfootball-sec').DataTable({
    dom: 'Bfrtip',
    buttons: [
        'copy', 'csv', 'excel', 'pdf', 'print', 'colvis', 'pageLength'
    ],
    ajax:  { 
        url: "https://ms-spring-server.dal1a.ciocloud.nonprod.intranet.ibm.com/api/v1/fbs-football/teams?filters=CONF_CD%3D'SEC'", // URL to fetch JSON data
        dataSrc: ''
    },
    scrollX: true,
    columnDefs: [
        {
            "targets": [2], // Indices of columns with long content
            "createdCell": function (td, cellData, rowData, row, col) {
                $(td).addClass('min-width-200');
            }
        },
        {
            "targets": [5],
            "className": "align-right",
            "render": function ( data, type, row ) {
                return new Intl.NumberFormat('en-US', { 
                    minimumFractionDigits: 0, 
                    maximumFractionDigits: 0 
                }).format(data);
            }
        },
        {
            "targets": [6],
            "className": "align-right",
            "render": function ( data, type, row ) {
                return new Intl.NumberFormat('en-US', { 
                    minimumFractionDigits: 2, 
                    maximumFractionDigits: 2 
                }).format(data);
            }
        }
    ],
    columns: [
        { "data": "teamCd" },
        { "data": "nickname" },
        { "data": "institutionNm" },
        { "data": "foundedYr" },
        { "data": "joinedDt" },
        { "data": "enrollmentCnt" },
        { "data": "endowmentAmt" },
        { "data": "confCd" },
        { "data": "divCd" }
    ]
});
</script>

<br/>


This setup allows DataTables to fetch and display data dynamically from an API while providing rich functionality like exporting and formatting.