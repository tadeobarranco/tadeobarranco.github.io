---
layout: post
title: "¿Cómo descargar Magento 2?"
description: ""
tags: [magento, magento 2, tutoriales, principiantes]
excerpt_separator: <!--more-->
image:
  path: /images/blog/download-magento.jpg
  feature: download-magento.jpg
  twitter: /blog/download-magento.jpg
---

El primer paso que necesitamos hacer cuando queremos profundizar en Magento 2, ya sea para extender las capacidades básicas de la plataforma o para administrar un ecommerce es saber cómo podemos <strong>DESCARGARLO</strong>.

<!--more-->

Antes de empezar con los comandos o acciones que te permiten instalar la aplicación, hay que obtener el paquete, es un pasito pequeño antes de la instalación. Existen tres formas para [obtener el paquete de Magento](https://devdocs.magento.com/guides/v2.3/install-gde/bk-install-guide.html){:target="blank"} ninguna es mejor o peor que la otra, todo dependerá de tus gustos, habilidades y necesidades.

## Descargando la plataforma

Como ya te mencioné, existen tres métodos en que podemos descargar la plataforma, tal cómo Magento lo dice son: <i>instalación fácil</i>, <i>descargando el metapackage</i> o <i>clonando el repositorio de Magento</i>.

### Instalación fácil (Easy installation (own server))

Sí, se conoce como <i>easy installation</i> pero en realidad esta opción aún no tiene que ver con la instalación, pues en este momento solo estamos hablando de como descargar el código de Magento. Posterior a cualquiera de las tres vías de descarga que tenemos se puede aplicar el mismo proceso de instalación que describiré paso a paso en otro artículo.

Bien, veamos los pasos a seguir para obtner el código de la plataforma de la manera más simple que existe:

- Ve al siguinte [link](https://magento.com/tech-resources/download){:target="blank"} y encontrarás una pantalla como la siguiente: 

<figure>
	<a href="/images/blog/magento-install/download.png">
		<img src="/images/blog/magento-install/download.png" alt="Magento 2 download view">
	</a>
</figure>

- Selecciona la versión y el formato de archivo que quieres descargar.

- Coloca el archivo en tu servidor o haz una petición al administrador de dicho servidor para que lo agregue.

- Descomprimer el archivo que descargaste.

Este método, es el que menos habilidades técnicas requiere, pues todos aquellos que tenemos a la mano una computadora alguna vez hemos descargo archivos. Cuándo te menciono <i>colocar el archivo en el servidor</i> es similar a cuando subes un documento a [Google Drive](https://www.google.com/drive/){:target="blank"} sólo que en este caso lo tienes que hacer por otros medio como una conección [FTP](https://filezilla-project.org/){:target="blank"} o a través de SSH.

### Descargando el metapackage (Get the metapackage)

Esta opción ya requiere un poco más de conocimientos técnicos, ya que tenemos que saber acerca de:

1. [Interfaz de línea de comandos](https://es.wikipedia.org/wiki/Interfaz_de_l%C3%ADnea_de_comandos){:target="blank"}
2. [Composer](https://getcomposer.org/){:target="blank"}
3. Servidores web: ya sea [Apache](https://httpd.apache.org/){:target="blank"} o [Nginx](https://nginx.org/en/){:target="blank"}

Si tienes esos conocimientos lo siguiente es bien simple:

- Haciendo uso de la línea de comandos, vas a la carpeta de tu servidor web en donde alojes tus proyectos.
- Previamente debes de tener instalado composer en tu maquina para poder correr la siguiente instrucción:

```bash
$ composer create-project --repository=https://repo.magento.com/ magento/project-community-edition nombre-de-tu-proyecto
```

Los puntos claves de esta instrucción son:

- `composer` es la palabre clave para decirle al servidor que paquete o programa ejecutará la instrucción.
- `create-project` es la acción que se ejecutará y recibe como valor la url donde se encuentra el código.
- `magento/project-community-edition` es el paquete a descargar.
- `nombre-de-tu-proyecto` aunque suene obvio, cabe aclarar que se refiere al nombre de la carpeta donde se decargará Magento.

Esta instrucción descargará la última versión de Magento 2.x, si necesitaras descargar una versión anterior bastaría con editar `magento/project-community-edition` con `magento-community-edition=#.#.#` donde `#.#.#`  representaría el número de la versión, por ejemplo `2.2.6`.

### Clonando el repositorio de Magento (Clone the Magento repository)

Esta última opción es muy interesante, ya te comente en un <strong>[artículo](http://www.tadeobarranco.com/magento-out-of-the-box-es-suficiente-para-poder-vender-en-internet/)</strong> anterior que Magento 2 tiene dos versiones, una que es gratuita y la otra enfocada en negocios grandes y que tiene un costo anual. Bien, la versión gratuita es además [Open Source](http://www.tadeobarranco.com/open-source/), es decir, tienes la oportunidad no sólo de obtener el código, sino de hacer modificaciones, solucionar problemas e incluso reportar problemas en la plataforma.

Si hablamos de modificaciones a la plataforma, esta opción al igual que la anterior requiere de más conocimientos técnicos ya que debes conocer acerca de:

1. [Interfaz de línea de comandos](https://es.wikipedia.org/wiki/Interfaz_de_l%C3%ADnea_de_comandos){:target="blank"}
2. [Git](https://git-scm.com/){:target="blank"}
3. [Git Hub](https://github.com/){:target="blank"}
4. [Composer](https://getcomposer.org/){:target="blank"}
5. Servidores web: ya sea [Apache](https://httpd.apache.org/){:target="blank"} o [Nginx](https://nginx.org/en/){:target="blank"}

Si decides utilizar esta opción por que te gustaría apoyar a la comunidad haciendo modificaciones y/o solucionando problemas en versiones específicas sigue los siguientes pasos para obtener el código:

- Primero en tu línea de comandos te colocas en la carpeta de archivos de tu servidor web.
- Con `git` previamente instalado deberás ejecutar la siguiente instrucción:

```bash
$ git clone git@github.com:magento/magento2.git nombre-de-tu-proyecto
```

- Ya que Magento utiliza librerías de terceros es necesario instalarlas, para esto ejecutaremos la siguiente línea:

```bash
$ composer install
```

Los aspectos importantes de las dos instrucciones son las siguientes:

- `git` es la palabra que le dice al servidor que paquete o programa ejecutará esta instrucción.
- `clone` indica que se realizará.
- `git@github.com:magento/magento2.git` es el `repositorio` a descargar.
- Igual que en la opción anterior `nombre-de-tu-proyecto` se refiere al nombre de la carpeta donde se decargará el código de Magento.
- `composer` le dice al servidor que ahora es ese paquete el que ejecutará una instrucción.
- `install` le dice a composer la acción a ejecutar, automáticamente buscará el archivo `composer.json` que se descargó con la plataforma para saber que paquetes instalar.

## Conclusiones

Ya tenemos el código de Magento 2 en nuestro servidor, ya sea en un ambiente de desarrollo (tu propia computadora) o en la nube (en internet). TODAS las opciones de descarga son válidas, ¿cuál te agrada más? ¿cuál cumple tus necesidades?

Estas listo ahora para instalar la plataforma, no te preocupes si no sabes como continuar, te voy a guiar paso a paso por la instalación en otro artículo. Si quieres aprender acerca de `git`, `composer` y los otros paquetes o tecnisismos que describí en las opciones dos y tres de descarga deja un comentario y con gusto prepararé artículos acerca de ellos.

Te invito a seguir leyendo el blog, a lo largo de mis artículos encontrarás mucha más información acerca de Magento y muchas guías de como iniciar y también de como modificar la plataforma.