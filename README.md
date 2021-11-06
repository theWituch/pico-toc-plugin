Pico Table Of Contents Plugin <!-- omit in toc -->
==================

Generate a table of contents for the pages of your [Pico](http://picocms.org) site.

- [Usage](#usage)
- [Getting Started](#getting-started)
  - [Install](#install)
  - [Update your theme](#update-your-theme)
  - [Configuration settings](#configuration-settings)
- [Example](#example)
  - [The `index.md` file](#the-indexmd-file)
  - [Screenshot](#screenshot)
- [License](#license)


# Usage

Automatically generates a table of contents (ToC) based on the `<h1>` to `<h6>` tags.

In your Markdown file, simply add the `<toc />` tag where you want the ToC to be inserted. This tag must be added for each page you want.

See the [configuration settings](#configuration-settings) section to see the available attributes.


# Getting Started

* [Install](#install) the plugin;
* [Update your theme](#update-your-theme) to add the plugin stylesheet in your Twig templates;
* Change default [configuration settings](#configuration-settings);
* [Use it](#usage) by adding the `<toc />` tag where you want the ToC to appear on your page.


## Install

Add the plugin in the `plugins` directory of your Pico installation (e.g. `/var/www/html/pico/plugins/`)
* using [Composer](https://getcomposer.org/) `composer require iridescent-dev/pico-toc-plugin`
* or manually by uploading the plugin’s files to your `plugins` directory
  - [download the latest release](https://github.com/iridescent-dev/pico-toc-plugin/releases/latest)
  - extract the archive into your `plugins` directory
  - rename the plugin's folder to `TableOfContents`

The structure should be as follows
```
plugins
└───TableOfContents
    │   style.css
    │   TableOfContents.php
```

Pico Table Of Contents plugin requires PHP >=7.0.

We always recommend you to use Composer whenever possible, because it makes updating the plugin way easier.


## Update your theme

In your template files, add a link to the plugin stylesheet in the `head` section:

``` twig
<!-- index.twig and/or page.twig, etc. -->
<head>
    ...
    <!-- Table Of Contents -->
    <link rel="stylesheet" href="{{ plugins_url }}/TableOfContents/style.css">
    ...
</head>
```


## Configuration settings

You can change the default configuration by adding values to your `config` file. Here are the options available and what they do.
* `toc_min_headers` - Minimum number of headers required to display the ToC. - *Default value: 2*
* `toc_min_level` - Minimum header level displayed in the ToC. - *Default value: 1*
* `toc_max_level` - Maximum header level displayed in the ToC. - *Default value: 5*
* `toc_tag` - The tag used for the list. - *Default value: ol*
  *  **ol** (ordered list)
  *  **ul** (unordered list)
* `toc_style` - The css style applied to the list. - *Default value: none*
  * **numbers** (1, 1.1, 1.2, ...)
  * **bullets** (● ○ ■)
  * **none** (no item marker is shown)
  * **default** (the default css style applied to lists)
* `toc_heading` - Heading text, if a heading for the ToC is desired. - *Default value: (unset)*

For reference, these values are set in `config/config.yml` using the following format:

``` yml
toc_min_headers: 2
toc_min_level: 1
toc_max_level: 5
toc_tag: ol
toc_style: numbers
toc_heading: Contents
```

This configuration will be applied to the entire site, but it's also possible to override it (except `toc_min_headers`) for a specific element using the `min-level`, `max-level`, `tag`, `style` and `heading` attributes.

``` html
<toc min-level="2" max-level="3" tag="ol" style="numbers" heading="Table of Contents" />
```


# Example

## The `index.md` file

``` html
---
Title: Table Of Contents Example
Description: 
---

Here is the Table Of Contents generated for the current page:

<toc max-level="3" heading="Example of Table of Contents" style="numbers" />

# This is a `<h1>`
Lorem ipsum dolor sit amet, consectetur adipisici elit, sed eiusmod tempor incidunt ut labore et dolore magna aliqua. 

## And this is a `<h2>`
Lorem ipsum dolor sit amet, consectetur adipisici elit, sed eiusmod tempor incidunt ut labore et dolore magna aliqua. 

### Then, you can see a `<h3>`
Lorem ipsum dolor sit amet, consectetur adipisici elit, sed eiusmod tempor incidunt ut labore et dolore magna aliqua. 

#### But `<h4>` are not visible in the Table Of Contents
Lorem ipsum dolor sit amet, consectetur adipisici elit, sed eiusmod tempor incidunt ut labore et dolore magna aliqua. 

### An other `<h3>`
Lorem ipsum dolor sit amet, consectetur adipisici elit, sed eiusmod tempor incidunt ut labore et dolore magna aliqua. 

# Again a `<h1>`
Lorem ipsum dolor sit amet, consectetur adipisici elit, sed eiusmod tempor incidunt ut labore et dolore magna aliqua. 

## An other `<h2>`
Lorem ipsum dolor sit amet, consectetur adipisici elit, sed eiusmod tempor incidunt ut labore et dolore magna aliqua. 

## And the last `<h2>`
Lorem ipsum dolor sit amet, consectetur adipisici elit, sed eiusmod tempor incidunt ut labore et dolore magna aliqua.
```


## Screenshot

<p align="center">
  <img src="Screenshot.png" title="Screenshot" width="600">
</p>


# License

Pico Table Of Contents Plugin is open-source licensed under the MIT License. See [LICENSE](LICENSE) for details.
