# Configure and deploy a Vue app web on Cloud Foundry

* Note:  If you download this repository, the app has all configuration files to deploy it but it is necessary do the step 4.

## Basic requirements
* Command prompt like `Terminal` or `PowerShell`
* Text editor like `Notepad++` or `Visual Studio Code`

### 1. Install Node.js and Vue
* Install the latest version of [Node.js](https://nodejs.org/en/)

* Verify the Node.js installation
```
node --version
```

* Verify the NPM installation
```
npm --version
```

* Install the lastest version of Vue CLI
```
npm install -g @vue/cli
```

* Verify the Vue version
```
vue --version
```

> If you can't see the Vue version on PowerShell, launch a PowerShell window run as an administrator and enter
```
Set-ExecutionPolicy Unrestricted
```
and finally verify the Vue version

### 2. Create and check the web app
* Create the web app
```
vue create vue-app
```

* Access the root folder of web app
```
cd vue-app
```

* Run the app
```
npm run serve
```
> Remeber give access to Node.js use the local network

* Open your web browser on 
```
localhost:8080
```

* Stop the web app with this combination keys
```
(Ctrl + C)
```

### 3. Configure the app to deploy
* Access the root folder and build the app
```
npm run build
```

* Go to the generated folder `dist\` and create the empty file `staticfile` (without extension)
* Go back to the root folder and create the file `manifest.yml` and edit it with following information
```
---
applications:
- name: vue-app-<your-initials>-<date>
  memory: 64M
  buildpack: staticfile_buildpack
  path: dist/
```

### 4. Put a name to your app
* Edit `manifest.yml` file changing the value of `- name` atribute. Rember that this value should be **unique**. You can use the before template.

## Reference link
* Deploying an Angular 6 Application to Cloud Foundry: https://dzone.com/articles/deploying-angular-6-application-to-cloud-foundry

## Information links
* Vue.js page: https://vuejs.org/
* Vue CLI documentation: https://cli.vuejs.org/
* Cloud Foundry page: https://docs.cloudfoundry.org/ 
* manifest.yml documentation: https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html