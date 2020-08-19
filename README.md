# Youi-tv React Native Mobile App & New Relic Mobile
## youi-newrelic-curl
React Native mobile test application implemented with the [You.i Engine One](https://www.youi.tv/) SDK.

### Main Goal
Instrumentation with New Relic Mobile to receive MobileRequest and MobileRequestError events.

### State of the Art
 - Some New Relic SDK methods were already exposed by Youi-tv and AT&T development team to the JS interface like sending customEvents.
 - You.i Engine One allows you to build with JavaScript or C++ and deploy it to over 11 different platforms. In this way, all native capabilities are marshaled in C or C++ libraries.
 - All Network capabilities for Android are implemented natively with [LibCurl](https://curl.haxx.se/libcurl/c/example.html).
 - You.i Engine One provides its own React Native solution.

## Install You.i Engine One SDK

Please follow instructions below:

https://developer.youi.tv/latest/Content/InstallationCommon/H1IntroToInstallSection.htm

API Key provided by Youi-tv support team to use in testing:

`AKCp5fUE1R5h344dSmBekNCA9rExE21uFbZqRjK7Uji8JpEmiDcgwCY4bpD289gH3kUBNWPUB`

## Install & Deploy test App

To install all React Native dependencies:

`yarn install`

To start the Metro server (development mode):

`yarn start`

To run the test app in an Android device (open other console and go to the project dir):

`youi-tv run -p android` 

For further information please visit the You.i Engine One documentation site [here](https://developer.youi.tv/latest/Content/API_Links.htm?cshid=API_Links).

# Results
 - For iOS and tvOS the agent was initialized inside the AppDelegate class which is not used by default with a You.i App. With that, we solve the issue on those platforms.
 - For Android, we use the C++ network interface to call the noticeHttpTransaction and the noticeNetworkFailure methods from the New Relic SDK. With that, we start seeing the proper events on the New Relic Mobile UI.
 
