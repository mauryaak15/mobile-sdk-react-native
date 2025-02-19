# Refiner Mobile SDK integration

## React Native

![npm](https://img.shields.io/npm/v/refiner-react-native)


### 1) Installation

`$ npm install refiner-react-native --save`


#### iOS

- Run command `pod install` in your ios directory


### 2) Usage

Visit our [documentation](https://refiner.io/docs/kb/mobile-sdk/mobile-sdk-reference/) for more information about how to use the SDK methods.

#### Initialization & Configuration

Initialize the SDK in your application with the needed configuration parameters.

```javascript
import RNRefiner from 'refiner-react-native';

RNRefiner.initialize("PROJECT_ID");
```

#### Identify User

Call `Identify User` to create or update user traits in Refiner.

```javascript
var userTraits = { email: "hello@hello.com", a_number: 123, a_date: "2022-16-04 12:00:00" };
RNRefiner.identifyUser("USER_ID", userTraits, "LOCALE");
```

#### Track Event

`Track Event` lets you track user events. Tracked events can be used to create user segments and target audiences in Refiner.

```javascript
RNRefiner.trackEvent("EVENT_NAME");
```

#### Track Screen

`Track Screen` provides to track screen that user is currently on. Screen information can be used to launch surveys in specific areas of your app.

```javascript
RNRefiner.trackScreen("SCREEN_NAME");
```

#### Show Form

If you use the Manual Trigger Event for your survey, you need to call `Show Form` whenever you want to launch the survey.

```javascript
RNRefiner.showForm("FORM_UUID", false);
```

The second parameter is a boolean value to `force` the display of the survey and bypass all targeting rules which were set in the Refiner dashboard. Setting the parameter to `true` can be helpful when testing the SDK. In production, the parameter should be set to `false`.

```javascript
RNRefiner.showForm("FORM_UUID", true);
```

#### Attach Contextual Data

Attach contextual data to the survey submissions with `attachToResponse`. Set `null` to remove the contextual data. 

```javascript
var contextualData = { some_data: "hello", some_more_data: "hello again" };
RNRefiner.attachToResponse(contextualData);
```

#### Reset User

Call `Reset User` to reset the user identifier previously set through `Identify User`. We recommend calling this method when the user logs out from your app.

```javascript
RNRefiner.resetUser();
```
