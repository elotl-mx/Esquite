# Esquite: framework para administrar corpus paralelos 🌽

[![Documentation Status](https://readthedocs.org/projects/esquite/badge/?version=latest)](https://esquite.readthedocs.io/es/latest/?badge=latest)
[![License](https://img.shields.io/github/license/ElotlMX/Esquite?label=Licencia&style=flat)](https://github.com/ElotlMX/Esquite/blob/master/LICENSE)

## Acerca de Esquite

Esquite es un *framework* está destinado para las personas que poseen corpus
paralelos (textos bilingües) y deseen generar un sistema web que les permita
subir estos documentos, administrarlos y realizar búsquedas de palabras
y frases en las dos lenguas.

### Características

* Realizar búsquedas avanzadas atreves de tus corpus paralelos gracias al motor
	de [*Elasticsearch*](https://www.elastic.co/es/)
* Gestionar tus documento por medio de su administrador de corpus
* Personalización de la interfaz web
	* Colores
	* Teclado con caracteres especiales (útil para lenguas minorizadas)
	* Agregar información personalizada a las vistas: **Ayuda**, **Acerca del Corpus**,
		etc.
* Nuevas características en desarrollo


### Ejemplo: [Tsunkua Corpus Paralelo Español-Otomí](https://tsunkua.elotl.mx/)

<p align="center">
	<img src="https://elotl.mx/wp-content/uploads/2020/07/tsunkua.png" width="40%" height="40%" />
	<img src="https://elotl.mx/wp-content/uploads/2020/07/export_csv.png" width="52%" height="52%" />
</p>

## Contacto

¿Eres hablante/estudioso de una lengua minorizada y te gustaría poner tu corpus
paralelo en línea? Contactamos: *contacto at elotl.mx*

## Documentación

Para una [guía de instalación](https://esquite.readthedocs.io/es/latest/install.html)
completa, [tutoriales](https://esquite.readthedocs.io/es/latest/tutorials.html)
y estructura del proyecto puedes revisar nuestra
[documentación](https://esquite.readthedocs.io/es/latest/).

## Dependencias

* `git`
* [Elasticsearch 7.6](https://www.elastic.co/guide/en/elasticsearch/reference/7.6/getting-started-install.html) o mayor
* `python3.6` o mayor
	* `pip`
	* Opcional: `virtualenv`: [Guía de instalación virtualenv](https://virtualenv.pypa.io/en/latest/installation.html)

## Instalación en servidor

1. Instalar y correr `elasticsearch`

	**Nota**: Puedes consultar la página oficial de
	[Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
	para completar este paso dependiendo de tu Sistema Operativo

2. Clona este repositorio

	```shell
	$ git clone https://github.com/ElotlMX/Esquite
	```

3. Preparación del entorno

	Entrar a la carpeta del proyecto, crea un entorno virtual de `python` con
	`virtualenv` y activarlo

	```shell
	$ cd Esquite
	$ virtualenv env -p /usr/bin/python3
	$ source env/bin/activate
	```

4. Instalar las dependencias

	```shell
	(env)$ pip install -r requirements.txt
	```

5. Iniciar el asistente de instalación e ingresar los datos que piden

	```shell
	(env)$ python wizard.py
	```

	**Nota**: El asistente menciona que debemos tener un índice de `elasticsearh`
	previamente creado. Para crear dicho índice puede ejecutar el siguiente
	comando.

	```shell
	$ curl -X PUT -H "Content-Type: application/json" -d @elastic-config.json localhost:9200/<nombre-de-tu-indice>
	```

	Donde dice `<nombre-de-tu-indice>` deberás poner el nombre que desees
	y ese será el nombre del índice para poner en el asistente de instalación.

6. Aplicar migraciones de `django`

	```shell
	(env)$ python manage.py migrate
	```

6. Correr `django` en segundo plano

	```shell
	(env)$ python manage.py runserver 0.0.0.0:8000 &
	```
