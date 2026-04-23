---
title: Emergency App
layout: tutorial
---

# Challenge

The Emergency App is an application that helps users quickly respond to dangerous or urgent situations. It provides a map to identify the user’s location and, in an emergency, can capture and share their real-time location. The app also allows users to record a message and take a photo, which can be sent along with their location to trusted contacts via text. Additionally, it includes an emergency button that plays a loud alarm sound to attract attention and deter potential threats.

<strong>Disclaimer!</strong>
This tutorial is provided for educational purposes only. If you are experiencing a real emergency, please contact emergency services and seek help from the proper authorities immediately.

![Finished Product](../images/emergencyApp/app.jpg){:.enlargeImage}

# Setup

## Getting Started

If you need help getting started and set up with App Inventor please visit our <a href="https://appinventor.mit.edu/explore/ai2/setup" target="_blank">Setting Up App Inventor</a> page.

## Familiarizing Yourself With App Inventor Layout

The screen you are currently looking at is the "Design" Screen. On the left hand side of your screen (outlined in red) is the Palette, where there are drawers with components you can add to your app. In the center of the screen (outlined in green) is the Viewer, which is an empty phone screen where you will build the User Interface (UI) of your app. On the right side of the screen (outlined in blue) is the Properties window, you can edit specific aspects of each component you add to your app. Take a few minutes to explore the components within the drawers.

![Familiarize with Layout](../images/digitaldoodlewithAI/app_inventor_layout.png){:.enlargeImage}

# Emergency App

## Emergency App UI

Most of the User Interface is already built, but we need to add some components to finish it.

From the Maps drawer, drag and drop a <strong> Map </strong> onto the phone screen into the grey HorizontalArrangement.

![Map](../images/emergencyApp/InsertMap.png){:.enlargeImage}

Under properties, change the <em> Height </em> to Fill parent, change the <em> Width </em> to Fill parent, and change the <em> ZoomLevel </em> to 18.

![Map Properties](../images/emergencyApp/MapProperties.png){:.enlargeImage}

From the Maps drawer, drag and drop a <strong> Marker </strong> onto the Map in the phone screen.

![Marker](../images/emergencyApp/AddMarker.png){:.enlargeImage}

Now we will add all of the non-visible components that work in the background to give functionality to the app. These components won’t show up on the screen, but you will see them on the page below the phone screen. From the Media drawer, drag and drop a <strong>Camera</strong>, <strong>Player</strong>, and <strong>SpeechRecognizer</strong> onto the phone screen.

![Non-visible Media](../images/emergencyApp/AddNonVisMedia.png){:.enlargeImage}

Under the <strong> Screen1 </strong> panel, select <strong>Player1</strong> and under properties, change the Source to “AlarmSound.m4a”.

![Player Source](../images/emergencyApp/PlayerProperties.png){:.enlargeImage}

From the Sensors drawer, drag and drop a <strong>LocationSensor</strong> onto the phone screen.

![Location Sensor](../images/emergencyApp/AddLocSensor.png){:.enlargeImage}

From the Social drawer, drag and drop a <strong>Sharing</strong> component onto the phone screen.

![Sharing](../images/emergencyApp/AddSharing.png){:.enlargeImage}

## Coding the UI Functionality
In the top right corner of your screen, click the Blocks button. The Blocks screen is where you will code the functionality of your app.

![Blocks Button](../images/emergencyApp/SwitchToBlocks.png){:.enlargeImage}

## Coding the Player
Under <strong>EmergencyButton</strong>, drag and drop when EmergencyButton.Click into your workspace.

![When Emergency Button](../images/emergencyApp/WhenEmergencyClick.png){:.enlargeImage}

Under <strong>Player1</strong>, drag call Player1.Start into your workspace and click it into the when EmergencyButton.Click block.

![Start Player](../images/emergencyApp/CallPlayer1Start.png){:.enlargeImage}

Under <strong>ResetButton</strong>, drag and drop when ResetButton.Click into your workspace.

![When Reset Button](../images/emergencyApp/WhenResetButtonClick.png){:.enlargeImage}

Under <strong>Player1</strong>, drag call Player1.Stop into your workspace and click it into the when ResetButton.Click block.

![Stop Player](../images/emergencyApp/CallPlayerStop.png){:.enlargeImage}

## Initialize Latitue and Longitude Variables

Under <strong>Variables</strong>, drag initialize global name to into your workspace.

![Initialize Latitude Variable](../images/emergencyApp/InitLatitude.png){:.enlargeImage}

Change “name” to “latitude”.

![Latitude Variable](../images/emergencyApp/NameLatitude.png){:.enlargeImage}

Under <strong>Text</strong>, drag “ “ into your workspace and click it into the initialize global latitude to block.

![Latitude Empty](../images/emergencyApp/LatitudeEmpty.png){:.enlargeImage}

Repeat the same steps to initialize a “longitude” variable.

![Longitude Variable](../images/emergencyApp/InitLongitude.png){:.enlargeImage}

## Get Location
Under <strong>GetLocationButton</strong>, drag when GetLocationButton.Click into your workspace.

![When Get Location Button](../images/emergencyApp/WhenGetLocClick.png){:.enlargeImage}

Under <strong>Variables</strong>, drag the set to block into your workspace and click it into the when GetLocationButton.Click block.

![Set Latitude Block](../images/emergencyApp/SetLat.png){:.enlargeImage}

Choose “global latitude” for the variable to set.

![Set Global Latitude](../images/emergencyApp/SelectGlobalLat.png){:.enlargeImage}

Under <strong>LocationSensor1</strong>, drag the LocationSensor1.Latitude block into your workspace and click it into the set global latitude to block.

![Location Sensor Latitude](../images/emergencyApp/SetLatToLocSenLat.png){:.enlargeImage}

Under <strong>Variables</strong>, drag the set to block into your workspace and click it into the when GetLocationButton.Click block.

![Set Longitude Block](../images/emergencyApp/SetLon.png){:.enlargeImage}

Choose “global longitude” for the variable to set.

![Set Global Longitude](../images/emergencyApp/SelectGlobalLon.png){:.enlargeImage}

Under <strong>LocationSensor1</strong>, drag the LocationSensor1.Longitude block into your workspace and click it into the set global longitude to block.

![Location Sensor Longitude](../images/emergencyApp/SetGlobalLontoLocLon.png){:.enlargeImage}

Under <strong>LocationSensor1</strong>, drag LocationSensor1.ReverseGeocode into your workspace and click it into the when GetLocationButton.Click block. Reverse geocode is used to get the actual address of the location given the latitude and longitude of the user.

![Reverse Geocode](../images/emergencyApp/LocSenReverseGeo.png){:.enlargeImage}

Under <strong>Variables</strong>, drag the get block into your workspace and click it into both the latitude and longitude sections of the call LocationSensor1.ReverseGeocode block.

![Get Latitude and Longitude](../images/emergencyApp/GeocodeLatandLon.png){:.enlargeImage}

Choose “global latitude” for the latitude attribute and “global longitude” for the longitude attribute.

![Global Latitude and Longitude](../images/emergencyApp/SetGeoLatLon.png){:.enlargeImage}

Under <strong>LattitudeLabel</strong>, drag set LattitudeLabel.Text to into your workspace and click it into the when GetLocationButton.Click block.

![Set Latitude Label](../images/emergencyApp/SetLatLabel.png){:.enlargeImage}

Under <strong>Variables</strong>, drag the get block into your workspace and click it into the set LattitudeLabel.Text to block.

![Latitdue Label Text](../images/emergencyApp/LatLabelText.png){:.enlargeImage}

Choose “global latitude” for the variable to set.

![Latitude Label Set Text](../images/emergencyApp/LatLabelGlobalLat.png){:.enlargeImage}

Under <strong>LongitudeLabel</strong>, drag set LongitudeLabel.Text to into your workspace and click it into the when GetLocationButton.Click block.

![Set Longitude Label](../images/emergencyApp/SetLonLabelText.png){:.enlargeImage}

Under <strong>Variables</strong>, drag the get block into your workspace and click it into the set LongitudeLabel.Text to block.

![Longitude Label Text](../images/emergencyApp/LonText.png){:.enlargeImage}

Choose “global longitude for the variable to set.

![Longitude Label Set Text](../images/emergencyApp/LonLabelGlobalLon.png){:.enlargeImage}

Under <strong>Map</strong>, drag call Map1.PanTo into your workspace and click it into the when GetLocationButton.Click block.

![Pan Map](../images/emergencyApp/MapPanTo.png){:.enlargeImage}

Under <strong>Variables</strong>, drag the get block into your workspace and click it into both the latitude and longitude sections of the call Map1.PanTo block.

![Pan Latitude and Longitude](../images/emergencyApp/PanLatLon.png){:.enlargeImage}

Choose “global latitude” for the latitude attribute and “global longitude” for the longitude attribute.

![Global Variables Pan](../images/emergencyApp/PanSetLonLat.png){:.enlargeImage}

Under <strong>Math</strong>, drag the 0 block into your workspace and click it into the zoom section of the call Map1.PanTo block.

![Zoom Set](../images/emergencyApp/MapZoom.png){:.enlargeImage}

Change 0 to 18. This zoom level will show the map at the city street level detail.

![Zoom Number](../images/emergencyApp/Zoom18.png){:.enlargeImage}

Under <strong>Marker1</strong>, drag call Marker1.SetLocation into your workspace and click it into the when GetLocationButton.Click block. This ensures that the marker is set at the exact location the user is at on the map.

![Call Marker Set Location](../images/emergencyApp/CallMarkerSetLoc.png){:.enlargeImage}

Under <strong>Variables</strong>, drag the get block into your workspace and click it into both the latitude and longitude sections of the call Marker1.SetLocation block.

![Marker Variables](../images/emergencyApp/MarkerLatLon.png){:.enlargeImage}

Choose “global latitude” for the latitude attribute and “global longitude” for the longitude attribute.

![Marker Set Latitude and Longitude](../images/emergencyApp/MarkerSetLonLat.png){:.enlargeImage}

## Getting Address
Under <strong>Variables</strong>, drag initialize global name to into your workspace.

![Initalize Address](../images/emergencyApp/initAddress.png){:.enlargeImage}

Change “name” to “currentAddress”.

![Name Address Variable](../images/emergencyApp/NameCurrentAddress.png){:.enlargeImage}

Under <strong>Text</strong>, drag the “ “ block into your workspace and click it into the initialize global currentAddress to block.

![Address Empty](../images/emergencyApp/AddressEmpty.png){:.enlargeImage}

Under <strong>LocationSensor1</strong>, drag when LocationSensor1.GotAddress into your workspace. When the LocationSensor1.ReverseGeocode block returns with the address, this event-handler block will be called.

![When Location Sensor Got Address](../images/emergencyApp/WhenGotAddress.png){:.enlargeImage}

Under <strong>Variables</strong>, drag the set to block into your workspace and click it into the when LocationSensor1.GotAddress block.

![Set Address](../images/emergencyApp/SetAddress.png){:.enlargeImage}

Choose “global currentAddress” for the variable to set.

![Global Address](../images/emergencyApp/pickCurrentAddress.png){:.enlargeImage}

Hover over “address” in the when LocationSensor1.GotAddress block. When the drop down option appears, drag the get address block and click it into the set global currentAddress to block.

![Get Address](../images/emergencyApp/setCurrentAddress.png){:.enlargeImage}

Under <strong>AddressLabel</strong>, drag set AddressLabel.Text to into your workspace and click it into the when LocationSensor1.GotAddress block.

![Address Label](../images/emergencyApp/SetAddressLabel.png){:.enlargeImage}

Hover over “address” in the when LocationSensor1.GotAddress block. When the drop down option appears, drag the get address block and click it into the set AddressLabel.Text to block.

![Get Address for Label](../images/emergencyApp/LocationTextCurrentAddress.png){:.enlargeImage}

## Reset Labels
Under <strong>LattitudeLabel</strong>, drag set LattitudeLabel.Text to into your workspace and click it into the when ResetButton.Click block.

![Reset Latitude Label](../images/emergencyApp/ClearLatLabel.png){:.enlargeImage}

Under <strong>Text</strong>, drag the “ “ block into your workspace and click it into the set LattitudeLabel.Text to block.

![Latitue Label Empty](../images/emergencyApp/LatLabelReset.png){:.enlargeImage}

Change the empty text to “0.0”.

![Latitude 0.0](../images/emergencyApp/Lat0.0.png){:.enlargeImage}

Under <strong>LongitudeLabel</strong>, drag set LongitudeLabel.Text to into your workspace and click it into the when ResetButton.Click block.

![Reset Longitude Label](../images/emergencyApp/ClearLonLabel.png){:.enlargeImage}

Under <strong>Text</strong>, drag the “ “ block into your workspace and click it into the set LongitudeLabel.Text to block.

![Longitude Label Empty](../images/emergencyApp/ResetLon.png){:.enlargeImage}

Change the empty text to “0.0”.

![Longitude 0.0](../images/emergencyApp/Lon0.0.png){:.enlargeImage}

Under<strong>AddressLabel</strong>, drag set AddressLabel.Text to into your workspace and click it into the when ResetButton.Click block.

![Reset Address Label](../images/emergencyApp/ClearAddressLabel.png){:.enlargeImage}

Under <strong>Text</strong>, drag the “ “ block into your workspace and click it into the set AddressLabel.Text to block.

![Address Label Empty](../images/emergencyApp/ResetAddress.png){:.enlargeImage}

Change the empty text to “Current Address”.

![Address Label Text](../images/emergencyApp/AddressCurrentAddress.png){:.enlargeImage}

## Record Message

Under <strong>RecordMessageButton</strong>, drag when RecordMessageButton.Click into your workspace.

![When Record Message Button](../images/emergencyApp/WhenRecordMessage.png){:.enlargeImage}

Under <strong>SpeechRecognizer1</strong>, drag call SpeechRecognizer1.GetText into your workspace and click it into the when RecordMessageButton.Click block.

![Call Speech Recognizer](../images/emergencyApp/CallSpeechRecognizer.png){:.enlargeImage}

Under <strong>SpeechRecognizer1</strong>, drag when SpeechRecognizer1.AfterGettingText into your workspace.

![Speech Recognizer After Text](../images/emergencyApp/SpeechAfterText.png){:.enlargeImage}

Under <strong>MessageTextBox</strong>, drag set MessageTextBox.Text to into your workspace and click it into the when SpeechRecognizer1.AfterGettingText block.

![Message Text Box](../images/emergencyApp/SetMessageTextBox.png){:.enlargeImage}

Hover over “result” in the when SpeechRecognizer1.AfterGettingText block. When the drop down option appears, drag the get result block and click it into the set MessageTextBox.Text to block.

![Message Text](../images/emergencyApp/getResultText.png){:.enlargeImage}

## Take Photo

Under <strong>TakePhotoButton</strong>, drag when TakePhotoButton.Click into your workspace.

![When Take Photo Button](../images/emergencyApp/WhenTakePhoto.png){:.enlargeImage}

Under <strong>Camera1</strong>, drag call Camera1.TakePicture into your workspace and click it into the when TakePhotoButton.Click block.

![Call Camera](../images/emergencyApp/CallCameraTakePic.png){:.enlargeImage}

Under <strong>Variables</strong>, drag initialize global name to into your workspace.

![Initialize Photo File](../images/emergencyApp/initPhotoFile.png){:.enlargeImage}

Change “name” to “photoFile”.

![Photo File Name](../images/emergencyApp/NamePhotoFile.png){:.enlargeImage}

Under <strong>Text</strong>, drag “ “ into your workspace and click it into the initialize global photoFile to block.

![Photo File Empty](../images/emergencyApp/PhotoFileEmpty.png){:.enlargeImage}

Under <strong>Camera1</strong>, drag when Camera1.AfterPicture into your workspace.

![After Picture](../images/emergencyApp/CameraAfterPic.png){:.enlargeImage}

Under <strong>Variables</strong>, drag set to into your workspace and click it into the when Camera1.AfterPicture block.

![Set Photo](../images/emergencyApp/SetPhotoFile.png){:.enlargeImage}

Choose “global photoFile” for the variable to set.

![Global Photo File](../images/emergencyApp/chooseGlobalPhotoFile.png){:.enlargeImage}

Hover over “image” in the when Camera1.AfterPicture block. When the drop down option appears, drag the get image block and click it into the set global photoFile to block.

![Set Image](../images/emergencyApp/getImage.png){:.enlargeImage}

## Reset Message and Photo

Under <strong>MessageTextBox</strong>, drag “set MessageTextBox.Text to” into your workspace and click it into the when ResetButton.Click block.

![Reset Message](../images/emergencyApp/ClearMessage.png){:.enlargeImage}

Under <strong>Text</strong>, drag the “ “ block into your workspace and click it into the setMessageTextBox.Text to block.

![Message Empty](../images/emergencyApp/MessageEmpty.png){:.enlargeImage}

Under <strong>Variables</strong>, drag the set to block into your workspace and click it into the when ResetButton.Click block.

![Reset Photo](../images/emergencyApp/ClearPhotoFile.png){:.enlargeImage}

Choose “global photoFile” for the variable to set.

![Global Photo File Reset](../images/emergencyApp/SelectPhotoFile.png){:.enlargeImage}

Under <strong>Text</strong>, drag the “ “ block into your workspace and click it into the set global photoFile to block.

![Photo File Empty](../images/emergencyApp/PhotoFileEmptyText.png){:.enlargeImage}

## Share Information

Under <strong>ShareButton</strong>, drag the when ShareButton.Click block into your workspace.

![When Share Button](../images/emergencyApp/WhenShare.png){:.enlargeImage}

Under <strong>Sharing1</strong>, drag call Sharing1.ShareFileWithMessage into your workspace and click it into the when ShareButton.Click block.

![Call Sharing](../images/emergencyApp/ShareFileWMessage.png){:.enlargeImage}

Under <strong>Variables</strong>, drag the get block into your workspace and click it into the file section of the call Sharing1.ShareFileWithMessage block.

![Sharing File](../images/emergencyApp/ShareFile.png){:.enlargeImage}

Choose “global photoFile” for the variable to get.

![Photo File Share](../images/emergencyApp/ChoosePhotoFile.png){:.enlargeImage}

Under <strong>Text</strong>, drag join into your workspace and click it into the message section of the call Sharing1.ShareFileWithMessage block.

![Join Message](../images/emergencyApp/MessageJoin.png){:.enlargeImage}

Under <strong>Text</strong>, drag the “ “ block into your workspace and click it into the first section of the join block.

![Message 1](../images/emergencyApp/Message1.png){:.enlargeImage}

Change the empty text to “Information about my whereabouts in case needed:... ”

![Message 1 Text](../images/emergencyApp/text1.png){:.enlargeImage}

Under <strong>Variables</strong>, drag the get block into your workspace and click it into the second section of the join block.

![Message 2](../images/emergencyApp/Message2.png){:.enlargeImage}

Choose “global currentAddress” for the variable to get.

![Message 2 Content](../images/emergencyApp/SetText2.png){:.enlargeImage}

Under Text, drag the “ “ block into your workspace and click it into the join block under get global currentAddress.

![Message 3](../images/emergencyApp/Message3.png){:.enlargeImage}

Change the empty text to “\n (”. The “\n” text creates a new line.

![Message 3 Content](../images/emergencyApp/Message3Content.png){:.enlargeImage}

Under <strong>Variables</strong>, drag the get block into your workspace and click it into the join block under “\n (“.

![Message 4](../images/emergencyApp/Message4.png){:.enlargeImage}

Choose “global latitude” for the variable to get.

![Message 4 Content](../images/emergencyApp/Message4Content.png){:.enlargeImage}

Under <strong>Text</strong>, drag the “ “ block into your workspace and click it into the join block under get global latitude.

![Message 5](../images/emergencyApp/Message5.png){:.enlargeImage}

Change the empty text to “, ”.

![Message 5 Content](../images/emergencyApp/SetText5.png){:.enlargeImage}

Under <strong>Variables</strong>, drag the get block into your workspace and click it into the join block under  “, “.

![Message 6](../images/emergencyApp/Message6.png){:.enlargeImage}

Choose “global longitude” for the variable to get.

![Message 6 Content](../images/emergencyApp/SetText6.png){:.enlargeImage}

Under <strong>Text</strong>, drag the “ “ block into your workspace and click it into the join block under get global longitude.

![Message 7](../images/emergencyApp/Message7.png){:.enlargeImage}

Change the empty text to “) \n\n”.

![Message 7 Content](../images/emergencyApp/setText7.png){:.enlargeImage}

Under <strong>MessageTextBox</strong>, drag MessageTextBox.Text into your workspace and click it into the join block under “) \n\n“.

![Message 8](../images/emergencyApp/Message8.png){:.enlargeImage}

Under <strong>Text</strong>, drag the “ “ block into your workspace and click it into the join block under MessageTextBox.Text.

![Message 9](../images/emergencyApp/Message9.png){:.enlargeImage}

Change the empty text to “\n\nPlease save this in case of an emergency”.

![Message 9 Content](../images/emergencyApp/setText9.png){:.enlargeImage}

## Finished Blocks

Congratulations! You have now completed the Emergency App tutorial.

![Finished Blocks](../images/emergencyApp/Final.png){:.enlargeImage}


## Testing the app

Now test your app by scanning the QR Code generated via your AI2 Companion.

![QR Code](../images/simpleChatBot/QRCode.png){:.enlargeImage}

Once the app is running, you can activate its features to simulate an emergency situation. Try using the map to view your location, record a short message, and take a photo. Then send this information to a trusted contact to confirm that the location, message, and image are shared correctly via text. You may want to warn your contact that this is a test run to see if your app is working and not an emergency.

You should also test the emergency button to ensure it plays a loud alert sound as expected.

Note that some features, such as messaging or location sharing, may have limitations depending on your device settings or permissions. Make sure all required permissions (location, camera, microphone) are enabled for full functionality.

Again, this tutorial is provided for educational purposes only. If you are experiencing a real emergency, please contact emergency services and seek help from the proper authorities immediately.

Congratulations! You’ve successfully built and tested an app designed to support users in responding more effectively during emergency situations.


## Saving the app
In the Companion App, you can save an app by opening it and clicking on the icon in the top right corner. Then click on “Download Project”.

![Download Project](../images/emergencyApp/DownloadProj.png){:.enlargeImage}

The next time you open the companion app, you can click on “my saved apps”, and the apps you downloaded should be saved for you to use.

![Saved Apps](../images/emergencyApp/SavedApps.png){:.enlargeImage}

# Expand Your App

Here are some ideas of how you can expand your app:

* Include a countdown timer before sending alerts, giving users a few seconds to cancel in case of accidental activation.
* Add a feature that logs past emergency alerts so users can review when and where alerts were sent along with the messages sent.
* Provide an option for users to select their preferred language for messages sent during emergencies.
* Currently the sharing component will allow you to share your message with one person at a time. If you would like to send a text message to multiple people all at once, add a list of trusted or preferred contacts, allowing users to press one button to automatically send their location and message to everyone on the list.

Hints:

![Safe List Hint](../images/emergencyApp/Hint1.png){:.enlargeImage}

![Social Texting Hint](../images/emergencyApp/Hint2.png){:.enlargeImage}

Multiple phone numbers must be comma separated.

![Comma Seperation Hint](../images/emergencyApp/Hint3.png){:.enlargeImage}
