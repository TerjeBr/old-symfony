UPGRADE FROM 4.3 to 4.4
=======================

Cache
-----

 * Added argument `$prefix` to `AdapterInterface::clear()`

Debug
-----

 * Deprecated `FlattenException`, use the `FlattenException` of the `ErrorRenderer` component
 * Deprecated the whole component in favor of `ErrorHandler` component

DependencyInjection
-------------------

 * Deprecated support for short factories and short configurators in Yaml

   Before:
   ```yaml
   services:
     my_service:
       factory: factory_service:method
   ```

   After:
   ```yaml
   services:
     my_service:
       factory: ['@factory_service', method]
   ```
 * Deprecated `tagged` in favor of `tagged_iterator`

   Before:
   ```yaml
   services:
       App\Handler:
           tags: ['app.handler']

       App\HandlerCollection:
           arguments: [!tagged app.handler]
   ```

   After:
   ```yaml
   services:
       App\Handler:
       tags: ['app.handler']

   App\HandlerCollection:
       arguments: [!tagged_iterator app.handler]
   ```

 * Passing an instance of `Symfony\Component\DependencyInjection\Parameter` as class name to `Symfony\Component\DependencyInjection\Definition` is deprecated.

   Before:
   ```php
   new Definition(new Parameter('my_class'));
   ```

   After:
   ```php
   new Definition('%my_class%');
   ```

Filesystem
----------

 * Support for passing a `null` value to `Filesystem::isAbsolutePath()` is deprecated.

Form
----

 * Using `int` or `float` as data for the `NumberType` when the `input` option is set to `string` is deprecated.

FrameworkBundle
---------------

 * Deprecated booting the kernel before running `WebTestCase::createClient()`.
 * Deprecated support for `templating` engine in `TemplateController`, use Twig instead
 * The `$parser` argument of `ControllerResolver::__construct()` and `DelegatingLoader::__construct()`
   has been deprecated.
 * The `ControllerResolver` and `DelegatingLoader` classes have been marked as `final`.
 * The `controller_name_converter` and `resolve_controller_name_subscriber` services have been deprecated.
 * Deprecated `routing.loader.service`, use `routing.loader.container` instead.

HttpClient
----------

 * Added method `cancel()` to `ResponseInterface`

HttpFoundation
--------------

 * `ApacheRequest` is deprecated, use `Request` class instead.

HttpKernel
----------

 * Implementing the `BundleInterface` without implementing the `getPublicDir()` method is deprecated.
   This method will be added to the interface in 5.0.
 * The `DebugHandlersListener` class has been marked as `final`

Lock
----

 * Deprecated `Symfony\Component\Lock\StoreInterface` in favor of `Symfony\Component\Lock\BlockingStoreInterface` and
   `Symfony\Component\Lock\PersistingStoreInterface`.
 * `Factory` is deprecated, use `LockFactory` instead

Messenger
---------

 * Deprecated passing a `ContainerInterface` instance as first argument of the `ConsumeMessagesCommand` constructor,
   pass a `RoutableMessageBus`  instance instead.

MonologBridge
--------------

 * The `RouteProcessor` has been marked final.
 
Process
-------

 * Deprecated the `Process::inheritEnvironmentVariables()` method: env variables are always inherited.

PropertyAccess
--------------

 * Deprecated passing `null` as 2nd argument of `PropertyAccessor::createCache()` method (`$defaultLifetime`), pass `0` instead.

Routing
-------

 * Deprecated `ServiceRouterLoader` in favor of `ContainerLoader`.
 * Deprecated `ObjectRouteLoader` in favor of `ObjectLoader`.

Security
--------

 * Implementations of `PasswordEncoderInterface` and `UserPasswordEncoderInterface` should add a new `needsRehash()` method

Stopwatch
---------

 * Deprecated passing `null` as 1st (`$id`) argument of `Section::get()` method, pass a valid child section identifier instead.

TwigBridge
----------

 * Deprecated to pass `$rootDir` and `$fileLinkFormatter` as 5th and 6th argument respectively to the
   `DebugCommand::__construct()` method, swap the variables position.

Validator
---------

 * Deprecated passing an `ExpressionLanguage` instance as the second argument of `ExpressionValidator::__construct()`.
 * Deprecated using anything else than a `string` as the code of a `ConstraintViolation`, a `string` type-hint will
   be added to the constructor of the `ConstraintViolation` class and to the `ConstraintViolationBuilder::setCode()`
   method in 5.0.
 * Deprecated passing an `ExpressionLanguage` instance as the second argument of `ExpressionValidator::__construct()`. 
   Pass it as the first argument instead.
 * The `Length` constraint expects the `allowEmptyString` option to be defined
   when the `min` option is used.
   Set it to `true` to keep the current behavior and `false` to reject empty strings.
   In 5.0, it'll become optional and will default to `false`.

WebProfilerBundle
-----------------

 * Deprecated the `ExceptionController::templateExists()` method
 * Deprecated the `TemplateManager::templateExists()` method

WebServerBundle
---------------

 * The bundle is deprecated and will be removed in 5.0.
