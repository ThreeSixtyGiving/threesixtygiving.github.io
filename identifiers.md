---
layout: page
title: Identifiers
permalink: /Identifiers/
---

## Why we need identifiers
Identifiers are an important part of any dataset. They let a computer uniquely identify and refer to specific grants, organisations, transactions and so-on. 

Whilst a human being may be good at recognising that:

>INDIGO TRUST

>The Indigo Trust

and

>indigo-trust

all refer to the same organisation, computers find this is lot trickier. 

That's why 360 Giving requires you to give identifiers to:

* Grants;
* Transactions; 
* Classifications;
* Organisations;
* and other unique elements in your data.

These go in ```Identifier``` columns alongside human-readable text descriptions of the grant, the name of an organisation, or the title of a classification.

## Creating identifiers

Often you will already have identifiers in your own records. For example, you might assign a numbers to each application or grant, or you might record a reference number for a funding recipient.

You can use these existing **internal identifiers** in constructing the identifiers that you will use in your 360 Giving data files. 

*However,* because there might be an overlap between the internal identifiers you use, and the internal identifiers another funder uses, in 360 Giving you add a **prefix** to your internal identifiers. 

> For example, if Indigo Trust have a grant called 'Grant27', and Nominet Trust also have a grant called 'Grant27' the two will get confused when combining the two datasets. But if, when publishing, each one adds a prefix, then we end up with two unique identifiers: '360G-indigotrust-Grant27' and '360G-Nominet-Grant27'

For your grants, and any <span class="tooltip" title="For example, you might maintain your own codes to classify grants, or you might have an internal numbering scheme for organisations rather than recording charity and company numbers.">other identifiers that are particular to your organisation</span>, you use can use a **360 Giving prefix**. You can get this when registering on the data registry. 

For organisation identifiers, follow the [organisation identifier](#organisation-identifier) guidance below which is designed to support links to be made between 360 Giving, and other datasets about an organisation.

## Using your identifiers

We use simple text identifiers in 360 Giving. As well as using these identifiers in your published data, you could also tell your grantees their prefixed identifier, and encourage them to include it in any documents they publish about their funded projects, or to include it as a 'machine tag' when uploading photos and videos to social media sites. 

> For example, some of the development of 360 Giving was funded by grant '360G-indigotrust:IND233'. If you [search the web for that identifier](https://www.google.co.uk/search?q=360G-indigotrust%3AIND233), you will find this site. If there were project reports published online about this grant, or photos and videos, you might be able to discover those as well. If you just searched for the **internal identifer** [IND233](https://www.google.co.uk/search?q=IND233) you would have to comb through details of all sorts of other things identified as IND233 before finding any information about the grant.

You can also make use of your 360 Giving identifiers in internal reports and documents, as this will make it easier to digitally link these up with the data in your 360 Giving data files in future.

## Register a prefix

To register a prefix see the [publisher guidance](/publish/).

All registered prefixes should start with 360G unless you have been advised otherwise by the support team. 

# Grant Identifier

To create your grant identifiers:

1. Make sure you have registered for 360 Giving prefix;
2. Look for an <span class="tooltip" title="This might be a sequential number assigned to each grant at the point of application, or a combination of the 'funding scheme' identifier and a sequential number for the grant. The important thing is that the identifier should be unique inside your organisation, so adding the prefix will make it unique across the whole world.">existing internal identifier</span> given to your grants;
2. Add this onto the end of your 360 Giving prefix;

For example, if your prefix is ```360G-xyztrust``` and you have a grant identified internally as '123', you would combine these to give:

>360G-xyztrust-123

If your internal identifiers include spaces or special characters, we recommend replacing these with underscore (_).

There are no set rules on the separator to use between your prefix and the internal identifier but we recommend using a hyphen (-).

# Organisation Identifier

There are many different kinds of grant recipient, including:

* Registered companies
* Registered charities
* Community organisations
* Overseas organisations
* Individuals

Some recipients will have official registration numbers that can be used to identify them. Wherever possible 360 Giving encourages you to collect and record these registered identifiers. Other types of grant recipient are not registered anywhere, and so you may only have names, or internal IDs, for them recorded on your data.

To give users of 360 Giving data the best chance of joining up information about the same organisations across different data files, we follow a simple methodology to create Organisation Identifiers.

This can be summarised through the following process. As soon as a step gives you an identifier, you can stop at that step and use the given identifier. 

1. If you have a **registered company number** for the organisation, use the prefix 'GB-COH-' and the registered number (indicating that the number could be looked up at [Companies House](http://www.companieshouse.gov.uk))

2. If you have a **registered charity number** for the organisation, use the prefix 'GB-CHC-' for a charity [registered in England and Wales](www.charitycommission.gov.uk/), 'GB-SC-' for a [charity registered in Scotland](http://www.oscr.org.uk/), or 'GB-NIC-' for a [charity registered in Northern Ireland](http://www.charitycommissionni.org.uk/) along with the registered number.

3. If you have a registered number from some other scheme, including overseas registrars, check the [IATI Organisation Registration Codelist](http://iatistandard.org/201/codelists/OrganisationRegistrationAgency/) for a prefix to use. If the prefix you need is not listed, [contact the support team](/support/).

4. If you do not have any external registration numbers for the organisation, use your 360 Giving prefix and <span class="tooltip" title="If you use a database that records details of organisations in a separate lookup table, this may provide an identifier you can use. If you only record data in a spreadsheet, and don't assign organisations an ID, you could use a spreadsheet formula to turn the organisation name into an identifier (e.g. removing spaces and lowercasing the name). The support team can provide guidance on this. If there is a chance that your organisation identifiers might overlap with grant identifiers, just add 'ORG' into the identifier string (e.g. '360G-xyztrust-ORG123')">any internal identifier you have for this organisation</span>. 

Sometimes you may have recorded both the company number, and charity number, of an organisation in your data. Because having both of these is important, 360 Giving also includes two extra separate fields for ```Company Number``` and ```Charity Number```. If you have these details, you should fill them in, in addition to providing the unique organisation identifier using the method above. 


# Codes

Contact support for details of prefixes to use when publishing classification codes for your grants.