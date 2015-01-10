---
layout: page
title: Documentation
permalink: /docs/
---

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

