Changelog
=========

3.0.0
-----

* Support Symfony 6
* Drop support for Symfony older than 6 and PHP older than 8
* Removed deprecated classes, see UPGRADE-3.0.md
* Removed RouteConditionMetadataListener and added condition mapping to ORM and PHPCR route mapping.

2.6.0
-----

* Implemented a new configuration option `redirectable_url_matcher` under `dynamic`.
  If set to `true`, the router will try to detect and redirect between URLs with and without trailing slashes. See https://symfony.com/doc/4.1/routing.html#routing-trailing-slash-redirection.

2.5.1
-----

* Creating a correct index for ORM, without duplicating indexes for the "name" column

2.5.0
-----

* Make dependency on twig optional, as it is not necessary for the bundle.

2.4.2
-----

* Allow installation with PHP 8.

2.4.1
-----

* Fix for indirect dependency doctrine/persistence dropping the BC layer in its new major version.

2.4.0
-----

* Minimum PHP version is now 7.2
* Support Symfony 5. Minimum Symfony version is now 4.4.
* If you generate routes with the CMF route generator, see the CHANGELOG of the routing component as well!

2.3.0
-----

* Implemented redirect route feature for the Doctrine ORM model
* Removed the name for the database index configuration on the staticPrefix field on the Route model due to name colision when the model is inherited by RediretRoute model

2.2.0
-----

* Autowiring support for ChainRouterInterface
* Fix Symfony deprecations and raise lowest versions to 3.4 || 4.3
* Allow installation with Twig 3
* Fix PHPCR route candidates handling for PHPCR node name edge cases

2.1.1
-----

* Make redirect controller service public to avoid errors while handling redirects.

2.1.0
-----

* Symfony 4 support
* **2017-11-11**: Removed php 5.6 and 7.0 support, removed Symfony 3.0.* and 3.1.* support

2.0.3
-----

* **2018-01-22**: Fixed syntax error in ValidationPass.

2.0.2
-----

* **2018-01-18**: Do not fail when the validator is not enabled.

2.0.1
-----

* **2017-09-25**: This bundle can now also directly use the Twig loader instead of the deprecated templating
  component. Symfony FrameworkBundle no longer requires symfony/templating since 3.2. If the templating component
  is available in your application, it is however still used for BC.

2.0.0
-----

Released

2.0.0-RC3
---------

 * **2017-02-17**: [BC BREAK] DynamicRouter::setRequest has been replaced with DynamicRouter::setRequestStack.

2.0.0-RC2
---------

 * **2017-02-06**: [BC BREAK] The `_template` request parameter will be renamed
   to the `template` attribute instead of the `contentTemplate` attribute. The
   old attribute will still be available for backwards compatibility.
 * **2017-02-03**: [BC BREAK] Removed unused `cmf_routing.dynamic.persistence.phpcr.content_basepath`

2.0.0-RC1
---------

 * **2016-12-02**: [BC BREAK] Moved all sonata related code to sonata-phpcr-admin-integration-bundle
 * **2016-10-10**: [ORM] Add option to use custom Route class in ORM
 * **2016-06-18**: [BC BREAK] Removed all `*.class` parameters.
 * **2016-06-18**: [BC BREAK] Removed the `cmf_routing.dynamic.persistence.phpcr.route_basepath`
   setting.
 * **2016-06-18**: [BC BREAK] Removed the `getAddFormatPattern()`/`setAddFormatPattern()`
   and `getPattern()` methods from the model `Route`.
 * **2016-06-18**: [BC BREAK] Removed the `getAddTrailingSlash()`/`setAddTrailingSlash()`
   methods from the PHPCR `Route` and `RedirectRoute`.
 * **2016-06-18**: [BC BREAK] Removed `RouteAdmin::setControllerResolver()` and
   `RouteAdmin::$controllerResolver`.

1.4.0
-----

1.4.0-RC1
---------

* **2016-01-09**: [ORM] Hardcoded some column names to match what we index on to avoid
  issues with non-default `orm.naming_strategy`. It is now safe to use a non-default
  naming strategy. If you did a workaround to use a naming strategy, you might need to
  look into that.
* **2015-10-28**: Deprecated `cmf_routing.dynamic.persistence.phpcr.route_basepath`
  setting and parameter in favor of `cmf_routing.dynamic.persistence.phpcr.route_basepaths`.
  The old names will be kept for BC reasons and removed in 2.0.

1.3.0
-----

1.3.0-RC1
---------

* **2014-08-07**: PHPCR RouteProvider no longer allows colons in the URI as they are
  interpreted as namespaces, leading to errors.
* **2014-06-06**: Updated to PSR-4 autoloading

1.2.0
-----

Release 1.2.0

1.2.0-RC2
---------

* **2014-04-23**: changed ``cmf_routing.dynamic.route_collection_limit`` default to ``0``

* **2014-04-15**: Removed the unused ContentAwareGenerator class from the
  bundle. Since 1.1 the one from the routing component was used.

* **2014-04-14**: DynamicRouter no longer implements the ContainerAwareInterface
* **2014-04-11**: drop Symfony 2.2 compatibility

1.2.0-RC1
---------

* **2014-03-29**: [Multilang] Added some options to support locale matching
  without separate routes per locale. See the new configuration options
  `match_implicit_locale` and `auto_locale_pattern`.

* **2014-03-29**: [PHPCR] The route provider can now load Routes from more than
  path in PHPCR. The configuration option `route_basepath` is renamed to
  `route_basepaths` and accepts a list of base paths. See the changelog of
  the SimpleCmsBundle as the main impact is on that side.

* **2014-03-29**: Route document and entity constructor changed. The options
  are no longer mapped separately but as route options. See UPGRADE-1.2.md for
  instructions.

* **2014-03-26**: [ORM] Applied the cleanup for the PHPCR provider to the ORM
  provider now: If the route matched a pattern with a format extension, the
  format extension is no longer set as route a default.

* **2014-03-25**: [PHPCR] setParent() and getParent() are now deprecated.
  Use setParentDocument() and getParentDocument() instead.
  Moreover, you should now enable the ChildExtension from the CoreBundle.

* **2014-03-23**: [PHPCR] urls can now be generated from the route
  uuid as route name as well, in addition to the repository path.

* **2013-12-23**: add support for ChainRouter::getRouteCollection(), added new
  config setting ``cmf_routing.dynamic.route_collection_limit``

* **2013-11-28**: [BC BREAK for xml configuration] the alias attribute of the
  <template-by-class> is renamed to class in the bundle configuration.

1.1.0
-----

* **2013-10-14**: The route enhancers now have a non-default priority so that
  the order is defined and you can add your own enhancers.

1.1.0-RC8
---------

* **2013-10-08**: The idPrefix is now used as a filter in getRouteByName() and
  getRoutesByNames() in the PHPCR RouteProvider. This means its no longer
  possible to get routes that are not children of a path that begins with
  idPrefix.

1.1.0-RC5
---------

* **2013-09-04**: If the route matched a pattern with a format extension, the
  format extension is no longer set as route a default.
* **2013-09-04**: Marked ContentAwareGenerator as obsolete, use
  ContentAwareGenerator from the CMF routing component directly instead. This
  class will be removed in 1.2.
* **2013-08-09**: dynamic.generic_controller is now defaulting to null instead
  of the controller from CmfContentBundle. CmfCoreBundle is prepending the
  CmfContentBundle generic controller if that bundle is present. If you do not
  have Core and Content, you need to configure the value explicitly if you want
  routes specifying a template to use the generic controller or have
  template_by_class mapping configuration.

1.1.0-RC2
---------

* **2013-08-04**: [PHPCR-ODM] Fixed the configuration of the LocaleListener to
  make routes again automatically provide the _locale based on their repository
  path if the bundle is configured with locales.
* **2013-08-04**: [Bundle] Only build the compiler passes for ORM and PHPCR-ODM
  if all required repositories are present.

1.1.0-RC1
---------

* **2013-07-31**: [EventDispatcher] Added events to the dynamic router at the
  start of match and matchRequest.
* **2013-07-29**: [DependencyInjection] restructured `phpcr_provider` config
  into `persistence` -> `phpcr` to match other Bundles.
* **2013-07-28**: [DependencyInjection] added `enabled` flag to
  `phpcr_provider` config.
* **2013-07-26**: [Model] Removed setRouteContent and getRouteContent, use
  setContent and getContent instead.
* **2013-07-19**: [Model] Separated database agnostic, doctrine generic and
  PHPCR-ODM specific code to prepare for Doctrine ORM support.
* **2013-07-17**: [FormType] Moved TermsFormType to CoreBundle and renamed it
  to CheckboxUrlLableFormType.

1.1.0-beta2
-----------

* **2013-05-28**: [Bundle] Only include Doctrine PHPCR compiler pass if
  PHPCR-ODM is present.
* **2013-05-25**: [Bundle] Drop symfony_ from symfony_cmf prefix.
* **2013-05-24**: [Document] ContentRepository now requires ManagerRegistry in
  the constructor and provides `setManagerName()` in the same way as
  RouteProvider.
* **2013-05-24**: [Document] RouteProvider now requires ManagerRegistry in the
  constructor (the `cmf_routing.default_route_provider` does this for you). To
  use a different document manager from the registry, call `setManagerName()`
  on the RouteProvider.
