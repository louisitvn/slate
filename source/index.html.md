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

# Get quickly started

When it comes to saving or publishing your HTML designs (e.g., when clicking the Save or Export button), BuilderJS sends the content to a server-side script. This script handles the content by either saving the current HTML design to storage or preparing it for download.

The installation process is covered in detail in the Installation section. However, if you'd like to quickly see BuilderJS in action with its core features, follow these steps:

* Download the BuilderJS package.

* The package includes a `demo` folder. Copy this folder to your web server's document root, for exmaple `/var/www/demo`.

* Open the corresponding URL in your browser to launch the demo: http://your-host.com/demo/

That's it! you can now play around with your own instance of BuilderJS on your own hosting server.

The demo includes a sample index.php file that loads the required BuilderJS files. It also contains server-side scripts (written in PHP) to handle BuilderJS interactions such as SAVE and EXPORT. You can use the provided PHP script, or implement similar functionality in any server-side language you're familiar with such as Ruby, Perl, .NET, Java, etc.

# Installation

In the previous section, we provide a guideline to quickly run a demo installation of BuilderJS so that you can see how it works in your environment. In this section, we provide a step-by-step guideline to install BuilderJS as well as configure it to works with your server-side scripting.

Basically, there are 2 parts of installation:

* The BuilderJS itself on the client side
* The server-side script.

Explanation: BuilderJS itself works on the client side of a web application, i.e. in a browser, and it interacts with users, allowing them to build beautiful HTML pages. However, when it come to saving or publishing users' design work, you will need to capture the output of BuilderJS (i.e. HTML page) and pass it to a server-side script, which stores the HTML content to a storage or publish it (allowing users to download)

In the next section, we guide how to set up BuilderJS and provide a sample demo of how to capture its data to pass to a server-side script for storing or exporting

## Include required files

> Put the following HTML / JavaScript code snippet to your HTML page. Make sure you update the reference paths `href` and `root` values accordingly to your setup:

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
            });
        </script>
    </body>
</html>
```

> It's that simple! Include the whole HTML drag & drop builder to your webapp. In the next sections, we will explain how you can initialize and have it populate your page.

There are 2 files which are shipped with BuilderJS bundle

* builder.js - include all core functionality of BuilderJS
* style.css - the default styles for BuilderJS, used for its controls and dashboard.

Optionally, you can include Bootstrap CSS to improve userbility experience.

Once you have included BuilderJS .js file, the next step is to write JavaScript code to initalize the Builder. The example code on the right to see how to initalize a `builder` object with minimum configuration. After this step, you will have a `builder` object available for rendering in the next step

## Create a new page

> Notice the `themeUrl` parameter of construction method: it is required in order to initialize a new page

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
                themeUrl: "/myAwesomeTheme/", // required by init() function
            });


            builder.init(theme = "/theme/abc");
        </script>
    </body>
</html>
```

It is now time to load the builder to your browser. If you want to load a blank page for your new HTML page or Email design, execute the <code>init</code> function. See code example in the right panel. Notice the `themeUrl` parameter of construction method: it is required in order to initialize a new page. In BuilderJS, every page is created based on a theme which is comprised of a set of related styles and page elements. You can see some examples of a BuilderJS theme below:

If configured correctly, the browser will be rendered to the browser and a new sample page will also be loaded like below:

UPDATE-01 - thay 1 cái hình builder đẹp đẹp ở đây, với 1 cái theme đẹp đẹp nào đó

![Theme Đẹp A](https://static.vecteezy.com/system/resources/previews/008/253/599/large_2x/future-technology-vr-virtual-universe-free-vector.jpg "Sample Builder page")

UPDATE-02 - Chọn một theme đẹp

![Theme Đẹp B](https://static.vecteezy.com/system/resources/previews/007/822/564/non_2x/virtual-universe-concept-free-vector.jpg "Theme Đẹp A")

UPDATE-03 - Chọn một theme đẹp

![Theme Đẹp C](https://static.vecteezy.com/system/resources/previews/059/180/340/non_2x/young-woman-flying-on-a-big-bird-of-hope-to-the-stars-and-moon-in-hopes-of-peace-and-happiness-vector.jpg "Theme Đẹp B")


## Open a page

Rather than creating a blank page, normally, you might want to open a previous saved work to continue the design work. BuilderJS supports some ways to load HTML content to its builder view.

### From JSON string

> Load a page from JSON string

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
            });

            var data = "<?php echo file_get_contents('/data/Pages/MyPage.json'); ?>";
            builder.load(data);
        </script>
    </body>
</html>
```

In the example, the `data` variable holds the entire JSON structure of an HTML page as a string. Then this string is passed to the load function of builder to load to the browser. In brief, BuilderJS pages are created in JSON format which can be stored in any storage like: filesystem, RDBMS, etc. Then it can be loaded to the design view.

Don't worry about the JSON format as well as how to create it, it will be covered in the Storage section below.

### From URL

> Load a page from URL

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
            });

            var url = "http://example.com/pages/MyPage.json";
            builder.loadFromUrl(url);
        </script>
    </body>
</html>
```

Instead of loading the entire JSON data into a JavaScript variable like above, a more convenient way is to use the `loadFromUrl()` method to load JSON content from a remote URL. Suppose you have a page JSON stored on a server storage and is available at http://example.com/pages/MyPage.json, then you can load it as in the example.

Don't worry about the JSON format as well as how to create it, it will be covered in the Storage section below.
Below is the summary of construction parameters for BuilderJS

Parameter | Description
--------- | -----------
mainContainer | The ID of the HTML element into which the builder design will be rendered
settingContainer | The ID of the HTML element into which the builder settings will be rendered
themeUrl | URL of the theme folder. BuilderJS comes with many themes and even more themes are coming.

<aside class="notice">
**Note**: Loading data from a URL is recommended over from a JSON string. When assigning a large JSON string to a vailable, it will increase your HTML page size, resulting in loading performance.
</aside>


# Theme & Template

A theme is comprised of sample element templates of the same unified styles. Every website or page belongs to a theme. Some examples of theme:

* Simple blogpost theme
* Clean and element landing page theme
* Minimal theme for online art gallery
* Amazon-like online store
* More...

Themes & templates are at the center of BuilderJS. A theme is comprised of many element templates that users can quickly use (by drag and drop them into the page designer). Each theme has its own styles as well as a set of available components for users to choose from. Some example components of a theme:

* Menu bar
* Main banner
* Carousel banner
* About us block
* New features block
* Footer area
* Testinomial area

Users can simply choose an element, drag and drop them into the designer view and modify the element phrases to quickly make their own page.

## Create a theme

Beside the available templates for BuilderJS, you can also create your own theme for BuilderJS to improve your users experience. The idea of creating a theme is

* Design a beautiful web page or email templte
* Break it into elements so that users can organize and customize them (drag and drop elements) the way they desire.

Then specify your theme in the BuilderJS construction so that users will be able to choose the theme. Below are the steps to create a theme for BuilderJS

* Open your terminal
* Go to the `builderjs/` folder
* Execute the following command to generate a theme skeleton `generate theme your_theme_name`

Once executed, it will create a theme folder namely your_theme_name containing sample templates for your theme, ready to modify.

**Note** The detailed specifications & guideline for working with a theme is still in development. Currently, BuilderJS team are working on this to publish more themes for BuilderJS users everyday. We will publish a comprehensive guideline soon so that any development team can create their own themes easily.

# Server-script

## Save current page

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
        data: {
          page_id: 'Page #ID',
          data: builder.getJson(),
        }
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
$pageId = $_POST['page_id'];
$data = $_POST['data'];

// Actually update the MySQL database
$sql = "UPDATE pages SET data = '{$data}'
        WHERE id = '{$pageId}'";

if ($conn->query($sql) === TRUE) {
    echo "Saved successfully";
}

$conn->close();
```

Once you have initialized the builder and either loaded a template or started a new page, you can begin designing your pages and emails.

When it comes to saving your current work for future editing, you’ll need to capture the current data from BuilderJS and store it in a system like a filesystem or MySQL.

Since BuilderJS is a pure JavaScript application that runs in the browser, it does not store any data by itself—this is where a server-side script becomes necessary.

The most common approach is to use BuilderJS’s `getJson()` API method to capture the current state, then send the result to a server script via Ajax for storage. In this example, we implement the backend handler in PHP and Ruby, although you can implement it in any programming language you are familiar with. The key is to capture the input. Click on the `php` or `ruby` tab in the code sample panel to see the details. See the example on the right to understand how this works in practice.

* Load BuilderJS
* Create a new page to design
* Add a "Save" button, when it is clicked, get the builder data and send to the server's `save.php` script which stores HTML to a MySQL database.


# Key Features

## Visual Drag & Drop

BuilderJS comes as a fully-functioned visual Drag & Drop editor, allowing you to quickly build your page or email templates without any hassle. Simply open a page and design it by dragging and dropping elements to your page content.

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
