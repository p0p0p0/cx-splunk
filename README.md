# Cx-Splunk
cx-Splunk is a React App for Splunk to gain information usage, insight Checkmarx's results as well as observe trends across projects.

# v0.0.1 - Beta - Caveat!
1. To use this current version, Once CxAnalytix is configured splunk search query changes need to be performed in `src/pages/summary/definition.json`.
2. By default, v0.0.1 comes with Mock search. This will soon be changed to match [CxAnalytix Specs](https://github.com/checkmarx-ts/CxAnalytix/blob/master/SPEC.md).

# Prerequisites
* Install [`CxAnalytix`](https://github.com/checkmarx-ts/CxAnalytix). Visit the below section [below](#CxAnalytix) for more information.
* Install [nodejs](https://nodejs.org/en/) 12.x.
* Install Splunk Enterprise locally and have $SPLUNK_HOME env variable setup.
* Install `yarn` as the package manager.
* In Windows environment, to avoid any file permission issues start the command prompt with "Run as Administrator" to run the commands mentioned in the [Development](#development) section.

# CxAnalytix
* `CxAnalytix` is our supported & recommended way to fetch analytical data for Splunk is the key dependency in-order to make use of `Cx-Splunk`.
* `CxAnalytix` [installation guide](https://github.com/checkmarx-ts/CxAnalytix/wiki/Installation) can be found here.
* In-order to forward data to Splunk, We recommend the use of Splunk Universal forwarder. Please read more [here](https://github.com/checkmarx-ts/CxAnalytix/wiki/Splunk) on how to configure Splunk Universal Forwarder.


# Development
* `yarn install` - install dependencies.
* `yarn run dev` - start the project in dev mode. This command will symlink the project into your Splunk instance. 
* Restart your Splunk instance if it's the first time you setup this project. `Checkmarx` application should shows up in app bar.


# Cx-Splunk - Creating a new view.
* Follow the below steps to create a new view.
    * Add an xml file in `resources/default/data/ui/views`.
    * Modify `resources/default/data/ui/nav/default.xml` to include your new page.
    * Create a new folder under `src/pages/` with the same name of the new xml file.
    * Create `index.jsx` and bootstrap the page using `@splunk/react-page`.
    * Restart Splunk, your new page should shows up.


# Package the app

Use the following steps to package the Checkmarx Dashboard app. 

Requirements:
* Make
* [Docker](https://docs.docker.com/install/)


# Build Steps
* Run `make build-image` to build the image to package the app.
* Run `make run` to package the app with NodeJS.
    * The app (`tgz`) will be created in the `splunkapps` folder.
* To start Splunk (`8.0`) with the dashboard app run `make start` (username: `admin` password: `changemeplease`).
* If password is changed, update the Makefile
* To remove all containers run `make down`