# Desplegar una aplicación web de Vue.js sobre Cloud Foundry de IBM Cloud

> Presentación [Introducción a Cloud Foundry](https://ibm.box.com/v/cf-ppt)

Este tutorial te indicará como desplegar una aplicación web de `Vue.js` sobre Cloud Foundry de IBM Cloud usando la ventana de comandos. Una vez la aplicación este desplegada, esta será accesible desde cualquier navegador web.

## Servicios Incluidos
* [IBM Cloud - Cloud Foundry](https://www.ibm.com/cloud/cloud-foundry): Servicio en la nube que ejecuta código fuente en una plataforma como servicio (PaaS). Open source, serverless y altamente escalable.

## Requisitos básicos
* Ventana de comandos como `Terminal` o `PowerShell`
* Editor de texto/código como `Notepad++` o `Visual Studio Code`
* Cuenta activa de [IBM Cloud](https://console.bluemix.net)

## 1. Opción A: Clonar el repositorio
Al descargar este repositorio, la aplicación `vuejs-cf` tendrá los archivos de configuración para el despliegue
* Clona este repositorio localmente: `$ git clone https://github.com/afforeroc/vuejs-cf`

## 2. Opción B: Crear, probar y configurar la aplicación web

### Instalar Node.js y Vue.js
* Instala la última versión de [Node.js](https://nodejs.org/en/)
* Verifica la instalación de Node.js: `$ node --version`
* Verifica la instalación de Node.js package manager: `$ npm --version`
* Instala la última versión de Vue.js CLI: `$ npm install -g @vue/cli`
* Verifica la instalación de Vue.js: `$ vue --version`

### Crear y probar la aplicación web
* Crea la aplicación: `$ vue create vuejs-cf`
* Accede a la carpeta del proyecto: `$ cd vuejs-cf`
* Prueba la aplicación en localhost: `$ npm run serve`
* Detén la aplicación: `(Ctrl + C)`

### Configurar la aplicación para el despliegue
Desde la carpeta raíz de la applicación
* Construye la aplicación: `$ npm run build`
* Ingresa a la carpeta generada `dist` y crea el archivo vacío `staticfile`
* Posiciónate de nuevo en la carpeta raíz del proyecto, crea el archivo `manifest.yml` y editalo con la siguiente información:
```
---
applications:
- name: vuejs-cf-<initials>-<date>
  memory: 64M
  buildpack: staticfile_buildpack
  path: dist/
``` 

## 2. Instalar IBM Cloud CLI
Instala según tu sistema operativo
* Instala en Mac/Linux: `$ curl -sL https://ibm.biz/idt-installer | bash`
* Instala en Windows: https://clis.ng.bluemix.net/download/bluemix-cli/latest/win64
* Verifica la versión del CLI: `$ ibmcloud -v`

## 3. Iniciar sesión con IBM Cloud CLI
Sigue las instrucciones interactivas del CLI en cada paso 
* Inicia sesión en IBM Cloud: `$ ibmcloud login`
* Apunta al espacio de trabajo de Cloud Foundry: `$ ibmcloud target --cf`
* Si deseas hacer cambios a tu sesión: `$ ibmcloud target -r <REGION> -o <ORG> -s <SPACE>`

## 4. Desplegar la aplicación usando el CLI
* Dentro del archivo `manifest.yml`, cambia el valor del atributo `- name` colocando un nombre **único**, ya que este será usado como parte de la URL generada. Puedes usar la plantilla para colocar tus iniciales y una fecha.
* Dentro del archivo `package.json`, verifica que exista el comando `"serve": "vue-cli-service serve"` dentro de la sección `"scripts"`, ya que este permitirá ejecutar la aplicación en la nube.
* Posicionate en la carpeta raíz de la aplicación web
* Sube la aplicación a Cloud Foundry de IBM Cloud: `$ ibmcloud app push`
* Visualiza tu aplicación web accediendo al [Dashboard de IBM Cloud](https://console.bluemix.net/dashboard/apps)

## Links de interés:
* Documentación de Vue.js: https://vuejs.org/
* Documentación de Vue CLI: https://cli.vuejs.org/
* Documentación de IBM Cloud: https://console.bluemix.net/docs/
* Documentación de IBM Cloud CLI: https://console.bluemix.net/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_cli
* Documentación de Cloud Foundry: https://docs.cloudfoundry.org/ 
* Documentación sobre manifest.yml: https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html