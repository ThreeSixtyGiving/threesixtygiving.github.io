---
layout: page
title: Reference
permalink: /docs/
---

<div id="toc"></div>

## Standard Reference

This page provides reference information on publishing to the 360 Giving Data Standard.

It assumes some technical knowledge.

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

The JSON Schema is the authoritative source of information about the standard, and it should always be possible to transform 360 Giving data into structured JSON data according to this schema. 

You can view the JSON Schema below, or [fullscreen here](/js/docson/index.html#/assets/standard/schema/360-giving-schema.json). In general, most publishers will initially only use a sub-set of the possible features of the standard, but it is designed to accommodate comprehensive data about all stages of a grant process: for a full 360-degree view.

<div style="height:400px; overflow:auto;">
<script src="/js/docson/widget.js" 
        data-schema="/assets/standard/schema/360-giving-schema.json">      
</script>
</div>

To make it possible to work with 360 Giving data in everyday desktop tools, such as Excel or OpenOffice Calc, the standard provides a number of flattened serializations. These are created using the ‘360 bridge’ tool. 

#### Summary table
In many cases, publishers have data that can be expressed in a single abbreviated table row. This is generally the case when:

* They do not have any one-to-many relationships in the data;
* They do not have data to provide detailed descriptions of every element that the 360 Giving standard requires;

For this use case we provide a summary table. This summary table flattens out properties of related entities into the main Activity table, allowing information such as the recipient organisation address, beneficiary locations and grant programme details all to be given in a single Activity row. 

For example, the structure:

* Activity
  * recipientOrganization
    * Name

can by represented in the Activity table under the column name:

* ```recipientOrganization[]/name``` 

or the column title

* ```Recipient Org:Name```

The default summary table template (with a selection of related entity properties brought into the Activity table) is defined by use of ‘rollUp’ properties in the JSON Schema file. However, it is possible, following the same naming convention for fields, to bring most properties into the Activity table if a particular use-case requires.

The naming convention for field names is to:

* If the relationship can be a one-to-many relationship, append ```[]``` to the relationship property name 
* Concatenate the relationship and property names using /
* If required, indicate the type of the column values using the ```:number```, ```:integer```, ```:string```, ```:date-time``` and so-on.

The naming convention for field titles is to:

* Concatenate the relationship and property titles using :

In the event that a value for a property is given in both a sub-table, and the summary table, the sub-table value always takes precedence, and will over-write the summary value. 


#### Multi-table data package
The basic flat template (to be provided as a data package [coming soon]) provides an Activity table, and creates a table for each of the key entities in the standard, including extra columns in these tables for:

* The ID of the Activity that the row describes;
* The relationship that the row describes (e.g. in the Organisation table, whether the row describes a Funding or Recipient organisation)

In most cases, the entry in the relevant relationship column can be ‘1’. When there are one-to-many relationships represented (e.g. multiple classifications for a single activity), then the value in the relationship column should identify the position of the particular classification in the one-to-many sequence. 

TODO: WORKED EXAMPLE HERE

TODO: To generate a flattened template

TODO: To convert a flattened template



### Field names and titles
Each entity, property and relationship in the schema has both a machine-readable field name and an English language title.

The English language titles are important for humans working to make sense of the data in everyday desktop software, and so the default Summary Template makes use of titles as opposed to field names.

This could also support provision of the template in other languages in future. 

It is possible to map between titles and field names using the information in the JSON Schema. 

TODO: Also provide JSON TABLE SCHEMA FOR EACH OF THE SUB-TABLES

## Converting data (NEED TO RUN A SET OF TESTS)




# Publication schemas

## Summary Table

Download summary table template

Excel | CSV

### Guidance

You must:

* **Read the column definitions carefully and follow the format they request** - for example, formatting identifiers and dates according to the standard
* **Provide an identifier for each grant, and whenever the status of a grant changes, update this row, including updating the last modified date**

You can:

* **Remove or hide non-required columns that you are not using** - although make sure you check any [hidden columns](#hidden-columns) before publishing your data
* **Re-order the columns** so that information is arranged in the way you want
* **Add extra columns** to include information you want to share, but that is not covered by the standard. 

You must not:

* **Add extra rows at the top of the table**
* **Change the field names provided by the standard**  

### Field definitions

<table>
    <tr>
        <th>Column Heading</th>
        <th>Description</th>
        <th>Format</th>
        <th>Field Name</th>
    </tr>
{% for field in site.data.360-summary-json-table-schema.fields %}
<tr>
    <td>{{ field.title }}</td>
    <td>{{ field.description }}</td>
    <td>{{ field.type }} {{ field.format }} </td>
    <td>{{ field.name }}</td>
</tr>
{% endfor %}
</table>



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

