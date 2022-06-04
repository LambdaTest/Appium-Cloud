# Appium Testing On LambdaTest

<p align="center">
<img height="500" src="https://user-images.githubusercontent.com/95698164/171945587-c776c668-8a4e-4d13-bcb5-d8f197f14070.png">
</p>

<p align="center">
  <a href="https://www.lambdatest.com/blog/?utm_source=github&utm_medium=repo&utm_campaign=Appium-Cloud" target="_bank">Blog</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/support/docs/?utm_source=github&utm_medium=repo&utm_campaign=Appium-Cloud" target="_bank">Docs</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/learning-hub/?utm_source=github&utm_medium=repo&utm_campaign=Appium-Cloud" target="_bank">Learning Hub</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/newsletter/?utm_source=github&utm_medium=repo&utm_campaign=Appium-Cloud" target="_bank">Newsletter</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/certifications/?utm_source=github&utm_medium=repo&utm_campaign=Appium-Cloud" target="_bank">Certifications</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.youtube.com/c/LambdaTest" target="_bank">YouTube</a>
</p>
&emsp;
&emsp;
&emsp;

*Appium is a tool for automating native, mobile web, and hybrid applications on iOS, Android, and Windows platforms. It supports iOS native apps written in Objective-C or Swift and Android native apps written in Java or Kotlin. It also supports mobile web apps accessed using a mobile browser (Appium supports Safari on iOS and Chrome or the built-in 'Browser' app on Android). Perform Appium automation tests on [LambdaTest's online cloud](https://www.lambdatest.com/appium-mobile-testing).*

## Table of Contents

* [Languages and Frameworks](#languages-and-frameworks)
* [Desired Capabilities In Appium](#desired-capabilities-in-appium)
* [Testing Locally Hosted Apps](#testing-locally-hosted-apps)
* [Appium Inspector](#appium-inspector)
* [APIs For App Testing](#apis-for-app-testing)
* [Migrate Appium Tests](#migrate-appium-tests)

## Pre-requisites

1. You will need a LambdaTest username and access key. To obtain your access credentials, [purchase a plan](https://billing.lambdatest.com/billing/plans) or access the [automation dashboard](https://appautomation.lambdatest.com/).
2. Ensure you have Appium’s [Java client library](https://github.com/appium/java-client) installed.
3. Access to an **Android** app (.apk or .aab file) or an **iOS** app (.ipa file).

**Tip:** If you do not have any **.apk** or **.ipa** file, you can run your sample tests on LambdaTest by using our sample :link: [Android app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or sample :link: [iOS app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa).

## Run Your First Test

### **Upload Your Application**

Upload your **_iOS_** application (.ipa file) or **_android_** application (.apk file) to the LambdaTest servers using our **REST API**. You need to provide your **Username** and **AccessKey** in the format `Username:AccessKey` in the **cURL** command for authentication. Make sure to add the path of the **appFile** in the cURL request. Here is an example cURL request to upload your app using our REST API:

**For macOS/Linux:**

```js
curl -u "shantanuw:abcdefghijklmnopqrstuvwxyz" \
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \
--form 'name="Android_App"' \
--form 'appFile=@"/Users/shantanuwali/Desktop/LT_Java_Appium/proverbial_android.apk"'
```

**For Windows:**

```js
curl -u "shantanuw:abcdefghijklmnopqrstuvwxyz" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -F "appFile=@"/Users/shantanuwali/Desktop/LT_Java_Appium/proverbial_android.apk""
```

**Using App URL:**

**For macOS/Linux:**

```js
curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \
--form 'name="Android_App"' \
--form 'url="https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk"'
```

**For Windows:**

```js
curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \
-X POST "https://manual-api.lambdatest.com/app/upload/realDevice" \
-d "{\"url\":\"https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk\", \
\"name\":\"sample.apk\"'
```

**Info Note:**

Response of above cURL will be a **JSON** object containing the `App URL` of the format - <lt://APP123456789123456789> and will be used in the next step.

### **Write Your Automation Script**

1. Write your automation script in the client language of your choice from the ones [supported by Appium](https://appium.io/downloads.html). An automation script for the sample applications have been provided below. You can clone the automation code in Java for the sample app from our [GitHub repository](https://github.com/LambdaTest/LT_Java_Appium).

Here is a sample automation script in Java for the sample app downloaded above. Ensure to update the `app_url`, `username` and `accesskey` in the below code.

<Tabs className="docs__val">
  <TabItem value="android" label="Android" default>

```java
import io.appium.java_client.AppiumDriver;
import io.appium.java_client.MobileBy;
import io.appium.java_client.MobileElement;
import io.appium.java_client.android.AndroidElement;
import org.openqa.selenium.remote.DesiredCapabilities;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import java.net.URL;
import java.util.List;

public class AndroidApp {

    public static String userName = "username"; //Enter your LT Username here
    public static String accessKey = "accesskey"; //Enter your LT AccessKey here

    public String gridURL = "@mobile-hub.lambdatest.com/wd/hub";

    String DeviceValue;
    String versionValue;
    String PlatformValue;


    @org.testng.annotations.Parameters(value = {"device", "version", "platform"})
    public AndroidApp(String device, String version, String platform) {
        try {
            DeviceValue = device;
            versionValue = version;
            PlatformValue = platform;
            DesiredCapabilities capabilities = new DesiredCapabilities();
            capabilities.setCapability("build","ParallelSample Android");
            capabilities.setCapability("name",platform+" "+device+" "+version);
            capabilities.setCapability("deviceName", device);
            capabilities.setCapability("platformVersion",version);
            capabilities.setCapability("platformName", platform);
            capabilities.setCapability("isRealMobile", true);
            //AppURL (Create from Wikipedia.apk sample in project)
            capabilities.setCapability("app", "app url"); //Enter your app URL from previous step here
            capabilities.setCapability("deviceOrientation", "PORTRAIT");
            capabilities.setCapability("console", true);
            capabilities.setCapability("network", true);
            capabilities.setCapability("visual", true);
            capabilities.setCapability("devicelog", true);

            String hub = "https://" + userName + ":" + accessKey + gridURL;
            AppiumDriver driver = new AppiumDriver(new URL(hub), capabilities);

            MobileElement color = (MobileElement) driver.findElementById("com.lambdatest.proverbial:id/color");
            //Changes color
            color.click();
            //Back to black color
            color.click();

            MobileElement text = (MobileElement) driver.findElementById("com.lambdatest.proverbial:id/Text");
            //Changes the text to proverbial
            text.click();

            //toast is visible
            MobileElement toast = (MobileElement) driver.findElementById("com.lambdatest.proverbial:id/toast");
            toast.click();

            //notification is visible
            MobileElement notification = (MobileElement) driver.findElementById("com.lambdatest.proverbial:id/notification");
            notification.click();

            //Open the geolocation page
            MobileElement geo = (MobileElement) driver.findElementById("com.lambdatest.proverbial:id/geoLocation");
            geo.click();
            Thread.sleep(5000);

            //takes back to home page
            MobileElement home = (MobileElement) driver.findElementByAccessibilityId("Home");
            home.click();

            //Takes to speed test page
            MobileElement speedtest = (MobileElement) driver.findElementById("com.lambdatest.proverbial:id/speedTest");
            speedtest.click();
            Thread.sleep(5000);
            MobileElement el10 = (MobileElement) driver.findElementByXPath("/hierarchy/android.widget.FrameLayout/android.widget.LinearLayout/android.widget.FrameLayout/android.view.ViewGroup/android.widget.FrameLayout[2]/android.view.ViewGroup/android.widget.RelativeLayout/android.widget.FrameLayout[1]/android.widget.FrameLayout/android.widget.RelativeLayout/android.webkit.WebView/android.webkit.WebView/android.view.View/android.view.View/android.view.View[1]/android.view.View[3]/android.view.View[1]/android.view.View/android.widget.Button");
            el10.click();
            Thread.sleep(25000);


            MobileElement el11 = (MobileElement) driver.findElementByXPath("//android.widget.FrameLayout[@content-desc=\"Home\"]/android.widget.FrameLayout/android.widget.ImageView");
            el11.click();

            //Opens the browser
            MobileElement browser = (MobileElement) driver.findElementByAccessibilityId("Browser");
            browser.click();
            MobileElement el13 = (MobileElement) driver.findElementById("com.lambdatest.proverbial:id/url");
            el13.sendKeys("www.lambdatest.com");
            MobileElement el14 = (MobileElement) driver.findElementById("com.lambdatest.proverbial:id/find");
            el14.click();
            driver.quit();


        } catch (Exception t) {
            System.out.println();

        }


    }
}
```

</TabItem>
<TabItem value="iOS" label="iOS" default>

```java
import io.appium.java_client.AppiumDriver;
import io.appium.java_client.MobileElement;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.remote.DesiredCapabilities;
import java.net.URL;

public class iOSApp {

    public static String userName = "username"; //Enter your LT Username here
    public static String accessKey = "accesskey"; //Enter your LT AccessKey here

    public String gridURL = "@mobile-hub.lambdatest.com/wd/hub";

    String DeviceValue;
    String versionValue;
    String PlatformValue;
    AppiumDriver driver;


    @org.testng.annotations.Parameters(value = {"device", "version", "platform"})
    public iOSApp(String device, String version, String platform) {
        try {
            DeviceValue = device;
            versionValue = version;
            PlatformValue = platform;
            DesiredCapabilities capabilities = new DesiredCapabilities();
            capabilities.setCapability("build","ParallelSample iOS");
            capabilities.setCapability("name",platform+" "+device+" "+version);
            capabilities.setCapability("deviceName", device);
            capabilities.setCapability("platformVersion",version);
            capabilities.setCapability("platformName", platform);
            capabilities.setCapability("isRealMobile", true);
            //AppURL (Create from proverbial.ipa sample in project)
            capabilities.setCapability("app", "app url"); //Enter your app URL from previous step here
            capabilities.setCapability("deviceOrientation", "PORTRAIT");
            capabilities.setCapability("console", true);
            capabilities.setCapability("network", true);
            capabilities.setCapability("visual", true);
            capabilities.setCapability("devicelog", true);
            //capabilities.setCapability("geoLocation", "HK");

            String hub = "https://" + userName + ":" + accessKey + gridURL;
            driver = new AppiumDriver(new URL(hub), capabilities);

            MobileElement color = (MobileElement) driver.findElementByAccessibilityId("Colour");
            //Changes color
            color.click();
            //Back to black color
            color.click();

            MobileElement text = (MobileElement) driver.findElementByAccessibilityId("Text");
            //Changes the text to proverbial
            text.click();

            //toast is visible
            MobileElement toast = (MobileElement) driver.findElementByAccessibilityId("Toast");
            toast.click();

            //notification is visible
            MobileElement notification = (MobileElement) driver.findElementByAccessibilityId("Notification");
            notification.click();

            //Open the geolocation page
            MobileElement geo = (MobileElement) driver.findElementByAccessibilityId("GeoLocation");
            geo.click();
            Thread.sleep(5000);

            //Takes back
            driver.navigate().back();

            //Takes to speed test page
            MobileElement speedtest = (MobileElement) driver.findElementByAccessibilityId("Speed Test");
            speedtest.click();
            Thread.sleep(5000);
            MobileElement el10 = (MobileElement) driver.findElementByAccessibilityId("start speed test - connection type multi");
            el10.click();
            Thread.sleep(25000);

            driver.navigate().back();

            //Opens the browser
            MobileElement browser = (MobileElement) driver.findElementByAccessibilityId("Browser");
            browser.click();
            Thread.sleep(3000);

            MobileElement el4 = (MobileElement) driver.findElementByAccessibilityId("Search");
            el4.click();
            el4.sendKeys("Lambdatest");

            ((JavascriptExecutor) driver).executeScript("lambda-status=passed");
            driver.quit();


        } catch (Exception t) {
            System.out.println();
            ((JavascriptExecutor) driver).executeScript("lambda-status=failed");
            driver.quit();

        }


    }
}
```

</TabItem>
</Tabs>

2. Create `.XML` file in order to run your test and define device capabilities. Please find sample code below for the same.

<Tabs className="docs__val">
  <TabItem value="androidXML" label="Android" default>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE suite SYSTEM "http://testng.org/testng-1.0.dtd">
<suite thread-count="100" name="Mobile" parallel="tests">


    <test name="AppTest 1">
        <parameter name="version" value="11"/>
        <parameter name="platform" value="Android"/>
        <parameter name="device" value="Galaxy S21 Ultra 5G"/>
        <classes>
            <class name="AndroidApp"/>
        </classes>
    </test>

    <test name="AppTest 2">
        <parameter name="version" value="11"/>
        <parameter name="platform" value="Android"/>
        <parameter name="device" value="Galaxy S21"/>
        <classes>
            <class name="AndroidApp"/>
        </classes>
    </test>
</suite>
```

</TabItem>

<TabItem value="iOSXML" label="iOS" default>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE suite SYSTEM "http://testng.org/testng-1.0.dtd">
<suite thread-count="100" name="Mobile" parallel="tests">


    <test name="iOSApp 1">
        <parameter name="version" value="14"/>
        <parameter name="platform" value="iOS"/>
        <parameter name="device" value="iPhone 11"/>
        <classes>
            <class name="iOSApp"/>
        </classes>
    </test>

    <test name="iOSApp 2">
        <parameter name="version" value="14"/>
        <parameter name="platform" value="iOS"/>
        <parameter name="device" value="iPhone 12 Pro"/>
        <classes>
            <class name="iOSApp"/>
        </classes>
    </test>
</suite>
```

</TabItem>
</Tabs>

### **Execute Your Test Case**

Debug and run your code. Run `iOSApp.java` or `AndroidApp.java` in your editor.

### **View Test Execution**

Once you have run your tests, you can view the test execution along with logs. You will be able to see the test cases passing or failing. You can view the same at [LambdaTest Automation](https://accounts.lambdatest.com/login).

## More About Desired Capabilities

Sample Capabilities for both android and iOS are mentioned below -
<Tabs className="docs__val">
<TabItem value="androidCaps" label="Android" default>

```java
{
    "deviceName": "Galaxy Tab S4",
    "platformName": "android",
    "platformVersion": "10",
    "app": "App_url",
    "visual": True,
    "console": True,
    "deviceOrientation": "PORTRAIT",
    "build": "new-12",
    "isRealMobile": True,
}
```

</TabItem>
<TabItem value="iOSCaps" label="iOS" default>

```
{
    "deviceName": "iPhone 12 Mini",
    "platformName": "ios",
    "platformVersion": "14",
    "app": "App_url",
    "isRealMobile": True,
    "visual": True,
    "console": True,
    "build": "lt-web-4",
    "network": True,
}
```

</TabItem>
</Tabs>

## Additional Capability Reference Guide

- A more Detailed Capability Guide (PDF) is available [here](https://prod-mobile-artefacts.lambdatest.com/assets/docs/LambdaTest+App+Automation+Capability+Reference+Guide.pdf).

# Languages And Frameworks 

Here is a list of languages and frameworks that are supported by the LambdaTest to run Appium automation tests on [LambdaTest Real Device Cloud Platform](https://www.lambdatest.com/real-device-cloud).

| Java | PHP | Ruby | C# | Python | JavaScript |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| [JUnit](https://github.com/LambdaTest/LT-appium-java-junit) | [PHP](https://github.com/LambdaTest/LT-appium-php) | [Cucumber](https://github.com/LambdaTest/LT-appium-ruby-cucumber) | [C#](https://github.com/LambdaTest/LT-appium-CSharp) | [Behave](https://github.com/LambdaTest/LT-appium-python-behave) | [WebdriverIO](https://github.com/LambdaTest/LT-appium-nodejs-webdriverio) |
|   |   |   |   | [Robot](https://github.com/LambdaTest/LT-appium-python-robot) |   | 

We support all languages and frameworks that are compatible with Appium, so in case your favorite isn't in the table. Don't worry, you can still run the test. **[Contact Us](https://www.lambdatest.com/contact-us)** for any help.

**Note:** We are preparing documentation for more frameworks. If you want us to prioritize documentation of your preferred framework then feel free to give us a **shout**.

# Desired Capabilities In Appium

> **Note:** Mandatory fields are marked with asterisk \*

| KEY                  | VALUES                                                                                                                                                                   | CAPABILITY DESCRIPTION                                                                                                                                                                                                                                                                                                                                                        |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| \*user               | TYPE: STRING                                                                                                                                                             | Your LT username.                                                                                                                                                                                                                                                                                                                                                             |
| \*accessKey          | TYPE: STRING                                                                                                                                                             | Your LT Access Key.                                                                                                                                                                                                                                                                                                                                                           |
| build                | TYPE: STRING <br/> DEFAULT: Untitled <br/> `build=iOS Small Run`                                                                                                         | You can group your tests like a job containing multiple tests.                                                                                                                                                                                                                                                                                                                |
| name                 | TYPE: STRING <br/> DEFAULT: TestID of the Test. Incase the Name is not passed. <br/> `name=iphone 6 Small Run`                                                           | Name of your test.                                                                                                                                                                                                                                                                                                                                                            |
| project              | Will remain blank in case 'project' is not passed in capability. <br/> `project=Small Run`                                                                               | You can group your builds like a project containing multiple jobs.                                                                                                                                                                                                                                                                                                            |
| \*deviceName         | TYPE: STRING <br/> `iPhone 13`                                                                                                                                           | Name of the device.                                                                                                                                                                                                                                                                                                                                                           |
| \*platformName       | TYPE: STRING <br/> `ios`                                                                                                                                                 | Name of the OS.                                                                                                                                                                                                                                                                                                                                                               |
| \*platformVersion    | TYPE: STRING <br/> `14`                                                                                                                                                  | OS version.                                                                                                                                                                                                                                                                                                                                                                   |
| \*app                | TYPE: STRING <br/> `app=lt://APP100201061631704657918380`                                                                                                                | Accepts App URL returned after uploading an app on the LambdaTest servers.                                                                                                                                                                                                                                                                                                    |
| queueTimeout         | TYPE: STRING <br/> DEFAULT: 600 <br/> `queueTimeout=300`                                                                                                                 | This capability can be used to modify the Queue timeout value within a range. queueTimeout Range : 300-900.                                                                                                                                                                                                                                                                   |
| idleTimeout          | TYPE: STRING <br/> DEFAULT: 120 <br/> `idleTimeout=120`                                                                                                                  | This capability can be used to modify the timeout value.                                                                                                                                                                                                                                                                                                                      |
| visual               | TYPE: BOOLEAN <br/> DEFAULT: FALSE <br/> `visual=TRUE` <br/> OR <br/> `visual=FALSE`                                                                                     | Command by command screenshots will be recorded at each test step. By default the flag is set as off. Note: test execution time will increase if it’s set as ‘true’.                                                                                                                                                                                                          |
| video                | TYPE: BOOLEAN <br/> DEFAULT: TRUE <br/> `video=TRUE` <br/> OR <br/> `video=FALSE`                                                                                        | Video recording of the complete screen.                                                                                                                                                                                                                                                                                                                                       |
| devicelog            | TYPE: BOOLEAN <br/> DEFAULT: TRUE <br/> `devicelog=TRUE` <br/> OR <br/> `devicelog=FALSE`                                                                                | Enable Device logs.                                                                                                                                                                                                                                                                                                                                                           |
| network              | TYPE: BOOLEAN <br/> DEFAULT: TRUE <br/> `network=TRUE` <br/> OR <br/> `network=FALSE`                                                                                    | Enable Network logs.                                                                                                                                                                                                                                                                                                                                                          |
| deviceOrientation    | TYPE: STRING <br/> `deviceOrientation=portrait` <br/> OR <br/> `deviceOrientation=landscape`                                                                             | Change the screen orientation of the device.                                                                                                                                                                                                                                                                                                                                  |
| tunnel               | TYPE: BOOLEAN <br/> `tunnel=TRUE` <br/> OR <br/> `tunnel=FALSE`                                                                                                          | To test local applications with LambdaTest.                                                                                                                                                                                                                                                                                                                                   |
| tunnelName           | TYPE: BOOLEAN <br/> `tunnelName=RabbitHole`                                                                                                                              | Name of the tunnel.                                                                                                                                                                                                                                                                                                                                                           |
| dedicatedProxy       | TYPE: BOOLEAN <br/> `dedicatedProxy=TRUE` <br/> OR <br/> `dedicatedProxy=FALSE`                                                                                          | Dedicated Proxy.                                                                                                                                                                                                                                                                                                                                                              |
| autoGrantPermissions | TYPE: BOOLEAN <br/> `autoGrantPermissions=TRUE` <br/> OR <br/> `autoGrantPermissions=FALSE`                                                                              | Have Appium automatically determine which permissions your app requires and grant them to the app on install. Defaults to false. If noReset is true, this capability doesn't work.                                                                                                                                                                                            |
| autoDismissAlerts    | TYPE: BOOLEAN <br/> `autoDismissAlerts=TRUE` <br/> OR <br/> `autoDismissAlerts=FALSE`                                                                                    | [iOS Only] Appium capability to Dismiss alerts/popups on iOS Devices.                                                                                                                                                                                                                                                                                                         |
| autoAcceptAlerts     | TYPE: BOOLEAN <br/> `autoAcceptAlerts=TRUE` <br/> OR <br/> `autoAcceptAlerts=FALSE`                                                                                      | [iOS Only] Appium capability to Accept alerts/popups on iOS Devices.                                                                                                                                                                                                                                                                                                          |
| newCommandTimeout    | TYPE: STRING <br/> `60`                                                                                                                                                  | How long (in seconds) Appium will wait for a new command from the client before assuming the client quit and ending the session.                                                                                                                                                                                                                                              |
| language             | TYPE: STRING <br/> `fr`                                                                                                                                                  | Language to set for iOS (XCUITest driver only) and Android.                                                                                                                                                                                                                                                                                                                   |
| locale               | TYPE: STRING <br/> `fr_CA, CA`                                                                                                                                           | Locale to set for iOS (XCUITest driver only) and Android. fr_CA format for iOS. CA format (country name abbreviation) for Android.                                                                                                                                                                                                                                            |
| noReset              | TYPE: BOOLEAN <br/> `true`                                                                                                                                               | Don't reset app state before this session. See [here](http://appium.io/docs/en/writing-running-appium/other/reset-strategies/index.html) for more details.                                                                                                                                                                                                                    |
| automationName       | TYPE: BOOLEAN <br/> DEFAULT: Appium <br/> `automationName = Appium`                                                                                                      | Which automation engine to use. Note : Set as False in the App Automation Code, so can't be changed. Appium (default), or UiAutomator2, Espresso, or UiAutomator1 for Android, or XCUITest or Instruments for iOS, or YouiEngine for application built with YouiEngine.                                                                                                       |
| eventTimings         | TYPE: BOOLEAN <br/> DEFAULT: False <br/> `true`                                                                                                                          | Enable or disable the reporting of the timings for various Appium-internal events (e.g., the start and end of each command, etc.). To enable, use true. The timings are then reported as events property on response to querying the current session. See the event timing docs for the the structure of this response.                                                       |
| geoLocation          | TYPE: STRING <br/> `fr`                                                                                                                                                  | Allows you to simulate mobile behavior from different locations by selecting IP addresses hosted in multiple countries around the world.                                                                                                                                                                                                                                      |
| otherApps            | TYPE: ARRAY OF STRINGS <br/> DEFAULT: [ ] or Empty Array <br/> `"otherApps":` <br/> `["lt://APP1002211081648217405891389",` <br/> `"lt://APP1002211081648217429465823"]` | "Accepts list of App URL returned after uploading an app on the LambdaTest servers. <br/> Conditions to be satisfied:<br/>1. App should also be passed if “otherApps” is passed.<br/> 2. Length of app URL <br/>array <= 3.<br/>3. At max 3 other apps can be installed.<br/>4. App should not be present inside 'otherApp' array.<br/>5. No duplicated in ‘otherApp’ array." |

> Got any questions?
> Please reach out at our **24x7 Chat Support** or you could also mail us at [support@lambdatest.com](https://support.lambdatest.com/).

# Testing Locally Hosted Apps

Using the LambdaTest tunnel, you can test locally and privately hosted apps across various real Android and iOS devices on the LambdaTest Appium test automation platform. LambdaTest tunnel uses protocols like **Web Socket, HTTPS, SSH (Secure Shell)** and more to let you build a secure and unique tunnel connection between your local system and LambdaTest cloud servers.

In this documentation, learn how to configure LambdaTest tunnel to test locally or privately hosted apps while performing mobile app automation.

To test apps locally, you will need to configure:

1. Connection with LambdaTest tunnel.

2. Test scripts to run via LambdaTest tunnel.

## Setting Up Connection With LambdaTest Tunnel

Shown below are the steps to configure the connection with LambdaTest tunnel.

1. Download the binary file based on your operating system.

- Windows **[64 Bit](https://downloads.lambdatest.com/tunnel/v3/windows/64bit/LT_Windows.zip) | [32 Bit](https://downloads.lambdatest.com/tunnel/v3/windows/32bit/LT_Windows.zip)**
- macOS **[64 Bit](https://downloads.lambdatest.com/tunnel/v3/mac/64bit/LT_Mac.zip) | [32 Bit](https://downloads.lambdatest.com/tunnel/v3/mac/32bit/LT_Mac.zip)**
- Linux **[64 Bit](https://downloads.lambdatest.com/tunnel/v3/linux/64bit/LT_Linux.zip) | [32 Bit](https://downloads.lambdatest.com/tunnel/v3/linux/32bit/LT_Linux.zip)**

2. Extract the downloaded binary file.

3. Navigate to the Command Prompt and point to the directory/folder where you extracted the binary file.

4. Run the below command in the terminal.

```js
./LT --user {user's login email} --key {user's access key} --tunnelName {user's tunnel name}
```

## Configuring Test Scripts

After configuring the connection with LambdaTest tunnel, you will need to set the capability `tunnel` to `True`.

| Key    | Values     | Description          | Desired Capability |
| ------ | ---------- | -------------------- | ------------------ |
| tunnel | true/false | Configure the tunnel | `"tunnel" : True,` |

You can also add the `tunnel` capability using LambdaTest Capability Generator.

> In case you have any questions or need any additional information, drop them at our **24X7 Chat Support** or mail us directly at support@lambdatest.com.

# Appium Inspector

A **GUI inspector** for mobile apps and more, powered by a (separately installed) **Appium server**. Appium Inspector is an Appium client (like WebdriverIO, Appium's Java client, Appium's Python client, etc) with a User Interface. We can use the interface for specifying Appium Server Version, Setting Capabilities. Once the Appium Server is up & running with the App, we can interact with elements and run other Appium Commands.

By the end of this topic, you will be able to:

1. Upload your Application to LambdaTest Server & Receive the Unique App URL.
2. Run the Test using the Unique App URL.

## Instructions

### Step 1: Upload your Application.

Upload your **_iOS_** application (.ipa file) or **_android_** application (.apk file) to the LambdaTest servers using our **REST API**. You need to provide your **Username** and **AccessKey** in the format `Username:AccessKey` in the **cURL** command for authentication. Make sure to add the path of the **appFile** in the cURL request. Here is an example cURL request to upload your app using our REST API:

**Using App File:**

**For iOS:**
```js
curl -u "shantanuw:abcdefghijklmnopqrstuvwxyz" \
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \
--form 'name="Android_App"' \
--form 'url="https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk"'
```

**For Windows:**
```js
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -F "appFile=@"/Users/macuser/Downloads/proverbial_android.apk"'
```

**Using App URL:**

**For macOS/Linux:**
```js
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" \
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \
--form 'name="Android_App"' \
--form 'url="https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk"'
```

**For Windows:**
```js
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -d "url\":\"https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk\",\"name\":\"sample.apk\"'
```

**Tip:**

- If you do not have any **.apk** or **.ipa** file, you can run your sample tests on LambdaTest by using our sample :link: [Android app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or sample :link: [iOS app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa).
- Response of above cURL will be a **JSON** object containing the `App URL` of the format - <lt://APP123456789123456789> and will be used in the next step.

### Step 2: Start a Session on Appium Inspector

Start the Appium Inspector & Select LambdaTest from the list of Cloud Test Providers.

### Step 3: Configure your Credentials

Enter in your UserName & Access Key. You may find the credentials available on [LambdaTest Dashboard](https://appautomation.lambdatest.com/)

### Step 4: Configure Desired Capabilities & Start the Session

Configure LambdaTest capabilities in the desired capabilities tab on Appium inspector. Use the unique app URL obtained in Step 1 to set the app capability Value. A list of all the capabilities supported by LambdaTest is available [here](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/)

Alternatively, we can also go to our [capabilities generator](https://www.lambdatest.com/capabilities-generator/beta/index.html) and generate the Capability Representation using GUI.

<p align="center">
<img height="500" src="https://user-images.githubusercontent.com/95698164/171989140-ce22d5e5-dbe8-4835-8503-6fdd7b8e6493.png">
</p>

Once this is complete, you can now run the test by clicking on start session. Once you start the session, a video recording along with detailed information and logs of the test run will be available on the [LambdaTest Dashboard](https://appautomation.lambdatest.com/build).

<p align="center">
<img height="500" src="https://user-images.githubusercontent.com/95698164/171989186-ec6d03da-6a0f-45f3-b37d-d654ec04513a.png">
</p>

> **Got any questions?**<br/>
> Please reach out at our **24x7 Chat Support** or you could also mail us at [support@lambdatest.com](https://support.lambdatest.com/).

# APIs For App Testing

In this documentation, we look at some APIs that will help you optimize your mobile app testing workflow. If you are performing live or automated app testing, you can use these APIs to fetch and delete the apps. 

## Fetching The Apps

To fetch the list of your uploaded apps along with their App IDs, run the below cURL command.

```js
curl --location --request GET 'https://YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY@manual-api.lambdatest.com/app/data?type=ios&level=user'
```

Shown below is the response to the above cURL request.

```js
{"metaData":{"type":"ios","total":1},
"data":[{
  "app_id":"APP100245789181570497850",
  "name":"proverbial_ios.ipa",
  "type":"ios",
  "updated_at":"2022-05-10T11:19:30.000Z",
  "shared":false,
  "source":"web-client"
  }]
  ```

## Deleting The Apps

To delete your uploded apps, run the below cURL command. 

```js
curl --location --request DELETE 'https://YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY@manual-api.lambdatest.com/app/delete' \
--header 'Content-Type: application/json' \
--data-raw '{
    "appIds" : "APPID1,APPID2"
}'
```

Shown below is the response to the above cURL request.

```js
{"message":"Deleted successfully."}
```

>That’s all! In case you have any questions or need any additional information, you could reach out at our **24X7 Chat Support** or mail us directly at [support@lambdatest.com](https://support.lambdatest.com/).

# Migrate Appium Tests

## From Local Grid, BrowserStack Or SauceLabs To LambdaTest

LambdaTest offers an online Appium automation grid to perform App automation. The online Appium Grid is available on local grid, BrowserStack, SauceLabs and LambdaTest. Therefore, you can effortlessly migrate your current Appium automation scripts (or suites) from local grid, Sauce Labs or BrowserStack to LambdaTest.

In this documentation, we look at how to leverage LambdaTest cloud for App automation and migrate your test scripts (or test suites) from your local grid, Sauce labs or BrowserStack. You can use LambdaTest's desired capabilities in your tests, authenticate your test session, and execute tests on the cloud.

## Introduction

Migrating your current local grid, BroweseStack or Sauce Labs tests to LambdaTest requires a few tweaks in your code. In this guide, we'll look at how to leverage LambdaTest's desired capabilities in your tests, authenticate your test session, and execute tests on our cloud browsers.

### Changes In The Test Script

To move from the local grid, BroweseStack or Sauce Labs to LambdaTest, you need to make some changes to your test suites such as authentication, desired capabilities etc.

## Migration From BrowserStack And SauceLabs

### Authentication

Firstly, you need to change the authentication in the configuration settings of your test suite. For running tests on LambdaTest Appium Grid, you need to have a valid `user_name` and `access_key` to perform tests on our cloud Grid. In case you don’t have an account on LambdaTest, visit the LambdaTest **signup** page and create a new account.

The following are the changes in the parameters:

- Username
- Access Key

You can find the `Username` and `Access Key` in the **LambdaTest Profile Section** of the **Automation Dashboard**.

<p align="center">
<img height="500" src="https://user-images.githubusercontent.com/95698164/171991090-3f9257dc-70d4-4db6-af93-89d2ad319f75.png">
</p>

When migrating from BrowserStack or SauceLabs to LambdaTest, you need to make the following changes in the existing code:

1. UserName
2. AccessKey
3. Hub URL
4. Desired Capabilities

Here is a side-by-side comparison of each of the fields that we have highlighted above:

| Property  | Type   | BrowserStack                                    | SauceLabs                                     | LambdaTest                                    |
| --------- | ------ | ----------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
| UserName  | String | UserName to access Appium Grid on BrowserStack  | UserName to access Appium Grid on Sauce Labs  | UserName to access Appium Grid on LambdaTest  |
| AccessKey | String | AccessKey to access Appium Grid on BrowserStack | AccessKey to access Appium Grid on Sauce Labs | AccessKey to access Appium Grid on LambdaTest |
| Hub URL   | String | @hub-cloud.browserstack.com/wd/hub              | ondemand.us-west-1.saucelabs.com/wd/hub       | @hub.lambdatest.com/wd/hub                    |

For a Python-based implementation, here are the changes in the script for the authentication process.

**BrowserStack**

```python
userName = "BrowserStack_UserName"
accessKey = "BrowserStack_AccessKey"
```

**SauceLabs**

```python
userName = "SAUCE_USERNAME"
accessKey = "SAUCE_ACCESS_KEY"
```

**LambdaTest**

```python
userName = "LambdaTest_UserName"
accessKey = "LambdaTest_AccessKey"
```

### Changes To The Hub URL

Now you have to modify the hub URL in your test suite's configuration settings. The Hub URL is of the String type and specifies the Hub location to which the Appium tests will be routed for execution.

For a Python-based implementation, here are the changes in the script for Hub URL.

**BrowserStack**

```
@hub-cloud.browserstack.com/wd/hub
```

**SauceLabs**

```
@ondemand.us-west-1.saucelabs.com/wd/hub
```

**LambdaTest**

```
@mobile-hub.lambdatest.com/wd/hub
```

### Desired Capability Generator

Capabilities generator allows you to specify the desired capabilities (or capabilities), which are configuration options that allow you to specify the following:

1. Device
2. Operating system

You can also select other advanced options available in the LambdaTest Capabilities Generator.

For the migration, we have taken Java-based Appium tests. Below are the screenshots of the capability generator of BrowserStack and LambdaTest.

#### **BrowserStack**

<p align="center">
<img height="500" src="https://user-images.githubusercontent.com/95698164/171991137-8f109d2b-8979-4800-9212-6e6e657b6331.png">
</p>

#### **Sauce Labs**

<p align="center">
<img height="400" src="https://user-images.githubusercontent.com/95698164/171991167-0d8a1a0c-bac8-4eca-98b0-ac1edb05295d.png">
</p>

#### **LambdaTest**

<p align="center">
<img height="400" src="https://user-images.githubusercontent.com/95698164/171991187-2e9be366-3e9f-4d65-a6dd-e3fd08ad26e4.png">
</p>

The comparison of the capabilities generated by BrowserStack and LambdaTest capabilities generator:

| Capabilities     | BrowserStack | SauceLabs       | LambdaTest      |
| ---------------- | ------------ | --------------- | --------------- |
| Device           | device       | deviceName      | deviceName      |
| Operating System | os_version   | platformVersion | platformVersion |

The following is an overview of the comparison of Desired Capabilities for the Java language:

**BrowserStack**

```js
//demo.java
DesiredCapabilities capabilities = new DesiredCapabilities();
capabilities.setCapability("os_version", "9.0");
capabilities.setCapability("device", "Google Pixel 3");
capabilities.setCapability("browserstack.appium_version", "1.21.0");
```

**SauceLabs**

```java
//demo.java
MutableCapabilities caps = new MutableCapabilities();
caps.setCapability("platformName", "Android");
caps.setCapability("browserName", "Chrome");
caps.setCapability("appium:deviceName", "Google Pixel 3 GoogleAPI Emulator");
caps.setCapability("appium:platformVersion", "12.0");
MutableCapabilities sauceOptions = new MutableCapabilities();
sauceOptions.setCapability("appiumVersion", "1.21.0");
caps.setCapability("sauce:options", sauceOptions);
```

**LambdaTest**

```js
//demo.java
DesiredCapabilities capabilities = new DesiredCapabilities();
capabilities.setCapability("build", "your build name");
capabilities.setCapability("name", "your test name");
capabilities.setCapability("platformName", "Android");
capabilities.setCapability("deviceName", "Google Pixel 3");
capabilities.setCapability("isRealMobile", true);
capabilities.setCapability("platformVersion","9");
```

### Example: Migration To LambdaTest

Let's look an example that shows the entire migration process. The test scenario is to open a Wikipedia app that search the term ‘lambdatest’. The following test runs on Google Pixel 3 running Android 11.

#### **BrowserStack**

```python

from appium import webdriver
from appium.webdriver.common.mobileby import MobileBy
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time

userName = "BrowserStack_UserName"
accessKey = "BrowserStack_AccessKey"

desired_caps = {
    "build": "Python Android",
    "device": "Google Pixel 3",
    "app": "<app_url>"
}

driver = webdriver.Remote("https://" + userName + ":" + accessKey + "@hub-cloud.browserstack.com/wd/hub", desired_caps)

search_element = WebDriverWait(driver, 30).until(
    EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID, "Search Wikipedia"))
)
search_element.click()

search_input = WebDriverWait(driver, 30).until(
    EC.element_to_be_clickable((MobileBy.ID, "org.wikipedia.alpha:id/search_src_text"))
)
search_input.send_keys("BrowserStack")
time.sleep(5)

search_results = driver.find_elements_by_class_name("android.widget.TextView")
assert(len(search_results) > 0)

driver.quit()
```

#### **SauceLabs**

```python
#samplewikipedia.py
import ssl

try:
    _create_unverified_https_context = ssl._create_unverified_context
except AttributeError:
    # Legacy Python that doesn't verify HTTPS certificates by default
    pass
else:
    # Handle target environment that doesn't support HTTPS verification
    ssl._create_default_https_context = _create_unverified_https_context

from threading import Thread
import time
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities
from selenium.common.exceptions import TimeoutException
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from appium.webdriver.common.mobileby import MobileBy
from appium import webdriver

# This array 'caps' defines the capabilities browser, device and OS combinations where the test will run

caps = {
    caps['platformName'] = 'Android'
    caps['browserName'] = 'Chrome'
    caps['appium:deviceName'] = 'Google Pixel 3a GoogleAPI Emulator'
    caps['appium:platformVersion'] = '11.0'
    caps['sauce:options'] = {}
    caps['sauce:options']['appiumVersion'] = '1.20.2'
}

# run_session function searches for 'saucelabs' on google.com

def run_session(desired_cap):
    driver = webdriver.Remote(

        command_executor="https://SAUCE_USERNAME:SAUCE_ACCESS_KEY@ondemand.us-west-1.saucelabs.com/wd/hub",
        desired_capabilities=desired_cap)

    # driver.get("https://www.ifconfig.me")
    # time.sleep(10)
    # Test case for the saucelabs sample Android app.
# If you have uploaded your app, update the test case here.
    search_element = WebDriverWait(driver, 30).until(
        EC.element_to_be_clickable(
            (MobileBy.ACCESSIBILITY_ID, "Search Wikipedia"))
    )
    search_element.click()
    search_input = WebDriverWait(driver, 30).until(
        EC.element_to_be_clickable(
            (MobileBy.ID, "org.wikipedia.alpha:id/search_src_text"))
    )
    search_input.send_keys("saucelabs")
    time.sleep(5)
    search_results = driver.find_elements_by_class_name(
        "android.widget.TextView")
    assert(len(search_results) > 0)

# Invoke driver.quit() after the test is done to indicate that the test is completed.
    driver.quit()

# The Thread function takes run_session function and each set of capability from the caps array as an argument to run each session in parallel
for cap in caps:
    Thread(target=run_session, args=(cap,)).start()
```

#### **LambdaTest**

```python
#samplewikipedia.py

import ssl

try:
    _create_unverified_https_context = ssl._create_unverified_context
except AttributeError:
    # Legacy Python that doesn't verify HTTPS certificates by default
    pass
else:
    # Handle target environment that doesn't support HTTPS verification
    ssl._create_default_https_context = _create_unverified_https_context

from threading import Thread
import time
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities
from selenium.common.exceptions import TimeoutException
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from appium.webdriver.common.mobileby import MobileBy
from appium import webdriver


# This array 'caps' defines the capabilities browser, device and OS combinations where the test will run
caps = [

    {
        "deviceName": "Google Pixel 3",
        "platformName": "Android",
        "platformVersion": "11",
        "app": "<lt_app_url>",
        "isRealMobile": True,
        "deviceOrientation": "PORTRAIT",
        "build": "Demo",
           },
]
# run_session function searches for 'lambtest' on google.com


def run_session(desired_cap):
    driver = webdriver.Remote(
        # hub.mobile-dev-1.dev.lambdatest.io/wd/hub",
        command_executor="https://LT_USERNAME:LT_ACCESS_KEY@mobile-hub.lambdatest.com/wd/hub",
        desired_capabilities=desired_cap)

    # driver.get("https://www.ifconfig.me")
    # time.sleep(10)
    # Test case for the lambdatest sample Android app.
# If you have uploaded your app, update the test case here.
    search_element = WebDriverWait(driver, 30).until(
        EC.element_to_be_clickable(
            (MobileBy.ACCESSIBILITY_ID, "Search Wikipedia"))
    )
    search_element.click()
    search_input = WebDriverWait(driver, 30).until(
        EC.element_to_be_clickable(
            (MobileBy.ID, "org.wikipedia.alpha:id/search_src_text"))
    )
    search_input.send_keys("lambdatest")
    time.sleep(5)
    search_results = driver.find_elements_by_class_name(
        "android.widget.TextView")
    assert(len(search_results) > 0)

# Invoke driver.quit() after the test is done to indicate that the test is completed.
    driver.quit()


# The Thread function takes run_session function and each set of capability from the caps array as an argument to run each session in parallel
for cap in caps:
    Thread(target=run_session, args=(cap,)).start()
```

The majority of the implementation, as shown above, remains unchanged. Only changes to the infrastructure are made (i.e. instead of BrowserStack, the app automation tests would be run on LambdaTest).

Let's analyze what has changed from the implementation point of view.

**BrowserStack**

```python

from appium import webdriver
from appium.webdriver.common.mobileby import MobileBy
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time

userName = "BrowserStack_UserName"
accessKey = "BrowserStack_AccessKey"

desired_caps = {
    "build": "Python Android",
    "device": "Google Pixel 3",
    "app": "<app_url>"
}

driver = webdriver.Remote("https://" + userName + ":" + accessKey + "@hub-cloud.browserstack.com/wd/hub", desired_caps)
```

**SauceLabs**

```python

from threading import Thread
import time
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities
from selenium.common.exceptions import TimeoutException
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from appium.webdriver.common.mobileby import MobileBy
from appium import webdriver


# This array 'caps' defines the capabilities browser, device and OS combinations where the test will run

caps = {
    caps['platformName'] = 'Android'
    caps['browserName'] = 'Chrome'
    caps['appium:deviceName'] = 'Google Pixel 3a GoogleAPI Emulator'
    caps['appium:platformVersion'] = '11.0'
    caps['sauce:options'] = {}
    caps['sauce:options']['appiumVersion'] = '1.20.2'
}


# run_session function searches for 'saucelabs' on google.com


def run_session(desired_cap):
    driver = webdriver.Remote(

        command_executor="https://SAUCE_USERNAME:SAUCE_ACCESS_KEY@ondemand.us-west-1.saucelabs.com/wd/hub",
        desired_capabilities=desired_cap)

```

**LambdaTest**

```python
from threading import Thread
import time
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities
from selenium.common.exceptions import TimeoutException
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from appium.webdriver.common.mobileby import MobileBy
from appium import webdriver

caps = [

    {
        "deviceName": "Google Pixel 3",
        "platformName": "Android",
        "platformVersion": "11",
        "app": "<lt_app_url>",
        "build": "Demo",
           },
]

def run_session(desired_cap):
    driver = webdriver.Remote(command_executor="https://LT_USERNAME:LT_ACCESS_KEY@mobile-hub.lambdatest.com/wd/hub", desired_capabilities=desired_cap)

```

We have discussed how to migrate from Sauce Labs or BrowserStack to LambdaTest. Let’s explore how to migrate from the local grid to the cloud-based Appium grid.

## Migration From Local Grid

### Desired Capabilities In Appium

Appium's Desired Capabilities are a collection of key-value pairs wrapped inside a JSON object. These key-value pairs request the Appium server for the required test automation session.

Let’s say you want to run an app test in Python on SAMSUNG GALAXY TAB S4 running ANDROID 10. You can define the same in the form of capability as given below.

```python
caps = [

    {
        "deviceName": "Galaxy Tab S4",
        "platformName": "Android",
        "platformVersion": "10",
        "build": "Demo",
    },
]
```

### Running Tests On LambdaTest Appium Grid

To begin, change the authentication in your test suite's configuration settings. To run the tests on LambdaTest Appium Grid, you need a valid user name and access key. If you were already performing tests on your local grid, you will need to modify your test script to initialize an Appium driver along with your desired capabilities.

Pass the capabilities to `@hub.lambdatest.com/wd/hub` with your LambdaTest authentication details, and you are done. Here is the sample Python test script.

```python
#samplewikipedia.py

import ssl

try:
    _create_unverified_https_context = ssl._create_unverified_context
except AttributeError:
    # Legacy Python that doesn't verify HTTPS certificates by default
    pass
else:
    # Handle target environment that doesn't support HTTPS verification
    ssl._create_default_https_context = _create_unverified_https_context

from threading import Thread
import time
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities
from selenium.common.exceptions import TimeoutException
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from appium.webdriver.common.mobileby import MobileBy
from appium import webdriver


# This array 'caps' defines the capabilities of the browser, device, and OS combinations where the test will run
caps = [

    {
        "deviceName": "Galaxy Tab S4",
        "platformName": "Android",
        "platformVersion": "10",
        "app": "lt://APP10051525539885437397",
        "isRealMobile": True,
        "deviceOrientation": "PORTRAIT",
        "visual": True,
        "console": True,
        "build": "Demo",
           },
]
# run_session function searches for 'lambdatest' on google.com


def run_session(desired_cap):
    driver = webdriver.Remote(
        # hub.mobile-dev-1.dev.lambdatest.io/wd/hub",
        command_executor="https://LT_USERNAME:LT_ACCESS_KEY@mobile-hub.lambdatest.com/wd/hub",
        desired_capabilities=desired_cap)

    # driver.get("https://www.ifconfig.me")
    # time.sleep(10)
    # Test case for the lambdatest sample Android app.
# If you have uploaded your app, update the test case here.
    search_element = WebDriverWait(driver, 30).until(
        EC.element_to_be_clickable(
            (MobileBy.ACCESSIBILITY_ID, "Search Wikipedia"))
    )
    search_element.click()
    search_input = WebDriverWait(driver, 30).until(
        EC.element_to_be_clickable(
            (MobileBy.ID, "org.wikipedia.alpha:id/search_src_text"))
    )
    search_input.send_keys("lambdatest")
    time.sleep(5)
    search_results = driver.find_elements_by_class_name(
        "android.widget.TextView")
    assert(len(search_results) > 0)

# Invoke driver.quit() after the test is done to indicate that the test is completed.
    driver.quit()


# The Thread function takes run_session function and each set of capability from the caps array as an argument to run each session in parallel
for cap in caps:
    Thread(target=run_session, args=(cap,)).start()

```

> That’s all! In case you have any questions or need any additional information, you could reach out at our **24X7 Chat Support** or mail us directly at [support@lambdatest.com](https://support.lambdatest.com/).

## Documentation & Resources :books:
      
Visit the following links to learn more about LambdaTest's features, setup and tutorials around test automation, mobile app testing, responsive testing, and manual testing.

* [LambdaTest Documentation](https://www.lambdatest.com/support/docs/?utm_source=github&utm_medium=repo&utm_campaign=Appium-Cloud)
* [LambdaTest Blog](https://www.lambdatest.com/blog/?utm_source=github&utm_medium=repo&utm_campaign=Appium-Cloud)
* [LambdaTest Learning Hub](https://www.lambdatest.com/learning-hub/?utm_source=github&utm_medium=repo&utm_campaign=Appium-Cloud)    

## LambdaTest Community :busts_in_silhouette:

The [LambdaTest Community](https://community.lambdatest.com/) allows people to interact with tech enthusiasts. Connect, ask questions, and learn from tech-savvy people. Discuss best practises in web development, testing, and DevOps with professionals from across the globe 🌎

## What's New At LambdaTest ❓

To stay updated with the latest features and product add-ons, visit [Changelog](https://changelog.lambdatest.com/) 
      
## About LambdaTest

[LambdaTest](https://www.lambdatest.com) is a leading test execution and orchestration platform that is fast, reliable, scalable, and secure. It allows users to run both manual and automated testing of web and mobile apps across 3000+ different browsers, operating systems, and real device combinations. Using LambdaTest, businesses can ensure quicker developer feedback and hence achieve faster go to market. Over 500 enterprises and 1 Million + users across 130+ countries rely on LambdaTest for their testing needs.    

### Features

* Run Selenium, Cypress, Puppeteer, Playwright, and Appium automation tests across 3000+ real desktop and mobile environments.
* Real-time cross browser testing on 3000+ environments.
* Test on Real device cloud
* Blazing fast test automation with HyperExecute
* Accelerate testing, shorten job times and get faster feedback on code changes with Test At Scale.
* Smart Visual Regression Testing on cloud
* 120+ third-party integrations with your favorite tool for CI/CD, Project Management, Codeless Automation, and more.
* Automated Screenshot testing across multiple browsers in a single click.
* Local testing of web and mobile apps.
* Online Accessibility Testing across 3000+ desktop and mobile browsers, browser versions, and operating systems.
* Geolocation testing of web and mobile apps across 53+ countries.
* LT Browser - for responsive testing across 50+ pre-installed mobile, tablets, desktop, and laptop viewports
    
[<img height="53" width="200" src="https://user-images.githubusercontent.com/70570645/171866795-52c11b49-0728-4229-b073-4b704209ddde.png">](https://accounts.lambdatest.com/register)

      
## We are here to help you :headphones:

* Got a query? we are available 24x7 to help. [Contact Us](support@lambdatest.com)
* For more info, visit - [LambdaTest](https://www.lambdatest.com/?utm_source=github&utm_medium=repo&utm_campaign=Appium-Cloud)
