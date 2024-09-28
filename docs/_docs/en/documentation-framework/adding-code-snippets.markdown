---
title: Adding code snippets
permalink: /en/documentation-framework/adding-code-snippets
features:
  - mermaid
abstract: >- # this means to ignore newlines until "baseurl:"
  The documentation framework allows users to highlight the syntax for many languages and script like html, xml, python, C, C++, Java, groovy etc. in a super way using Syntax Highlighter (by Alex Gorbatchev). 
---
<style>
.alert-info {
    color: #0c5460;
    background-color: #d1ecf1;
    border-color: #bee5eb;
}
.alert {
    position: relative;
    padding: 0.75rem 1.25rem;
    margin-bottom: 1rem;
    border: 1px solid transparent;
    border-radius: 0.25rem;
}
.svg-inline--fa.fa-w-16 {
    width: 1em;
}
.svg-inline--fa {
    display: inline-block;
    font-size: inherit;
    height: 1em;
    vertical-align: -0.125em;
}
</style>


To include formatted and numbered code snippets within your markdown document, enclose the snippet in `<pre>` tags, including the attributes:

- **`name`**: must be set to **`code`**.
- **`class`**: type of code snippet.  The available **class** values are:
    1. C# (`class="c-sharp"`)
    1. CSS (`class="css"`)
    1. C++ (`class="cpp"`)
    1. Delphi (`class="delphi"`)
    1. Java (`class="java"`)
    1. JavaScript (`class="js"`)
    1. PHP (`class="php"`)
    1. Python (`class="python"`)
    1. Ruby (`class="ruby"`)
    1. SQL (`class="sql"`)
    1. Visual Basic (`class="vb"`)
    1. XML / HTML (`class="xml"`)

For example:

```
<pre name="code" class="java">
public static void bubbleSort(int[] arr) {
    int n = arr.length;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap arr[j] and arr[j + 1]
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}
</pre>
```

The rendered output looks like this:


<pre name="code" class="java">
public static void bubbleSort(int[] arr) {
    int n = arr.length;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap arr[j] and arr[j + 1]
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}
</pre>


<div class="alert alert-info">
  <svg class="svg-inline--fa fa-info-circle fa-w-16" aria-hidden="true" focusable="false" data-prefix="fas" data-icon="info-circle" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" data-fa-i2svg=""><path fill="currentColor" d="M256 8C119.043 8 8 119.083 8 256c0 136.997 111.043 248 248 248s248-111.003 248-248C504 119.083 392.957 8 256 8zm0 110c23.196 0 42 18.804 42 42s-18.804 42-42 42-42-18.804-42-42 18.804-42 42-42zm56 254c0 6.627-5.373 12-12 12h-88c-6.627 0-12-5.373-12-12v-24c0-6.627 5.373-12 12-12h12v-64h-12c-6.627 0-12-5.373-12-12v-24c0-6.627 5.373-12 12-12h64c6.627 0 12 5.373 12 12v100h12c6.627 0 12 5.373 12 12v24z"></path></svg><!-- <i class="fas fa-info-circle"></i> --> <strong>Note:</strong> When using a class other than XML, any angled brackets (<>) must be escaped with &amp;lt;&amp;gt;.
</div>

## C#

```
<pre name="code" class="c-sharp">
static void BubbleSort(int[] arr) {
    int n = arr.Length;
    bool swapped;
    do {
        swapped = false;
        for (int i = 0; i < n - 1; i++)
        {
            if (arr[i] > arr[i + 1])
            {
                // Swap arr[i] and arr[i + 1]
                int temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
                swapped = true;
            }
        }
    } while (swapped);
}
</pre>
```

The rendered output looks like this:

<pre name="code" class="c-sharp">
static void BubbleSort(int[] arr) {
    int n = arr.Length;
    bool swapped;
    do {
        swapped = false;
        for (int i = 0; i < n - 1; i++)
        {
            if (arr[i] > arr[i + 1])
            {
                // Swap arr[i] and arr[i + 1]
                int temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
                swapped = true;
            }
        }
    } while (swapped);
}
</pre>

## CSS

```
<pre name="code" class="css">
button {
    box-shadow: none;
    border: 1px solid transparent;
    font-size: 14px;
    outline: none;
    line-height: 100%;
    white-space: nowrap;
    vertical-align: middle;
    padding: 0.6rem 1rem;
    border-radius: 2px;
    transition: all 0.2s ease-in-out;
    cursor: pointer;
    min-height: 38px;
}

button.primary {
    background-color: #128ff2;
    box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.12);
    color: #fff;
}
</pre>
```

The rendered output looks like this:

<pre name="code" class="css">
button {
    box-shadow: none;
    border: 1px solid transparent;
    font-size: 14px;
    outline: none;
    line-height: 100%;
    white-space: nowrap;
    vertical-align: middle;
    padding: 0.6rem 1rem;
    border-radius: 2px;
    transition: all 0.2s ease-in-out;
    cursor: pointer;
    min-height: 38px;
}

button.primary {
    background-color: #128ff2;
    box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.12);
    color: #fff;
}
</pre>

## C++

```
<pre name="code" class="cpp">
#include <iostream>

void bubbleSort(int arr[], int n) {
    bool swapped;
    for (int i = 0; i < n - 1; i++) {
        swapped = false;
        for (int j = 0; j < n - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap arr[j] and arr[j + 1]
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                swapped = true;
            }
        }
        // If no two elements were swapped in inner loop, the array is already sorted
        if (!swapped) {
            break;
        }
    }
}
</pre>
```

The rendered output looks like this:

<pre name="code" class="cpp">
#include &lt;iostream&gt;

void bubbleSort(int arr[], int n) {
    bool swapped;
    for (int i = 0; i < n - 1; i++) {
        swapped = false;
        for (int j = 0; j < n - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap arr[j] and arr[j + 1]
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                swapped = true;
            }
        }
        // If no two elements were swapped in inner loop, the array is already sorted
        if (!swapped) {
            break;
        }
    }
}
</pre>

## Delphi

```
<pre name="code" class="delphi">
procedure BubbleSort(var arr: array of Integer);
var
  n, i, j, temp: Integer;
begin
  n := Length(arr);
  for i := 0 to n - 1 do
  begin
    for j := 0 to n - i - 2 do
    begin
      if arr[j] > arr[j + 1] then
      begin
        // Swap arr[j] and arr[j + 1]
        temp := arr[j];
        arr[j] := arr[j + 1];
        arr[j + 1] := temp;
      end;
    end;
  end;
end;
</pre>
```

The rendered output looks like this:

<pre name="code" class="delphi">
procedure BubbleSort(var arr: array of Integer);
var
  n, i, j, temp: Integer;
begin
  n := Length(arr);
  for i := 0 to n - 1 do
  begin
    for j := 0 to n - i - 2 do
    begin
      if arr[j] > arr[j + 1] then
      begin
        // Swap arr[j] and arr[j + 1]
        temp := arr[j];
        arr[j] := arr[j + 1];
        arr[j + 1] := temp;
      end;
    end;
  end;
end;
</pre>

## Java

```
<pre name="code" class="java">
public static void bubbleSort(int[] arr) {
    int n = arr.length;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap arr[j] and arr[j + 1]
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}
</pre>
```

The rendered output looks like this:


<pre name="code" class="java">
public static void bubbleSort(int[] arr) {
    int n = arr.length;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap arr[j] and arr[j + 1]
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}
</pre>

## JavaScript

```
<pre name="code" class="js">
function bubbleSort(arr) {
    var len = arr.length;
    var swapped;
    do {
        swapped = false;
        for (var i = 0; i < len - 1; i++) {
            if (arr[i] > arr[i + 1]) {
                // Swap arr[i] and arr[i + 1]
                var temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
                swapped = true;
            }
        }
    } while (swapped);
}
</pre>
```

The rendered output looks like this:

<pre name="code" class="js">
function bubbleSort(arr) {
    var len = arr.length;
    var swapped;
    do {
        swapped = false;
        for (var i = 0; i < len - 1; i++) {
            if (arr[i] > arr[i + 1]) {
                // Swap arr[i] and arr[i + 1]
                var temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
                swapped = true;
            }
        }
    } while (swapped);
}
</pre>

## Php

```
<pre name="code" class="php">
<?php
function bubbleSort($arr) {
    $n = count($arr);
    $swapped = true;

    while ($swapped) {
        $swapped = false;

        for ($i = 0; $i < $n - 1; $i++) {
            if ($arr[$i] > $arr[$i + 1]) {
                // Swap $arr[$i] and $arr[$i + 1]
                $temp = $arr[$i];
                $arr[$i] = $arr[$i + 1];
                $arr[$i + 1] = $temp;
                $swapped = true;
            }
        }
    }

    return $arr;
}

// Example usage
$array = [64, 34, 25, 12, 22, 11, 90];

echo "Original array: " . implode(', ', $array) . "\n";

$sortedArray = bubbleSort($array);

echo "Sorted array: " . implode(', ', $sortedArray) . "\n";
?>
</pre>
```

The rendered output looks like this:

<pre name="code" class="php">
<?php
function bubbleSort($arr) {
    $n = count($arr);
    $swapped = true;

    while ($swapped) {
        $swapped = false;

        for ($i = 0; $i < $n - 1; $i++) {
            if ($arr[$i] > $arr[$i + 1]) {
                // Swap $arr[$i] and $arr[$i + 1]
                $temp = $arr[$i];
                $arr[$i] = $arr[$i + 1];
                $arr[$i + 1] = $temp;
                $swapped = true;
            }
        }
    }

    return $arr;
}

// Example usage
$array = [64, 34, 25, 12, 22, 11, 90];

echo "Original array: " . implode(', ', $array) . "\n";

$sortedArray = bubbleSort($array);

echo "Sorted array: " . implode(', ', $sortedArray) . "\n";
?>
</pre>

## Python

```
<pre name="code" class="python">
def bubble_sort(arr):
    n = len(arr)
    swapped = True

    while swapped:
        swapped = False

        for i in range(n - 1):
            if arr[i] > arr[i + 1]:
                # Swap arr[i] and arr[i + 1]
                arr[i], arr[i + 1] = arr[i + 1], arr[i]
                swapped = True

# Example usage
if __name__ == "__main__":
    array = [64, 34, 25, 12, 22, 11, 90]

    print("Original array:")
    print(array)

    bubble_sort(array)

    print("Sorted array:")
    print(array)
</pre>
```

The rendered output looks like this:

<pre name="code" class="python">
def bubble_sort(arr):
    n = len(arr)
    swapped = True

    while swapped:
        swapped = False

        for i in range(n - 1):
            if arr[i] > arr[i + 1]:
                # Swap arr[i] and arr[i + 1]
                arr[i], arr[i + 1] = arr[i + 1], arr[i]
                swapped = True

# Example usage
if __name__ == "__main__":
    array = [64, 34, 25, 12, 22, 11, 90]

    print("Original array:")
    print(array)

    bubble_sort(array)

    print("Sorted array:")
    print(array)
</pre>

## Visual Basic

```
<pre name="code" class="vb">
Sub BubbleSort(ByVal arr() As Integer)
    Dim n As Integer = arr.Length
    Dim swapped As Boolean

    Do
        swapped = False

        For i As Integer = 0 To n - 2
            If arr(i) > arr(i + 1) Then
                ' Swap arr(i) and arr(i + 1)
                Dim temp As Integer = arr(i)
                arr(i) = arr(i + 1)
                arr(i + 1) = temp
                swapped = True
            End If
        Next
    Loop While swapped
End Sub
</pre>
```

The rendered output looks like this:

<pre name="code" class="vb">
Sub BubbleSort(ByVal arr() As Integer)
    Dim n As Integer = arr.Length
    Dim swapped As Boolean

    Do
        swapped = False

        For i As Integer = 0 To n - 2
            If arr(i) > arr(i + 1) Then
                ' Swap arr(i) and arr(i + 1)
                Dim temp As Integer = arr(i)
                arr(i) = arr(i + 1)
                arr(i + 1) = temp
                swapped = True
            End If
        Next
    Loop While swapped
End Sub
</pre>

## SQL

```
<pre name="code" class="sql">
WITH                                                              
  WBS_RECURSION (CODE, LEVELNUM, PARENTCODE, LONGDESCRIPTION, RECORDSTATUS
               , ROW_CREATE_TS, ROW_UPDATE_TS, CODE_TYPE, COMPLIANCE_CD, USAGE_RULE)
         AS          
        (SELECT  CODE, LEVELNUM, PARENTCODE,  LONGDESCRIPTION, RECORDSTATUS
            , ROW_CREATE_TS, ROW_UPDATE_TS, CODE_TYPE, COMPLIANCE_CD, USAGE_RULE
            , 1 AS LVL         
         FROM    ERDM_ERDMPRODSTRAT.IBM_GEOGRAPHY                     
         WHERE   PARENTCODE IS NULL  --pulls the entire taxonomy
           AND   RECORDSTATUS='A'
         UNION ALL                                                
         SELECT  C.CODE, C.LEVELNUM, C.PARENTCODE, C.LONGDESCRIPTION, C.RECORDSTATUS
               , C.ROW_CREATE_TS, C.ROW_UPDATE_TS, C.CODE_TYPE, C.COMPLIANCE_CD, C.USAGE_RULE
               ,  P.LVL+1 AS LVL 
         FROM    WBS_RECURSION                    P                    
              ,  ERDM_ERDMPRODSTRAT.IBM_GEOGRAPHY C                    
         WHERE   P.CODE = C.PARENTCODE   
           AND   C.RECORDSTATUS='A'
        )                                                         
SELECT CODE, LEVELNUM, PARENTCODE,  LONGDESCRIPTION, RECORDSTATUS, ROW_CREATE_TS
     , ROW_UPDATE_TS, CODE_TYPE, COMPLIANCE_CD, USAGE_RULE
FROM   WBS_RECURSION                                              
ORDER BY LEVELNUM DESC, PARENTCODE, CODE 
</pre>
```

The rendered output looks like this:

<pre name="code" class="sql">
WITH                                                              
  WBS_RECURSION (CODE, LEVELNUM, PARENTCODE, LONGDESCRIPTION, RECORDSTATUS
               , ROW_CREATE_TS, ROW_UPDATE_TS, CODE_TYPE, COMPLIANCE_CD, USAGE_RULE)
         AS          
        (SELECT  CODE, LEVELNUM, PARENTCODE,  LONGDESCRIPTION, RECORDSTATUS
            , ROW_CREATE_TS, ROW_UPDATE_TS, CODE_TYPE, COMPLIANCE_CD, USAGE_RULE
            , 1 AS LVL         
         FROM    ERDM_ERDMPRODSTRAT.IBM_GEOGRAPHY                     
         WHERE   PARENTCODE IS NULL  --pulls the entire taxonomy
           AND   RECORDSTATUS='A'
         UNION ALL                                                
         SELECT  C.CODE, C.LEVELNUM, C.PARENTCODE, C.LONGDESCRIPTION, C.RECORDSTATUS
               , C.ROW_CREATE_TS, C.ROW_UPDATE_TS, C.CODE_TYPE, C.COMPLIANCE_CD, C.USAGE_RULE
               ,  P.LVL+1 AS LVL 
         FROM    WBS_RECURSION                    P                    
              ,  ERDM_ERDMPRODSTRAT.IBM_GEOGRAPHY C                    
         WHERE   P.CODE = C.PARENTCODE   
           AND   C.RECORDSTATUS='A'
        )                                                         
SELECT CODE, LEVELNUM, PARENTCODE,  LONGDESCRIPTION, RECORDSTATUS, ROW_CREATE_TS
     , ROW_UPDATE_TS, CODE_TYPE, COMPLIANCE_CD, USAGE_RULE
FROM   WBS_RECURSION                                              
ORDER BY LEVELNUM DESC, PARENTCODE, CODE    
</pre>

## JSON

JSON stands for JavaScript Object Notation, therefore format using the class equal to `js`.

```
<pre name="code" class="js">
[
  {
    "code": "10J00",
    "fullKey": "10J00",
    "description": "IBM Consulting",
    "level": 0,
    "children": [
      {
        "code": "15BS",
        "fullKey": "10J00:15BS",
        "description": "Business Support",
        "level": 1,
        "children": null,
        "growthPlatformId": 10000,
        "growthPlatformCd": "15BS",
        "growthPlatformNm": "Business Support",
        "growthPlatformDesc": "Business Support",
        "lgcyGrowthPlatformCd": null,
        "brandCd": "10J00",
        "effTms": null,
        "expirTms": null,
        "rowStatusCd": null
      },
      {
        "code": "15CAI",
        "fullKey": "10J00:15CAI",
        "description": "Hybrid Cloud Services",
        "level": 1,
        "children": null,
        "growthPlatformId": 10001,
        "growthPlatformCd": "15CAI",
        "growthPlatformNm": "Hybrid Cloud Services",
        "growthPlatformDesc": "Hybrid Cloud Services",
        "lgcyGrowthPlatformCd": "CA",
        "brandCd": "10J00",
        "effTms": null,
        "expirTms": null,
        "rowStatusCd": null
      },
      {
        "code": "15CPT",
        "fullKey": "10J00:15CPT",
        "description": "Business Transformation Services",
        "level": 1,
        "children": null,
        "growthPlatformId": 10002,
        "growthPlatformCd": "15CPT",
        "growthPlatformNm": "Business Transformation Services",
        "growthPlatformDesc": "Business Transformation Services",
        "lgcyGrowthPlatformCd": "CP",
        "brandCd": "10J00",
        "effTms": null,
        "expirTms": null,
        "rowStatusCd": null
      },
      {
        "code": "15GEN",
        "fullKey": "10J00:15GEN",
        "description": "Sec/Ind-aligned JRSs",
        "level": 1,
        "children": null,
        "growthPlatformId": 10004,
        "growthPlatformCd": "15GEN",
        "growthPlatformNm": "Sec/Ind-aligned JRSs",
        "growthPlatformDesc": "Sector/Industry-aligned JRSs",
        "lgcyGrowthPlatformCd": null,
        "brandCd": "10J00",
        "effTms": null,
        "expirTms": null,
        "rowStatusCd": null
      },
      {
        "code": "15STS",
        "fullKey": "10J00:15STS",
        "description": "Cybersecurity Services",
        "level": 1,
        "children": null,
        "growthPlatformId": 3,
        "growthPlatformCd": "15STS",
        "growthPlatformNm": "Cybersecurity Services",
        "growthPlatformDesc": "Cybersecurity Services",
        "lgcyGrowthPlatformCd": null,
        "brandCd": "10J00",
        "effTms": null,
        "expirTms": null,
        "rowStatusCd": null
      },
      {
        "code": "15TSL",
        "fullKey": "10J00:15TSL",
        "description": "IBM Consulting Top Service Line (AUO)",
        "level": 1,
        "children": null,
        "growthPlatformId": 10003,
        "growthPlatformCd": "15TSL",
        "growthPlatformNm": "IBM Consulting Top Service Line (AUO)",
        "growthPlatformDesc": "IBM Consulting Top Service Line (AUO)",
        "lgcyGrowthPlatformCd": "TP",
        "brandCd": "10J00",
        "effTms": null,
        "expirTms": null,
        "rowStatusCd": null
      }
    ],
    "brandId": 1,
    "brandCd": "10J00",
    "brandNm": "IBM Consulting",
    "brandDesc": "IBM Consulting",
    "lgcyBrandCd": null,
    "effTms": null,
    "expirTms": null,
    "rowStatusCd": null
  }
]
</pre>

```

The rendered output looks like this:

<pre name="code" class="js">
[
  {
    "code": "10J00",
    "fullKey": "10J00",
    "description": "IBM Consulting",
    "level": 0,
    "children": [
      {
        "code": "15BS",
        "fullKey": "10J00:15BS",
        "description": "Business Support",
        "level": 1,
        "children": null,
        "growthPlatformId": 10000,
        "growthPlatformCd": "15BS",
        "growthPlatformNm": "Business Support",
        "growthPlatformDesc": "Business Support",
        "lgcyGrowthPlatformCd": null,
        "brandCd": "10J00",
        "effTms": null,
        "expirTms": null,
        "rowStatusCd": null
      },
      {
        "code": "15CAI",
        "fullKey": "10J00:15CAI",
        "description": "Hybrid Cloud Services",
        "level": 1,
        "children": null,
        "growthPlatformId": 10001,
        "growthPlatformCd": "15CAI",
        "growthPlatformNm": "Hybrid Cloud Services",
        "growthPlatformDesc": "Hybrid Cloud Services",
        "lgcyGrowthPlatformCd": "CA",
        "brandCd": "10J00",
        "effTms": null,
        "expirTms": null,
        "rowStatusCd": null
      },
      {
        "code": "15CPT",
        "fullKey": "10J00:15CPT",
        "description": "Business Transformation Services",
        "level": 1,
        "children": null,
        "growthPlatformId": 10002,
        "growthPlatformCd": "15CPT",
        "growthPlatformNm": "Business Transformation Services",
        "growthPlatformDesc": "Business Transformation Services",
        "lgcyGrowthPlatformCd": "CP",
        "brandCd": "10J00",
        "effTms": null,
        "expirTms": null,
        "rowStatusCd": null
      },
      {
        "code": "15GEN",
        "fullKey": "10J00:15GEN",
        "description": "Sec/Ind-aligned JRSs",
        "level": 1,
        "children": null,
        "growthPlatformId": 10004,
        "growthPlatformCd": "15GEN",
        "growthPlatformNm": "Sec/Ind-aligned JRSs",
        "growthPlatformDesc": "Sector/Industry-aligned JRSs",
        "lgcyGrowthPlatformCd": null,
        "brandCd": "10J00",
        "effTms": null,
        "expirTms": null,
        "rowStatusCd": null
      },
      {
        "code": "15STS",
        "fullKey": "10J00:15STS",
        "description": "Cybersecurity Services",
        "level": 1,
        "children": null,
        "growthPlatformId": 3,
        "growthPlatformCd": "15STS",
        "growthPlatformNm": "Cybersecurity Services",
        "growthPlatformDesc": "Cybersecurity Services",
        "lgcyGrowthPlatformCd": null,
        "brandCd": "10J00",
        "effTms": null,
        "expirTms": null,
        "rowStatusCd": null
      },
      {
        "code": "15TSL",
        "fullKey": "10J00:15TSL",
        "description": "IBM Consulting Top Service Line (AUO)",
        "level": 1,
        "children": null,
        "growthPlatformId": 10003,
        "growthPlatformCd": "15TSL",
        "growthPlatformNm": "IBM Consulting Top Service Line (AUO)",
        "growthPlatformDesc": "IBM Consulting Top Service Line (AUO)",
        "lgcyGrowthPlatformCd": "TP",
        "brandCd": "10J00",
        "effTms": null,
        "expirTms": null,
        "rowStatusCd": null
      }
    ],
    "brandId": 1,
    "brandCd": "10J00",
    "brandNm": "IBM Consulting",
    "brandDesc": "IBM Consulting",
    "lgcyBrandCd": null,
    "effTms": null,
    "expirTms": null,
    "rowStatusCd": null
  }
]
</pre>


## XML

```
<pre name="code" class="xml">
<?xml version="1.0" encoding="UTF-8"?>
<library>
  <book>
    <title>Harry Potter and the Sorcerer's Stone</title>
    <author>J.K. Rowling</author>
    <published>1997</published>
  </book>
  <book>
    <title>The Hobbit</title>
    <author>J.R.R. Tolkien</author>
    <published>1937</published>
  </book>
  <book>
    <title>To Kill a Mockingbird</title>
    <author>Harper Lee</author>
    <published>1960</published>
  </book>
</library>

</pre>
```

The rendered output looks like this:

<pre name="code" class="xml">
<?xml version="1.0" encoding="UTF-8"?>
<library>
  <book>
    <title>Harry Potter and the Sorcerer's Stone</title>
    <author>J.K. Rowling</author>
    <published>1997</published>
  </book>
  <book>
    <title>The Hobbit</title>
    <author>J.R.R. Tolkien</author>
    <published>1937</published>
  </book>
  <book>
    <title>To Kill a Mockingbird</title>
    <author>Harper Lee</author>
    <published>1960</published>
  </book>
</library>

</pre>
