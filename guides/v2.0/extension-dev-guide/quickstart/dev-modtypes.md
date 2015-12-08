---
layout: default
group: quickstart
subgroup: 02_Dev
title: Component types
menu_title: Component types
menu_order: 5
menu_node: 
github_link: extension-dev-guide/quickstart/dev-modtypes.md
---

#### Contents
*	<a href="#types-spt">Supported component types</a>
*	TBD
*	<a href="#types-vers">Versioning</a>

<h2 id="types-spt">Supported component types</h2>

{% include php-dev/composer-types.md %}

## TBD
"Different types of packaging: module vs metapackages , pricing considerations and impact on packaging"

(Do not understand this part.)

<h2 id="types-vers">Versioning</h2>
Components have the following types of versions:

*	Marketing version; in other words, the version the merchant interacts with. 

	Your initial version might be 1.0.0 or 2.0.0, for example. You should follow TBD guidelines for setting marketing version numbers.

*	Composer version; in other words, the version of each module, theme, language package, and its dependencies. 

	These versions are up to you. 

Using Magento code as an example, Magento CE marketing version 2.0.0 includes component versions such as 100.0.1, 100.0.2, and so on. These versioning strategy prevents collisions between the marketing version and component versions.