The H5BP1 Bundle is a Symfony2/Assetic/Twig bundle implementation of the popular h5bp boiler plate code.

Add to your deps

Add the autoload paths

Register the bundle

# Background
The [h5bp](http://html5boilerplate.com/) project provides a standard boiler plate for web projects. The boiler plate code has been incorporated into the bundle `FlintLabs\Bundle\H5BP1Bundle`.

## Setting up the base template

By default, your applications will extend the base template, `::base.html.twig`. In your `::base.html.twig`, you can inherit again from the h5bp bundle.

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
        ...
    {% endblock %}

## Regions available

    {% block ascii %}{% endblock %}

    {% block title %}{% endblock %}

    {% block canonical %}{% endblock %}

    {% block metadata %}{% endblock %}

    {% block stylesheets %}{% endblock %}

    {% block body %}{% endblock %}

    {% block javascripts %}{% endblock %}

    {% block analytics %}{% endblock %}

## Example twig template

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

    {% block ascii %}
       _
      (_)           _
       _ _   _  ___| |_      ____  ____ _   _  ___  ____
      | | | | |/___)  _)    / ___)/ _  | | | |/___)/ _  )
      | | |_| |___ | |__   ( (___( ( | | |_| |___ ( (/ /
     _| |\____(___/ \___)   \____)\_||_|\____(___/ \____)
    (__/
    {% endblock %}

Update your ::base.html.twig

Specify your CSS Bundle

Optionally use the other filters available