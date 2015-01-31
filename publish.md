---
layout: page
title: Publish
permalink: /publish/
---
<div id="toc"></div>

Publishing 360 data is a simple process. This page will step you through the basics. 

(Page under development - contact [support](/support/)) with any questions.


## 1. Register as a publisher

Drop a line to the [support team](/support/) to register as a new 360 Giving publisher, and to request a 360 Giving prefix.

You will need your prefix to give all your grants globally unique identifiers. 

(A self-service registration system is coming soon).

## 2. Choose your template

<div class="section">
<div class="col span_1_of_3 center-text">
<img src="{{site.baseurl}}/assets/img/spreadsheet.png" class="icon-image"/>
<h4>Summary spreadsheet</h4>
One row for each grant with simple descriptive column titles. Easy to edit in spreadsheet software, or to export as a report from existing systems.
</div>
<div class="col span_1_of_3 center-text">
<img src="{{site.baseurl}}/assets/img/json.png" class="icon-image"/>
<h4>JSON</h4>
Designed for developers: a structured representation of 360 data. Ideal for building APIs onto your data.
</div>
<div class="col span_1_of_3 center-text">
<img src="{{site.baseurl}}/assets/img/package.png" class="icon-image"/>
<h4>Multi-table data package</h4>
For when you want to share more detail and have lots of one-to-many relationships in your data. 
</div>
</div>

<div class="section">
<div class="col span_1_of_3 center-text">
<a href="/assets/standard/schema/summary-table/360-giving-schema-titles.xlsx">Excel Template</a> | <a href="/assets/standard/schema/summary-table/360-giving-schema-titles.csv/Activity.csv">CSV Template</a>
</div>
<div class="col span_1_of_3 center-text">
<a href="/assets/json-template-temp.json">Template</a> | <a href="/docs/#json-schema">View schema</a>
</div>
<div class="col span_1_of_3 center-text">
<a href="/assets/standard/schema/multi-table/360-giving-schema-fields.xlsx">Excel Template</a> | Data Package Coming Soon
</div>
</div>

<br clear="all"/>

The [360 Bridge tools](/tools/) can be used to convert between different formats. 

## 3. Fill in your grants data

If you are using the JSON or multi-table templates, you should consult the schema reference for detailed definitions of each field. Users of the Summary Spreadsheet can find a description of each of the fields below. 

You might fill in the template by copying data manually - but in most cases it is possible to automatically fill in this template from your existing data. The best way to do this depends on how you currently manage your datasets. Contact the [support team](/support/) for impartial and free guidance on the best options.


### Field definitions

<table class="reference-table">
    <tr>
        <th>Column Title</th>
        <th>Description</th>
    </tr>
{% for field in site.data.360-summary-table-schema.fields %}
<tr>
    <td class="col-title">{{ field.title }}</td>
    <td class="col-desc">{{ field.description | markdownify }}</br><span class="extra-info">{{field.type}} {{field.format}}</span></td>
</tr>
{% endfor %}
</table>


## 4. Check your data

### Quality

We will soon provide online validation tools that will let you check the technical quality of your data.

For now - when you are ready with a file, e-mail it over to support@threesixtygiving.org and we'll take a look and give you feedback on it.

### Privacy

Before you publish, make sure you have checked that:

* **If you make grants on sensitive topics, you have considered what level of detail to include.** You can include as much or as little detail in 360 Giving as you wish. In most cases, more detail is better - but there may be instances where you need to be careful with what is put in the public domain. In most cases it is possible to include a row in your grant file, but with a note in the description on why full information can't be provided for this grant, or at this point in time.
* **If you give grants to individuals, that you have made a clear decision on what level of address information to include**. If you are not able to include address details or postcodes, you may be able to use web services to convert addresses to Ward or Local Authority area codes before publishing - maintaining the privacy of individual recipient addresses, whilst also providing useful location information. Contact the [support team](/support/) to find out how.
* **You have removed any private data from the spreadsheet you are sharing.** Remember - hidden columns or sheets in Excel can be unhidden by anyone with the spreadsheet. Make sure you delete data you are not planning to publish, and check it is not stored in tracked changes or version histories. This is only an issue if you created your 360 Giving data from a spreadsheet that contains additional private information.

## 5. Publish

It's time to upload your data to the Web. 

The best option is if you can host it on your own organisation web pages. We recommend following the [slashopen](http://slashopen.net) convention of placing it on a page called /open if possible. However, any stable location on your web page is possible to use.

If you cannot upload the data directly to your organisation web pages, we can help host it on our registry site. 

## 6. License your data

To make sure your information can be included in the maps, visualisations and other tools that third-parties will build using 360 Giving data you will need to provide a license statement alongside it.

When you upload data to our registry you can select a license, but you should also link to your chosen license if you publish data on your own website.

We recommend using either:

* [Public Domain Dedication](https://creativecommons.org/licenses/publicdomain/)
* [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/)

Other licenses may place restrictions on your data which prevent it being re-used, visualised and analysed. 


## 7. Tell us about it

Drop us a line to tell us about your data. Soon we will have a registry where you can register your data direct.



<script>
$('#toc').toc({
    'selectors': 'h2', //elements to use as headings
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
