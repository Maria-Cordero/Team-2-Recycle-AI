# Recycle AI

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
2. [Schema](#Schema)

## Overview
### Description
This application identifies which recyclable material an item is made of based on an image submitted by the user. The user also has the ability to find nearby recycling centers based on their current location.

### App Evaluation
[Evaluation of your app across the following attributes]
- **Category:** Utilities
- **Mobile:** Only Mobile as it will require camera for the main functionality. If Marketplace is expanded upon, we may have a website for easier to view store functionality.
- **Story:** This app will be able to scan any article and analyze its material. After that, a description of the scanned material would be provided along with available recycling locations across the country.
- **Market:** Any individual could choose to use this app, and to keep it a safe environment, people would be organized into age groups.
- **Habit:** This app contains a reward system for the users. Users earn points everytime they take a picture of a new item to recycle and reach milestones. This gamified approach can make users prone to visiting the app more often.
- **Scope:** The app targets a demographic interested in recycling. We want to grow and maintain our user base by helping streamline the recycling process. Later, we would like to expand the application to have an interactive aspect through the marketplace where users can put up items that they will no longer use for somebody else to have. 

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

*	User can take photo of item and model will analyze recyclability
*	User will be shown nearest locations to recycle analyzed item
*	Information pane for recycling statistics including but not limited to material hazards

**Optional Nice-to-have Stories**

*	Global news page related to environmental issues
*	Marketplace page to donate household inventory with search filters(predetermined) 
*	Profile:
    - Preferred recycling location
    - donation history(bought/sold) 
    - Avatar upgrades
    - Reward system
*	People near me page to see others around you who recycle

### 2. Screen Archetypes

* Home: This is the main and principal view of the app. It will be prompted as soon as the user launches the app.
*	Map: This view allows the users to browse through the available locations of recycling centers around the country.
*	Profile: Allows user to upload a photo and fill in valuable information.
*	Camera: The camera view will allow users to scan their items. They can do so using the front or back camera of their devices.
*	Marketplace: The marketplace will allow users to navigate and browse, as well as to post items with certain characteristics in order to sell or buy them.
*	Information: The information section will provide user with useful information, tips and other related facts regarding the material of their items.

### 3. Navigation

**Tab Navigation** (Tab to Screen)
* Map
* Camera
* Information

Optional:
* Marketplace
* Profile

**Flow Navigation** (Screen to Screen)
* Camera Screen -> Information
* Log In screen -> Account creation if new user -> Camera Screen
* Marketplace -> Filtered Listings
* Information -> News article redirect to browser

## Wireframes
<img src="https://github.com/Maria-Cordero/Team-2-Recycle-AI/blob/main/Images/wireframe.jpg" width=600>

### [BONUS] Digital Wireframes & Mockups
<img src="https://github.com/Maria-Cordero/Team-2-Recycle-AI/blob/main/Images/wireframe-digital.PNG" width=600>

## Schema 
### Models

**User Profile**  
|   Property   	|     Type    	|                Description                	|
|:------------:	|:-----------:	|:-----------------------------------------:	|
| userId       	| String      	| Unique id for user profile; PK            	|
| profileImage 	| File        	| Image that user uploads                   	|
| donations    	| Arrays      	| Information of all donations made by user 	|
| credentials  	| JSON object 	| Credentials used for user login           	|
| levels       	| Number      	| Level progression system                  	|

**Camera**  
|    Property   	|     Type    	|       Description      	|
|:-------------:	|:-----------:	|:----------------------:	|
| materialImage 	| File        	| Image of the material  	|
| Model data    	| JSON Object 	| Material data response 	|

**Recyclable Material information**  
|  Property  	|     Type     	|                Description               	|
|:----------:	|:------------:	|:----------------------------------------:	|
| materialId 	| String       	| Unique id for recyclable material; PK    	|
| news       	| JSON  Object 	| Data response of news about the material 	|

**Maps**
|    Property    	|     Type    	|                                                                                                  Description                                                                                                 	|
|:--------------:	|:-----------:	|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:	|
| locationId     	| String      	| Unique id for map location; PK                                                                                                                                                                               	|
| Recycling hubs 	| Array       	| Array of objects containing data of all nearby recycling centers [{   name: string,      acceptedMaterials: array,      location: {          longitud: string,         latitud: string,      }, },... {...}] 	|
| User location  	| JSON Object 	| Current location of user                                                                                                                                                                                     	|  

**Marketplace Posts**
|  Property 	|       Type      	|           Description           	|
|:---------:	|:---------------:	|:-------------------------------:	|
| objectId  	| String          	| unique id for the user post; PK 	|
| author    	| Pointer to User 	| image author; FK                	|
| image     	| File            	| image that user posts           	|
| caption   	| String          	| image caption by author         	|
| createdAt 	| DateTime        	| date when post is created       	|
| updatedAt 	| DateTime        	| date when post is last updated  	|

### Networking
*	Maps Screen  
    * (Read/GET) Query Location id  
    * (Read/GET) Recycling hubs  
    * (Read/GET) Query User location  
*   Profile Screen  
    * (Read/GET) Query logged in user object  
    * (Update/PUT) Update user profile image  
    * (Read/GET) Query market listings  
*   Camera  
    * (Read/GET) Query Model Data  
    * (Update/PUT) Update material image  
*   Recyclable Material Information  
    * (Read/GET) Query news related to recycling  
    * (Read/GET) Query array of recyclable materials with pictures / data 


