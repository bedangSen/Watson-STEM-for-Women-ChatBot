# Watson STEM for Women ChatBot [![](https://img.shields.io/badge/bluemix-powered-blue.svg)](https://bluemix.net)


This Node.js app demonstrates the [Watson Assistant](https://www.ibm.com/watson/services/conversation/) service in a simple chat interface while discussing STEM topics and Women in STEM.

## Getting started

### Before you begin

-  Ensure that you have an [IBM Cloud account][sign_up]. While you can do part of this deployment locally, you must still use IBM Cloud.

<a name="returnlocal">
</a>

### Create the services

1. In IBM Cloud, [create a Watson Assistant Service instance](https://console.bluemix.net/registration/?target=/catalog/services/conversation/).
  * Create the Service Credentials.
  * Launch the tool and create a new skill from the skill tab 
  * Import a skill using the `skills.json` file.

2. In IBM Cloud, [create a Discovery Service instance](https://console.bluemix.net/registration/?target=/catalog/services/discovery/).
  * Create the [Service Credentials](#credentials).
  * [Ingest the documents into a new Discovery collection](#ingestion).

### Building locally

To build the application:

1. Clone the repository
   ```
   git clone https://github.com/watson-developer-cloud/assistant-with-discovery
   ```

2. Navigate to the `assistant-with-discovery` folder

3. For Windows, type `gradlew.bat build`. Otherwise, type `./gradlew build`.

4. The built WAR file (watson-assistant-with-discovery-0.1-SNAPSHOT.war) is in the `assistant-with-discovery/build/libs/` folder.


### Configuring workspace

The following steps are to optionally retrieve a workspace id and configure it for your application. If you do not configure a workspace id, the first workspace in your space will be used, or a new workspace will be created.

1. From the [Service Dashboard](https://console.bluemix.net/dashboard/apps) click on your Watson Assistance instance

1. From the **Manage** page, click **Launch tool**. 

1. Click the dots in the upper right hand corner for the workspace you want and click **View details**

1. Copy the `Workspace ID` and add this as an environment variable labeled `WORKSPACE_ID` in your application

### Running locally

The following steps are for running locally with Node.js. You can also [run locally with Docker](#running-locally-with-docker).

1. To develop locally, first install [Node.js](https://nodejs.org) ([LTS](https://github.com/nodejs/Release) supported versions).

1. At the command line, go to your project directory.

1. Install the dependencies:

    ```sh
    npm install
    ```

1. Start the app:

    ```sh
    npm start
    ```

1. Point your browser to [localhost:3000](http://localhost:3000).

### Testing the app

After your app is installed and running, experiment with it to see how it responds.

The chat interface is on the left, and the JSON that the JavaScript code receives from the Watson Assistant service is on the right. Your questions and commands are interpreted using a small set of sample data trained with the following intents:

    learn_stem
    stem_importance
    women_in_stem
    factors_affecting_stem
    general_greetings
    general_endigns
    general_jokes

Type a request, such as `What is STEM` or `Tell me more about psychology`. The system understands your intent and responds. You can see the details of how your input was understood by examining the JSON data in the `Watson understands` section on the right side.

For example, if you type `Tell me more about Computer Science`, the JSON data shows that the system understood the `learn_stem` intent with a high level of confidence, along with the `science_branches` entity with a value of `computer science`.

* Visit the documentation to learn more about [intents](https://console.bluemix.net/docs/services/conversation/intents.html#defining-intents) and [entities](https://console.bluemix.net/docs/services/conversation/entities.html#defining-entities)

* Go to the tool to learn more about the Chatbot's intents, entities, and dialog.
  1. To launch the tool you need to return to your [Project List](https://console.bluemix.net/developer/watson/projects) and select your Watson Assistant Basic Project.
  2. Click on `Train Service` from the Service List, next to `Watson Assistant`.
  3. Log into the tool with your IBM Cloud login and password
  4. Click on the STEM for Women workspace
  5. You will land on the `Intents` tab. Here you can view the intents such as `learn_stem`, to modify these visit the [documentation](https://console.bluemix.net/docs/services/conversation/intents.html#editing-intents) for the service.
  6. The next tab is where you can modify `entities` such as `appliance`. View the [documentation](https://console.bluemix.net/docs/services/conversation/entities.html#editing-entities) to learn how to modify.
  7. The third tab is for modifying the `dialog`. You can learn more about modifying `dialog` in the [documentation](https://console.bluemix.net/docs/services/conversation/dialog-build.html#dialog-build).

### Modifying the app

After you have the app deployed and running, you can explore the source files and make changes. Try the following:

* Modify the .js files to change the app logic.
* Modify the .html file to change the appearance of the app page.
* Use the Watson Assistant tool to train the service for new intents, or to modify the dialog flow. For more information, see the [Watson Assistant service documentation](https://console.bluemix.net/docs/services/conversation/intents.html#defining-intents).
* Try creating your own bot with the tool:
  1. To launch the tool you need to return to your [App List](https://console.bluemix.net/developer/watson/apps) and select your Watson Assistant Basic Project.
  2. Click on `Train Service` from the Service List, next to `Watson Assistant`.
  3. Log into the tool.
  4. Follow the [Getting started guide](https://console.bluemix.net/docs/services/conversation/getting-started.html#create-workspace) to create your own Watson Assistant workspace

### Deploying to IBM Cloud as a CloudFoundry application

1. Login to IBM Cloud with the [IBM Cloud CLI](https://console.bluemix.net/docs/cli/index.html#overview):

    ```
    ibmcloud login
    ```

1. Target a Cloud Foundry organization and space:

    ```
    ibmcloud target --cf
    ```

1. Deploy the application:

    ```
    ibmcloud dev deploy
    ```
    The application will be deployed with the settings in your *manifest.yml* file.

1. Access your app at the URL specified in the command output.

    After your app is deployed, you can manage it from your [IBM Cloud dashboard](https://console.bluemix.net/dashboard/apps).
    
## Managing your project in the Watson Console

Select your project from the [Projects list](https://console.bluemix.net/developer/watson/projects) in the Watson developer console. From the project page, you can do the following:

    - Add additional services to your project
    - View documentation and credentials for your project's services
    - Configure a DevOps toolchain

## Running locally with Docker

1. Install the [IBM Cloud CLI tools](https://console.bluemix.net/docs/cli/index.html#overview).

1. If you installed any node dependencies into your project folder, remove them. Open a terminal and run the following command from your project folder, where your starter kit code is:

    ```sh
    rm -rf node_modules
    ```
    
1. Build the Docker container:

    ```sh
    ibmcloud dev build
    ```
    
    The build may take a few minutes to complete.
    
1. Run the Docker container:

    ```sh
    ibmcloud dev run
    ```
    
1. Point your browser to [localhost:3000](http://localhost:3000).

## License

  This sample code is licensed under Apache 2.0.

## Open Source @ IBM

  Find more open source projects on the [IBM Github Page](http://ibm.github.io/)
