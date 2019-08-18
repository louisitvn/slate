---
title: BuilderJS API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript
  - php
  - ruby
  - python

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

# Get Started

## Quick installation

> Put the following HTML / JavaScript code snipets to your HTML page:

```html
<html>
    <head>
        <link rel="stylesheet" href="builderjs/builder.min.css"></link>
        <script type='text/javascript' src="builderjs/builder.min.js"></script>
    </head>
    <body>
        <script language="Javascript">
            var builder = new Editor();
            builder.init();
        </script>
    </body>
</html>
```

> It's that simple! The builder's `init()` function will do the magic of rendering the entire builder view with its default settings and append it to your page's `body`.

BuilderJS comes with `init()` helper function allowing you to quickly initiate the builder and append it to your current web page.

Simply include the BuilderJS JavaScript and CSS files to your HTML page and initiate it on page load. See sample code to see how easy it is to load a fully-functioning builder to your webpage. With minimum configuration like that, the builder loads with a default blank design page like below

![Default Blank Page](https://builderjs.s3.amazonaws.com/BuilderJS-00303.png "Default Blank Page")

<aside class="notice">
Instantiate the <code>builder</code> variable without any parameters and use <code>init()</code> helper function is the easiest way to get started with the builder. See more advanced configuration options in the next sections of this document.
</aside>

## Examples

BuilderJS also comes with a sample package so that you can quickly explore the builder features. Just put the `sample` folder to your document root and open it in a web browser to see it in action

`http://example.com/sample/`

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

<aside class="warning">
Loading a template from an HTML string is not a good practice and is, in general, not recommended. The preferred way is to load it from a public URL. See section below for details
</aside>

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

```javascript
// Initialize BuilderJS with tags

var builder = new Editor({
    tags: [
      {name: 'First Name', type: 'display'},
      {name: 'Last Name', type: 'display'},
      {name: 'Current Year', type: 'display'},
      {name: 'Current Date', type: 'display'},
    ]
});
builder.render(document.body);
```

Tag is a powerful feature of BuildJS, allowing users to inject dynamic content to page or email content. For example, very often user wants to inject a dynamic contact first name or last name to an email template. Dynamic content can be achieved by inserting a place holder, or, in other word, a tag to your email or page content. When it comes to load your page or send your email, tags will be translated to appropriate values. Example of tags are:

* {CONTACT_FIRST_NAME}
* {CONTACT_LAST_NAME}
* {PRODUC_TITLE}
* {PRODUC_PRICE}
* {PRODUC_DESCRIPTION}
* {ORDER_NUMBER}
* {ORDER_VOLUME}
* {ORDER_AMOUNT}

Other examples of constant tags

* {CURRENT_DATE}
* {CURRENT_TIME}

You can define your own list of tags and pass those to the `tags` parameter of BuilderJS construction. BuilderJS has a very powerful feature allowing you to drag and drop a tag to your template content page, without you having to manually type in the tag. Even more, you can benefit from tag autocomplete feature. That is, just type an open bracket and BuilderJS will render a autocomplete dropdown list of all available tags for you

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

# Key Features

## Visual Drag & Drop Editor

BuilderJS comes as a fully-functioned visual Drag & Drop editor, allowing you to quickly build your page or email templates without any hassle

## Source Editor

Beside the visual Drag & Drop editor, BuilderJS also supports a Source Editor which allows you to completely customize your page or email design by updating HTML / CSS directly. This is for advanced users who are familiar with HTML / CSS markup language

![Source Editor](https://builderjs.s3.amazonaws.com/BuilderJS-Source-View.png "Source Editor")

## Template

```javascript
// Pass a list of available templates to the builder
// which will be available for user to choose from
// by going to Design > New From A Template

// List of available templates
var templates = [
  {
      name: 'My Awesome Template 1',
      url: 'http://example.com/template/030331',
      thumbnail: 'http://example.com/template/030331/thumb.png'
  }, {
      name: 'My Awesome Template 2',
      url: 'http://example.com/template/030332',
      thumbnail: 'http://example.com/template/030332/thumb.png'
  }, {
      name: 'My Awesome Template 3',
      url: 'http://example.com/template/030333',
      thumbnail: 'http://example.com/template/030333/thumb.png'
  }, {
      name: 'My Awesome Template 4',
      url: 'http://example.com/template/030334',
      thumbnail: 'templates/030334/thumb.png'
  }
];

// Pass to the builder
var builder = new Editor({
    templates: templates
});
```

> Notice that `templates` parameter expects an array of templates, each with `name`, `url` and `thumbnail`

BuilderJS allows you to create new blank workspace and build your design from scratch.
However, most of the time, you may want to start making your own email or page design from an existing template, then taylor it to your own needs.

You can also pass a list of available templates to BuilderJS, and it will in turn show up to user for choosing from, by going to `Design > New From Template`

![Available Templates selection](https://builderjs.s3.amazonaws.com/BuilderJS-Template-Selection.png "Available Templates selection")

See example on the right to find out how to pass a list of available templates to your builder.

## Responsive

BuilderJS supports making email or pages that are fully responsive. You can preview your design with a PC, tablet or mobile phone simulator supported by BuilderJS. It is to make sure your email or page will show up correctly in reality

## HTML Widgets

BuilderJS comes with lots of pre-defined HTML widgets (or block or common HTML content) like image box, text box, divider, page footer, email signature, banner, etc. providing you everything you need to build an email or page

## Custom Widgets

You can also add your own widget to the list for using later on. BuilderJS supports "Add to widget library" feature, allowing you to select an element or group of elements to become a widget.

![Add to widget](https://builderjs.s3.amazonaws.com/BuilderJS-Add-To-Widget.png "Add to widget")

# Storage

```javascript
// Initiate builder with `saveUrl`
// See `php` or `ruby` tab to see how to
// handle save request sent from builder in PHP and Ruby respectively
var builder = new Editor({
    url: 'http://example.com/template/02093403',
    saveUrl: 'http://example.com/save?id=02093403',
    saveMethod: 'POST'
});
```

```python
# Sample controller code for handling the save request
# sent from BuilderJS

# Python code sample is not yet available
# comming soon!
```

```ruby
# Sample controller code for handling the save request
# sent from BuilderJS

require 'activerecord'
require 'mysql'

# Set up MySQL connection
ActiveRecord::Base.establish_connection(
  adapter: 'mysql2',
  database: 'myDB',
  username: 'user',
  password: 'password'
)

# Associate Template class with the `templates` data table
class Template < ActiveRecord::Base
  # associated with `templates` table
end

# Retrieve parameters passed to the server script
content = params[:content]
template_id = params[:id]

# Actually update the MySQL database
template = Template::find(template_id)
template.content = content

template.save
```

```php
<?php

// Sample controller code for handling the save request
// sent from BuilderJS

// MySQL credentials
$servername = "localhost";
$username = "user";
$password = "password";
$dbname = "myDB";

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);

// Retrieve parameters passed to the server script
$html = $_POST['content'];
$html = $conn->real_escape_string($html);
$templateId = $_GET['id'];

// Actually update the MySQL database
$sql = "UPDATE templates SET content = '{$html}'
        WHERE id = '{$templateId}'";

if ($conn->query($sql) === TRUE) {
    echo "Template updated successfully";
}

$conn->close();
```

When it comes to save, **BuilderJS** allows you to specify a Save URI, to which it will make a POST request, passing the latest updates to the server side scripting for handling. The request is triggered when user clicks on Save button in the builder.

Actual job of storing the submitted content is handled by a server-side scripting language like PHP, Ruby, Python, Java, .Net, etc.

Below is an example of how BuilderJS sends its content to the server. By default, when user clicks Save button, BuilderJS makes a `POST` request to the URL specified by `saveUrl` parameter passed to the builder construction method.

See sample code on the right panel, `javascript` tab to see how to specify a save URL mentioned above. See `php` or `ruby` or `python` tabs for sample code snippet that handles such request.

### Sample POST request
`POST http://example.com/template/save?id=02093403`

### Request header

Below are request headers added by BuilderJS. Note that it is an Ajax request (specified by the `X-Requested-With: XMLHttpRequest` header) that accepts a JSON response from your server

* **Accept**: application/json
* **Content-Type**: application/x-www-form-urlencoded; charset=UTF-8
* **X-Requested-With**: XMLHttpRequest

### Request parameters

Below are POST parameter passed to the server along with the request

Parameter | Description
--------- | -----------
content | HTML content of the design, including any update made to the design. Simply store its value to a server's database like MySQL, PostgreSQL, Oracle or any other database management system
token | CSRF token just in case your server requires it

# Integration

Since BuilderJS is a pure JavaScript library, accepting parameters passed to its initialization, it is open to any kind of integration no matter what your programming language or database system is.

All its job is to load a template in HTML, allow user to make changes using its visual drag & drop or source edit then submit the changes to the server for storing.

# Customization

```javascript
class MySampleWidget extends Widget {
    // get HTML to insert into content
    init() {
        super.init();
    }

    title() {
        return 'My Sample Widget';
    }

    renderHtml() {
        return '<div> A Simple Widget with 1 line of text </div>';
    }

    // custom behavior goes here...
```

BuilderJS is written in a well designed structure, allowing easy and straightforward customization. For example, you can add your own widget to the library beside the default ones like Text, Image, Video, Social Network Icons, etc. See the right panel, `javascript` tab to find out how to write a custom widget.

By extending the Widget base class, your `MySampleWidget` will automatically inherit all behaviors of a common widget like drag & drop enabled, move/duplicate/delete support. You can specify its own characteristics like title, thumbnail, etc. by overwriting the corresponding methods.

Documentation is being updated. In the mean time, please contact us for more details on this topic.

# SaaS Support

BuilderJS is also pre-design for SaaS (Software as a Service). That is, you have full control of how BuilderJS features are available to your users. For example, you can always turn a feature ON or OFF for different types of users.

Documentation is being updated. In the mean time, please contact us for more details on this topic.
