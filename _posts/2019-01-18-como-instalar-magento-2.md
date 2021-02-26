---
layout: post
title: ¿Cómo instalar Magento 2?
description: "NO son necesarios demasiados conocimientos técnicos para instalar la plataforma. Ya hemos visto cómo descargar Magento 2), y existen dos métodos de instalación, ambos los describo paso a paso."
tags: [magento, magento 2, tutoriales, principiantes]
excerpt_separator: <!--more-->
image:
  feature: install-magento.png
  twitter: install-magento.png
---

<strong>NO</strong> son necesarios demasiados conocimientos técnicos para instalar la plataforma. Ya hemos visto [cómo descargar Magento 2](http://www.tadeobarranco.com/como-descargar-magento-2/), y existen <strong>dos</strong> métodos de <strong>instalación</strong>, ambos los describo paso a paso.

<!--more-->

Con una de las opciones que te voy a compartir, <strong>INSTALAR</strong> Magento 2, es tan fácil como instalar cualquier software en tu computadora, ya sabes, dar click al botón siguiente tantas veces cómo el software te lo pide. La otra es a través de tu terminal de línea de comandos, pero es super simple.

Antes de comenzar con el proceso de instalación es necesario prepararnos con lo siguiente:

- [Descargar Magento 2](http://www.tadeobarranco.com/como-descargar-magento-2/)
- Crear la base de datos que utilizaras para tu tienda.

Recuerda, si tu perfil no es el de un programador o un administrador de bases de datos, y no tienes idea de como hacer el paso relacionado con la base de datos, tienes varias opciones, si necesitas instalar Magento para un proyecto de tu empresa y quieres hacer el proceso de instalación por tu cuenta, puedes pedir a tu equipo técnico que cree la base de datos para que tu la configures. Así mismo existen servidores cuyo equipo de soporte son muy buenos y amables como para ayudarte con estos detalles. 

Si no cuentas con un equipo técnico, un equipo de soporte para tu servidor o quieres instalarlo localmente en tu maquina, puedes contactarme a mí y yo te orientaré hasta que lo logres.

## Instalar con ayuda del asistente de instalación

Si tienes una computadora con [Windows](https://www.microsoft.com/es-mx/windows){:target="blank"} o [Mac OS](https://www.apple.com/mx/macos){:target="blank"} y haz tenido la necesidad de instalar algún software seguramente haz tenido que utilizar el asistente de instalación que los desarrolladores de ese software crean y lo único que tienes que hacer es dar click en siguiente muchas veces, sin ser necesario leer completamente las instrucciones.

Magento 2 en todas sus versiones al igual que su antecesor Magento 1 cuentan con un <i>Wizard</i>, que te asiste en el proceso de instalación. La pantalla de inicio de este asistente se ve de la siguiente manera:

<figure>
	<a href="/images/blog/magento-install/landing-install.png">
		<img width="100%" src="/images/blog/magento-install/landing-install.png" alt="Magento 2 landing de asistente de instalación">
	</a>
</figure>

Después de leer los términos y condiciones de la plataforma y dar click en el botón de <i>"Agree and Setup Magento"</i>, veremos una pantalla como la siguiente, donde podemos ver los pasos que se deben cumplir para llenar la información antes de iniciar con el proceso de instalación.

<figure>
	<a href="/images/blog/magento-install/readiness-check-install.png">
		<img width="100%" src="/images/blog/magento-install/readiness-check-install.png" alt="Magento 2 pantalla para checar si los requerimientos estan listos.">
	</a>
</figure>

Como un pre-paso está <i>"Readiness check"</i> dónde valida la versión de <i>PHP</i>, su configuración, sus extensiones instaladas, y la validación de ciertos directorios del código que descargamos que deben tener permisos de escritura.

<figure>
	<a href="/images/blog/magento-install/readiness-check-ok.png">
		<img width="100%" src="/images/blog/magento-install/readiness-check-ok.png" alt="Magento 2 requerimientos ok.">
	</a>
</figure>

Con todas las validaciones en verde podemos avanzar al siguiente paso dando click en el botón de <i>"Next"</i>. Lo siguiente que se muestra es el formulario para configurar la base de datos a utilizar, es super importante que esta base de datos ya este creada, de lo contrario marcará un error y no se puede continuar.

Los datos que este paso solicita a través del formulario son:

- <strong>Database server host</strong>. Es decir la maquina o el servidor donde se creo la base de datos.
- <strong>Database server username</strong>. Solicita el nombre de usuario de la base de datos.
- <strong>Database server password</strong>. Se refiere a la contraseña del usuario que configuramos arriba para la base de datos.
- <strong>Database Name</strong>. El nombre de la base de datos que configuramos.
- <strong>Table prefix</strong>. El único dato opcional, el cual es utilizado para asignar el valor como prefijo en todas las tablas.

Esta pantalla para la configuración de la base de datos luce de la siguiente manera:

<figure>
	<a href="/images/blog/magento-install/add-database.png">
		<img width="100%" src="/images/blog/magento-install/add-database.png" alt="Magento 2 add database.">
	</a>
</figure>

Como siguiente paso toca configurar las direcciones web del área donde los clientes verán nuestra tienda y del área del administrador.

<figure>
	<a href="/images/blog/magento-install/web-configuration.png">
		<img width="100%" src="/images/blog/magento-install/web-configuration.png" alt="Magento 2 configuración web.">
	</a>
</figure>

Para continuar con la configuración de los siguientes valores:

- Zona horaria
- Moneda
- Idioma

Puedes dejar los valores por defecto que Magento 2 selecciona para estos requerimientos, los cuales se ven en la siguiente imagen, después cuando estes configurando algunos valores de tu tienda desde el administrador puedes editar también estos valores.

<figure>
	<a href="/images/blog/magento-install/customize-store.png">
		<img width="100%" src="/images/blog/magento-install/customize-store.png" alt="Magento 2 configuración web.">
	</a>
</figure>

Ya casi estamos por terminar, hay que configurar simplemente los datos de acceso para el admnistrador de Magento, completamos el siguiente formulario y listo.

<figure>
	<a href="/images/blog/magento-install/admin-account.png">
		<img width="100%" src="/images/blog/magento-install/admin-account.png" alt="Magento 2 configuración web.">
	</a>
</figure>

Da click en el botón de <i>"Next"</i> y verás la última pantalla con un botón con la leyenda <i>"Install Now"</i>. Da click en este botón y <i>vualá</i>, comienza la instalación.

Si todo marcha bien verás un mensaje de instalación <strong>EXITOSA</strong>. Ahora puedes entrar a la dirección web (url) que configuraste en el proceso de instalación para ver la vista de tu tienda y también a la url de tu administrador para empezar ahora si a trabajar en tu ecommerce.

## Instalación utilizando línea de comandos

Lo sé, la opción anterior es tan simple y sencilla de seguir que quizás estas pensando en saltarte esta parte, sobre todo por que menciona esas palabras que si no tienes mucha experiencia asustan a cualquiera <i>línea de comandos</i>. Pero aunque suene complicado no lo es, es igual de simple sino es que más, que la anterior, el grado de dificultad solo aumenta por que necesitas saber utilizar el <strong>CLI</strong> (Interfaz de Línea de Comandos) que viene con el paquete de la plataforma.

Esta opción de instalación si es 100% nueva en la versión 2 de Magento que ya cuenta con toda una serie de instrucciones que podemos realizar a través de la terminal. En otros artículos estaré profundizando en esto. La instrucción para instalar magento usando el <i>CLI</i> quedará de la siguiente manera.

```bash
php bin/magento setup:install \
--base-url=http://urldelproyecto/ \
--db-host=localhost \
--db-name=database_name \
--db-user=database_user \
--db-password=database_password \
--backend-frontname=admin_url \
--admin-firstname=Admin Firstname \
--admin-lastname=Admin Lastname \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1
``` 

Debes cambiar los valores después de cada signo de <i>=</i> para asignar los valores según tu configuración. Para ahorrarte tiempo, sólo cambia los valores para `--base-url`, `--db-host`, `--db-name`, `--db-user`, `--db-password` y `--backend-frontname`. Después de la instalación podrás entrar al administrador y actualizar los demás datos.

Unos cuantos minutos después de ejecutar la instrucción anteriormente mencionada tendrás tu tienda Magento 2 lista para utilizar.

## Conclusiones

Instalar Magento 2 es relativamente sencillo sea cual sea la opción con la que decidas hacerlo. Aunque claro, yo sé que siempre la primera vez que realizas algo da temor, o es confuso. No tengas miedo, de verdad es un proceso bien simple, si tienes ganas de intentarlo, hazlo, si te equivocas o te frustras, no pasa nada, vuelve a intentralo. Yo me tarde más escribiendo este artículo que instalando Magento 2 veces seguidas.

Te vuelvo a invitar, como en todas las ocasiones, a compartir esta artículo, seguro conoces a alguién que le pueda interesar. También puedes contactarme si lo quieres intentar y no encuentras por donde empezar, yo te puedo guiar con gusto.

Puedes dejarme un comentario en este blog o en mis redes sociales. Tu <i>feedback</i> es super importante, es la única forma que tengo para saber si estos artículos te estan sirviendo, si son entendibles y por que solo así puedo mejorar.