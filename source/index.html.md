---
title: BuilderJS API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Download BuilderJS 2.0 Now</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to **BuilderJS 2.0**, the most powerful Email or Web Page Builder tool. BuilderJS is the easiest, quickest way to design elegant, mobile responsive emails or pages for your business.

BuilderJS is made in pure Javascript and HTML, making it easy to integrate with any web application no matter what the backend programming language is (Java, .Net, PHP, Ruby on Rails, Python, etc.)

BuilderJS is made fully customizable and open to any integration scenario: you can make it a standalone web page or embed it into your own site. For example, when it comes to save user work, BuilderJS allow you to configure a Save URI, to which it will make a POST request, passing the latest updates to the server side scripting for handling. The request is triggered when user clicks on Save button in the builder. And there are lots of other configuration settings allowing you to customize how it works and interact with the your other components.

This API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to help contribute to the our documentation.

# Quick Installation

> Put the following HTML / JavaScript code snipets to your HTML page:

```html
<html>
    <head>
        <link rel="stylesheet" href="builderjs/builder.min.css"></link>
        <script type='text/javascript' src="builderjs/builder.min.js"></script>
    </head>
    <body>
        <script language="Javascript">
            var builder = new Builder();
            builder.render(document.body);
        </script>
    </body>
</html>
```

> It's that simple! The `render()` function will do the magic of rendering the entire builder view with its default settings and append it to your page's `body`.

BuilderJS comes with `render()` helper function allowing you to quickly initiate the builder and append it to your current web page. [developer portal](http://example.com/developers).

Simply include the BuilderJS JavaScript and CSS files to your HTML page and initiate it on page load. See sample code to see how easy it is to load a fully-functioning builder to your webpage. With minimum configuration like that, the builder loads with a default blank design page like below

![Default Blank Page](https://camo.envatousercontent.com/4836be2faacd94b1f6eb8558ad3e7cf3eb50d914/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6163656c6c656d61696c2f6c616e64696e672d706167652d62616e6e65722e706e67 "Default Blank Page")

<aside class="notice">
Instantiate the <code>builder</code> variable without any parameters and use <code>render()</code> helper function is the easiest way to get started with the builder. See more advanced configuration options in the next sections of this document.
</aside>

# Configuration

## Load a Template

By default BuilderJS loads with a blank design for you to start making your own page / email. You can also start working with an existing email or page template by loading it into the design view. There are 2 options for loading an existing template

### From HTML string

```javascript
var builder = new Builder();
builder.render(document.body);
builder.load('<div> <h1>Awesome title</h1> <p> Page content... </p> </div>')
```

Use the `load(html)` function, passing an HTML string. See code example in the right panel

Parameter | Default | Description
--------- | ------- | -----------
html | [empty] | HTML content for loading to the viewer

### From a URL

Very often, your template is also available as a public URL. Then you can pass it to the `url` parameter to your builder initialization code. See example in the right panel

```javascript
var builder = new Builder({
    url: 'http://example.com/template/2001990'
});
builder.render(document.body);
```

Parameter | Default | Description
--------- | ------- | -----------
url | null | URL to the template page which will be fetched and loaded to the builder

<aside class="success">
You can try passing with any URL to the `url` parameter of the builder initialization function for experiment. BuilderJS can load also every website with HTML content to its design view
</aside>

### Upload a template

Remember that BuildJS is a pure front-end application. Uploading a template to the server requires server scripting language like Ruby on Rails, PHP, Java... to handle file upload and pass the URL of the newly uploaded template as `url` parameter of the builder construction function.

## Tags

Tag is a powerful feature of BuildJS, allowing users to inject dynamic content to page or email content. For example, very often user wants to inject a dynamic contact first name or last name to an email template. dynamic content can be achieved by inserting a place holder, or, in other word, a tag to your email or page content. When it come to load your page or send your email, tags will be translated to an appropriate value. Example of tags are

{CONTACT_FIRST_NAME}
{CONTACT_LAST_NAME}

Other examples of constant tag

{CURRENT_DATE}
{CURRENT_TIME}

You can define your own list of tags and pass those to the `tags` parameter of BuilderJS construction. There are 3 types of tags

* Display tag
* Action tag
* Binding tag

### Display tags

```javascript
var builder = new Builder({
    tags: [
      {name: 'First Name', type: 'display'},
      {name: 'Last Name', type: 'display'},
      {name: 'Current Year', type: 'display'},
      {name: 'Current Date', type: 'display'},
    ]
});
builder.render(document.body);
```

Display tags are simple tags that represent a dynamic value like contact first name, last name, etc. or a constant value like current year, current date. See sample code in the right panel to see how to pass display tags to BuilderJS

The very question that may come to your mind is: why do I have to pass tags to the builder?

BuilderJS has a very powerful feature allowing you to drag and drop a tag to your template content page, without you having to manually type in the tag. Even more, you can benefit from tag autocomplete feature. That is, just type an open bracket and BuilderJS will render a autocomplete dropdown list of all available tags for you

That's how BuilderJS helps with tag editing, making it easy for user to add tags to email or page content.

## Other Settings

Below is the complete list of configuration settings (optional) that can be passed to the Builder construction

### Construction Parameters

Parameter | Description
--------- | -----------
url | URL of the template to be loaded. If not provided, BuildJS will load a blank design page
backUrl | URL of the page that builder redirects to when Exit or Back button is clicked
templates | List of templates available for user to choose from. See Templates section for details
title | Title to set for the current HTML page, overwriting the `<title>` tag value
saveUrl | The URL to which BuilderJS submits its latest content for storing (handled by server script). See Storage section for details
tags | Tags used by the BuilderJS to represent a dynamic value. See Tags section for the details
view | Possible values include `design` and `preview`. Tell the builder to open in design or preview mode

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

# Key Features

## Visual Drag & Drop Editor

BuilderJS comes as a fully-functioned visual Drag & Drop editor, allowing you to quickly build your page or email templates without any hassle

## Source Editor

For advanced user, BuilderJS also supports a source editor which allow you to completely customize your page or email design using HTML / CSS

## Template

With BuilderJS, you can always start from a great template to taylor it, making it your own without having to make a design from scratch. BuilderJS support all possible ways of loading your template: from HTML string, from a public web URL or by uploading a template package from your PC

## Responsive

## HTML Widget

With BuilderJS, you can always start from a great template to taylor it, making it your own without having to make a design from scratch. BuilderJS support all possible ways of loading your template: from HTML string, from a public web URL or by uploading a template package from your PC

## Customizable Widgets

With BuilderJS, you can always start from a great template to taylor it, making it your own without having to make a design from scratch. BuilderJS support all possible ways of loading your template: from HTML string, from a public web URL or by uploading a template package from your PC

# Storage

When it comes to save user work, **BuilderJS** allow you to configure a Save URI, to which it will make a POST request, passing the latest updates to the server side scripting for handling. The request is triggered when user clicks on Save button in the builder.

Actual job of storing the submitted content is handled by a server-side scripting language like Ruby, PHP, Java, .Net, etc.

Below is an example of how BuilderJS sends its content to the server. By default, when user clicks Save button, BuilderJS makes a `POST` request to the URL specified by `url` parameter in the builder construction settings.

`POST http://example/template/save`

# Integration

# Customization

# SaaS Support

BuilderJS is also pre-design for SaaS (Software as a Service). That is, you have full control of how BuilderJS features are available to your users. For example, you can always turn a feature ON or OFF for different types of users.
