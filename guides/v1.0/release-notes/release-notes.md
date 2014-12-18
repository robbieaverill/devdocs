---
layout: default
group: release-notes
subgroup: Release Notes
title: Release Notes
menu_title: Release Notes
menu_node: parent
menu_order: 1
github_link: release-notes/release-notes.md
---

<h4>Contents</h4>
These Release Notes have the following contents:

*	<a href="#highlights">Highlights</a>
*	<a href="#known-devbeta">Known issues</a>
*	<a href="#install">Installation</a>
*	<a href="#help">Help us improve this documentation</a>

<h2 id="highlights">Highlights</h2>

Welcome to Magento 2.0 Developer Beta documentation! And welcome to Magento 2.0!

For this first release of Magento 2.0, here is a summary of some important
features of the release.

-   PHP and MySQL. Magento 2 supports PHP 5.5, with PHP 5.4 (actually 5.4.11 or
    later) as the minimum requirement, and MySQL 5.6. See [System
    requirements][1].

    [1]: <{{ site.gdeurl }}install-gde/system-requirements.html>

-   HTML5. The reference themes available out of the box are responsive and
    based on HTML5. See [Themes][2] and [Responsive web design.][3]

    [2]: <{{ site.gdeurl }}frontend-dev-guide/themes/theme-general.html>

    [3]: <{{ site.gdeurl }}frontend-dev-guide/responsive-web-design/rwd_overview.html>

-   CSS3, and CSS preprocessing. The reference themes use CSS3. Magento 2 uses
    the LESS CSS pre-processor, or you can add support for Sass and Compass. See
    [Cascading style sheets][4], and [CSS pre-processor.][5]

    [4]: <{{ site.gdeurl }}frontend-dev-guide/css-topics/css-overview.html>

    [5]: <{{ site.gdeurl }}frontend-dev-guide/css-topics/css-preprocess.html>

-   jQuery. Magento 2 uses jQuery as the primary JavaScript library. Magento
    ships with an extensible set of jQuery widgets. See [Magento JQuery
    widgets][6].

    [6]: <{{ site.gdeurl }}frontend-dev-guide/javascript/jquery-widgets-about.html>
-   RequireJS. The RequireJS library helps load JS resources on demand to
    improve page load times. It's also intended to encourage modular design of
    frontend components. See [JavaScript resources][6].

    [6]: <{{ site.gdeurl }}config-guide/config/js-resources.html>

-   PHP and MySQL. Magento 2 supports PHP 5.5, with PHP 5.4 (actually 5.4.11 or
    later) as the minimum requirement, and MySQL 5.6. See [System
    requirements][7].

    [7]: <{{ site.gdeurl }}install-gde/system-requirements.html>

-   PSR Compliance. PSR compliance standardizes the use of PHP to allow
    different sets of code libraries to work together. See [PHP coding
    standard][8].

    [8]: <{{ site.gdeurl }}coding-standards/code-standard-php.html>

-   Modular architecture. Define your own set of modules. Cross-module
    dependencies are reduced, and interfaces among multiple extensions are
    cleaner and more discrete. See [What is Magento?][9], [Magento as a modular
    system][10], and [Service contracts][11].

    [9]: <{{ site.gdeurl }}architecture/arch_whatis.html>

    [10]: <{{ site.gdeurl }}architecture/arch_asmodsys.html>

    [11]: <{{ site.gdeurl }}extension-dev-guide/service-contracts/service-contracts.html>

-   Testing framework. Magento 2 includes a pre-packaged series of test scripts,
    including tests for integration, units, static environments, functional
    areas, and performance criteria. See [Magento Test Framework][12], and the
    [JavaScript unit tests][13].

    [12]: <https://github.com/magento/mtf/blob/master/docs/install-config.md>

    [13]: <{{ site.gdeurl }}extension-dev-guide/test/test_js-unit.html>

See also
--------

-   [XML validation][14].

    [14]: <{{ site.gdeurl }}architecture/view/xml-schema-layout.html>

-   [Service contracts][15].

    [15]: <{{ site.gdeurl }}extension-dev-guide/service-contracts/service-contracts.html>

-   [Translation][16].

    [16]: <{{ site.gdeurl }}architecture/behavior/xlate.html>

-   [Services as web APIs.][17]

    [17]: <{{ site.gdeurl }}get-started/bk-get-started-api.html>
	
<h2 id="known-devbeta">Known issues</h2>
We have identified the following known issues in this release:

*   Magento sample data is available only if you edit `composer.json` as follows:

    1.  Log in to your Magento server as the web server user or as a user with `root` privileges.
    2.  Change to your Magento installation directory.
    3.  Open `composer.json` in a text editor.
    4.  Under `"repositories":`, add the following:

        <pre>{
            "type": "composer",
            "url": "http://packages.magento.com/"
        }
    ],
     "require": {
         "php": "~5.4.11|~5.5.0",
           "magento/sample-data": "0.42.0-beta1",        
           "magento/sample-data-media": "0.42.0-beta1”</pre>
    5.  Install the Magento software using either the command line or Setup Wizard as discussed in the <a href="{{ site.gdeurl }}install-gde/bk-install-guide.html">Magento installation guide</a>.

    <div class="bs-callout bs-callout-info" id="info">
        <p>An exception might display after you run `composer install` to install the Magento software. This error is harmless. The error follows:</p>
        <code>[ErrorException]</code><br>                                                                                                
  <code>Target ./dev/tools/Magento/Tools/SampleData/InstallerApp.php already exists.</code></div>


*	<!-- <a href="https://jira.corp.x.com/browse/MAGETWO-31834">MAGETWO-31834</a> and <a href="https://jira.corp.x.com/browse/MAGETWO-31180">MAGETWO-31180</a> --> Errors might display when you attempt to access the Magento storefront or Magento Admin after installation:

	Storefront:
	
	<pre>"Can't create directory /var/www/html/m/var/generation/Magento/Framework/App/PageCache/Identifier/."
#0 /var/www/html/m/lib/internal/Magento/Framework/Code/Generator/Autoloader.php(34): Magento\Framework\Code\Generator->generateClass('Magento\\Framewo...')
#1 [internal function]: Magento\Framework\Code\Generator\Autoloader->load('Magento\\Framewo...')
#2 [internal function]: spl_autoload_call('Magento\\Framewo...')
... more </pre>

    Magento Admin:

    <pre>"Class Magento\Logging\Model\FlagFactory does not exist"
"#0 /var/www/html/ui/lib/internal/Magento/Framework/ObjectManager/Definition/Runtime.php(46): Magento\Framework\Code\Reader\ClassReader->getConstructor('Magento\\Logging...')
#1 /var/www/html/ui/lib/internal/Magento/Framework/ObjectManager/Factory/Factory.php(170): Magento\Framework\ObjectManager\Definition\Runtime->getParameters('Magento\\Logging...')
#2 /var/www/html/ui/lib/internal/Magento/Framework/ObjectManager/ObjectManager.php(71): Magento\Framework\ObjectManager\Factory\Factory->create('Magento\\Logging...')
... more</pre>

    In either case, try accessing the storefront or Magento Admin again.

*   <!-- <a href="https://jira.corp.x.com/browse/MAGETWO-31949">MAGETWO-31949</a> --> In some cases, the Setup Wizard appears to have failed when it has not failed. 

    Symptoms:

    *   The following message displays at the top of your browser on the last page: `Installation is incomplete. Check the console log for errors before trying again.`
    *   If you open the console, a success message displays at the bottom with no errors or exceptions.

    In this case, the installation *was* successful. You can access the storefront and Magento Admin as discussed in <a href="{{ site.gdeurl }}install-gde/install/verify.html">Verify the installation</a>.

    To access your Magento-created encryption key:

    1.  Log in to your Magento server as a user with `root` privileges.
    2.  Open `<your Magento install dir>/app/etc/config.php` in a text editor.
    3.  Locate the value of `'key' =>`.
        
        This is your encryption key.

*   <!-- <a href="https://jira.corp.x.com/browse/MAGETWO-31850">MAGETWO-31850</a> --> In some cases (such as running the Setup Wizard in two browser windows or tab pages at the same time), the installation fails because it cannot create `install.log`. 

    To work around this issue, see <a href="{{ site.gdeurl }}install-gde/trouble/tshoot_install-log.html">Installation fails; cannot create install.log</a>

*   <!-- <a href="https://jira.corp.x.com/browse/MAGETWO-31851">MAGETWO-31851</a> and <a href="https://github.com/magento/magento2/issues/792">GitHub issue 792</a> --> There is a known issue that prevents the usage of <a href="http://php.net/manual/en/configuration.changes.php" target="_blank">php_admin_value</a> for some session configuration settings. Specifically, we are aware that the <a href="http://php.net/manual/en/session.configuration.php#ini.session.save-path" target="_blank">session.save_path</a> cannot be set with `php_admin_value` at this time.

    Workarounds:

     *   If you're using a hosting provider that does not allow you to change the value of `php_admin_value`, there is no workaround currently. However, the only known instance that we are aware of at this time is ISPManager/ISPConfig which appears to have a <a href="http://www.howtoforge.com/forums/showthread.php?t=61127" target="_blank">method of disabling</a> the `php_admin_value` setting.


    *   If you're running the Magento software on your own server and you can log in as a user with `root` privileges, you can replace the `session.save_path` setting with a dependency injection call as follows:

        1.  Log in to your Magento server as a user with `root` privileges.
        2.  Open `php.ini` in a text editor.
        3.  Search for `session.save_path`.
        4.  Comment it out.
        5.  Save your changes to `php.ini` and exit the text editor.
        6.  Restart your web server.
        7.  Open `<your Magento install dir>/app/etc/config.php` in a text editor.
        8.  Add the following:

            <pre>‘session’ => [
‘save_path’ => ‘<your session save path>'
]</pre>
    1.  Save your changes and exit the text editor.
    2.  The Magento system now uses dependency injection for session save settings.

    If you don't know where `php.ini` is located, use the following steps:

    1.  If you haven't already done so, create <a href="{{ site.gdeurl }}install-gde/prereq/optional.html#install-optional-phpinfo">phpinfo.php</a>.
    2.  Enter the following URL in your browser's address or location field:

        <code>http://&lt;your web server IP or host name>/&lt;path to docroot>/phpinfo.php</code>

    3.  Look for the location of `php.ini`.

        `php.ini` is typically specified as **Loaded Configuration File** in the displayed results.

    4.  As a user with <code>root</code> privileges, open `php.ini` in a text editor.
    5.  Locate the value of `open_basedir` and change it.
    6.  Save your changes to `php.ini`.
    7.  Restart the web server.


<h2 id="install">Installation</h2>

Installation is simplified, and now uses Composer. See our friendly
[Installation Guide][18].

[18]: <{{ site.gdeurl }}install-gde/bk-install-guide.html>

<h2 id="help">Help improve this documentation</h2>

Magento 2.0 product documentation is hosted on GitHub, and we welcome your
feedback there.

Click the "Edit this page on GitHub" link at the top of a documentation page to
open the file in our GitHub repository, where you are invited to suggest changes
by creating pull requests, or open a discussion by creating an issue.
Feel free to contact the documentation team directly at
DL-Magento-Doc-Feedback@ebay.com.