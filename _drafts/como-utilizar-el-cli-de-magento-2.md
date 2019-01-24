---
layout: post
title: ¿Cómo utilizar el CLI de Magento 2?
description: ""
tags: [magento, magento 2, tutoriales, principiantes]
excerpt_separator: <!--more-->
image:
  path: 
  feature: 
  twitter: 
---

La curva de aprendizaje de Magento 2 ha resultado más larga de lo que la comunidad esperaba, por las diferencias entre *tecnologías* y *paradigmas* utilizadas respecto a sus versiones anteriores. Pero en definitiva, una mejora **ENORME** es la integración del **Command Line Interface** (CLI).

<!--more-->

La *interfaz de línea de comandos* que viene con Magento 2 son una serie de *comandos* que ejecutan alguna funcionalidad que antes era solo accesible manualmente a través del *admin* de Magento o que incluso no existía.

Para conocer la lista de comandos disponibles es necesario que abrabamos nuestra *terminal* e ingresemos a la ruta de archivos donde nuestro proyecto fue creado. Ya estando ahí escribimos la siguiente línea:

```bash
$ php bin/magento
```

La respuesta tras la ejecución de dicha línea de código es la siguiente:

```
Magento CLI version 2.2.6

Usage:
  command [options] [arguments]

Options:
  -h, --help            Display this help message
  -q, --quiet           Do not output any message
  -V, --version         Display this application version
      --ansi            Force ANSI output
      --no-ansi         Disable ANSI output
  -n, --no-interaction  Do not ask any interactive question
  -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug

Available commands:
  help                                     Displays help for a command
  list                                     Lists commands
 admin
  admin:user:create                        Creates an administrator
  admin:user:unlock                        Unlock Admin Account
 app
  app:config:dump                          Create dump of application
  app:config:import                        Import data from shared configuration files to appropriate data storage
  app:config:status                        Checks if config propagation requires update
 cache
  cache:clean                              Cleans cache type(s)
  cache:disable                            Disables cache type(s)
  cache:enable                             Enables cache type(s)
  cache:flush                              Flushes cache storage used by cache type(s)
  cache:status                             Checks cache status
 catalog
  catalog:images:resize                    Creates resized product images
  catalog:product:attributes:cleanup       Removes unused product attributes.
 config
  config:sensitive:set                     Set sensitive configuration values
  config:set                               Change system configuration
  config:show                              Shows configuration value for given path. If path is not specified, all saved values will be shown
 cron
  cron:install                             Generates and installs crontab for current user
  cron:remove                              Removes tasks from crontab
  cron:run                                 Runs jobs by schedule
 customer
  customer:hash:upgrade                    Upgrade customer's hash according to the latest algorithm
 deploy
  deploy:mode:set                          Set application mode.
  deploy:mode:show                         Displays current application mode.
 dev
  dev:di:info                              Provides information on Dependency Injection configuration for the Command.
  dev:profiler:disable                     Disable the profiler.
  dev:profiler:enable                      Enable the profiler.
  dev:query-log:disable                    Disable DB query logging
  dev:query-log:enable                     Enable DB query logging
  dev:source-theme:deploy                  Collects and publishes source files for theme.
  dev:template-hints:disable               Disable frontend template hints. A cache flush might be required.
  dev:template-hints:enable                Enable frontend template hints. A cache flush might be required.
  dev:tests:run                            Runs tests
  dev:urn-catalog:generate                 Generates the catalog of URNs to *.xsd mappings for the IDE to highlight xml.
  dev:xml:convert                          Converts XML file using XSL style sheets
 i18n
  i18n:collect-phrases                     Discovers phrases in the codebase
  i18n:pack                                Saves language package
  i18n:uninstall                           Uninstalls language packages
 indexer
  indexer:info                             Shows allowed Indexers
  indexer:reindex                          Reindexes Data
  indexer:reset                            Resets indexer status to invalid
  indexer:set-dimensions-mode              Set Indexer Dimensions Mode
  indexer:set-mode                         Sets index mode type
  indexer:show-dimensions-mode             Shows Indexer Dimension Mode
  indexer:show-mode                        Shows Index Mode
  indexer:status                           Shows status of Indexer
 info
  info:adminuri                            Displays the Magento Admin URI
  info:backups:list                        Prints list of available backup files
  info:currency:list                       Displays the list of available currencies
  info:dependencies:show-framework         Shows number of dependencies on Magento framework
  info:dependencies:show-modules           Shows number of dependencies between modules
  info:dependencies:show-modules-circular  Shows number of circular dependencies between modules
  info:language:list                       Displays the list of available language locales
  info:timezone:list                       Displays the list of available timezones
 maintenance
  maintenance:allow-ips                    Sets maintenance mode exempt IPs
  maintenance:disable                      Disables maintenance mode
  maintenance:enable                       Enables maintenance mode
  maintenance:status                       Displays maintenance mode status
 module
  module:disable                           Disables specified modules
  module:enable                            Enables specified modules
  module:status                            Displays status of modules
  module:uninstall                         Uninstalls modules installed by composer
 newrelic
  newrelic:create:deploy-marker            Check the deploy queue for entries and create an appropriate deploy marker.
 sampledata
  sampledata:deploy                        Deploy sample data modules
  sampledata:remove                        Remove all sample data packages from composer.json
  sampledata:reset                         Reset all sample data modules for re-installation
 setup
  setup:backup                             Takes backup of Magento Application code base, media and database
  setup:config:set                         Creates or modifies the deployment configuration
  setup:cron:run                           Runs cron job scheduled for setup application
  setup:db-data:upgrade                    Installs and upgrades data in the DB
  setup:db-schema:upgrade                  Installs and upgrades the DB schema
  setup:db:status                          Checks if DB schema or data requires upgrade
  setup:di:compile                         Generates DI configuration and all missing classes that can be auto-generated
  setup:install                            Installs the Magento application
  setup:performance:generate-fixtures      Generates fixtures
  setup:rollback                           Rolls back Magento Application codebase, media and database
  setup:static-content:deploy              Deploys static view files
  setup:store-config:set                   Installs the store configuration. Deprecated since 2.2.0. Use config:set instead
  setup:uninstall                          Uninstalls the Magento application
  setup:upgrade                            Upgrades the Magento application, DB data, and schema
 store
  store:list                               Displays the list of stores
  store:website:list                       Displays the list of websites
 theme
  theme:uninstall                          Uninstalls theme
 varnish
  varnish:vcl:generate                     Generates Varnish VCL and echos it to the command line
```

En las primeras líneas de este mensaje vemos la versión del **CLI** que siempre será igual a la versión de Magento que tenemos instalada. Vemos también, la forma en que debemos utilizar cada opción de esta lista. Para enseguida mostrarnos las *opciones* que tenemos al ejecutar `php bin/magento`. Por ejemplo, según la lista de opciones, puedes conocer solo la versión del *CLI* y por lo tanto de tu Magento sin necesidad de ver <strong>TODO</strong> el mensaje anterior. Esto sería posible ejecutando lo siguiente:

```bash
$ php bin/magento -V
```

Y la respuesta será algo similar a:

```bash
Magento CLI version 2.2.6
```

Lo siguiente es una lista de cada **comando** disponible, dicha lista puede verse alterada dependiendo de la versión de Magento instalada así como de la distribución, que puede ser *Open Source* o *Enterprides*. Así mismo, tú puedes crear un módulo para tener tus propios comandos.

De la lista podemos observar varios puntos interesantes. **Primero** tenemos a dos comandos listados que son `help` y `list`. Estos comandos pdriamos tomarlo como *generales* ya que pueden interactuar con todos los demás. Por ejemplo, ejecutando:

```bash
$ php bin/magento help list
```

El *script* nos mostraría la siguiente respuesta:

```bash
Usage:
  list [options] [--] [<namespace>]

Arguments:
  namespace            The namespace name

Options:
      --xml            To output list as XML
      --raw            To output raw command list
      --format=FORMAT  The output format (txt, xml, json, or md) [default: "txt"]

Help:
  The list command lists all commands:

    php bin/magento list

  You can also display the commands for a specific namespace:

    php bin/magento list test

  You can also output the information in other formats by using the --format option:

    php bin/magento list --format=xml

  It is also possible to get raw list of commands (useful for embedding command runner):

    php bin/magento list --raw
```

Lo que pasa con este comando y su respuesta es lo siguiente, le estamos diciendo al comando `help` que nos *explique* como utilizar el comando `list`, a lo que responde con la forma de utilizarlo, sus opciones y argumentos válidos y diferentes ejemplos de uso para una mejor interpretación. 

El comando `list` funciona de forma muy similar, sin embargo, podemos diferenciar que el comando *help* funciona para instrucciones o comandos finales, es decir aquellos que ya ejecutan una acción, mientras que list trabaja con los grupos o conjuntos de comandos. Por ejemplo si ejecutaramos solo `php bin/magento list` veríamos el mismo resultado obtenido de ejecutar `php bin/magento`.

Ahora, identificando los *grupos* de códigos disponibles en una instalación *default* de Magento 2 tenemos que son:

- admin
- app
- cache
- catalog
- config
- cron
- customer
- deploy
- dev
- i18n
- indexer
- info
- maintenance
- module
- newrelic
- sampledata
- setup
- store
- theme
- varnish

Claro, esta lista de grupos puede tener más o menos opciones dependiendo nuevamente de la versión. Estos grupos puedes diferenciarlos en la lista que tenemos arriba pues tienen diferente *identación* que el resto de la lista, separando así las agrupaciones de los comandos disponibles.

Con la práctica y el desarrollo de muchos proyectos en Magento 2 estas agrupaciones te seran muy familiares y utilizando los comandos `list` y `help` podrás hacer un uso adecuado de cada comando. Por ejemplo, utilicemos el comando list para saber que comandos tengo disponibles en el grupo *admin*, escribe en tu terminal:

```bash
$ php bin/magento list admin
```

La respuesta, además de indicarte la forma de uso y opciones disponibles lista los comandos disponibles para la palabra clave "admin", en este caso `admin:user:create` y `admin:user:unlock` los cuales son útiles para crear y desbloquear un usario del administrador de Magento 2 respectivamente.

Ahora puedes ejecutar el comando *help* para alguno de esos comandos disponibles y saber cuáles son los argumentos y opciones disponibles. Por ejemplo, la respuesta tras ejecutar `php bin/magento help admin:user:create` será:

```bash
Usage:
  admin:user:create [options]

Options:
      --admin-user=ADMIN-USER                    (Required) Admin user
      --admin-password=ADMIN-PASSWORD            (Required) Admin password
      --admin-email=ADMIN-EMAIL                  (Required) Admin email
      --admin-firstname=ADMIN-FIRSTNAME          (Required) Admin first name
      --admin-lastname=ADMIN-LASTNAME            (Required) Admin last name
      --magento-init-params=MAGENTO-INIT-PARAMS  Add to any command to customize Magento initialization parameters
                                                 For example: "MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache"
  -h, --help                                     Display this help message
  -q, --quiet                                    Do not output any message
  -V, --version                                  Display this application version
      --ansi                                     Force ANSI output
      --no-ansi                                  Disable ANSI output
  -n, --no-interaction                           Do not ask any interactive question
  -v|vv|vvv, --verbose                           Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug

Help:
  Creates an administrator
```

Puedes notar que dentro del menú **Options** los primeros cinco parámetros tienen la leyenda **Required**, lo cual quiere decir que al momento de ejecutar el comando `admin:user:create` son **obligatorios**. En este caso si no ingresas tú los campos requeridos Magento 2 en tu misma *terminal* te preguntará por ellos.  

Los comandos auxiliares `help` y `list` los puedes utilizar con todos los comandos y grupos respecitivamente de la misma forma en que los utilizaste con los ejemplos de este blog. De ese modo te será más fácil y simple poder interactuar desde la terminal con tu ecommerce en Magento 2. 

## Conclusiones

Ahora ya tienes una visión general del uso y los alcances del **CLI** que viene integrado en Magento 2. Utilizar estos comandos te serán indispensables para trabajar con tu ecommerce. Aún cuando tu no seas un desarrollador *backend* o *frontend*, puede que seas el *project manager* y estes actualizando el catálogo de productos, seguro vas a pedir que reindexen el sitio y adivina que, ese proceso es posible únicamente con la *interfaz de línea de comandos*.

¿Te gustaría aprender sobre como utilizar cada uno de los comandos? ¿Quieres aprender a crear tus propios comandos? Seguramente en otros artículos crearemos un módulo con nuestro propio comando disponible a través de la terminal.

Nuevamente te invito a compartir este artículo y dejar algún comentario. Si tienes dudas estoy dispuesto a resolverlas. La idea principal de tener este blog es compartir de forma que todos conozcamos algo del día a día de un trabajo como programador o en el área del comercio electrónico.