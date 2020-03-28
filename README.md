# Create and configure a Vue app to deploy on Cloud Foundry
This is a tutorial about how to create and configure a simple web app to deploy on cloud using Cloud Foundry service.<br>
Additional, it contains a web app sample for study and use.

## Tutorial
This tutorial was designed to be done on a personal computer. <br> 
Most every steps require using of console commands except when is indicated.

## Required software
* Command prompt like Terminal, PowerShell, etc.
* Text editor like Notepad++, Visual Studio Code, etc.

### 1. Install Node JS and Vue
1.1 Install stable/latest version of [Node.js](https://nodejs.org/en/).

1.2 Verify Node JS installation.
```
node --version
```
```
npm --version
```

1.3 Install and verify the framework.
```
npm install -g @vue/cli
```
```
vue --version
```

> If you can't see the framework version on Windows, launch a PowerShell window as an administrator and enter this following command. Later, try again to verify.
```
Set-ExecutionPolicy Unrestricted
```

### 2. Create and run the app
2.1 Create the app.
```
vue create vue-app
```

2.2 Go to `vue-app\` folder.
```
cd vue-app
```

> If you downloaded the web app sample, you should install dependencies to run it.
```
npm install
```

2.3 Run the app and open your favorite web browser (by default) on `localhost:4200`.
> Remember give access to Node.js to use local network 
```
npm run serve
```

2.4 Stop the app with <kbd>ctrl</kbd> + <kbd>C</kbd>.

### 3. Configure the app to deploy
3.1 Go to `vue-app\` folder and build the app.
```
npm run build
```

3.2  Go to `vue-app\dist\` folder and create `staticfile` file(empty and without file extension).

3.3 Go back to `vue-app\` folder and create `manifest.yml` file and edit it with following template. It is necessary change of value of `name` attribute and this should be **unique** because it will used as part of an **URL** where your app will deployed. For example, you can put your initials and today's date.
> Text 
```
---
applications:
- name: vue-app-<initials>-<date>
  memory: 64M
  buildpack: staticfile_buildpack
  path: dist/
```

3.4 The web app is configurated. Now, you can learn how to [Deploy a web application on Cloud Foundry Service](https://github.com/afforeroc/deploy-on-cloudfoundry).

## Reference links
* [Deploying an Angular 6 Application to Cloud Foundry](https://dzone.com/articles/deploying-angular-6-application-to-cloud-foundry)

## Information links
* [Vue page](https://vuejs.org/)
* [Vue CLI page](https://cli.vuejs.org/)
* [Cloud Foundry Documentation](https://docs.cloudfoundry.org/) 
* [Deploying with App Manifests](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html)
