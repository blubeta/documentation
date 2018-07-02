# Google Tag Manager

### Tips:

- Always use camelCase and not snake_case, GTM has a hard time parsing snake_case for some reason
- Make sure in Scheme OS_ACTIVITY_MODE is de-selected or destroyed (probably destroyed is better)
- For most Events Tracking to end up on GA, they need a Event Action, Event Label, and Event Category
- Clean your build everytime you update a container, and maybe even delete your emulator settings - otherwise it will be cached and won't look to update the container

 
## Setting Up

### General Container Set Up with Firebase

- Container Tag Type: Universal Analytics
- Track Type: Event
- Event Tracking Parameters
	- Category, Action, and Label should all be variables that are custom event parameters which look for 	eventCategory, eventAction, and eventLabel
	- When setting up with the same names in the actual firebase javascript event logging
- Non-Interaction Hit: False
- [x] Use Firebase Event Parameters for Campaign Attribution
- Google Analytics - Don't set
- [x] Enable overriding settings in this tag
- Tracking ID - Set to a variable constant that containt Google Analytics Tracking ID
	- Make sure this a CONSTANT and not another type of variable
- Triggering
	- Create a Custom Event 
		- Trigger Fires on Some Events 
		- Event Name contains `{ eventName from JS }` - good default to use is `generalEvent` for most events


### Adding Containers to Native Builds

#### iOS

- Adding the Container
	1. Download GTM Container from the latest version of GTM Container for iOS, and place in the top level iOS folder. 
	2. Open xCode.
	3. In the Menu > File > Add files to `{ project }`
	4. Add file to the boat-trader xcworkspace directory (the second-to-top level folder) (make sure create folder references is checked in options)
	5. Clean Your Build and Erase Your Emulator to get immediate access to new GTM Container

#### Android 

- 

