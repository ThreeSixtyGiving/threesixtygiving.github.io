---
layout: page
title: Reference
permalink: /docs/
---

<div id="toc"></div>

## Standard Reference

This page provides reference information on publishing to the 360 Giving Data Standard.

It assumes some technical knowledge.

If you are just getting started with the 360 Giving data standard, consult the [publish](/publish/) pages.

## Data formats

### Summary

There are three main formats available for representing 360 Giving data.

1. **Summary spreadsheet**: provided with user-friendly **column titles**, and for recording one grant per row. This is the most common template that publishers choose. CSV, Excel, Documentation
2. **Multi-table data package** (under development): for when you have more in-depth information to share, such as the location of multiple beneficiary groups, or detailed payments schedules. Provided with machine-readable field names.  <i class="fa fa-envelope-o"></i> [ Get in touch](/support/) if you would like to use this format. 
3. **JSON Schema**: for providing a structured representation of your data direct from your internal databases or via an API. Ideal for direct use by developers building visualisations and web apps. Schema

The [‘360 Bridge’ tool](/tools/) will convert between each of these template formats, providing structured data for developers, and spreadsheet simplicity if you want to browse, sort and filter data on your desktop. 

### Data model & serialisation

The 360 Giving standard is defined by a modified [JSON Schema](http://json-schema.org/). This describes the entities that can be described using the standard, and the properties recognised by the standard. 

At the root of the data model is a grant-making Activity. Activities have a number of direct properties (e.g. Title, Description, Currency, Amount Awarded etc.) and then a number of related entities, including Organisations (Funder and Recipient), Locations (Recipient, Beneficiary), Classifications, Grant Programmes, and Transactions. 

#### JSON Schema
The JSON Schema is the authoritative source of information about the standard, and it should always be possible to transform 360 Giving data into structured JSON data according to this schema. 

You can view the JSON Schema below, or [fullscreen here](/js/docson/index.html#/assets/standard/schema/360-giving-schema.json). In general, most publishers will initially only use a sub-set of the possible features of the standard, but it is designed to accommodate comprehensive data about all stages of a grant process: for a full 360-degree view.

<div style="height:400px; overflow:auto; border:1px solid grey;">
<script src="/js/docson/widget.js" 
        data-schema="/assets/standard/schema/360-giving-schema.json">      
</script>
</div>

To make it possible to work with 360 Giving data in everyday desktop tools, such as Excel or OpenOffice Calc, the standard provides a number of flattened serializations. These are created using the ‘360 bridge’ tool. 

### Field names and titles

Each entity, property and relationship in the schema has both a machine-readable field name and an English language title.

The English language titles are important for humans working to make sense of the data in everyday desktop software, and so the default Summary Template makes use of titles as opposed to field names. 

The field names are important for computers reading the data, and even if other language titles are provided in future, the underlying field names will remain constant.

A mapping between column titles and field names for the Summary Table is given below:

<table>
    <tr>
        <th>Column Title</th>
        <th>Field Name</th>
    </tr>
{% for field in site.data.360-summary-table-schema.fields %}
<tr>
    <td>{{ field.title }} {%if field.required %}*{%endif%}</td>
    <td>{{ field.name }}</td>
</tr>
{% endfor %}
</table>

### Summary spreadsheet
In many cases, publishers have data that can be expressed in a single abbreviated table row. This is generally the case when:

* They do not have any one-to-many relationships in the data;
* They do not have data to provide detailed descriptions of every element that the 360 Giving standard requires;

For this use case we provide a summary table. This summary table flattens out selected properties of related entities into the main Activity table, allowing information such as the recipient organisation address, beneficiary locations and grant programme details all to be given in a single Activity row. To ensure it is user-friendly, the summary table also uses titles, rather than field names.

You can download the Summary Template as a [CSV File](/assets/standard/schema/summary-table/360-giving-schema-titles.csv/Activity.csv), or you can find it in the Activity tab of [this Excel template](/assets/standard/schema/summary-table/360-giving-schema-titles.xlsx), or you can scroll through the template table below.

<div style="width:100%; overflow:auto; border:1px solid grey;">
    (<a href="javascript:$('.extra-info').toggle();">Toggle field information</a>)
<table class="schema-table">
<tr class="schema-title">
    <td class="extra-info" style="background-color:white;"><strong>Column Title &gt;</strong></td>
{% for field in site.data.360-summary-table-schema.fields %}
    <td>{{ field.title }}</td>
{% endfor %}
</tr>
<tr class="schema-format">
    <td class="extra-info"></td>
{% for field in site.data.360-summary-table-schema.fields %}
    <td> - </td>
{% endfor %}
</tr>

<tr class="schema-format extra-info">
    <td class="extra-info"><strong>Variable Type &gt;</strong></td>
{% for field in site.data.360-summary-table-schema.fields %}
    <td> {{ field.type }} {{ field.format }} </td>
{% endfor %}
</tr>
<tr class="schema-fieldname extra-info">
    <td class="extra-info"><strong>Field name &gt;</strong></td>
{% for field in site.data.360-summary-table-schema.fields %}
    <td> {{ field.name }} </td>
{% endfor %}
</tr>
</table>
</div>

<br/>

#### Guidance

You must:

* **Read the column definitions carefully and follow the format they request** - for example, formatting identifiers and dates according to the standard. Full reference information is provided below.
* **Provide an identifier for each grant, and whenever the status of a grant changes, update this row, including updating the last modified date**

You can:

* **Remove or hide non-required columns that you are not using** - although make sure you check any [hidden columns](#hidden-columns) before publishing your data, and always remove rather than hide sensitive information.
* **Re-order the columns** so that information is arranged in the way you want
* **Add extra columns** to include information you want to share, but that is not covered by the standard. 

You must not:

* **Add extra rows at the top of the table**
* **Change the field names provided by the standard**

#### Extending the summary table
The default summary table template is defined by use of special ‘rollUp’ properties in the [underlying JSON Schema file](/assets/standard/schema/360-giving-schema.json). The [360 Bridge](/tools/) tool uses these properties when creating templates. However, it is possible, following the same naming convention for fields, to bring most properties into the Activity table if a particular use-case requires. 

For example, the structure:

* Activity
  * relatedDocument
    * url

can by represented in the Activity table under the column name:

* ```relatedDocument[]/url``` 

or the column title

* ```Related Document:Web Address```

The naming convention for field names is to:

* If the relationship can be a one-to-many relationship, append ```[]``` to the relationship property name 
* Concatenate the relationship and property names using /
* If required, indicate the type of the column values using the ```:number```, ```:integer```, ```:string```, ```:date-time``` and so-on.

The naming convention for field titles is to:

* Concatenate the relationship and property titles using :

In the event that a value for a property is given in both a sub-table, and the summary table, the sub-table value always takes precedence, and will over-write the summary value. 


### Multi-table data package

The machine-readable multi-table template provides an Activity table, and creates a table for each of the key entities in the standard, including extra columns in these tables for:

* The ID of the Activity that the row describes;
* The relationship that the row describes (e.g. in the Organisation table, whether the row describes a Funding or Recipient organisation)

In most cases, the entry in the relevant relationship column can be ‘1’. When there are one-to-many relationships represented (e.g. multiple classifications for a single activity), then the value in the relationship column should identify the position of the particular classification in the one-to-many sequence. 

You can find the [multi-table Excel template here](/assets/standard/schema/multi-table/360-giving-schema-fields.xlsx). 

The summary spreadsheet Excel template (see above) also includes additional tabs, so that in cases where most data can fit in a summary table, but a few one-to-many relationships are required, this simpler human-readable template can be used.

In future, the machine-readable multi-table template will be provided as a data package. 

TODO: Provide Excel and Datapackage multi-table templates

TODO: WORKED EXAMPLE HERE

TODO: To generate a flattened template

TODO: To convert a flattened template

### JSON

When data is being generated directly out of a database system, publishers should consider using the JSON schema to provide a JSON file.

Developers may also wish to build their applications of JSON versions of the data. 

The [360 Bridge tool](/tools/) supports round-tripping of data between Summary spreadsheet, multi-table datapackage and JSON representations. 

## Schema documentation


Identifiers are documented on the [identifiers](/identifiers/) pages.




<script>
$('#toc').toc({
    'selectors': 'h2,h3,h4', //elements to use as headings
    'smoothScrolling': true, //enable or disable smooth scrolling on click
    'prefix': 'toc', //prefix for anchor tags and class names
    'onHighlight': function(el) {}, //called when a new section is highlighted 
    'highlightOnScroll': true, //add class to heading that is currently in focus
    'highlightOffset': 100, //offset to trigger the next headline
    'anchorName': function(i, heading, prefix) { //custom function for anchor name
        return prefix+i;
    },
    'headerText': function(i, heading, $heading) { //custom function building the header-item text
        return $heading.text();
    }
});
</script>

