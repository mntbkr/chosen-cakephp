# ChosenHelper for CakePHP 2.0x

ChosenHelper is a class for integrating HarvestHQ [Chosen](https://github.com/harvesthq/chosen/) select boxes in CakePHP 2.0x.

Check out HarvestHQ's [demo](http://harvesthq.github.com/chosen/) for documentation and usage.

### Installation

Chosen CakePHP 2 plugin supports [Composer](https://github.com/composer/composer) and [Packagist](http://packagist.org/). After you [download](http://packagist.org/) composer.phar and put it in your path:

```
cd path/to/app/Plugin or /plugins
git clone git@github.com:paulredmond/chosen-cakephp.git Chosen
cd Chosen
php composer.phar install
```

Bootstrap the plugin in app/Config/bootstrap.php:

```php
<?php

// ...

CakePlugin::load('Chosen');

?>
```

### Optional webroot symlink
```
cd /path/to/app/webroot
ln -s ../path/to/chosen/plugin/webroot chosen
```
*Cloning into the folder Chosen is important, as that path is referenced in tests and resource urls.*

### Setup

In /app/Controller/AppController.php:

```php
<?php

public $helpers = array(
    'Chosen.Chosen',
);
```

### JQuery
Make sure that you are loading JQuery (1.4+) however you want:

```php
<?php

// One way in In default.ctp
echo $this->Html->script('jquery'); // sets src to /js/jquery.js
```

*Note: Chosen CSS/JS files are only loaded if the helper select method is called at least once.*

### Examples
Chosen inputs behave identically to the FormHelper::input() method.

Multi-select:

```php
<?php
echo $this->Chosen->select(
    'Article.category_id',
    array(1 => 'Category 1', 2 => 'Category 2'),
    array('data-placeholder' => 'Pick categories...', 'multiple' => true)
);
?>
```

Default selected:

```php
<?php
echo $this->Chosen->select(
    'Article.category_id',
    array(1 => 'Category 1', 2 => 'Category 2'),
    array(
        'data-placeholder' => 'Pick categories...',
        'default' => 1,
    ) 
);
?>
```

Grouped:

```php
<?php
echo $this->Chosen->select(
    'Profile.favorite_team',
    array(
        'NFC East' => array(
            'Dallas Cowboys',
            'New York Giants',
            'Philadelphia Eagles',
            'Washington Redskins'
        ),
        'NFC North' => array(
            'Chicago Bears',
            'Detroit Lions',
            'Greenbay Packers',
            'Minnesota Vikings'
        ),
        // ....
    ),
    array(
        'data-placeholder' => 'Pick your favorite NFL team...',
        'style' => 'width: 350px'
    )
);
?>
```
