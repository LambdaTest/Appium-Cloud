# Languages And Frameworks Supported By LambdaTest For App Automation

Here is a list of languages and frameworks that are supported by the LambdaTest to run Appium automation tests on [LambdaTest Real Device Cloud Platform](https://www.lambdatest.com/real-device-cloud).

<div className="lt_row lt_framework_list_row">
    <div className="lt_col lt_framework_wrapper"> 
      <img loading="lazy" src={require('../assets/images/getting-started/java-icon.webp').default} alt="Java" width="200" height="200" className="language-icon"/>
      <ul className="lt_framework_list">
        <li>
          <a className="lt_primary" href="/docs/appium-java/">Java</a>
        </li>
        <li>
          <a href="/docs/appium-java-junit/">JUnit</a>
        </li>
      </ul>
    </div>
    <div className="lt_col lt_framework_wrapper">
      <img loading="lazy" src={require('../assets/images/getting-started/php-icon.webp').default} alt="PHP" width="2500" height="1250" className="language-icon"/>
      <ul className="lt_framework_list">
        <li>
          <a className="lt_primary" href="/docs/php-with-selenium-running-php-automation-scripts-on-lambdatest-selenium-grid/">PHP</a>
        </li>
        </ul>
    </div>
    <div className="lt_col lt_framework_wrapper">
       <img loading="lazy" src={require('../assets/images/getting-started/ruby-icon.webp').default} alt="Ruby" width="200" height="200" className="language-icon"/>
      <ul className="lt_framework_list">
        <li>
          <a className="lt_primary" href="/docs/appium-ruby/">Ruby</a>
        </li>
        <li>
          <a href="/docs/appium-ruby-cucumber/">Cucumber</a>
        </li>
      </ul>
    </div>
    <div className="lt_col lt_framework_wrapper">
     <img loading="lazy" src={require('../assets/images/getting-started/c-sharp-icon.webp').default} alt="C#" width="200" height="200" className="language-icon"/>
      <ul className="lt_framework_list">
        <li>
          <a className="lt_primary" href="/docs/appium-csharp/">C#</a>
        </li>
      </ul>
    </div>
    <div className="lt_col lt_framework_wrapper">
      <img loading="lazy" src={require('../assets/images/getting-started/python-icon.webp').default} alt="Python" width="200" height="200" className="language-icon"/>
      <ul className="lt_framework_list">
      <li>
          <a className="lt_primary" href="/docs/appium-python/">Python</a>
        </li>
        <li>
          <a href="/docs/appium-python-behave/">Behave</a>
        </li>
        <li>
          <a href="/docs/appium-python-robot/">Robot</a>
        </li>
      </ul>
    </div>
    <div className="lt_col lt_framework_wrapper">
       <img loading="lazy" src={require('../assets/images/getting-started/color-js.webp').default} alt="Javascript" width="181" height="200" className="language-icon"/>
      <ul className="lt_framework_list">
        <li>
          <a className="lt_primary" href="/docs/appium-nodejs/">JavaScript</a>
        </li>
        <li>
          <a href="/docs/appium-nodejs-webdriverio/">WebDriverIO</a>
        </li>
      </ul>
    </div>
  </div>
  <div className="lt-framework-list-footer">
    <p>We support all languages and frameworks that are compatible with Appium, so in case your favorite isn't in the table.<br/>Don't worry, you can still run the test. **Contact Us** for any help.</p>
  </div>

Note: We are preparing documentation for more frameworks. If you want us to prioritize documentation of your preferred framework then feel free to give us a **shout**.

# Java
## Tutorial To Run Your First Test On LambdaTest

In this topic, you will learn how to configure and run your **Java** automation testing scripts with **Appium** on **LambdaTest Real Device Cloud platform**.

## Objective

By the end of this topic, you will be able to:

1. Run a sample automation script of **Java** for application testing with **Appium** on **LambdaTest**.
2. Learn more about Desired Capabilities for Appium testing.
3. Explore advanced features of LambdaTest.

Sample Repo: All the code samples in this documentation can be found in the :link: [LambdaTest's Repository on GitHub](https://github.com/LambdaTest/LT-appium-java). You can either download or clone the repository to quickly run your tests.

## Pre-requisites

Before you can start performing App automation testing with Appium, you would need to follow these steps:

- Ensure you have the [Java client library](https://github.com/appium/java-client) installed for Selenium and Appium.
- Download and install **Maven** following the steps from [the official website](https://maven.apache.org/). Maven can also be installed easily on **Linux/MacOS** using [**Homebrew**](https://brew.sh/) package manager.

### Clone The Sample Project

**Step-1:** Clone the LambdaTest’s :link: [LT-appium-java](https://github.com/LambdaTest/LT-appium-java) repository and navigate to the code directory as shown below:

```bash
git clone https://github.com/LambdaTest/LT-appium-java
cd LT-appium-java
```

### Setting Up Your Authentication

Make sure you have your LambdaTest credentials with you to run test automation scripts on LambdaTest. To obtain your access credentials, [purchase a plan](https://billing.lambdatest.com/billing/plans) or access the [Automation Dashboard](https://appautomation.lambdatest.com/).

**Step-2:** Set LambdaTest `Username` and `Access Key` in environment variables.

**For Linux/macOS:**

`{`export LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()}"` \\
`export LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"`
 
**For Windows:**

  `{`set LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()}" \`
`set LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"`
 
### Upload Your Application

**Step-3:** Upload your **_iOS_** application (.ipa file) or **_android_** application (.apk file) to the LambdaTest servers using our **REST API**. You need to provide your **Username** and **AccessKey** in the format `Username:AccessKey` in the **cURL** command for authentication. Make sure to add the path of the **appFile** in the cURL request. Here is an example cURL request to upload your app using our REST API:

**Using App File:**

**Linux/macOS:**

`{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \\

--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\

--form 'name="Android_App"' \\

--form 'appFile=@"/Users/macuser/Downloads/proverbial_android.apk"' 
`}`

**Windows:**

`{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -F "appFile=@"/Users/macuser/Downloads/proverbial_android.apk""`}`

**Using App URL:**

**Linux/macOS:**

`{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \\

--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\

--form 'name="Android_App"' \\

--form 'url="https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk"'`}`

**Windows:**

`{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -d "{\"url\":\"https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk\",\"name\":\"sample.apk\"}"`}`

Tip: 

- If you do not have any **.apk** or **.ipa** file, you can run your sample tests on LambdaTest by using our sample :link: [Android app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or sample :link: [iOS app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa).
- Response of above cURL will be a **JSON** object containing the `App URL` of the format - <lt://APP123456789123456789> and will be used in the next step.

## Run Your First Test

### Sample Test With Java

Here are sample JUnit automation scripts used to run on an Android app and iOS app. Ensure to update the `app_url` in the code scripts before running the tests.

<Tabs className="docs__val">
<TabItem value="android" label="Android" default>

```java title="vanilla_android.java"
import io.appium.java_client.AppiumDriver;
import io.appium.java_client.MobileBy;
import io.appium.java_client.MobileElement;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.remote.DesiredCapabilities;
import org.openqa.selenium.remote.RemoteWebDriver;
import java.net.MalformedURLException;
import java.net.URL;

public class vanilla_android {
    public static String userName = System.getenv("LT_USERNAME") == null ? "LT_USERNAME"  //Add username here
            : System.getenv("LT_USERNAME");
    public static String accessKey = System.getenv("LT_ACCESS_KEY") == null ? "LT_ACCESS_KEY" //Add accessKey here
            : System.getenv("LT_ACCESS_KEY");

    private static AppiumDriver driver;

    public static void main(String args[]) throws MalformedURLException, InterruptedException {

        try {
            DesiredCapabilities capabilities = new DesiredCapabilities();
            capabilities.setCapability("deviceName", "Galaxy S20");
            capabilities.setCapability("platformVersion", "11");
            capabilities.setCapability("platformName", "Android");
            capabilities.setCapability("isRealMobile", true);
            capabilities.setCapability("app", "lt://APP100202491650550026383902"); //Enter your app url
            capabilities.setCapability("deviceOrientation", "PORTRAIT");
            capabilities.setCapability("build", "Java Vanilla - iOS");
            capabilities.setCapability("name", "Sample Test Java");
            capabilities.setCapability("console", true);
            capabilities.setCapability("network", false);
            capabilities.setCapability("visual", true);
            capabilities.setCapability("devicelog", true);

            driver = new AppiumDriver(new URL("https://" +userName + ":" + accessKey + "@beta-hub.lambdatest.com/wd/hub"), capabilities);

            MobileElement color = (MobileElement) driver.findElement(MobileBy.id("com.lambdatest.proverbial:id/color"));
            color.click();

            MobileElement text = (MobileElement) driver.findElement(MobileBy.id("com.lambdatest.proverbial:id/Text"));
            //Changes the text to proverbial
            text.click();

            //toast is visible
            MobileElement toast = (MobileElement) driver.findElement(MobileBy.id("com.lambdatest.proverbial:id/toast"));
            toast.click();

            //notification is visible
            MobileElement notification = (MobileElement) driver.findElement(MobileBy.id("com.lambdatest.proverbial:id/notification"));
            notification.click();

            //Open the geolocation page
            MobileElement geo = (MobileElement) driver.findElement(MobileBy.id("com.lambdatest.proverbial:id/geoLocation"));
            geo.click();
            Thread.sleep(5000);

            //takes back to home page
            MobileElement el3 = (MobileElement) driver.findElementByAccessibilityId("Home");

            driver.navigate().back();
            Thread.sleep(2000);

            //Takes to speed test page
            MobileElement speedtest = (MobileElement) driver.findElement(MobileBy.id("com.lambdatest.proverbial:id/speedTest"));
            speedtest.click();
            Thread.sleep(5000);

            driver.navigate().back();

            //Opens the browser
            MobileElement browser = (MobileElement) driver.findElement(MobileBy.AccessibilityId("Browser"));
            browser.click();

            MobileElement url = (MobileElement) driver.findElement(MobileBy.id("com.lambdatest.proverbial:id/url"));
            url.sendKeys("https://www.lambdatest.com");
            MobileElement find = (MobileElement) driver.findElement(MobileBy.id("com.lambdatest.proverbial:id/find"));
            find.click();

        } catch (AssertionError a) {
            ((JavascriptExecutor) driver).executeScript("lambda-status=failed");
            a.printStackTrace();
        }
// The driver.quit statement is required, otherwise the test continues to execute, leading to a timeout.
        driver.quit();
    }
    }
```

</TabItem>

<TabItem value="ios" label="iOS" default>

```java title="vanilla_ios.java"
import io.appium.java_client.AppiumDriver;
import io.appium.java_client.MobileBy;
import io.appium.java_client.MobileElement;
import io.appium.java_client.ios.IOSDriver;

import org.openqa.selenium.remote.DesiredCapabilities;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

import java.net.URL;

public class vanilla_ios {

    public static String userName = System.getenv("LT_USERNAME") == null ? "LT_USERNAME"  //Add username here
            : System.getenv("LT_USERNAME");
    public static String accessKey = System.getenv("LT_ACCESS_KEY") == null ? "LT_ACCESS_KEY" //Add accessKey here
            : System.getenv("LT_ACCESS_KEY");

    public static final String URL = "https://" + userName + ":" + accessKey + "@beta-hub.lambdatest.com/wd/hub";
    public static IOSDriver driver = null;

    public static void main(String[] args) throws Exception {

       try {
            DesiredCapabilities caps = new DesiredCapabilities();
            caps.setCapability("platformVersion", "15");
            caps.setCapability("deviceName", "iPhone 12");
            caps.setCapability("isRealMobile", true);
            caps.setCapability("app", "lt://APP100202491650549951124834"); //Enter your app url
            caps.setCapability("platformName", "iOS");
            caps.setCapability("build", "Java Vanilla - iOS");
            caps.setCapability("name", "Sample Test Java");
            caps.setCapability("devicelog", true);
            caps.setCapability("network", true);


        driver = new IOSDriver(new URL("https://" + userName + ":" + accessKey + "@beta-hub.lambdatest.com/wd/hub"), caps);


            Thread.sleep(2000);

            //Changes color

            driver.findElement(MobileBy.id("color")).click();
            Thread.sleep(1000);

            //Back to black color
            driver.navigate().back();

            Thread.sleep(1000);

            //Changes the text to proverbial
            driver.findElement(MobileBy.id("Text")).click();
            Thread.sleep(1000);

            //toast is visible
            driver.findElement(MobileBy.id("toast")).click();
            Thread.sleep(1000);

            //notification is visible
            driver.findElement(MobileBy.id("notification")).click();
            Thread.sleep(2000);

            //Open the geolocation page
            driver.findElement(MobileBy.id("geoLocation")).click();
            Thread.sleep(4000);
            driver.navigate().back();
            Thread.sleep(1000);

            //Takes to speed test page
            driver.findElement(MobileBy.id("speedTest")).click();
            Thread.sleep(5000);
            driver.navigate().back();
            Thread.sleep(1000);

            //Opens the browser
            MobileElement browser = (MobileElement) driver.findElementByAccessibilityId("Browser");
            browser.click();
            Thread.sleep(3000);

           WebDriverWait el7 =  new WebDriverWait(driver, 30);
           el7.until(ExpectedConditions.elementToBeClickable(MobileBy.id("url")));
           driver.findElementById("url").sendKeys("https://www.lambdatest.com/");

            //Clicks on the text box
            WebDriverWait el = new WebDriverWait(driver,90);
            MobileElement el4 = (MobileElement) driver.findElementByAccessibilityId("find");
            el.until(ExpectedConditions.elementToBeClickable(el4));
            el4.click();
            el4.sendKeys("Lambdatest");

            //((JavascriptExecutor) driver).executeScript("lambda-status=passed");
            driver.quit();

        } catch (Exception t) {
           System.out.println(t);
           driver.quit();

       }
    }
}
```

</TabItem>

</Tabs>

### Configuring Your Test Capabilities

**Step-4:** You can update your custom capabilities in test scripts. In this sample project, we are passing platform name, platform version, device name and app url (generated earlier) along with other capabilities like build name and test name via capabilities object. The capabilities object in the sample code are defined as:

<Tabs className="docs__val">
<TabItem value="android-config" label="Android" default>

```java
DesiredCapabilities capabilities = new DesiredCapabilities();
            capabilities.setCapability("deviceName", "Galaxy S20");
            capabilities.setCapability("platformVersion", "11");
            capabilities.setCapability("platformName", "Android");
            capabilities.setCapability("isRealMobile", true);
            capabilities.setCapability("app", "YOUR_APP_URL"); //Enter your app url
            capabilities.setCapability("deviceOrientation", "PORTRAIT");
            capabilities.setCapability("build", "Java Vanilla - iOS");
            capabilities.setCapability("name", "Sample Test Java");
            capabilities.setCapability("console", true);
            capabilities.setCapability("network", false);
            capabilities.setCapability("visual", true);
            capabilities.setCapability("devicelog", true);
```

</TabItem>

<TabItem value="ios-config" label="iOS" default>

```java
DesiredCapabilities caps = new DesiredCapabilities();
            caps.setCapability("platformVersion", "15");
            caps.setCapability("deviceName", "iPhone 12");
            caps.setCapability("isRealMobile", true);
            caps.setCapability("app", "YOUR_APP_URL"); //Enter your app url
            caps.setCapability("platformName", "iOS");
            caps.setCapability("build", "Java Vanilla - iOS");
            caps.setCapability("name", "Sample Test Java");
            caps.setCapability("devicelog", true);
            caps.setCapability("network", true);
```

</TabItem>

</Tabs>

Note:

- You must add the generated **APP_URL** to the `"app"` capability in the config file.
- You can generate capabilities for your test requirements with the help of our inbuilt **[Capabilities Generator tool](https://www.lambdatest.com/capabilities-generator/beta/index.html)**. A more Detailed Capability Guide is available [here](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/).

### Executing The Test

**Step-5:** Execute the following commands to install the required dependencies:

```bash
mvn clean install
```

**Step-6:** The tests can be executed in the terminal using the following command:

**Android:**

```bash
mvn compile exec:java -Dexec.mainClass=vanilla_android -Dexec.classpathScope="test"
```

**iOS:**

```bash
mvn compile exec:java -Dexec.mainClass=vanilla_ios -Dexec.classpathScope="test"
```

Info: Your test results would be displayed on the test console (or command-line interface if you are using terminal/cmd) and on the :link: [LambdaTest App Automation Dashboard](https://appautomation.lambdatest.com/build).

## Additional Links

- [Advanced Configuration for Capabilities](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/)
- [How to test locally hosted apps](https://www.lambdatest.com/support/docs/testing-locally-hosted-pages/)
- [How to integrate LambdaTest with CI/CD](https://www.lambdatest.com/support/docs/integrations-with-ci-cd-tools/)

