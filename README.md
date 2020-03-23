# Create and configure a Vue app to deploy on Cloud Foundry

**Note**: this repository has a Vue app with all necessary files to deploy it on cloud, but it is necessary do the step 4.

## Recommended software
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

> If you can't see the Vue version on PowerShell, launch a PowerShell window as an administrator and enter this command
```
Set-ExecutionPolicy Unrestricted
```
and again verify the Vue version

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
> Remember give access to Node.js to use the local network

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
* Go back to the root folder and create the file `manifest.yml` and edit it with following template
```
---
applications:
- name: vue-app-<initials>-<date>
  memory: 64M
  buildpack: staticfile_buildpack
  path: dist/
```

### 4. Put a name to your app
* Edit `manifest.yml` file changing the value of `- name` atribute. The name that should be **unique** because it will used as part of url of app. You can use the previous template putting your initials and the today's date.

## Reference links
* Deploying an Angular 6 Application to Cloud Foundry: https://dzone.com/articles/deploying-angular-6-application-to-cloud-foundry

## Information links
* Vue.js page: https://vuejs.org/
* Vue CLI documentation: https://cli.vuejs.org/
* Cloud Foundry page: https://docs.cloudfoundry.org/ 
* manifest.yml documentation: https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html
