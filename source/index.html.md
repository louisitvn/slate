---
title: BuilderJS API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - html
  - php
  - ruby
  - python

toc_footers:
  - <a href='https://codecanyon.net/item/builderjs-html-email-page-builder/27146783'>Download BuilderJS 5.0 Now</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to **BuilderJS 6.0**, the most powerful HTML Email or Page builder tool. BuilderJS is the easiest, quickest way to design elegant, mobile responsive emails or landing pages for your business.

BuilderJS is built using pure JavaScript and HTML, making it easy to integrate with any web application, regardless of the server-side programming language (e.g., Java, .NET, PHP, Ruby on Rails, Python, etc.).

BuilderJS is fully customizable and designed for flexible integration scenarios. You can use it as a standalone application or embed it into your own web app, interacting with it through its simple and easy API. BuilderJS has been choosen by many popular frameworks as their site or email builder.

Details of all available API methods are explained throughout this documentation.

# Installation

## Include required files

> Put the following HTML / JavaScript code snippet to your HTML page. Make sure you update the reference paths `href` and `root` values accordingly to your setup:

```html
<!DOCTYPE html>
    <head>
        <link rel="stylesheet" href="/builder.css"></link>
        <script type='text/javascript' src="/builder.js"></script>
    </head>
</html>
```

> It's that simple! Include the whole HTML drag & drop builder to your webapp. In the next sections, we will explain how you can initialize and have it populate your page.

There are 2 files which are shipped with BuilderJS bundle

* builder.js - include all core functionality of BuilderJS
* style.css - the default styles for BuilderJS, used for its controls and dashboard.



## Initialize the builder

```html
<!DOCTYPE html>
    <head>
        <link rel="stylesheet" href="/builderjs/dist/builder.css"></link>
        <script type='text/javascript' src="/builderjs/dist/builder.js"></script>
    </head>
    <body>
        <script language="Javascript">
            new BuilderJS({
                mainContainer: '#main',
                settingContainer: '#idDiv3',
            });
        </script>
    </body>
</html>
```

Once you have included BuilderJS .js file, the next step is to write JavaScript code to initalize the Builder. The example code on the right to see how to initalize a <code>builder</code> object with minimum configuration. After this step, you will have a <code>builder</code> object available for rendering in the next step

## Create a new page

```html
<!DOCTYPE html>
    <head>
        <link rel="stylesheet" href="/builderjs/dist/builder.css"></link>
        <script type='text/javascript' src="/builderjs/dist/builder.js"></script>
    </head>
    <body>
        <script language="Javascript">
            var builder = new BuilderJS({
                mainContainer: '#main',
                settingContainer: '#idDiv3',
                themeUrl: "/myAwesomeTheme/",
            });


            builder.init(theme = "/theme/abc");
        </script>
    </body>
</html>
```

It is now time to load the builder to your browser. If you want to load a blank page for your new HTML page or Email design, execute the <code>init</code> function. See code example in the right panel.

If configured correctly, the browser will be rendered to the browser and a new sample page will also be loaded like below:

UPDATE-01 - thay 1 cái hình builder đẹp đẹp ở đây, với 1 cái theme đẹp đẹp nào đó

![Default Blank Page](https://static.vecteezy.com/system/resources/previews/008/253/599/large_2x/future-technology-vr-virtual-universe-free-vector.jpg "Sample Builder page")

Notice the "themeUrl" parameter of the init() function. As you can see, in order to load a blank page, you need to tell BuilderJS the theme to use. BuilderJS comes with many themes/templates available for users to choose from. See THEME section for a list of available themes to specify as well as more details about BuilderJS theme system.

As a quick reference, below are some default themes that you can choose as well as how they look

Name | Description
--------- | -----------
mailux | The default email theme, it is a clean and elegant theme suitable for all types of email
minpage | The default website/page theme, it is simple and nice looking, suitable for getting started with.

Below are some examples of different themes loaded to BuilderJS

UPDATE-02 - Chọn một theme đẹp A

![Theme Đẹp A](https://static.vecteezy.com/system/resources/previews/007/822/564/non_2x/virtual-universe-concept-free-vector.jpg "Theme Đẹp A")

UPDATE-03 - Chọn một theme đẹp B

![Theme Đẹp B](https://static.vecteezy.com/system/resources/previews/059/180/340/non_2x/young-woman-flying-on-a-big-bird-of-hope-to-the-stars-and-moon-in-hopes-of-peace-and-happiness-vector.jpg "Theme Đẹp B")


## Open a saved work

> hello

```html
<!DOCTYPE html>
    <head>
        <link rel="stylesheet" href="/builderjs/dist/builder.css"></link>
        <script type='text/javascript' src="/builderjs/dist/builder.js"></script>
    </head>
    <body>
        <script language="Javascript">
            var builder = new BuilderJS({
                mainContainer: '#main',
                settingContainer: '#idDiv3',
                themeUrl: "/myAwesomeTheme/",
            });

            var data = "<?php echo file_get_contents('/data/Pages/MyPage.json'); ?>";
            builder.load(data);
        </script>
    </body>
</html>
```

Rather than opening a blank page, normally, you might want to open a previous saved work to continue. Then you can execute the load() function. This function take a json storage of an HTML template and render it to the designer view. See example in the right panel.

In the example, the <code>data</code> variable holds the entire JSON structure of an HTML page as a string. Then this string is passed to the load function of builder.

## More about BuilderJS JSON storage

BuilderJS stores design work in a JSON structure, which is a universal format which is supported by certain HTML builder. Normally, when users want to save their current work


### Construction Parameters
Below are the required construction parameters for BuilderJS

Parameter | Description
--------- | -----------
mainContainer | The ID of the HTML element into which the builder design will be rendered
settingContainer | The ID of the HTML element into which the builder settings will be rendered
themeUrl | URL of the theme folder. BuilderJS comes with many themes and even more themes are coming.
assetUploadHandler | URL of the server-side script (PHP, Python, .NET...) to handle files / images uploading

<aside class="notice">
**Note**: Like any other app, the builder should be loaded only after the page has fully loaded. Therefore, you should place the BuilderJS initialization code inside a <code>DOMContentLoaded</code> listener (or <code>$(document).ready()</code> if using jQuery) to ensure all DOM elements are available.
</aside>

## Examples

BuilderJS also comes with a sample package so that you can quickly explore the builder features. Just put the `sample` folder to your document root and open it in a web browser to see it in action

`http://example.com/sample/`

## Advanced

```html
<script>
    // A more complicated setup
    var builder = new Editor({
        root: '/builderjs/dist/',
        url: 'http://example.com/template/02093403',
        saveUrl: 'http://example.com/save?id=02093403',
        saveMethod: 'POST',
        backUrl: 'http://example.com',
        tags: [
            {name: 'First Name', type: 'display'},
            {name: 'Last Name', type: 'display'},
            {name: 'Current Year', type: 'display'},
            {name: 'Current Date', type: 'display'}
        ]
    });
</script>
```
> Notice the `"root"` parameter which is important for BuilderJS to find the related resources. For example, if your builderjs distributable (`dist`) is available at `http://example.com/builderjs/dist/`, then you need to set your `"root"` value to `"/builderjs/dist/"`. Remember to keep both leading and trailing slashes.

See the right panel for a more complicated setup. See the **Configuration** section for advanced installation options which provide you more control over how the builder functions.

By default, BuilderJS renders its HTML content to the `document.body` element of the page. i.e. the builder view will occupy the whole page. You can also configure it to render to a child element of your page.


# Configuration

## Load a Template

By default BuilderJS loads with a blank design for you to start making your own HTML email or page. You can also start working with an existing email or page template by loading it into the design view. There are 2 ways of loading an existing template:

### From an HTML string

```html
<script>
    var builder = new Editor({ root: '/builderjs/dist/' });
    builder.load('<div> <h1>Awesome title</h1> <p> Page content... </p> </div>')
</script>
```

Use the `load(html)` function, passing an HTML string. See code example in the right panel

Parameter | Default | Description
--------- | ------- | -----------
html | [empty] | HTML content for loading to the viewer

<aside class="warning">
Loading a template from an HTML string is not a good practice and is, in general, not recommended. The preferred way is to load it from a public URL. See section below for details
</aside>

### From a public URL

Very often, your template is also available as a public URL. Then you can pass it to the `url` parameter to your builder initialization code. See example in the right panel

```html
<script>
    var builder = new Editor({
        root: '/builderjs/dist/',
        url: 'http://example.com/template/2001990'
    });

    builder.init();
</script>
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

```html
<script>
    // Initialize BuilderJS with tags

    var builder = new Editor({
        root: '/builderjs/dist/',
        tags: [
          {name: 'First Name', type: 'display'},
          {name: 'Last Name', type: 'display'},
          {name: 'Current Year', type: 'display'},
          {name: 'Current Date', type: 'display'},
        ]
    });
    builder.init();
</script>
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
renderTo | The parent element to which BuilderJS renders its content. It is `document.root` by default

# Key Features

## Visual Drag & Drop Editor

BuilderJS comes as a fully-functioned visual Drag & Drop editor, allowing you to quickly build your page or email templates without any hassle

## Source Editor

Beside the visual Drag & Drop editor, BuilderJS also supports a Source Editor which allows you to completely customize your page or email design by updating HTML / CSS directly. This is for advanced users who are familiar with HTML / CSS markup language

![Source Editor](https://builderjs.s3.amazonaws.com/BuilderJS-Source-View.png "Source Editor")

## Template

```html
<script>
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
    root: '/builderjs/dist/',
    templates: templates
});

</script>
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

```html
<!DOCTYPE html>
<html lang="en">
<body>

  <button id="btnSave">Save</button>

  <script>

    // Function that handles saving
    function save() {
      var data = builder.getJson();

      $.ajax({
        url: 'save.php',       // Your server-side script
        data: JSON.stringify(data),
        success: function (response) {
          console.log("Save successful:", response);
        },
      });
    }

    // Assign click event
    document.getElementById("btnSave").addEventListener("click", save);
  </script>

</body>
</html>
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

Once you have initialized the builder, loaded a template or init a new page. You can start designing your pages & emails. WHen it comes to saving the current work for future editing, you will need to capture the current data on BuilderJS to save it to a storage like filesystem or MySQL.

Since BuilderJS is a pure JavaScript application which works on a browser, it does not actually store anything, it is when a server script is needed.

The most common use case is to capture the current data of BuilderJS, using its API method <code>getJson()</code> and pass the result to a server script using Ajax for storing. See a mini example on the right to see how it works



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

All its job is to load a template in HTML, allow user to make changes using its visual drag & drop or source edit then submit the changes to the server for storing. You can use PHP, Ruby, Python, Java, .NET or any other server side scripting language to handle BuilderJS requests. In the distributable package, we also include sample PHP scripts for saving, exporting, etc.

# Customization

```html
<script>
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
</script>
```

BuilderJS is written in a well designed structure, allowing easy and straightforward customization. For example, you can add your own widget to the library beside the default ones like Text, Image, Video, Social Network Icons, etc. See the right panel, `javascript` tab to find out how to write a custom widget.

By extending the Widget base class, your `MySampleWidget` will automatically inherit all behaviors of a common widget like drag & drop enabled, move/duplicate/delete support. You can specify its own characteristics like title, thumbnail, etc. by overwriting the corresponding methods.

Documentation is being updated. In the mean time, please contact us for more details on this topic.

# SaaS Support

BuilderJS is also suitable for SAAS (Software as a Service). That is, you have control of how BuilderJS features are available to your users. For example, you can always turn a feature ON or OFF for different classes of users.

Documentation is being updated. In the mean time, please contact us for more details on this topic.
