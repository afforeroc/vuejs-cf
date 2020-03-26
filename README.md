# Create and configure an Vue app to deploy on Cloud Foundry
This repository belongs to [tutorial set](https://github.com/afforeroc/deploy-on-cloudfoundry) about how to create and configure a web app to deploy on cloud. Additional, contains a web app sample for study and use.
> If you want to ...
>  * **run app sample locally**- review steps 1 and 2.
>  * **deploy app sample on cloud**- review step 3.

## Tutorial
This tutorial was designed to be done on a personal computer. Most every steps require using of console commands except when is indicated.

## 0. Required software
* Command prompt like Terminal, PowerShell, etc.
* Text editor like Notepad++, Visual Studio Code, etc.

### 1. Install Node JS and Vue
  **1.1** Install the stable/latest version of [Node.js](https://nodejs.org/en/).

  **1.2** Verify the Node JS installation.
  ```
  node --version
  ```
  ```
  npm --version
  ```

  **1.3** Install and verify the framework.
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
  **2.1** Create the app.
  ```
  vue create vue-app
  ```

  **2.2** Go to the root folder of app.
  ```
  cd vue-app
  ```

  **2.3** Run the app and open your favorite web browser (by default) on `localhost:4200`.
  > Remember give access to Node.js to use the local network 
  ```
  npm run serve
  ```

  **2.4** Stop the app with <kbd>ctrl</kbd> + <kbd>C</kbd>.

### 3. Configure the app to deploy
  **3.1** Go to the root folder `vue-app\` and build the app.
  ```
  npm run build
  ```

  **3.2**  Go to the generated folder `vue-app\dist\` and create the empty file `staticfile` (without file extension).

  **3.3** Go back to the root folder `vue-app\` and create the file `manifest.yml` and edit it with following template.
  > Text editing<br> 
  ```
  ---
  applications:
  - name: vue-app-<initials>-<date>
    memory: 64M
    buildpack: staticfile_buildpack
    path: dist/
  ```
  
  **3.4** Edit `manifest.yml` file changing the value of `- name` attribute. The name that should be **unique** because this will used as part of an **URL** where your app will deployed.You can use the previous template putting your initials and the today's date.

## Reference links
* Deploying an Angular 6 Application to Cloud Foundry- https://dzone.com/articles/deploying-angular-6-application-to-cloud-foundry

## Information links
* Vue page- https://vuejs.org/
* Vue CLI page- https://cli.vuejs.org/
* Cloud Foundry Documentation: https://docs.cloudfoundry.org/ 
* Deploying with App Manifests- https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html
