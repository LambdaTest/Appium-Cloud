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

# 1. Java With Appium
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

`{`export LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()`}"` \\
`export LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"`
 
**For Windows:**

  `{`set LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()}" \`
`set LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"`
 
### Upload Your Application

**Step-3:** Upload your **_iOS_** application (.ipa file) or **_android_** application (.apk file) to the LambdaTest servers using our **REST API**. You need to provide your **Username** and **AccessKey** in the format `Username:AccessKey` in the **cURL** command for authentication. Make sure to add the path of the **appFile** in the cURL request. Here is an example cURL request to upload your app using our REST API:

**Using App File:**

**Linux/macOS:**

`{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()`}" \\`

`--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\`

`--form 'name="Android_App"' \\`

`--form 'appFile=@"/Users/macuser/Downloads/proverbial_android.apk"' 
`}`

**Windows:**

`{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -F "appFile=@"/Users/macuser/Downloads/proverbial_android.apk""`}`

**Using App URL:**

**Linux/macOS:**

`{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()`}" \\`

`--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\`

`--form 'name="Android_App"' \\`

`--form 'url="https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk"'`}`

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

# 1.1 JUnit With Appium

# Tutorial To Run Your First Test On LambdaTest

In this topic, you will learn how to configure and run your **JUnit** automation testing scripts with **Appium** on **LambdaTest Real Device Cloud platform**.

## Objective

By the end of this topic, you will be able to:

1. Run a sample automation script of **JUnit** for application testing with **Appium** on **LambdaTest**.
2. Run test cases in **parallel** using JUnit with Appium to reduce build times.
3. Learn more about Desired Capabilities for Appium testing.
4. Explore advanced features of LambdaTest.

**Sample Repo:** All the code samples in this documentation can be found in the :link: [LambdaTest's Repository on GitHub](https://github.com/LambdaTest/LT-appium-java-junit). You can either download or clone the repository to quickly run your tests.

## Pre-requisites

Before you can start performing App automation testing with Appium, you would need to follow these steps:

- Make sure you have Appium’s [Java client library](https://github.com/appium/java-client) installed.

### Clone The Sample Project

**Step-1:** Clone the LambdaTest’s :link: [LT-appium-java-junit](https://github.com/LambdaTest/LT-appium-java-junit) repository and navigate to the code directory as shown below:

```bash
git clone https://github.com/LambdaTest/LT-appium-java-junit
cd LT-appium-java-junit
```

### Setting Up Your Authentication

Make sure you have your LambdaTest credentials with you to run test automation scripts on LambdaTest. To obtain your access credentials, [purchase a plan](https://billing.lambdatest.com/billing/plans) or access the [Automation Dashboard](https://appautomation.lambdatest.com/).

**Step-2:** Set LambdaTest `Username` and `Access Key` in environment variables.

**For Linux/macOS:**
  {`export LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()}" \\
export LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"
 
 **For Windows:**
  {`set LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()}" \`
set LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"
  
### Upload Your Application

**Step-3:** Upload your **_iOS_** application (.ipa file) or **_android_** application (.apk file) to the LambdaTest servers using our **REST API**. You need to provide your **Username** and **AccessKey** in the format `Username:AccessKey` in the **cURL** command for authentication. Make sure to add the path of the **appFile** in the cURL request. Here is an example cURL request to upload your app using our REST API:

**Using App File:**

**For Linux/macOS:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \\
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\
--form 'name="Android_App"' \\
--form 'appFile=@"/Users/macuser/Downloads/proverbial_android.apk"' 
`}

**For Windows:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -F "appFile=@"/Users/macuser/Downloads/proverbial_android.apk""`}

**Using App URL:**

**For Linux/macOS:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \\
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\
--form 'name="Android_App"' \\
--form 'url="https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk"'`}

**For Windows:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -d "{\"url\":\"https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk\",\"name\":\"sample.apk\"}"`}

**Tip:**

- If you do not have any **.apk** or **.ipa** file, you can run your sample tests on LambdaTest by using our sample :link: [Android app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or sample :link: [iOS app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa).
- Response of above cURL will be a **JSON** object containing the `App URL` of the format - <lt://APP123456789123456789> and will be used in the next step.

## Run Your First Test

### Sample Test With JUnit

Here are sample JUnit automation scripts used to run on an Android app and iOS app. Ensure to update the `app_url` in the code scripts before running the tests.

<Tabs className="docs__val">
<TabItem value="android" label="Android" default>

```java title="android.java"
package com.lambdatest;

import io.appium.java_client.MobileBy;
import org.junit.After;
import org.junit.Before;
import org.junit.Test;
import org.openqa.selenium.remote.DesiredCapabilities;
import org.openqa.selenium.remote.RemoteWebDriver;
import org.openqa.selenium.By;

import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

import java.net.MalformedURLException;
import java.net.URL;

public class android {
    String username = System.getenv("LT_USERNAME") == null ? "LT_USERNAME" //Enter the Username here
            : System.getenv("LT_USERNAME");
    String accessKey = System.getenv("LT_ACCESS_KEY") == null ? "LT_ACCESS_KEY"  //Enter the Access key here
            : System.getenv("LT_ACCESS_KEY");
    public static RemoteWebDriver driver = null;
    public String gridURL = "@beta-hub.lambdatest.com/wd/hub";
    public String status = "passed";
    @Before
    public void setUp() throws Exception {
        DesiredCapabilities capabilities = new DesiredCapabilities();

        capabilities.setCapability("build", "JUNIT Native App automation");
        capabilities.setCapability("name", "Java JUnit Android Pixel 6");
        capabilities.setCapability("platformName", "android");
        capabilities.setCapability("deviceName", "Pixel 6"); //Enter the name of the device here
        capabilities.setCapability("isRealMobile", true);
        capabilities.setCapability("platformVersion","12");
        capabilities.setCapability("app","YOUR_APP_URL"); //Enter the App ID here
        capabilities.setCapability("deviceOrientation", "PORTRAIT");
        capabilities.setCapability("console",true);
        capabilities.setCapability("network",true);
        capabilities.setCapability("visual",true);
        try
        {
            driver = new RemoteWebDriver(new URL("https://" + username + ":" + accessKey + gridURL), capabilities);
        }
        catch (MalformedURLException e)
        {
            System.out.println("Invalid grid URL");
        } catch (Exception e)
        {
            System.out.println(e.getMessage());
        }
    }

    @Test
    public void testSimple() throws Exception
    {
        try
        {
            WebDriverWait wait = new WebDriverWait(driver, 30);
            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("color"))).click();

            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("geoLocation"))).click();;
            Thread.sleep(5000);
            driver.navigate().back();

            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("Text"))).click();

            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("notification"))).click();;

            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("toast"))).click();

            wait.until(ExpectedConditions.elementToBeClickable(By.id("Browser"))).click();;
            Thread.sleep(10000);

            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("url"))).sendKeys("https://www.lambdatest.com/");

            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("find"))).click();
            Thread.sleep(5000);
            driver.navigate().back();

            status="passed";
        }
            catch (Exception e)
             {
                System.out.println(e.getMessage());
                status="failed";
             }
    }
    @After
    public void tearDown() throws Exception
    {
        if (driver != null)
        {
            driver.executeScript("lambda-status=" + status);
            driver.quit();
        }
    }
}
```

</TabItem>

<TabItem value="ios" label="iOS" default>

```java title="ios.java"
package com.lambdatest;

import io.appium.java_client.MobileBy;
import org.junit.After;
import org.junit.Before;
import org.junit.Test;
import org.openqa.selenium.remote.DesiredCapabilities;
import org.openqa.selenium.remote.RemoteWebDriver;
import org.openqa.selenium.By;

import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

import java.net.MalformedURLException;
import java.net.URL;

public class ios {
    String username = System.getenv("LT_USERNAME") == null ? "LT_USERNAME"   //Enter the Username here
            : System.getenv("LT_USERNAME");
    String accessKey = System.getenv("LT_ACCESS_KEY") == null ? "LT_ACCESS_KEY"   //Enter the Access key here
            : System.getenv("LT_ACCESS_KEY");
    public static RemoteWebDriver driver = null;
    public String gridURL = "@beta-hub.lambdatest.com/wd/hub";
    public String status = "passed";
    @Before
    public void setUp() throws Exception {
        DesiredCapabilities capabilities = new DesiredCapabilities();

        capabilities.setCapability("build", "JUNIT Native App automation");
        capabilities.setCapability("name", "Java JUnit iOS iPhone 12");
        capabilities.setCapability("platformName", "ios");
        capabilities.setCapability("deviceName", "iPhone 12");
        capabilities.setCapability("isRealMobile", true);
        capabilities.setCapability("platformVersion","15");
        capabilities.setCapability("app","YOUR_APP_URL"); //Enter the APP_ID here
        capabilities.setCapability("deviceOrientation", "PORTRAIT");
        capabilities.setCapability("console",true);
        capabilities.setCapability("network",true);
        capabilities.setCapability("visual",true);
        try
        {
            driver = new RemoteWebDriver(new URL("https://" + username + ":" + accessKey + gridURL), capabilities);
        }
        catch (MalformedURLException e)
        {
            System.out.println("Invalid grid URL");
        } catch (Exception e)
        {
            System.out.println(e.getMessage());
        }
    }

    @Test
    public void testSimple() throws Exception
    {
        try
        {
            WebDriverWait wait = new WebDriverWait(driver, 30);
            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("color"))).click();

            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("geoLocation"))).click();
            Thread.sleep(5000);
            driver.navigate().back();

            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("Text"))).click();

            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("notification"))).click();

            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("toast"))).click();

            wait.until(ExpectedConditions.elementToBeClickable(By.id("Browser"))).click();
            Thread.sleep(10000);

            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("url"))).sendKeys("https://www.lambdatest.com/");;

            wait.until(ExpectedConditions.elementToBeClickable(MobileBy.id("find"))).click();
            Thread.sleep(5000);
            driver.navigate().back();

            status="passed";
        }
            catch (Exception e)
             {
                System.out.println(e.getMessage());
                status="failed";
             }
    }
    @After
    public void tearDown() throws Exception
    {
        if (driver != null)
        {
            driver.executeScript("lambda-status=" + status);
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

        capabilities.setCapability("build", "JUNIT Native App automation");
        capabilities.setCapability("name", "Java JUnit Android Pixel 6");
        capabilities.setCapability("platformName", "android");
        capabilities.setCapability("deviceName", "Pixel 6"); //Enter the name of the device here
        capabilities.setCapability("isRealMobile", true);
        capabilities.setCapability("platformVersion","12");
        capabilities.setCapability("app","YOUR_APP_URL"); //Enter the App ID here
        capabilities.setCapability("deviceOrientation", "PORTRAIT");
        capabilities.setCapability("console",true);
        capabilities.setCapability("network",true);
        capabilities.setCapability("visual",true);
```

</TabItem>

<TabItem value="ios-config" label="iOS" default>

```java
DesiredCapabilities capabilities = new DesiredCapabilities();

        capabilities.setCapability("build", "JUNIT Native App automation");
        capabilities.setCapability("name", "Java JUnit iOS iPhone 12");
        capabilities.setCapability("platformName", "ios");
        capabilities.setCapability("deviceName", "iPhone 12");
        capabilities.setCapability("isRealMobile", true);
        capabilities.setCapability("platformVersion","15");
        capabilities.setCapability("app","YOUR_APP_URL"); //Enter the APP_ID here
        capabilities.setCapability("deviceOrientation", "PORTRAIT");
        capabilities.setCapability("console",true);
        capabilities.setCapability("network",true);
        capabilities.setCapability("visual",true);
```

</TabItem>

</Tabs>

**Info Note:**

- You must add the generated **APP_URL** to the `"app"` capability in the config file.
- You can generate capabilities for your test requirements with the help of our inbuilt **[Capabilities Generator tool](https://www.lambdatest.com/capabilities-generator/beta/index.html)**. A more Detailed Capability Guide is available [here](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/).

### Executing The Test

**Step-5:** Execute the following commands to install the required dependencies:

```bash
mvn clean
```

**Step-6:** The tests can be executed in the terminal using the following command:

<Tabs className="docs__val">
<TabItem value="android-exec" label="Android" default>

```bash
mvn test android.java
```

</TabItem>

<TabItem value="ios-exec" label="iOS" default>

```bash
mvn test ios.java
```

</TabItem>
</Tabs>

**Info:** Your test results would be displayed on the test console (or command-line interface if you are using terminal/cmd) and on the :link: [LambdaTest App Automation Dashboard](https://appautomation.lambdatest.com/build).

## Additional Links

- [Advanced Configuration for Capabilities](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/)
- [How to test locally hosted apps](https://www.lambdatest.com/support/docs/testing-locally-hosted-pages/)
- [How to integrate LambdaTest with CI/CD](https://www.lambdatest.com/support/docs/integrations-with-ci-cd-tools/)


# 2. NodeJS With Appium
# Tutorial To Run Your First Test On LambdaTest

In this topic, you will learn how to configure and run your **NodeJS** automation testing scripts with **Appium** on **LambdaTest Real Device Cloud platform**.

## Objective

By the end of this topic, you will be able to:

1. Run a sample automation script of **NodeJS** for application testing with **Appium** on **LambdaTest**.
2. Learn more about Desired Capabilities for Appium testing.
3. Explore advanced features of LambdaTest.

**Sample Repo:** All the code samples in this documentation can be found in the :link: [LambdaTest's Repository on GitHub](https://github.com/LambdaTest/LT-appium-nodejs). You can either download or clone the repository to quickly run your tests.

## Pre-requisites

Before you can start performing App automation testing with Appium, you would need to follow these steps:

- Download and install **NodeJS**. You should be having **NodeJS v6** or newer. Click [here](https://nodejs.org/en/) to download.
- Make sure you are using the latest version of **JavaScript**.
- Install **npm** from the official website by clicking [here](https://www.npmjs.com/).

### Clone The Sample Project

**Step-1:** Clone the LambdaTest’s :link: [LT-appium-nodejs](https://github.com/LambdaTest/LT-appium-nodejs) repository and navigate to the code directory as shown below:

```bash
git clone https://github.com/LambdaTest/LT-appium-nodejs
cd LT-appium-nodejs
```

### Setting Up Your Authentication

Make sure you have your LambdaTest credentials with you to run test automation scripts on LambdaTest. To obtain your access credentials, [purchase a plan](https://billing.lambdatest.com/billing/plans) or access the [Automation Dashboard](https://appautomation.lambdatest.com/).

**Step-2:** Set LambdaTest `Username` and `Access Key` in environment variables.

**For Linux/macOS:**

  {`export LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()}" \\
export LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"
 
 **For Windows:**
 
  {`set LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()}" \`
set LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"
  
### Upload Your Application

**Step-3:** Upload your **_iOS_** application (.ipa file) or **_android_** application (.apk file) to the LambdaTest servers using our **REST API**. You need to provide your **Username** and **AccessKey** in the format `Username:AccessKey` in the **cURL** command for authentication. Make sure to add the path of the **appFile** in the cURL request. Here is an example cURL request to upload your app using our REST API:

**Using App File:**

**For Linux/macOS:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \\
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\
--form 'name="Android_App"' \\
--form 'appFile=@"/Users/macuser/Downloads/proverbial_android.apk"' 
`}

**For Windows:**

<CodeBlock className="language-powershell">
{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -F "appFile=@"/Users/macuser/Downloads/proverbial_android.apk""`}

**Using App URL:**

**For Linux/macOS:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \\
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\
--form 'name="Android_App"' \\
--form 'url="https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk"'`}

**For Windows:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -d "{\"url\":\"https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk\",\"name\":\"sample.apk\"}"`}

**Tip:**

- If you do not have any **.apk** or **.ipa** file, you can run your sample tests on LambdaTest by using our sample :link: [Android app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or sample :link: [iOS app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa).
- Response of above cURL will be a **JSON** object containing the `App URL` of the format - <lt://APP123456789123456789> and will be used in the next step.

## Run Your First Test

### Sample Test With NodeJS

To get started, here is an example of sample test on our sample Android App shown below.

```javascript title="android.js"
var wd = require("wd");
var assert = require("assert");
var asserter = wd.asserters;

username =
  process.env.LT_USERNAME == undefined
    ? "username" //Enter the username here
    : process.env.LT_USERNAME;
accesskey =
  process.env.LT_ACCESS_KEY == undefined
    ? "access_key" //Enter the access_key here
    : process.env.LT_ACCESS_KEY;

desired_capabilities = {
  deviceName: "Galaxy S20",
  platformVersion: "11",
  platformName: "android",
  isRealMobile: true,
  app: "lt://", //Enter the app_url here
  visual: true,
  video: true,
};

driver = wd.promiseRemote(
  `https://${username}:${accesskey}@beta-hub.lambdatest.com/wd/hub`
);

driver
  .init(desired_capabilities)
  .then(function () {
    return driver.waitForElementById("color", 10000);
  })
  .then(function (colorButton) {
    return colorButton.click();
  })
  .then(function () {
    return driver.waitForElementById("Text", 10000);
  })
  .then(function (text) {
    text.click();
    return driver.waitForElementById("toast", 10000);
  })
  .then(function (toast) {
    toast.click();
    return driver.waitForElementById("notification", 10000);
  })
  .then(function (notification) {
    notification.click();
    return driver.waitForElementById("geoLocation", 10000);
  })
  .then(function (geoLocation) {
    geoLocation.click();
    return driver.waitForElementById("buttonPage", 10000);
  })
  .then(function (Home) {
    Home.click();
    return driver.waitForElementById("speedTest", 10000);
  })
  .then(function (speedTest) {
    speedTest.click();
    return driver.waitForElementById("webview", 10000);
  })
  .then(function (Browser) {
    Browser.click();
    return driver.waitForElementById("url", 10000);
  })
  .then(function (url) {
    url.type("https://www.lambdatest.com");
    return driver.waitForElementById("find", 10000);
  })
  .then(function (find) {
    find.click();
    driver.quit();
  });
```

### Configuring Your Test Capabilities

**Step-4:** You can update your custom capabilities in the scripts. In our sample script, we are passing platform name, platform version, device name and app url (generated earlier) along with other capabilities like build name and test name via capabilities object. The capabilities object in the sample code for a single test are defined as:

<Tabs className="docs__val">

<TabItem value="ios-config" label="ios.js" default>

```javascript
desired_capabilities = {
  deviceName: "iPhone 12",
  platformVersion: "14",
  platformName: "iOS",
  isRealMobile: true,
  app: "lt://", //Enter the app_url here
  visual: true,
  video: true,
  build: "NodeJS Vanilla - iOS",
  name: "Sample Test - NodeJS",
};
```

</TabItem>
<TabItem value="android-config" label="android.js" default>

```javascript
desired_capabilities = {
  deviceName: "Galaxy S20",
  platformVersion: "11",
  platformName: "android",
  isRealMobile: true,
  app: "lt://", //Enter the app_url here
  visual: true,
  video: true,
  build: "NodeJS Vanilla - Android",
  name: "Sample Test - NodeJS",
};
```

</TabItem>

</Tabs>

**Info Note:**

- You must add the generated **APP_URL** to the `"app"` capability in the config file.
- You can generate capabilities for your test requirements with the help of our inbuilt :link: **[Capabilities Generator tool](https://www.lambdatest.com/capabilities-generator/beta/index.html)**. A more Detailed Capability Guide is available [here :page_facing_up:](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/) .

### Executing The Tests

<Tabs className="docs__val">

<TabItem value="ios" label="iOS" default>

If you are using an **iOS** app, the cURL command will generate an app URL for the corresponding iOS app and install the same for running the tests. You can either use our sample :link: [iOS app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa) or upload your own app as discussed earlier.

**Step-5:** Execute the following command to run your test on LambdaTest platform:

```bash
node android.js
```

</TabItem>

<TabItem value="android" label="Android" default>

If you are using an **android** app, the cURL command will generate an app URL for the corresponding Android app and install the same for running the tests. You can either use our sample :link: [Android app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or upload your own app as discussed earlier.

**Step-5:** Execute the following command to run your test on LambdaTest platform:

```bash
node ios.js
```

</TabItem>

</Tabs>

**Info:** Your test results would be displayed on the test console (or command-line interface if you are using terminal/cmd) and on the :link: [LambdaTest App Automation Dashboard](https://appautomation.lambdatest.com/build).

## Additional Links

- [Advanced Configuration for Capabilities](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/)
- [How to test locally hosted apps](https://www.lambdatest.com/support/docs/testing-locally-hosted-pages/)
- [How to integrate LambdaTest with CI/CD](https://www.lambdatest.com/support/docs/integrations-with-ci-cd-tools/)

# 2.1 WebDriverIO With Appium
# Tutorial To Run Your First Test On LambdaTest

In this topic, you will learn how to configure and run your **WebDriverIO** automation testing scripts with **Appium** on **LambdaTest Real Device Cloud platform**.

## Objective

By the end of this topic, you will be able to:

1. Run a sample automation script of **WebDriverIO** for application testing with **Appium** on **LambdaTest**.
2. Run test cases in **parallel** using WebDriverIO with Appium to reduce build times.
3. Learn more about Desired Capabilities for Appium testing.
4. Explore advanced features of LambdaTest.

**Sample Repo:** All the code samples in this documentation can be found in the :link: [LambdaTest's Repository on GitHub](https://github.com/LambdaTest/LT-appium-nodejs-webdriverio). You can either download or clone the repository to quickly run your tests.

## Pre-requisites

Before you can start performing App automation testing with Appium, you would need to follow these steps:

- Download and install **NodeJS**. You should be having **NodeJS v6** or newer. Click [here](https://nodejs.org/en/) to download.
- Make sure you are using the latest version of **JavaScript**.
- Install **npm** from the official website by clicking [here](https://www.npmjs.com/).

### Clone The Sample Project

**Step-1:** Clone the LambdaTest’s :link: [LT-appium-nodejs-webdriverio](https://github.com/LambdaTest/LT-appium-nodejs-webdriverio) repository and navigate to the code directory as shown below:

```bash
git clone https://github.com/LambdaTest/LT-appium-nodejs-webdriverio
cd LT-appium-nodejs-webdriverio
```

### Setting Up Your Authentication

Make sure you have your LambdaTest credentials with you to run test automation scripts on LambdaTest. To obtain your access credentials, [purchase a plan](https://billing.lambdatest.com/billing/plans) or access the [Automation Dashboard](https://appautomation.lambdatest.com/).

**Step-2:** Set LambdaTest `Username` and `Access Key` in environment variables.

**For Linux/macOS:**

  {`export LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()}" \\
export LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"

**For Windows:**

  {`set LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()}" \`
set LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"
 
### Upload Your Application

**Step-3:** Upload your **_iOS_** application (.ipa file) or **_android_** application (.apk file) to the LambdaTest servers using our **REST API**. You need to provide your **Username** and **AccessKey** in the format `Username:AccessKey` in the **cURL** command for authentication. Make sure to add the path of the **appFile** in the cURL request. Here is an example cURL request to upload your app using our REST API:

**Using App File:**

**For Linux/macOS:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \\
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\
--form 'name="Android_App"' \\
--form 'appFile=@"/Users/macuser/Downloads/proverbial_android.apk"' 
`}

**For Windows:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -F "appFile=@"/Users/macuser/Downloads/proverbial_android.apk""`}

**Using App URL:**

**For Linux/macOS:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \\
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\
--form 'name="Android_App"' \\
--form 'url="https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk"'`}

**For Windows:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -d "{\"url\":\"https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk\",\"name\":\"sample.apk\"}"`}

**Tip:**

- If you do not have any **.apk** or **.ipa** file, you can run your sample tests on LambdaTest by using our sample :link: [Android app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or sample :link: [iOS app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa).
- Response of above cURL will be a **JSON** object containing the `App URL` of the format - <lt://APP123456789123456789> and will be used in the next step.

## Run Your First Test

### Sample Test With WebDriverIO

To get started, here is an example of sample test on our sample Android App shown below. You can write or add your own Appium automation scripts in `specs` directory to run different tests on your app.

```javascript title="/specs/android-test.js"
describe("Proverbial APK", () => {
  it("Changes color", async () => {
    var color = await $("id=color");
    await color.waitForDisplayed({ timeout: 30000 });
    await color.click();
    await color.click();
  });

  it("Changes text", async () => {
    var text = await $("id=Text");
    await text.waitForDisplayed({ timeout: 30000 });
    await text.click();
  });

  it("Toast", async () => {
    var toast = await $("id=toast");
    await toast.waitForDisplayed({ timeout: 30000 });
    await toast.click();
  });

  it("Notification", async () => {
    var nf = await $("id=notification");
    await nf.waitForDisplayed({ timeout: 30000 });
    await nf.click();
  });

  it("Geolocation", async () => {
    var geo = await $("id=geoLocation");
    await geo.waitForDisplayed({ timeout: 30000 });
    await geo.click();

    driver.back();
  });

  it("SpeedTest", async () => {
    var st = await $("id=speedTest");
    await st.waitForDisplayed({ timeout: 30000 });
    await st.click();

    await browser.pause(10000);
    driver.back();
  });

  it("Browser", async () => {
    var browser = await $("id=webview");
    await browser.waitForDisplayed({ timeout: 30000 });
    await browser.click();

    let el7 = await $("id=url");
    await el7.click();
    await el7.setValue("https://www.lambdatest.com/");
    driver.back();
  });
});
```

### Configuring Your Test Capabilities

**Step-4:** You need to update your capabilities in `*.config.js` files. In this sample project, we have provided the examples for running tests on both **Android** and **iOS** apps. You can find the configs for both iOS and Android in the `iOS-sample` and `android-sample` directories correspondingly. We are passing platform name, platform version, device name and app url (generated earlier) along with other capabilities like build name and test name via capabilities object. You need to pass the path of your test script in `specs` object to run your own automation script. The capabilities object in the sample code for a single test are defined as:

<Tabs className="docs__val">

<TabItem value="ios-config" label="ios-single.conf.js" default>

```javascript title="ios/ios-single.conf.js"
exports.config = {
  user: process.env.LT_USERNAME || "YOUR_USERNAME",
  key: process.env.LT_ACCESS_KEY || "YOUR_ACCESS_KEY",

  updateJob: false,
  //highlight-next-line
  specs: ["./../specs/ios-test.js"], //path of your test script
  exclude: [],

  //highlight-start
  capabilities: [
    {
      build: "NodeJS WebDriverIO iOS",
      name: "Sample Test - WebDriverIO",
      isRealMobile: true,
      deviceName: "iPhone 13 Pro",
      platformVersion: "15",
      platformName: "iOS",
      app: "YOUR_APP_URL",
    },
  ],
  //highlight-end

  logLevel: "info",
  coloredLogs: true,
  screenshotPath: "./errorShots/",
  baseUrl: "",
  waitforTimeout: 10000,
  connectionRetryTimeout: 90000,
  connectionRetryCount: 3,
  path: "/wd/hub",
  hostname: "beta-hub.lambdatest.com",
  port: 80,

  framework: "mocha",
  mochaOpts: {
    ui: "bdd",
    timeout: 20000,
  },
};
```

</TabItem>
<TabItem value="android-config" label="android-single.conf.js" default>

```javascript title="android/android-single.conf.js"
exports.config = {
  user: process.env.LT_USERNAME || "YOUR_USERNAME",
  key: process.env.LT_ACCESS_KEY || "YOUR_ACCESS_KEY",

  updateJob: false,
  //highlight-next-line
  specs: ["./../specs/android-test.js"], //path of your test script
  exclude: [],

  //highlight-start
  capabilities: [
    {
      build: "NodeJS WebDriverIO Android",
      name: "Sample Test - WebDriverIO",
      isRealMobile: true,
      platformName: "Android",
      deviceName: "Galaxy S9",
      platformVersion: "10",
      app: "YOUR_APP_URL",
    },
  ],
  //highlight-end

  logLevel: "info",
  coloredLogs: true,
  screenshotPath: "./errorShots/",
  baseUrl: "",
  waitforTimeout: 10000,
  connectionRetryTimeout: 90000,
  connectionRetryCount: 3,
  path: "/wd/hub",
  hostname: "beta-hub.lambdatest.com",
  port: 80,

  framework: "mocha",
  mochaOpts: {
    ui: "bdd",
    timeout: 20000,
  },
};
```

</TabItem>

</Tabs>

**Info Note:**

- You must add the generated **APP_URL** to the `"app"` capability in the config file.
- You can generate capabilities for your test requirements with the help of our inbuilt :link: **[Capabilities Generator tool](https://www.lambdatest.com/capabilities-generator/beta/index.html)**. A more Detailed Capability Guide is available [here :page_facing_up:](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/) .

### Executing The Tests

<Tabs className="docs__val">

<TabItem value="ios" label="iOS" default>

If you are using an **iOS** app, the cURL command will generate an app URL for the corresponding iOS app and install the same for running the tests. You can either use our sample :link: [iOS app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa) or upload your own app as discussed earlier.

**Step-5:** Navigate to the corresponding directory based on your app.

```bash
cd ios
```

**Step-6:** Install the required dependencies using the following command:

```bash
npm i
```

**Step-7:** Execute the following command to run your test on LambdaTest platform:

```bash
npm run single
```

</TabItem>

<TabItem value="android" label="Android" default>

If you are using an **android** app, the cURL command will generate an app URL for the corresponding Android app and install the same for running the tests. You can either use our sample :link: [Android app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or upload your own app as discussed earlier.

**Step-5:** Navigate to the corresponding directory based on your app.

```bash
cd android
```

**Step-6:** Install the required dependencies using the following command:

```bash
npm i
```

**Step-7:** Execute the following command to run your test on LambdaTest platform:

```bash
npm run single
```

</TabItem>

</Tabs>

**Info:** Your test results would be displayed on the test console (or command-line interface if you are using terminal/cmd) and on the :link: [LambdaTest App Automation Dashboard](https://appautomation.lambdatest.com/build).

## Additional Links

- [Advanced Configuration for Capabilities](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/)
- [How to test locally hosted apps](https://www.lambdatest.com/support/docs/testing-locally-hosted-pages/)
- [How to integrate LambdaTest with CI/CD](https://www.lambdatest.com/support/docs/integrations-with-ci-cd-tools/)

# 3. Python With Appium
# # Tutorial To Run Your First Test On LambdaTest

This article will guide you in getting started with configuring and running your Python-based Appium automation test scripts on the **LambdaTest Real Device Cloud Platform**.

## Objective

1.  Set up an environment for testing your Apps using **Python** with **Appium**.
2.  Understand and configure the core capabilities required for your Appium test suite.
3.  Explore the advanced features of LambdaTest.

**Sample repo:** All the code samples in this documentation can be found in the [LambdaTest's Repository](https://github.com/LambdaTest/LT-appium-python) on GitHub. You can either **download** or **clone** the repository to quickly run your tests.

## Pre-requisites

Before you can start performing App automation testing with Appium, you would need to follow these steps:

- Install the latest Python build from the [official website](https://www.python.org/downloads/). We recommend using the latest version.
- Make sure **pip** is installed in your system. You can install **pip** from [here](https://pip.pypa.io/en/stable/installation/).

### Clone The Sample Project

**Step-1:** Clone the LambdaTest’s [LT-appium-python](https://github.com/LambdaTest/Python-UnitTest-Selenium) and navigate to the code directory as shown below:

```bash
git clone https://github.com/LambdaTest/LT-appium-python
cd LT-appium-python
```

### Setting Up Your Authentication

Make sure you have your LambdaTest credentials with you to run test automation scripts on LambdaTest. To obtain your access credentials, [purchase a plan](https://billing.lambdatest.com/billing/plans) or access the [Automation Dashboard](https://appautomation.lambdatest.com/).

**Step-2:** Set LambdaTest `Username` and `Access Key` in environment variables.

**For Linux/macOS:**

  {`export LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()}" \\
export LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"
  
**For Windows:**

  {`set LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()}" \`
set LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"
 
### Upload Your Application

**Step-3:** Upload your **_iOS_** application (.ipa file) or **_android_** application (.apk file) to the LambdaTest servers using our **REST API**. You need to provide your **Username** and **AccessKey** in the format `Username:AccessKey` in the **cURL** command for authentication. Make sure to add the path of the **appFile** in the cURL request. Here is an example cURL request to upload your app using our REST API:

**Using App File:**

**Linux/macOS:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \\
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\
--form 'name="Android_App"' \\
--form 'appFile=@"/Users/macuser/Downloads/proverbial_android.apk"' 
`}

**Windows:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -F "appFile=@"/Users/macuser/Downloads/proverbial_android.apk""`}

**Using App URL:**

**Linux/macOS:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \\
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\
--form 'name="Android_App"' \\
--form 'url="https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk"'`}

**For Windows:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -d "{\"url\":\"https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk\",\"name\":\"sample.apk\"}"`}

**Tip:**

- If you do not have any **.apk** or **.ipa** file, you can run your sample tests on LambdaTest by using our sample :link: [Android app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or sample :link: [iOS app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa).
- Response of above cURL will be a **JSON** object containing the `App URL` of the format - <lt://APP123456789123456789> and will be used in the next step.

## Run Your Sample Test

### Sample Test With Python

An automation script for the sample application available above has been provided here. Ensure to update the `app_url` in the below script before running the test.

<Tabs className="docs__val">

<TabItem value="ios" label="iOS" default>

```python title="ios.py"
from appium import webdriver
from appium.webdriver.common.mobileby import MobileBy
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time
import os

desired_caps = {
    "deviceName":"iPhone 12",
    "platformName":"ios",
    "platformVersion":"14",
    "isRealMobile":True,
    "app":"YOUR_APP_URL",
    "build":"Python Vanilla iOS",
    "name":"Sample Test - Python",
    "network":True,
    "visual":True,
    "video":True
}

def startingTest():
    if os.environ.get("LT_USERNAME") is None:
        username = "username"
    else:
        username = os.environ.get("LT_USERNAME")
    if os.environ.get("LT_ACCESS_KEY") is None:
        accesskey = "accesskey"
    else:
        accesskey = os.environ.get("LT_ACCESS_KEY")

    try:

        driver = webdriver.Remote(desired_capabilities=desired_caps,
                                command_executor="https://"+username+":"+accesskey+"@beta-hub.lambdatest.com/wd/hub")
        time.sleep(3)
        colorElement = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"color")))
        colorElement.click()
        textElement = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"Text")))
        textElement.click()
        toastElement = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"toast")))
        toastElement.click()
        notification = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"notification")))
        notification.click()
        time.sleep(3)
        geolocation = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"geoLocation")))
        geolocation.click()
        time.sleep(5)
        driver.back()
        home = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"Home")))
        home.click()
        speedTest = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"speedTest")))
        speedTest.click()
        time.sleep(5)
        driver.back()
        browser = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"Browser")))
        browser.click()
        url = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"url")))
        url.send_keys("https://www.lambdatest.com")
        find = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBsy.ACCESSIBILITY_ID,"find")))
        find.click()
        driver.quit()
    except:
        driver.quit()

startingTest()
```

</TabItem>

<TabItem value="android" label="Android" default>

```python title="android.py"
from appium import webdriver
from appium.webdriver.common.mobileby import MobileBy
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time
import os

desired_caps = {
    "deviceName":"Galaxy S20",
    "platformName":"Android",
    "platformVersion":"10",
    "app":"YOUR_APP_URL",
    "isRealMobile":True,
    "build":"Python Vanilla Android",
    "name":"Sample Test - Python",
    "network":True,
    "visual":True,
    "video":True
}

def startingTest():
    if os.environ.get("LT_USERNAME") is None:
        username = "username"
    else:
        username = os.environ.get("LT_USERNAME")
    if os.environ.get("LT_ACCESS_KEY") is None:
        accesskey = "accesskey"
    else:
        accesskey = os.environ.get("LT_ACCESS_KEY")

    try:
        driver = webdriver.Remote(desired_capabilities=desired_caps,
            command_executor="https://"+username+":"+accesskey+"@beta-hub.lambdatest.com/wd/hub")
        colorElement = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/color")))
        colorElement.click()

        textElement = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/Text")))
        textElement.click()

        toastElement = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/toast")))
        toastElement.click()

        notification = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/notification")))
        notification.click()

        geolocation = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/geoLocation")))
        geolocation.click()
        time.sleep(5)

        driver.back()

        home = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/buttonPage")))
        home.click()

        speedTest = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/speedTest")))
        speedTest.click()
        time.sleep(5)

        driver.back()

        browser = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/webview")))
        browser.click()

        url = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/url")))
        url.send_keys("https://www.lambdatest.com")

        find = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/find")))
        find.click()
        driver.quit()
    except:
        driver.quit()

startingTest()

```

</TabItem>
</Tabs>

### Configuring Your Test Capabilities

**Step-4:** You can update your custom capabilities in test scripts. In this sample project, we are passing platform name, platform version, device name and app url (generated earlier) along with other capabilities like build name and test name via capabilities object. The capabilities object in the sample code are defined as:

<Tabs className="docs__val">

<TabItem value="ios-config" label="iOS" default>

```python title="iOS(.ipa)"
 desired_caps = {
    "deviceName":"iPhone 12",
    "platformName":"ios",
    "platformVersion":"14",
    "isRealMobile":True,
    "app":"YOUR_APP_URL",
    "build":"Python Vanilla iOS",
    "name":"Sample Test - Python",
    "network":True,
    "visual":True,
    "video":True
}
```

</TabItem>
<TabItem value="android-config" label="Android" default>

```python title="Android(.apk)"
desired_caps = {
    "deviceName":"Galaxy S20",
    "platformName":"Android",
    "platformVersion":"10",
    "app":"YOUR_APP_URL",
    "isRealMobile":True,
    "build":"Python Vanilla Android",
    "name":"Sample Test - Python",
    "network":True,
    "visual":True,
    "video":True
}
```

</TabItem>

</Tabs>

**Info Note:**

- You must add the generated **APP_URL** to the `"app"` capability in the config file.
- You can generate capabilities for your test requirements with the help of our inbuilt **[Capabilities Generator tool](https://www.lambdatest.com/capabilities-generator/beta/index.html)**. A more Detailed Capability Guide is available [here](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/).

### Executing The Tests

**Step-5:** Run the following command in the directory where your project has been saved to execute your build.

<Tabs className="docs__val">

<TabItem value="ios" label="iOS" default>

```bash
python3 ios.py
```

</TabItem>

<TabItem value="android" label="Android" default>

```bash
python3 android.py
```

</TabItem>

</Tabs>

Your test results would be displayed on the test console (or command-line interface if you are using terminal/cmd) and on the [LambdaTest App Automation Dashboard](https://appautomation.lambdatest.com/build).

## Additional Links

- [Advanced Configuration for Capabilities](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/)
- [How to test locally hosted apps](https://www.lambdatest.com/support/docs/testing-locally-hosted-pages/)
- [How to integrate LambdaTest with CI/CD](https://www.lambdatest.com/support/docs/integrations-with-ci-cd-tools/)

# 3.1 Behave With Appium
# Tutorial To Run Your First Test On LambdaTest

In this topic, you will learn how to configure and run your **Behave** automation testing scripts with **Appium** on **LambdaTest Real Device Cloud platform**.

## Objective

By the end of this topic, you will be able to:

1. Run a sample automation script of **Behave** for application testing with **Appium** on **LambdaTest**.
2. Learn more about Desired Capabilities for Appium testing.
3. Explore advanced features of LambdaTest.

**Sample Repo:** All the code samples in this documentation can be found in the :link: [LambdaTest's Repository on GitHub](https://github.com/LambdaTest/LT-appium-python-behave). You can either download or clone the repository to quickly run your tests.

## Pre-requisites

Before you can start performing App automation testing with Appium, you would need to follow these steps:

- Install the latest stable Python build from the [official website](https://www.python.org/downloads/).
- Make sure **pip** is installed in your system. You can install **pip** from [here](https://pip.pypa.io/en/stable/installation/).

### Clone The Sample Project

**Step-1:** Clone the LambdaTest’s :link: [LT-appium-python-behave](https://github.com/LambdaTest/LT-appium-python-behave) repository and navigate to the code directory as shown below:

```bash
git clone https://github.com/LambdaTest/LT-appium-python-behave
cd LT-appium-python-behave
```

### Setting Up Your Authentication

Make sure you have your LambdaTest credentials with you to run test automation scripts on LambdaTest. To obtain your access credentials, [purchase a plan](https://billing.lambdatest.com/billing/plans) or access the [Automation Dashboard](https://appautomation.lambdatest.com/).

**Step-2:** Set LambdaTest `Username` and `Access Key` in environment variables.

**For Linux/macOS:**

  {`export LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()}" \\
export LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"
 
**For Windows:**

  {`set LT_USERNAME="${ YOUR_LAMBDATEST_USERNAME()}" \`
set LT_ACCESS_KEY="${ YOUR_LAMBDATEST_ACCESS_KEY()}`}"
  
### Upload Your Application

**Step-3:** Upload your **_iOS_** application (.ipa file) or **_android_** application (.apk file) to the LambdaTest servers using our **REST API**. You need to provide your **Username** and **AccessKey** in the format `Username:AccessKey` in the **cURL** command for authentication. Make sure to add the path of the **appFile** in the cURL request. Here is an example cURL request to upload your app using our REST API:

**Using App File:**

**For Linux/macOS:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \\
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\
--form 'name="Android_App"' \\
--form 'appFile=@"/Users/macuser/Downloads/proverbial_android.apk"' 
`}

**For Windows:** 

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -F "appFile=@"/Users/macuser/Downloads/proverbial_android.apk""`}

**Using App URL:**

**Linux/macOS:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" \\
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \\
--form 'name="Android_App"' \\
--form 'url="https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk"'`}

**For Windows:**

{`curl -u "${ YOUR_LAMBDATEST_USERNAME()}:${ YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -d "{\"url\":\"https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk\",\"name\":\"sample.apk\"}"`}

**Tip:**

- If you do not have any **.apk** or **.ipa** file, you can run your sample tests on LambdaTest by using our sample :link: [Android app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or sample :link: [iOS app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa).
- Response of above cURL will be a **JSON** object containing the `App URL` of the format - <lt://APP123456789123456789> and will be used in the next step.

## Run Your First Test

### Sample Test With Behave

To get started, here is an example of sample test on our sample Android and iOS App shown below. You can write or add your own Appium automation scripts in `*StepDef.py` directory to run different tests on your app.

<Tabs className="docs__val">

<TabItem value="android-stepdef" label="Android" default>

```python title="AndroidStepDef.py"
import sys
import os
path = os.getcwd()
sys.path.append(os.path.abspath(os.path.join(path, os.pardir)))
from time import time
from behave import given
from appium import webdriver
import appConfig as appConf
from appium.webdriver.common.mobileby import MobileBy
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

@given("Start the android app automation test")
def startAndroidAppAutomationTest(self):
    if os.environ.get("LT_USERNAME") is None:
        username = "username" #Enter LT username here if environment variables have not been added
    else:
        username = os.environ.get("LT_USERNAME")
    if os.environ.get("LT_ACCESS_KEY") is None:
        accesskey = "accesskey" #Enter LT accesskey here if environment variables have not been added
    else:
        accesskey = os.environ.get("LT_ACCESS_KEY")

    driver = webdriver.Remote(
        command_executor="https://"+username+":"+accesskey+"@mobile-hub.lambdatest.com/wd/hub",
        desired_capabilities=appConf.app_android_desired_caps
        )
    try:
        colorElement = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/color")))
        colorElement.click()

        textElement = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/Text")))
        textElement.click()

        toastElement = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/toast")))
        toastElement.click()

        notification = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/notification")))
        notification.click()

        geolocation = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/geoLocation")))
        geolocation.click()

        home = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/Home")))
        home.click()

        speedTest = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/speedTest")))
        speedTest.click()

        home = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/Home")))
        home.click()

        browser = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/Browser")))
        browser.click()

        url = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/url")))
        url.send_keys("https://www.lambdatest.com")

        find = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ID,"com.lambdatest.proverbial:id/find")))
        find.click()

        driver.quit()
    except:
        driver.quit()
```

</TabItem>
<TabItem value="ios-stepdef" label="iOS" default>

```python title="iOSStepDef.py"
import sys
import os
path = os.getcwd()
sys.path.append(os.path.abspath(os.path.join(path, os.pardir)))
import appConfig as appConf
from behave import given
from appium import webdriver
import time
from appium.webdriver.common.mobileby import MobileBy
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

@given("Start the ios app automation test")
def startIOSAppAutomationTest(self):
    if os.environ.get("LT_USERNAME") is None:
        username = "username" #Enter LT username here if environment variables have not been added
    else:
        username = os.environ.get("LT_USERNAME")
    if os.environ.get("LT_ACCESS_KEY") is None:
        accesskey = "accesskey" #Enter LT accesskey here if environment variables have not been added
    else:
        accesskey = os.environ.get("LT_ACCESS_KEY")

    driver = webdriver.Remote(
        command_executor="https://"+username+":"+accesskey+"@mobile-hub.lambdatest.com/wd/hub",
        desired_capabilities=appConf.app_ios_desired_caps
    )
    try:
        colorElement = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"color")))
        colorElement.click()

        textElement = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"Text")))
        textElement.click()

        toastElement = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"toast")))
        toastElement.click()

        notification = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"notification")))
        notification.click()
        time.sleep(3)

        geolocation = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"geoLocation")))
        geolocation.click()
        time.sleep(3)

        home = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"Back")))
        home.click()

        speedTest = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"speedTest")))
        speedTest.click()
        time.sleep(3)

        home = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"Back")))
        home.click()

        browser = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"Browser")))
        browser.click()

        url = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"url")))
        url.send_keys("https://www.lambdatest.com")

        find = WebDriverWait(driver,20).until(EC.element_to_be_clickable((MobileBy.ACCESSIBILITY_ID,"find")))
        find.click()

        driver.quit()
    except:
        driver.quit()

```

</TabItem>

</Tabs>

### Configuring Your Test Capabilities

**Step-4:** You need to update your capabilities in `appConfig.py` files. In this sample project, we have provided the examples for running tests on both **Android** and **iOS** apps. We are passing platform name, platform version, device name and app url (generated earlier) along with other capabilities like build name and test name via capabilities object. The capabilities object in the sample code for a single test are defined as:

<Tabs className="docs__val">

<TabItem value="ios-config" label="iOS" default>

```python title="appConfig.py"
app_ios_desired_caps = {
    "deviceName":"iPhone 12",
    "platformName":"ios",
    "platformVersion":"14",
    "build":"Python Behave - iOS",
    "name":"Sample Test iOS",
    "isRealMobile":True,
    "network":True,
    "visual":True,
    "video":True,
    "app":"lt://" #Enter app_url here
}
```

</TabItem>
<TabItem value="android-config" label="Android" default>

```python title="appConfig.py"
app_android_desired_caps = {
    "deviceName":"Galaxy S20",
    "platformName":"Android",
    "platformVersion":"10",
    "build":"Python Behave - Android",
    "name":"Sample Test Android",
    "isRealMobile":True,
    "network":True,
    "visual":True,
    "video":True,
    "app":"lt://" #Enter app_url here
}
```

</TabItem>

</Tabs>

**Info Note:**

- You must add the generated **APP_URL** to the `"app"` capability in the config file.
- You can generate capabilities for your test requirements with the help of our inbuilt :link: **[Capabilities Generator tool](https://www.lambdatest.com/capabilities-generator/beta/index.html)**. A more Detailed Capability Guide is available [here :page_facing_up:](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/) .

### Executing The Tests

<Tabs className="docs__val">

<TabItem value="ios" label="iOS" default>

**Step-5:** Execute the following command to run your test on LambdaTest platform:

```bash
behave --tags @iosApp
```

</TabItem>

<TabItem value="android" label="Android" default>

**Step-5:** Execute the following command to run your test on LambdaTest platform:

```bash
behave --tags @androidApp
```

</TabItem>

</Tabs>

**Info:** Your test results would be displayed on the test console (or command-line interface if you are using terminal/cmd) and on the :link: [LambdaTest App Automation Dashboard](https://appautomation.lambdatest.com/build).

## Additional Links

- [Advanced Configuration for Capabilities](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/)
- [How to test locally hosted apps](https://www.lambdatest.com/support/docs/testing-locally-hosted-pages/)
- [How to integrate LambdaTest with CI/CD](https://www.lambdatest.com/support/docs/integrations-with-ci-cd-tools/)
