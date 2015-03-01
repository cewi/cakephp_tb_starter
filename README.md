# Plugin for CakePHP for using Twitter Bootstrap 3

At the moment this package is far from being complete and possibly broken. Use at your own risk!

The baked views need the [FriendsOfCake/bootstrap-ui](https://github.com/FriendsOfCake/bootstrap-ui) and the [CakeDC/search](https://github.com/CakeDC/search/tree/3.0) plugins to work, so my package depends on these plugin (required in composer.json).  Although you have to provide [jquery](http://jquery.com), [bootstrap](http://getbootstrap.com) and/or [bootswatch](http://bootswatch.com), [select2](https://select2.github.io/) and [jasny bootstrap](http://jasny.github.io/bootstrap/). 
All bake templates are highly opinionated and will only reflect my personal design ideas. However you can use them as a starting point or inspiration.

## What you get
1. Alternative Bake templates for the index, view, edit and add actions. The Templates produce less links in the sidebar. They include the options to output icons, when the provided Helpers are used. A search-form is provided in index.cp which uses the search-plugin.
2. HtmlHelper and FormHelper can add icons to links (Actually  ([Icomoon](https://icomoon.io/), [FontAwesome](http://fortawesome.github.io/Font-Awesome/) and [Glyphicons](http://getbootstrap.com/components/) supported). You have to include the Font-Libraries yourself. I recommend using bower. The HtmlHelper now has an icon() method which outputs a span with the icon.
3. some reusable elements (file-upload, button, search-buttons, pagination)

## Installation
You can install this plugin into your CakePHP application using [composer](http://getcomposer.org).
You first have to add the repository manually by adding to your composer.json:

```
"repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/cewi/cakephp_tb_starter"
        }
    ],
```


The recommended way to install the package then is:

```
composer require cewi/cakephp_tb_starter
```

Then load the Plugins in your bootstrap.php

```
Plugin::load('Search');
Plugin::load('BootstrapUI');
Plugin::load('Cewi/CakephpTbStarter', ['bootstrap' => true]);
```


Don't forget to check your controller-code! 

##Usage

###Helpers
If you plan to use the Helpers just include them in AppView:


     public $layout = 'Cewi/CakephpTbStarter.default';

     public function initialize()
     {
        $this->loadHelper('Form', ['className' => 'Cewi/CakephpTbStarter.Form']);
        $this->loadHelper('Html', ['className' => 'Cewi/CakephpTbStarter.Html']);
        $this->loadHelper('Flash', ['className' => 'BootstrapUI.Flash']);
     } 

- $this->Html->span($iconName) will output a span-Tag with the icon. I.e. $this->Icon->span('glyphicon-star') will output 
```
<span class="glyphicon glyphicon-star"  aria-hidden="true"></span>
```
- In $this->Html->link() and $this->Form->postLink() you can add 'icon'=>'the-icon-you-want' in the $options-Array. It then will output an icon before the title. Example: $this->Html->link(__('Edit'), ['action'=>'edit', 1], ['icon'=>'glyphicon-pencil']) will output:
```
<a href=foo_controller/edit/1><span class="glyphicon glyphicon-pencil"  aria-hidden="true"></span>Edit</a>
```
If you add 'short'=>true as an extra options, the generated code will not have the title string:
```
<a href=foo_controller/edit/1><span class="glyphicon glyphicon-pencil"  aria-hidden="true"></span></a>
```

###Bake-Templates
just add -t Cewi/CakeTbStarter to your bake commands. The templates rely on the layouts provided by the FriendsOfCake/bootstrap-ui Plugin (above). See there how to include them.
 
