# Agile App

[![Build Status](https://travis-ci.org/d3trax/agileConf.svg?branch=master)](https://travis-ci.org/d3trax/agileConf)

## Running The App

To run the app, follow these steps.

1. Ensure that **0.12.x** version of [NodeJS](http://nodejs.org/) is installed. This provides the platform on which the build tooling runs.
2. From the project folder, execute the following command:

  ```shell
  npm install
  ```
3. Ensure that [Gulp](http://gulpjs.com/) is installed. If you need to install it, use the following command:

  ```shell
  npm install -g gulp
  ```
4. Ensure that [jspm](http://jspm.io/) is installed. If you need to install it, use the following command:

  ```shell
  npm install -g jspm
  npm install -g jspm-bower-endpoint
  npm jspm registry create bower jspm-bower-endpoint
  ```
  > **Note:** jspm queries GitHub to install semver packages, but GitHub has a rate limit on anonymous API requests. It is advised that you configure jspm with your GitHub credentials in order to avoid problems. You can do this by executing `jspm registry config github` and following the prompts. If you choose to authorize jspm by an access token instead of giving your password (see GitHub `Settings > Personal Access Tokens`), `public_repo` access for the token is required.
5. Install the client-side dependencies with jspm:

  ```shell
  jspm install -y
  ```
  >**Note:** Windows users, if you experience an error of "unknown command unzip" you can solve this problem by doing `npm install -g unzip` and then re-running `jspm install`.
6. Install Typescript typings

  ```shell
  tsd install
  ```
7. To run the app, execute the following command:

  ```shell
  gulp watch
  ```

8. Browse to [http://localhost:9000](http://localhost:9000) to see the app. You can make changes in the code found under `src` and the browser should auto-refresh itself as you save files.


## Bundling

  ```shell
    gulp bundle
  ```

You can also unbundle using the command bellow:

  ```shell
  gulp unbundle
  ```

## Adding dependencies

Add Bower dependency

 ```shell
 jspm install bower:slimScroll
 ```
 >**Note:** It automatically saves it

## Running The Unit Tests

To run the unit tests, first ensure that you have followed the steps above in order to install all dependencies and successfully build the library. Once you have done that, proceed with these additional steps:

1. Ensure that the [Karma](http://karma-runner.github.io/) CLI is installed. If you need to install it, use the following command:

  ```shell
  npm install -g karma-cli
  ```
2. Install Aurelia libs for test visibility:

```shell
jspm install aurelia-framework
jspm install aurelia-http-client
jspm install aurelia-router
```
3. You can now run the tests with this command:

  ```shell
  karma start
  ```

## Running The E2E Tests
Integration tests are performed with [Protractor](http://angular.github.io/protractor/#/).

1. Place your E2E-Tests into the folder ```test/e2e/src```
2. Install the necessary webdriver

  ```shell
  gulp webdriver_update
  ```

3. Configure the path to the webdriver by opening the file ```protractor.conf.js``` and adjusting the ```seleniumServerJar``` property. Typically its only needed to adjust the version number.

4. Make sure your app runs and is accessible

  ```shell
  gulp watch
  ```

5. In another console run the E2E-Tests

  ```shell
  gulp e2e
  ```

## Mocking configuration

  To mock device events edit configuration on ```server/config.py``` 

 ```python
 MOCK = True
 ```
 
 Or better change data provider in ```src/app/services/BikeManager.ts```
 
 ```js
 import {MockProvider} from '../services/speed/provider/mockProvider';
 let provider = new MockProvider();
 ```
 >**Note:** This will not need to start any python applications

## Install py dependencies

 ```shell
 python setup.py install -v -n
 Need install patched **python-ant** library from [https://github.com/SamyCookie/python-ant](https://github.com/SamyCookie/python-ant)
 ```