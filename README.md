# Configurar una aplicación web de Vue para desplegarla en Cloud Foundry

Este tutorial te indicará como configurar una aplicación web de `Vue` para desplegarla en Cloud Foundry. 

* Nota: Al descargar este repositorio, la aplicación tendrá los archivos de configuración para el despliegue, pero es necesario que realices el paso 4.

## Requisitos básicos
* Ventana de comandos como `Terminal` o `PowerShell`
* Editor de texto/código como `Notepad++` o `Visual Studio Code`

### 1. Instalar Node.js y Vue
* Instala la última versión de [Node.js](https://nodejs.org/en/)
* Verifica la instalación de Node: `$ node --version`
* Verifica la instalación de NPM: `$ npm --version`
* Instala la última versión del CLI de Vue: `$ npm install -g @vue/cli`
* Verifica la instalación de Vue: `$ vue --version`

### 2. Crear y probar la aplicación web
* Crea la aplicación web: `$ vue create vue-app`
* Accede a la carpeta raíz de la aplicación: `$ cd vue-app`
* Prueba la aplicación en localhost: `$ npm run serve`
> Abre tu navegador web en `localhost:8080`
* Detén la aplicación: `(Ctrl + C)`

### 3. Configurar la aplicación para el despliegue
Desde la carpeta raíz de la aplicación
* Construye la aplicación: `$ npm run build`
* Ingresa a la carpeta generada `dist\` y crea el archivo vacío sin extensión `staticfile`
* Posiciónate de nuevo en la carpeta raíz del proyecto, crea el archivo `manifest.yml` y editalo con la siguiente información:
```
---
applications:
- name: vue-app-<initials>-<date>
  memory: 64M
  buildpack: staticfile_buildpack
  path: dist/
```

### 4. Colocar un nombre a la aplicación
* Dentro del archivo `manifest.yml`, cambia el valor del atributo `- name` colocando un nombre **único**. Puedes usar la plantilla para colocar tus iniciales y la fecha de hoy.

## Links de referencia
* Deploying an Angular 6 Application to Cloud Foundry: https://dzone.com/articles/deploying-angular-6-application-to-cloud-foundry

## Links de interés
* Documentación de Vue.js: https://vuejs.org/
* Documentación de Vue CLI: https://cli.vuejs.org/
* Documentación de Cloud Foundry: https://docs.cloudfoundry.org/ 
* Documentación sobre manifest.yml: https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html