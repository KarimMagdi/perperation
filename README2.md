 
## Introduction
The WelcomeMessage Screen component belongs to Vodafone's group components. The purpose of this component is displaying welcome message to the user when the app is launched. The message will differ according to the launching time i.e. it could be ‘Good Morning’, ‘Good Afternoon’, or ‘Good Evening’.   

## 📗 Documentation
All methods, properties, and types available in the Vov WelcomeMessage component are documented below.


##### Documentation Table of Contents
 * Installation
 * Usage
 * Code example
 * Dependencies
 
## Installation
To add the WelcomeMessage component to an existing application, please follow these steps:
1.	Edit build.gradle file in the application’s module directory and add notifications library to the dependencies block:
2.	dependencies {
3.	    ...
4.	    compile 'com.vfg:vov:1.x'   
5.	 ...
}
Note: The version number of the component should be updated to match the latest component release. The latest at the time of writing this is 1.18

## Usage
To get WelcomeMessage to work with your activity, please follow these steps:
1. Add the custom view to your layout
<com.vfg.vov.VovView
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:id="@+id/vovViewApp"
    />
2. The view displays list of different items. So, In the activity instantiate ArrayList of the type VovMessage.
3. VovMessage is the parent class of multiple classes like VovStandardMessage and VovWelcomeMessage. Our main interest is in The latest one. 
4. So,  Instantiate an object of type VovWelcomeMessage and set its the intervals and the messages.
5. Add this to the Arraylist
6.	vovMessagesList.add(vovWelcomeMessage);
7.	
8.	add the arraylist to the view:
vovView.viewVovMessages(vovMessagesList);

## Usage Considerations:
1.	the welcome message must have three intervals. However, to cover less than three intervals you can do that by passing One Interval includes other Intervals. No Workaround for more than 3 intervals.
2.	  Vov Intervals can’t accept null.
3.	You have to pass time either by millisecond in (AND)  or hours in (iOS) format.
4.	To set the Welcome Message Configuration :
You can pass it Using Vov Model , The App can fetch it from whatever source (Hardcoded – CMS – File ) then pass it to Vov Model.



Building the WelcomeMessage object
Initialize new VovWelcomeMessage object
       VovWelcomeMessage vovWelcomeMessage =new VovWelcomeMessage();



Set welcome message object attributes

vovWelcomeMessage.setMessageBody("This is a test Body message");
vovWelcomeMessage.setUsername("User1");
vovWelcomeMessage.setAppName("Ana Vodafone");
vovWelcomeMessage.setType(VovMessageType.WELCOME_MESSAGE);


For each interval in the day we have different message. So,
to set welcome message intervals and messages we use VovGreetingModel 
VovGreetingModel morningGreetingModel = new VovGreetingModel();
morningGreetingModel.setGreetingText("Good morning");
morningGreetingModel.setStartInterval(Calendar.getInstance().getTimeInMillis());
morningGreetingModel.setEndInterval(Calendar.getInstance().getTimeInMillis());
	
Then link it to the message
vovWelcomeMessage.setMorningGreetingModel(morningGreetingModel);

Repeat this step for the other two intervals. 

  





## Code example
This example activity shows how to add the WelcomeMessage component to your screen.
In onCreate Method:
vovView=(VovView)findViewById(R.id.vovViewApp);

//1-instantiate messages List
ArrayList<VovMessage> vovMessagesList=new ArrayList<>();


//2-instantiate welcome message object
VovWelcomeMessage vovWelcomeMessage =new VovWelcomeMessage();

//3-set welcome message object attributes
vovWelcomeMessage.setMessageBody("This is a test Body message");
vovWelcomeMessage.setUsername("User1");
vovWelcomeMessage.setAppName("Ana Vodafone");
vovWelcomeMessage.setType(VovMessageType.WELCOME_MESSAGE);

//4-instantiate welcome message object GreetingModel
VovGreetingModel morningGreetingModel = new VovGreetingModel();
morningGreetingModel.setGreetingText("Good morning");
morningGreetingModel.setStartInterval(Calendar.getInstance().getTimeInMillis());
morningGreetingModel.setEndInterval(Calendar.getInstance().getTimeInMillis());
vovWelcomeMessage.setMorningGreetingModel(morningGreetingModel);

vovWelcomeMessage.setAfternoonGreetingModel(morningGreetingModel);
vovWelcomeMessage.setEveningGreetingModel(morningGreetingModel);
vovWelcomeMessage.setMorningGreetingModel(morningGreetingModel);


vovMessagesList.add(vovWelcomeMessage);
vovView.viewVovMessages(vovMessagesList);


