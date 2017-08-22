# perperation Welcome Message Screen component 
## Introduction

The WelcomeMessage Screen component belongs to Vodafone's group components. The purpose of this component is displaying welcome message to the user when the app is launched. The message will differ according to the launching time i.e. it could be ‘Good Morning’, ‘Good Afternoon’, or ‘Good Evening’.  

## 📗 Documentation
All methods, properties, and types available in the Splash screen component are documented below.

##### Documentation Table of Contents  

* [Installation](#installation)
* [Usage](#usage)
* [Code example](#code-example)
* [Dependencies](#-dependencies)???


## Installation
To add the WelcomeMessage component to an existing application, please follow these steps:
1. Edit `build.gradle` file in the application’s module directory and add notifications library to the dependencies block:

    ```bash
    dependencies {
        ...
        compile 'com.vfg:vov:1.x'   
        ...
    }
    ```
    **Note: The version number of the component should be updated to match the latest component release.**
    **Note: The latest release number at the time of writing this is 1.18.**
    
## Usage
To get WelcomeMessage to work with your activity, please follow these steps:
 1.	Add the custom view to your layout
```
      <com.vfg.vov.VovView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/vovViewApp"
        />  
```

2. The view displays list of different items. So, In the activity instantiate ArrayList of the type VovMessage.
3.VovMessage is the parent class of multiple classes like VovStandardMessage and VovWelcomeMessage. Our main interest is in The latest   one. 
4. So,  Instantiate an object of type VovWelcomeMessage and set its the intervals and the messages.
5. Add it to the Arraylist:

```java
  vovMessagesList.add(vovWelcomeMessage);
```
       
       
6. Add the arraylist to the view:

```java
  vovView.viewVovMessages(vovMessagesList);
```

## Usage Considerations:
1.	the welcome message must have three intervals. However, to cover less than three intervals you can do that by passing One Interval includes other Intervals. No Workaround for more than 3 intervals.
2.	  Vov Intervals can’t accept null.
3.	You have to pass time either by millisecond in (AND)  or hours in (iOS) format.
4.	To set the Welcome Message Configuration :
You can pass it Using Vov Model , The App can fetch it from whatever source (Hardcoded – CMS – File ) then pass it to Vov Model.

## Building the WelcomeMessage object
1. Initialize new VovWelcomeMessage object
```java
 VovWelcomeMessage vovWelcomeMessage =new VovWelcomeMessage();
```


2.Set welcome message object attributes

```java
  vovWelcomeMessage.setMessageBody("This is a test Body message");
  vovWelcomeMessage.setUsername("User1");
  vovWelcomeMessage.setAppName("Ana Vodafone");
  vovWelcomeMessage.setType(VovMessageType.WELCOME_MESSAGE);
```

3.For each interval in the day we have different message. So,
to set welcome message intervals and messages we use VovGreetingModel
```java
  VovGreetingModel morningGreetingModel = new VovGreetingModel();
  morningGreetingModel.setGreetingText("Good morning");
  morningGreetingModel.setStartInterval(Calendar.getInstance().getTimeInMillis());
  morningGreetingModel.setEndInterval(Calendar.getInstance().getTimeInMillis());
```

4.Then link it to the message
```java
  vovWelcomeMessage.setMorningGreetingModel(morningGreetingModel);
```

Repeat the steps 3 and 4 for the other two intervals.

## Code example
This example snippet shows how to add the WelcomeMessage component to your screen.
In onCreate Method:
```java
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

```

## 👥 Dependencies
This component has no dependencies
