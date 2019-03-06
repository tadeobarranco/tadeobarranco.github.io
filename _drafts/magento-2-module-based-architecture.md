---
layout: post
title: Magento 2 - Module Based Architecture
description: "As part of my training to do the Magento 2 Certified Professional Developer exam I want to write in my own way about the topics I found in the oficial Magento guides, hoping this could help anyone else who wants to pass the test."
tags: [magento 2, certified professional developer, magento architecture and customization techniques]
excerpt_separator: <!--more-->
image:
  path: 
  feature: 
  twitter: 
---

As part of my **training** to do the **Magento 2 Certified Professional Developer** exam I want to write in my own way about the topics I found in the oficial Magento guides, hoping this could help anyone else who wants to pass the test.

<!--more-->

Also I'm inspired in these other guides: [SWIFTotter's Study Guide](https://swiftotter.com/technical/certifications/magento-2-certified-developer-study-guide){:target="blank"} and [Magento 2 Exam Notes](https://github.com/magento-notes/magento2-exam-notes){:target="blank"}, not only to clarify my doubts but to share it with you and together learn more about it. The only way to really understand something is practice, practice and more practice. So let's do it.

## Describe Magento's module-based architecture

In this topic the goal is to resolve the following text found in the Magento Guide:

> **Describe module limitations**. How do different modules interact with each other? What side effects can come from this
interaction?

If you are familiar with the Magento 1 code pools and folder structure, you should know that Magento 2 now works in a different way since it has all the files needed for each module in only one folder.

So, if you create a new module it would live inside of the `app/code/<vendor>/<type>-<module-name>`folder. But if the module is one of the Magento Core modules or a third party solution module it would be inside of the `vendor/<vendor>/<type>-<module-name>`. 

In both cases `<vendor>` is the vendor name, `<type>` is a reference of the type of this module which could be a `module`, a `theme` or a `lenguage`, and the `<module-name>` is a descriptive name of the module purpose. Let's see some examples:

```
app/
.. code/
.... Barranco/
...... CertificationTraining/
```

```
vendor/
.. magento/
.... module-catalog/
```

```
vendor/
.. amzn/
.... amazon-pay-and-login-with-amazon-core-module/
```

The two last examples are modules located inside of the `vendor` folder and that means they were installed using `composer`, while the first one is a custom module created by the `Barranco` company and that's the reason why it lives in `app/code`.

Maybe if you worked before with Magento 1.x you can remember than anything inside of the `app/code/core` code pool shouldn't be modified directly there, well, in Magento 2.x the same thing happens with anything inside the `vendor` folder.

Following with the module description we should talk about what are the minimum and required files to initiate a module. And those are `registration.php`, `etc/module.xml` and `composer.json`. Let's create an example:

{% highlight php linenos %}
<?php
/**
 * @category  Barranco
 * @package   Barranco\CertificationTraining
 * @author    Tadeo Barranco <tbarrancoa@gmail.com>
 * @license   MIT license
 */

\Magento\Framework\Component\ComponentRegistrar::register(
  \Magento\Framework\Component\ComponentRegistrar::MODULE,
  'Barranco_CertificationTraining',
  __DIR__
);
{% endhighlight %}

The content (above) is the content of a common **register.php** where you can find an instance of the `Magento\Framework\Component\ComponentRegistrat` class at **line 9** invoking the `register` method which requires three parameters: `type`, `componentName` and `path`.

In this case the `type` parameter at the **line 10** corresponds to the registration of a **MODULE** and yes it sounds redundant since we are talking about modules but we must not forget that the `type` could also be a **THEME** or a **LANGUAGE** package and its **registration.php** file should look like this respectively:

{% highlight php linenos %}
<?php
/**
 * @category  Barranco
 * @package   Barranco\venera-inspired
 * @author    Tadeo Barranco <tbarrancoa@gmail.com>
 * @license   MIT license
 */

\Magento\Framework\Component\ComponentRegistrar::register(
  \Magento\Framework\Component\ComponentRegistrar::THEME,
  'frontend/Barranco/venera-inspired',
  __DIR__
);
{% endhighlight %}

{% highlight php linenos %}
<?php
/**
 * @category  Barranco
 * @package   Barranco\es_mx
 * @author    Tadeo Barranco <tbarrancoa@gmail.com>
 * @license   MIT license
 */

\Magento\Framework\Component\ComponentRegistrar::register(
  \Magento\Framework\Component\ComponentRegistrar::LANGUAGE,
  'barranco_es_mx',
  __DIR__
);
{% endhighlight %}

This last two blocks of code are also **registration.php** files but the modules where their are instead of  be at the `app/code` folder they are in `app/design` and `app/i18n`.

The next parameter at the **line 11** in each example represents the **componentName** where for a module is the `<VendorName>` plus `<_>` plus `<ModuleName>`. In the module register example we have the following component name: `Barranco_CertificationTraining`. For a themes and languages the name convention is `<area>` plus `</>` plus `<VendorName>` plus `</>` plus `<theme_name>` for `themes` and `<vendor>` plus `<_>` plus `<package_name>` for `language` and as example we have `frontend/Barranco/venera_inspired` and `barranco_es_mx` respectively.

The last parameter always would be `__DIR__` as you can see in each example.

Once you have a complete `registration.php` file is time to work with the **etc/module.xml** file for your extension. Inside your module, just create an `etc` that contains a `module.xml` file. The content of this file would look like this:

{% highlight xml linenos %}
<?xml version="1.0" encoding="UTF-8"?>
<!--
/**
 * @category   Barranco
 * @package    Barranco\MexicanRegions
 * @author     Tadeo Barranco <tbarrancoa@gmail.com>
 * @license    MIT license
 */
-->
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
  <module name="Barranco_MexicanRegions" setup_version="1.0.0">
    <sequence>
      <module name="Magento_Directory" />
    </sequence>
  </module>
</config>
{% endhighlight %}

In this file we have a `etc/module.xml`  file for a different module, that's the reason why at **line 11** you can see `Barranco_MexicanRegions` as the **value** of the name **attribute** for the **module** tag. In the same line you can find the **version** of the module wich determinate which version of setup and upgrade should run.

Something else that is important to mention about this file is the capability to use a `sequence` tag which could include one or more module declaration. This list allows your module to set in which order would be loaded. In the example above you can see that inside the **sequence** tags we have a `module`tag with a name parameter value equals to `Magento_Directory`. It means that the `Magento_Directory` should be installed before our custom module as we can see in the `app/etc/config.php` file after we enable and install it.

{% highlight php linenos %}
<?php

return [
  'module' => [
    'Magento_Store' => 1,
    'Magento_Directory' => 1,
    'Magento_Eav' => 1,
    'Barranco_MexicanRegions' => 1,
    .
    .
    .
  ]
];
{% endhighlight %}

Finally the **composer.json** file in a custom module allows that the `Component Manager` can update, uninstall, enable or disable a module if it was installed using Composer and even if a module wasn't be installed using composer if it has a `composer.json` file. Magento recommend us to include this file even when we aren't going to distribute it. An example of this file look like this:

{% highlight composer linenos %}
{
  "name": "barranco/magento2-mexicanregions",
  "description": "Mexican Regions for Magento 2",
  "require": {
    "php": "~5.5.0|~5.6.0|~7.0.0",
    "magento/module-directory": "100.*"
  },
  "type": "magento2-module",
  "version": "1.0.0",
  "license": [
    "MIT"
  ],
  "authors": [
    {
      "name": "Tadeo Barranco",
      "email": "tbarrancoa@gmail.com",
      "homepage": "http://www.tadeobarranco.com"
    }
  ],
  "autoload": {
    "files": [
      "registration.php"
    ],
    "psr-4": {
      "Barranco\\MexicanRegions\\": ""
    }
  }
}
{% endhighlight %}

At this moment a custom module structure would look like:

```
app/
.. code/
.... Barranco/
...... CertificationTraining/
........ etc/
.......... module.xml
........ composer.json
........ registration.php
```

With this definition you are able to load your module in a correctly order to modify something you need of the core logic, templates, etc. However a module has some **limitations** to work properly:

- Your module should be enable and to be enable it should contains the require files `registration.php`, `etc/module.xml` and `composer.json`.

- A module should just resolve only one business feature and anything related to it should be whithin the same folder.

- If you disable a module, the data or tables won't be delated automatically to the database. An it shouldn't disable another module.

Now talking about **how different modules interact with each other** we found that Magento 2 use the **PSR-4** compliant which means that the namespace path of a class should match with it file path as we can see in this example:

{% highlight php linenos %}
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */
namespace Magento\Catalog\Block\Widget;

use Magento\Ui\Block\Wrapper;

/**
 * Dynamicly creates recently compared widget ui component, using information
 * from widget instance and Catalog/widget.xml
 */
class RecentlyCompared extends Wrapper implements \Magento\Widget\Block\BlockInterface
{
}
{% endhighlight %}

```
vendor/
.. magento/
.... module-catalog/
...... .
...... .
...... Block/
........ Widget/
.......... .
.......... .
.......... RecentlyCompared.php
.......... .
........ .
........ .
...... .
```

Also Magento 2 use the **dependency injection** pattern and **service contracts** to module interaction using **areas** to optimized request processing. Magento areas are: `adminhtml`, `frontend`, `base`, `cron`, `webapi_rest` and `webapi_soap`.

## Conclusions