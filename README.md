# IBM Cloud :cloud: and Smart Homes:house_with_garden:
## Workshop guide with SIMULATED SENSOR DATA

In this guide:
  - [Introduction](#introduction)
  - [PHASE 1](#phase-1): Create a web application
  - [PHASE 2](#phase-2): Visualize your data
  - [PHASE 3](#phase-3): Add AI powered chatbot to your application using Watson Assistant 
  - [PHASE 4](#phase-4): Connect with external APIs using Weather Insights

  
  
  #### Prerequisites
- IBM Cloud account
  - Create a free account https://cloud.ibm.com/

  ## Introduction 

This lab was created for Smart Homes Mimmitkoodaa workshop fall 2018. The idea is to show how to create a smart home application that uses artificial intelligence and connects with external APIs. 

**IBM Cloud** is a suite of cloud computing services from IBM that offers both platform as a service (PaaS) and infrastructure as a service (IaaS). A full-stack cloud platform with over 170 products and services covering data, serverless, containers, AI, IoT and blockchain. https://www.ibm.com/cloud/

<img src="/images/IBMCloud.png" width="90%" height="90%">

# PHASE 1
## Create an application

### Step 1. Create a Node-RED application

**Node-RED** is a visual tool for wiring the internet of things - connecting hardware devices, APIs and online services in a new and interesting way. Node-RED provides a browser-based flow editor that makes it easy to wire together flows using the wide range nodes in the palette. Flows can be then deployed to the runtime in a single click.

In a browser navigate to https://cloud.ibm.com/
Select '_LOG IN_' with your IBM id (your email). After login you should see your IBM Cloud dashboard. 
Select the '_CATALOG_' view.
![](/images/App1.png?raw=true)
Locate the Internet of things Platform starter service, under Starter Kit, and click on it. This starter kit contains a Cloudant dabatase, SDK for Node.js and the IoT platform. 

<img src="/images/simulation1.png" width="30%" height="30%">

Enter a name for your application, for example: *mysmarthome* (host will automatically be completed). The hostname must be unique on IBM Cloud, so please if you use the example name add your initials or a number. Be creative and try to make a unique name then click '_CREATE_'. 

<img src="/images/simulation2.png" width="100%" height="100%">
 
Your application is now staging and will be up and running in a short while. Click 'OVERVIEW' to see information about your application. 
The application will be ready in a couple of minutes. If you want to check the progress click on the  _LOGS_  icon on the left side menu. Go back to _Overview_ tab to see your app dashboard.

<img src="/images/App3b.png" width="20%" height="20%">

*Note: If you are using Lite accounts your application will be in an awake mode. That means that if after 10 days your application has not been used IBM will stop it.*

When fully staged, click on the _Visit app URL_, next to the green or half green circle, this launches the Node-RED main page.

<img src="/images/App4.png" width="90%" height="90%">
  
Configure your Node-RED editor. In this section, you will set up a username and password to protect your flow. We are working in the public cloud that means that anyone can access your application through a web browser, set a username and password to protect your code.

<img src="/images/App5.png" width="40%" height="40%">

Write an username and a password of your choice and click 'Next'. Remember that it does not have to be related to your IBM Cloud ID. Let the browser remember the password if you are using your own laptop, it will come in handy later. 

<img src="/images/App6.png" width="40%" height="40%">
 
#### Your Node-RED flow is all set! Enter your credentials to access the editor.

<img src="/images/App8.png" width="70%" height="70%">
 
Now click Go to your Node-RED flow editor to open the flow editor.

When using Node-RED we build our apps using this graphical editor interface to wire together the blocks we need. We can simply drag and drop the blocks from the left menu into the workspace in the center of the screen and connect them to create a new flow. 

This starter kit already has a simulation data flow. When you click in the "Send data" node you activate the data flow. Right now it only sends one data set per click, so let's transform the flow to send data every minute.

<img src="/images/simulation3.png" width="70%" height="70%">

Double click in the blue "Send data" node. Setup the node to send data every minute as shown in the image below. Then click on  Done.

<img src="/images/simulation4.png" width="40%" height="40%">

Start sending data by clicking in the left side of the Send Data node. You will see the data flowing in the debug tab on the right side. 

### Step 2: Add new nodes to the Node-RED palette
We are going to add new nodes to the Node-RED palette directly from the Node-RED window. For this lab we need the following nodes:

      - node-red-dashboard
      - node-red-node-openweathermap

In the Node-RED window click on the three lines on the top right corner and in the menu, click on the "Manage palette". This will open the node menu where you can add new nodes to your application. 

<img src="/images/App23.png" width="20%" height="20%">

You will see the nodes that are installed by default and if you go to the 'install' tab you can search for any node package and add it directly to your app.

<img src="/images/App24.png" width="30%" height="30%">
             
Search for the dashboard nodes by writing 'dashboard'. This will return multiple node packages, you need to install the package 'node-red-dashboard'. Find it in the search results and click on install. 

<img src="/images/App25.png" width="30%" height="30%">
 
This will prompt a window to confirm the installation. Click on install and wait few minutes. Click "Done" to close the left side menu. 

<img src="/images/App26.png" width="50%" height="50%">

After few seconds you will see the new nodes in your Node-RED palette.

**Remember to repeat this process to install node-red-node-openweathermap package.** :partly_sunny:

# PHASE 2
## Visualize your data

### Step 3: Import the Node-RED application flow
In this section we will build a simple flow to connect with our sensor data and create a web visualization. 

Copy the content of the **visualizationUI_simulatedData.json** file. Open the file URL. [Visualization UI code](https://raw.githubusercontent.com/sandra-calvo/smarthomes-SimulatedData/master/visualizationUI_simulatedData.json) 

Use the keyboard shortcuts to select all content and copy it.
    
  OSx
    <kbd>Cmd</kbd>+<kbd>A</kbd> -->
    <kbd>Cmd</kbd>+<kbd>C</kbd>

  Windows
    <kbd>Ctrl</kbd>+<kbd>A</kbd> -->
    <kbd>Ctrl</kbd>+<kbd>C</kbd>


Open a new tab in Node-RED by clicking on the '+' sign. 

<img src="/images/newflow.png" width="40%" height="40%">

Import the flow by simply clicking on the 3 white lines on the top right corner of the Node-RED window.  Import - Clipboard.

<img src="/images/App27.png" width="50%" height="50%">

Paste the text you copied from the file. 

<img src="/images/App28.png" width="50%" height="50%">

This flow reads sensor data from the Watson IoT Platform and creates a visualization in your application's user interface. 
The code will create a new tab called Environment with a flow like this:

<img src="/images/simulations5.png" width="60%" height="60%">

Deploy your application changes from the **Deploy** button on the top right side of the screen. 


### Step 4. Check your web app UI! 
The dashboard nodes added an UI to our Node-RED application. 

<img src="/images/simulation6.png" width="60%" height="60%">

To access the UI go to:
http://yourAppName.eu-gb.mybluemix.net/ui - UK

Remember that if you are in US, Germany Sydney the address will look slightly different:
http://yourAppName.mybluemix.net/ui - US South

http://yourAppName.eu-de.mybluemix.net/ui - Germany

http://yourAppName.au-syd.mybluemix.net/ui - Sydney

**COLOR**

It is also possible to change the looks of your user interface in the dashboard tab. :blush:
In Node-RED go to the Dashboard tab in the left side menu to change the theme of your user interface. 

<img src="/images/color1.png" width="40%" height="40%">

Click on the color and select the main color for your web app. You can change the Light, dark or even custom template to customize the colors of your app. 

**Fantastic! Your web app is ready.** 
Now you can observe your Smart Home dashboard. :+1:


# PHASE 3
## Add AI-powered chatbot to your application using Watson Assistant

In this phase we are going to add a chatbot to our application, powered by Watson Assistant. Through the chatbot you will be able to get information about the sensor data in your "Smart Home" environment. 

### Step 5. Create Watson Assistant service on IBM Cloud
With IBM Watson™ Assistant service you can build a solution that understands natural-language input and uses machine learning to respond to customers in a way that simulates a conversation between humans.

Go to your IBM Cloud account and open the catalog. Look for Watson Assistant service and click on it.

<img src="/images/WA1.png" width="50%" height="50%">

Choose the region and space where you want the service to be created. In new accounts it will automatically select your resource group, usually named as default. 
You don't need to change the name if you don't want to, just click on 'Create'. 
![](/images/WA2.png?raw=true)

### Step 6. Import a conversation
Once the service is created click on 'Launch tool' to access it. 

<img src="/images/WA3.png" width="60%" height="60%">

In the home tab you have videos and tutorials on how to get started building dialoges. Feel free to explore them. 
Let's move to the Skills tab.

<img src="/images/WA5b.png" width="50%" height="50%">

The natural-language processing happens inside a skill, which is a container for all of the artifacts that define the conversation flow for an application.

You can create a new skill and start from scratch or import an existing conversation. 
Download assistant conversation from here: https://ibm.box.com/v/assistantUI 

Click on the 'Create new' button and then click on the import skill tab.

<img src="/images/WA6b.png" width="30%" height="30%">

When you import a skill, you can choose to import only the intents and entities, which can be useful if you want to build a new dialog using the same training data. In this case we will import everything. Click on 'Choose JSON file ' button and find the file you just downloaded. Then click on Import.

<img src="/images/WA7b.png" width="50%" height="50%">

### Step 7. Test your dialog
As you make changes to your dialog, you can test it at any time to see how it responds to input.
From the Dialog tab, click the conversation bubble icon. In the chat panel, type some text and then press Enter.
Check the response to see if the dialog correctly interpreted your input and chose the right response. 

The chat window indicates what intents and entities were recognized in the input. In the dialog editor pane, the currently active node is highlighted
Feel free to create new intents for your bot.
![](/images/WA8.png?raw=true)

### Step 8. Get Watson Assistant credentials 
Once you have tested the dialoge, it's time to collect the credentials to take them to our Node-RED application. 
Click on the Skills name and go back to the Skills overview. 

<img src="/images/WA-1.png" width="40%" height="40%">

Click on the 3 dots in your IoT-Assistant to open a menu and then click on View API details. 

<img src="/images/WA-2.png" width="40%" height="40%">

Copy the credentials and save them for later. You will need the Workspace ID (skill), username ('apikey'), password and URL. 

<img src="/images/WA-3.png" width="60%" height="60%">

### Step 9. Build a Node-RED flow to connect with Watson Assistant
**Back to Node-RED window**

Copy the content of the **assistantUI_simulatedData.json** file. Open the file URL. [Assistant UI code](https://raw.githubusercontent.com/sandra-calvo/smarthomes-SimulatedData/master/botUI_simulatedData.json) 

Use the keyboard shortcuts to select all content and copy it. 
    
  OSx
    <kbd>Cmd</kbd>+<kbd>A</kbd> -->
    <kbd>Cmd</kbd>+<kbd>C</kbd>

  Windows
    <kbd>Ctrl</kbd>+<kbd>A</kbd> -->
    <kbd>Ctrl</kbd>+<kbd>C</kbd>

Import the flow by simply clicking on the 3 white lines on the top right corner of the Node-RED window. Import -> Clipboard. Paste the content in the Flow 2 tab. 
This is the flow we are importing:

<img src="/images/flow21.png" width="100%" height="100%">

Time to do some editing! :smiley:

Double click on the **blue** assistant node to edit the node with your own credentials saved in the previous step. 
Add your username, password and workspace ID.  

<img src="/images/WA12.png" width="40%" height="40%">

**Important** Check the URL of your Watson Assistant service. The assistant node calls the service located in US by default. If your bot URL is in UK, Sydney or Germany uncheck the "Use Default Service Endpoint" box and in the Service Enpoint write the following:

  Dallas: https://gateway.watsonplatform.net/assistant/api
  
  Washington, DC: https://gateway-wdc.watsonplatform.net/assistant/api
  
  Frankfurt: https://gateway-fra.watsonplatform.net/assistant/api
  
  Sydney: https://gateway-syd.watsonplatform.net/assistant/api
  
  Tokyo: https://gateway-tok.watsonplatform.net/assistant/api
  
  London: https://gateway.watsonplatform.net/assistant/api

You can see where your service was created in the URL of the credentials you copied in Step 8.

Once you have edited all the nodes click on the _Deploy_ button to save the changes in your application.

### Step 10. Check the final result! 
Go back to the UI and talk with your bot! 

You can ask the bot about IoT and even ask what is the temperature in the room. The bot is connected to the sensors in your "Smart Home" environment. 

Remember, to go back to your web app (in UK region)
http://yourAppName.eu-gb.mybluemix.net/ui - UK

<img src="/images/simulation7.png" width="60%" height="60%">


# PHASE 4
## Connect with external APIs like Weather

You can connect your application with any available API. In this case we are going to connect Watson Assistant to the weather data. This way our bot will be able to tell us the weather anywhere in the world. 

Normally, I would use **Weather Company Data** service available on IBM Cloud. This service lets you integrate weather data from The Weather Company into your application. It has a free tier, but it is not available for Lite accounts. 
If you have an upgraded account you can use the Weather Company service. Feel free to ask me for the code. :blush: 

For this lab we are using Open Weather Map data https://openweathermap.org/. 
Note: An API key is required to use these nodes. You can register and obtain your own API key, or use the one available for this workshop. 

Copy the content of the **weather_UI.json** file. Open the file URL. [Weather UI code](https://raw.githubusercontent.com/sandra-calvo/smarthomes-SimulatedData/master/weatherUI_simulatedData.json) 

Use the keyboard shortcuts to select all content and copy it. 
    
  OSx
    <kbd>Cmd</kbd>+<kbd>A</kbd> -->
    <kbd>Cmd</kbd>+<kbd>C</kbd>

  Windows
    <kbd>Ctrl</kbd>+<kbd>A</kbd> -->
    <kbd>Ctrl</kbd>+<kbd>C</kbd>

Import the flow to Node-RED by simply clicking on the 3 white lines on the top right corner of the Node-RED window. 
Import -> Clipboard. 
This is the flow we are importing:

<img src="/images/flow27.png" width="70%" height="70%">

This flow gets weather information from Open Weather Map API. The location comes through the chatbot from the user. Then the city name goes to Google Maps API to get the coordinates and longitude & latitude are sent to the weather service. Finally it is visualized in the UI. 

**Remember** Connect the node "Weather response" with the node "Bot response".

<img src="/images/simulation9.png" width="80%" height="80%">

We need to edit the yellow Open Weather Map node and add the API key. I recommend you get your own API key from https://openweathermap.org/. In the meantime use the following API key:

    API KEY: 3a1ac87a062142df79f4177302bd7ab9
    
Now connect the grey link node coming from the Switch node with the grey link node starting the weather flow. To do that double click on the grey link node:

<img src="/images/node2.png" width="10%" height="10%">

Connect weather-In with weather-Out and click on _Done_.

<img src="/images/weather.png" width="50%" height="50%">

Lastly we need to edit the location of the weather widget in our user interface. 
Click on the dashboard tab in the left side menu and you will see there is two Assistant tab. One contains the bot and last value visualization, created in the last phase, and the other contains the weather.

<img src="/images/widget1.png" width="50%" height="50%">

Drag the weather widget to the Assistant above so it's part of the same tab than the other widgets. It should now look like this:

<img src="/images/widget2.png" width="50%" height="50%">

Click on _Deploy_ and go to the UI to check the changes! Now your UI should look like this:

<img src="/images/simulation8.png" width="70%" height="70%">

**Congrats!** You finished the lab. :clap:
Here, take a :lollipop:. You deserve it!! 
