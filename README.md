**The H5BP1 Bundle is a Symfony2/Assetic/Twig bundle implementation of the popular h5bp boiler plate code.**

Technologies at work

* h5bp v1: Provides the boilerplate code HTML5/js and reset CSS
* Assetic: Provides filters for coding with various css/js technologies (Less, Sass, CoffeeScript, etc)
* Twig: Provides a easy to use template language, which you can leverage for 'extending' base code (like h5bp)
* Symfony2: Easy framework for bundling technologies, managing dependencies and writing your application

# Example
The [h5bp](http://html5boilerplate.com/) project provides a standard boiler plate for web projects. The boiler plate code has been incorporated into the bundle `FlintLabs\Bundle\H5BP1Bundle`.

## Your twig template

    {% extends '::base.html.twig' %}

    {% block title %}Hello world{% endblock %}

    {% block body %}
        <header>
            <h1>Example Site</h1>
            <nav>
                <ul>...</ul>
            </nav>
        </header>
        <article>
            <h1>Example Article</h1>
        </article>
    {% endblock %}

    {% block credits %}
       _
      (_)           _
       _ _   _  ___| |_      ____  ____ _   _  ___  ____
      | | | | |/___)  _)    / ___)/ _  | | | |/___)/ _  )
      | | |_| |___ | |__   ( (___( ( | | |_| |___ ( (/ /
     _| |\____(___/ \___)   \____)\_||_|\____(___/ \____)
    (__/

    Author: Example author and other branding information
    {% endblock %}

## HTML Output

    <!doctype html>
    <!--[if lt IE 7 ]> <html class="no-js ie6" lang="en"> <![endif]-->
    <!--[if IE 7 ]>    <html class="no-js ie7" lang="en"> <![endif]-->
    <!--[if IE 8 ]>    <html class="no-js ie8" lang="en"> <![endif]-->
    <!--[if (gte IE 9)|!(IE)]><!--> <html class="no-js" lang="en"> <!--<![endif]-->
    <head>
    <!--
       _
      (_)           _
       _ _   _  ___| |_      ____  ____ _   _  ___  ____
      | | | | |/___)  _)    / ___)/ _  | | | |/___)/ _  )
      | | |_| |___ | |__   ( (___( ( | | |_| |___ ( (/ /
     _| |\____(___/ \___)   \____)\_||_|\____(___/ \____)
    (__/

    Author: Example author and other branding information
    -->

        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">

        <title>Hello world</title>

        <meta name="description" content="">
        <meta name="author" content="">

        <!--<link rel="shortcut icon" href="/favicon.ico">-->
        <!--<link rel="apple-touch-icon" href="/apple-touch-icon.png">-->

        <link href="css/f9ccd32.css" type="text/css" rel="stylesheet" />
        <script src="bundles/flintlabsh5bp1/js/libs/modernizr-1.7.min.js"></script>
    </head>
    <body>
        <header>
            <h1>Example Site</h1>
            <nav>
                <ul>...</ul>
            </nav>
        </header>
        <article>
            <h1>Example Article</h1>
        </article>
        <script src="//ajax.googleapis.com/ajax/libs/jquery/1.5.1/jquery.js"></script>
        <script>window.jQuery || document.write("<script src='bundles/flintlabsh5bp1/js/libs/jquery-1.5.1.min.js'>\x3C/script>")</script>
        <!--[if lt IE 7 ]>
            <script src="bundles/flintlabsh5bp1/js/libs/dd_belatedpng.js"></script>
            <script>DD_belatedPNG.fix("img, .png_bg");</script>
        <![endif]-->
        <script src="bundles/flintlabsh5bp1/js/plugins.js" type="text/javascript"></script>
        <!-- Analytics -->
    </body>
    </html>

## Configuration of base template

By default, your applications will extend the base template, `::base.html.twig`. In your `::base.html.twig`, you can inherit again from the h5bp bundle.

* Leverage different technology filters to handle css/js Less, Sass, CoffeeScript, cssEmbed, Google Closuer, YUI css/js compressor, sprockets, stylus etc
* Manage your google analytics defaults
* Insert defaults for other regions

    {% extends 'FlintLabsH5BP1Bundle:Default:base.html.twig' %}

    {% block stylesheets %}
        {# Example mixing in the reset top/bottom to your css less file #}
        {% stylesheets filter='less,?yui_css'
            '@FlintLabsH5BP1Bundle/Resources/css/reset-top.css'
            '@MyBundle/Resources/less/site.less'
            '@FlintLabsH5BP1Bundle/Resources/css/reset-top.css'
            %}
            <link href="{{ asset_url }}" type="text/css" rel="stylesheet" />
        {% endstylesheets %}
    {% endblock %}

    {% block javascripts %}
        {# Include the parent JS that is provided by h5bp, like jquery, belated, .. #}
        {{ parent() }}
        {% javascripts output='/js/instant.js' filter='coffee' '@MyBundle/Resources/js/instant.coffee' %}
            <script type="text/javascript" src="{{ asset_url }}"></script>
        {% endjavascripts %}
    {% endblock %}

    {% block analytics %}
        <!-- Analytics -->
    {% endblock %}

## Other Template Regions

    {% block credits %}{% endblock %}

    {% block title %}{% endblock %}

    {% block canonical %}{% endblock %}

    {% block metadata %}{% endblock %}

    {% block stylesheets %}{% endblock %}

    {% block body %}{% endblock %}

    {% block javascripts %}{% endblock %}

    {% block analytics %}{% endblock %}

# Installation with Symfony2

## Update your deps file

    [h5bp1]
    git=git@github.com:FlintLabs/H5BP1Bundle.git

## Update your vendors

    php bin/vendors update

## Update your autoloader

    // app/autoload.php
    $loader->registerNamespaces(array(
        // ...
        'FlintLabs\\H5BP1Bundle' => __DIR__.'/../vendor/h5bp1/src',
        // ...
    ));

## Register the bundle references

    // app/AppKernel.php
    public function registerBundles()
    {
        return array(
            // ...
            new FlintLabs\Bundle\H5BP1Bundle\FlintLabsH5BP1Bundle(),
            // ...
        );
    }

# Other useful resources and documents
[Assetic](https://github.com/kriswallsmith/assetic) Managing resources (JS/CSS) in PHP/Symfony2
[Twig](http://twig.sensiolabs.org/) Twig templating language for PHP/Symfony2