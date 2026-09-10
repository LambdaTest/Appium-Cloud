# Run Appium Tests on TestMu AI Cloud (Formerly LambdaTest)

<p align="center">
  <a href="https://www.testmuai.com/"><img src="https://img.shields.io/badge/MADE%20BY%20TestMu%20AI-000000.svg?style=for-the-badge&labelColor=000" alt="Made by TestMu AI"></a>
  <a href="https://mvnrepository.com/artifact/io.appium/java-client"><img src="https://img.shields.io/maven-central/v/io.appium/java-client.svg?style=for-the-badge&labelColor=000000" alt="Appium version"></a>
  <a href="https://community.testmuai.com/"><img src="https://img.shields.io/badge/Join%20the%20community-blueviolet.svg?style=for-the-badge&labelColor=000000" alt="Community"></a>
</p>

## Getting Started

[TestMu AI](https://www.testmuai.com/) (Formerly LambdaTest) is the world's first full-stack AI Agentic Quality Engineering platform that empowers teams to test intelligently, smarter, and ship faster. Built for scale, it offers a full-stack testing cloud with 10K+ real devices and 3,000+ browsers. With AI-native test management, MCP servers, and agent-based automation, TestMu AI supports Selenium, Appium, Playwright, and all major frameworks.

With TestMu AI (Formerly LambdaTest), you can run Appium tests for native, mobile web, and hybrid applications on iOS and Android across thousands of real devices. This sample shows how to configure and execute Appium automation tests on the TestMu AI cloud.

- [Sign up on TestMu AI](https://www.testmuai.com/register/) (Formerly LambdaTest).
- Follow the [TestMu AI documentation](https://www.testmuai.com/support/docs/getting-started-with-appium-testing/) (Formerly LambdaTest) for the full setup walkthrough.

### Prerequisites

1. You will need a TestMu AI (Formerly LambdaTest) username and access key. To obtain your access credentials, [purchase a plan](https://billing.lambdatest.com/billing/plans) or access the [automation dashboard](https://appautomation.lambdatest.com/).
2. Ensure you have Appium's [Java client library](https://github.com/appium/java-client) installed.
3. Access to an **Android** app (.apk or .aab file) or an **iOS** app (.ipa file).

**Tip:** If you do not have any **.apk** or **.ipa** file, you can run your sample tests on TestMu AI (Formerly LambdaTest) by using our sample [Android app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or sample [iOS app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa).

### Setup

Set your credentials as environment variables.

**macOS / Linux:**

```bash
export LT_USERNAME="YOUR_USERNAME"
export LT_ACCESS_KEY="YOUR_ACCESS_KEY"
```

**Windows:**

```bash
set LT_USERNAME="YOUR_USERNAME"
set LT_ACCESS_KEY="YOUR_ACCESS_KEY"
```

## Languages And Frameworks

Here is a list of languages and frameworks that are supported by TestMu AI (Formerly LambdaTest) to run Appium automation tests on the [TestMu AI Real Device Cloud Platform](https://www.testmuai.com/).

| Java | PHP | Ruby | C# | Python | JavaScript |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| [JUnit](https://github.com/LambdaTest/LT-appium-java-junit) | [PHP](https://github.com/LambdaTest/LT-appium-php) | [Cucumber](https://github.com/LambdaTest/LT-appium-ruby-cucumber) | [C#](https://github.com/LambdaTest/LT-appium-CSharp) | [Behave](https://github.com/LambdaTest/LT-appium-python-behave) | [WebdriverIO](https://github.com/LambdaTest/LT-appium-nodejs-webdriverio) |
|   |   |   |   | [Robot](https://github.com/LambdaTest/LT-appium-python-robot) |   |

We support all languages and frameworks that are compatible with Appium, so in case your favorite isn't in the table, don't worry, you can still run the test. **[Contact Us](https://www.testmuai.com/contact-us)** for any help.

## Run Your First Test

### Upload Your Application

Upload your **_iOS_** application (.ipa file) or **_Android_** application (.apk file) to the TestMu AI (Formerly LambdaTest) servers using our **REST API**. You need to provide your **Username** and **AccessKey** in the format `Username:AccessKey` in the **cURL** command for authentication. Make sure to add the path of the **appFile** in the cURL request. Here is an example cURL request to upload your app using our REST API:

**For macOS/Linux:**

```js
curl -u "{username}:{accesskey}" \
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \
--form 'name="Android_App"' \
--form 'appFile=@"/Users/{desktop_username}/Desktop/LT_Java_Appium/proverbial_android.apk"'
```

**For Windows:**

```js
curl -u "{username}:{accesskey}" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -F "appFile=@"/Users/Desktop_username/Desktop/LT_Java_Appium/proverbial_android.apk""
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

Response of above cURL will be a **JSON** object containing the `App URL` of the format - `lt://APP123456789123456789` and will be used in the next step.

### Write Your Automation Script

Write your automation script in the client language of your choice from the ones [supported by Appium](https://appium.io/downloads.html). An automation script for the sample applications have been provided below. You can clone the automation code in Java for the sample app from our [GitHub repository](https://github.com/LambdaTest/LT_Java_Appium).

Here is a sample automation script in Java for the sample app downloaded above. Ensure to update the `app_url`, `username` and `accesskey` in the below code.

**Android:**

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

    @org.testng.annotations.Parameters(value = {"device", "version", "platform"})
    public AndroidApp(String device, String version, String platform) {
        try {
            DesiredCapabilities capabilities = new DesiredCapabilities();
            capabilities.setCapability("build","ParallelSample Android");
            capabilities.setCapability("name",platform+" "+device+" "+version);
            capabilities.setCapability("deviceName", device);
            capabilities.setCapability("platformVersion",version);
            capabilities.setCapability("platformName", platform);
            capabilities.setCapability("isRealMobile", true);
            capabilities.setCapability("app", "app url"); //Enter your app URL from previous step here
            capabilities.setCapability("deviceOrientation", "PORTRAIT");
            capabilities.setCapability("console", true);
            capabilities.setCapability("network", true);
            capabilities.setCapability("visual", true);
            capabilities.setCapability("devicelog", true);

            String hub = "https://" + userName + ":" + accessKey + gridURL;
            AppiumDriver driver = new AppiumDriver(new URL(hub), capabilities);
            // ... test steps
            driver.quit();
        } catch (Exception t) {
            System.out.println();
        }
    }
}
```

**iOS:**

```java
import io.appium.java_client.AppiumDriver;
import io.appium.java_client.MobileElement;
import org.openqa.selenium.remote.DesiredCapabilities;
import java.net.URL;

public class iOSApp {

    public static String userName = "username"; //Enter your LT Username here
    public static String accessKey = "accesskey"; //Enter your LT AccessKey here

    public String gridURL = "@mobile-hub.lambdatest.com/wd/hub";

    @org.testng.annotations.Parameters(value = {"device", "version", "platform"})
    public iOSApp(String device, String version, String platform) {
        try {
            DesiredCapabilities capabilities = new DesiredCapabilities();
            capabilities.setCapability("build","ParallelSample iOS");
            capabilities.setCapability("name",platform+" "+device+" "+version);
            capabilities.setCapability("deviceName", device);
            capabilities.setCapability("platformVersion",version);
            capabilities.setCapability("platformName", platform);
            capabilities.setCapability("isRealMobile", true);
            capabilities.setCapability("app", "app url"); //Enter your app URL from previous step here
            capabilities.setCapability("deviceOrientation", "PORTRAIT");
            capabilities.setCapability("console", true);
            capabilities.setCapability("network", true);
            capabilities.setCapability("visual", true);
            capabilities.setCapability("devicelog", true);

            String hub = "https://" + userName + ":" + accessKey + gridURL;
            AppiumDriver driver = new AppiumDriver(new URL(hub), capabilities);
            // ... test steps
            driver.quit();
        } catch (Exception t) {
            System.out.println();
        }
    }
}
```

## Desired Capabilities In Appium

Appium's Desired Capabilities are a collection of key-value pairs wrapped inside a JSON object. These key-value pairs request the Appium server for the required test automation session.

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

### Running Tests On TestMu AI (Formerly LambdaTest) Appium Grid

Pass the capabilities to `@hub.lambdatest.com/wd/hub` with your TestMu AI (Formerly LambdaTest) authentication details. Here is a sample Python test script:

```python
from threading import Thread
import time
from appium import webdriver
from appium.webdriver.common.mobileby import MobileBy
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

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

def run_session(desired_cap):
    driver = webdriver.Remote(
        command_executor="https://LT_USERNAME:LT_ACCESS_KEY@mobile-hub.lambdatest.com/wd/hub",
        desired_capabilities=desired_cap)
    # ... test steps
    driver.quit()

for cap in caps:
    Thread(target=run_session, args=(cap,)).start()
```

## Testing Locally Hosted Apps

To test locally hosted apps, use the TestMu AI (Formerly LambdaTest) Tunnel. Set `tunnel: true` in your desired capabilities:

```python
caps = [
    {
        "tunnel": True,
        # ... other capabilities
    }
]
```

## Appium Inspector

Use Appium Inspector to identify elements in your app. Connect it to the TestMu AI (Formerly LambdaTest) cloud by setting the remote host to `mobile-hub.lambdatest.com`.

## APIs For App Testing

Use the TestMu AI (Formerly LambdaTest) REST API to upload apps, list uploaded apps, and delete apps. All API endpoints use your `Username:AccessKey` for authentication.

## Migrate Appium Tests

### Migrating From BrowserStack

**BrowserStack:**

```python
driver = webdriver.Remote(
    command_executor="https://BROWSERSTACK_USERNAME:BROWSERSTACK_ACCESS_KEY@hub-cloud.browserstack.com/wd/hub",
    desired_capabilities=desired_cap)
```

**TestMu AI (Formerly LambdaTest):**

```python
driver = webdriver.Remote(
    command_executor="https://LT_USERNAME:LT_ACCESS_KEY@mobile-hub.lambdatest.com/wd/hub",
    desired_capabilities=desired_cap)
```

### Migrating From Sauce Labs

**Sauce Labs:**

```python
caps['appium:deviceName'] = 'Google Pixel 3a GoogleAPI Emulator'
caps['appium:platformVersion'] = '11.0'
caps['sauce:options'] = {}
caps['sauce:options']['appiumVersion'] = '1.20.2'

driver = webdriver.Remote(
    command_executor="https://SAUCE_USERNAME:SAUCE_ACCESS_KEY@ondemand.us-west-1.saucelabs.com/wd/hub",
    desired_capabilities=desired_cap)
```

**TestMu AI (Formerly LambdaTest):**

```python
caps = [
    {
        "deviceName": "Google Pixel 3",
        "platformName": "Android",
        "platformVersion": "11",
        "app": "<lt_app_url>",
        "build": "Demo",
    },
]

driver = webdriver.Remote(
    command_executor="https://LT_USERNAME:LT_ACCESS_KEY@mobile-hub.lambdatest.com/wd/hub",
    desired_capabilities=desired_cap)
```

### Migration From Local Grid

To migrate from a local Appium grid, change the `command_executor` URL to point to the TestMu AI (Formerly LambdaTest) cloud endpoint and pass your credentials along with the desired capabilities.

### Run tests

Run your Appium tests using your chosen framework's run command, then view results on your TestMu AI dashboard.

## Contributions

Contributions are welcome. Open an issue to discuss your idea before submitting a pull request. When reporting bugs, include your Java version, OS, and Appium version.

## TestMu AI (Formerly LambdaTest) Community

Connect with testers and developers in the [TestMu AI Community](https://community.testmuai.com/). Ask questions, share what you are building, and discuss best practices in test automation and DevOps.

## TestMu AI (Formerly LambdaTest) Certifications

Earn free [TestMu AI Certifications](https://www.testmuai.com/certifications/) for testers, developers, and QA engineers. Validate your skills in Selenium, Cypress, Playwright, Appium, Espresso and more. Industry-recognized, shareable on LinkedIn, and built by practitioners, not marketers.

## Learning Resources by TestMu AI (Formerly LambdaTest)

Learn modern testing through tutorials, guides, videos, and weekly updates:

* [TestMu AI Blog](https://www.testmuai.com/blog/)
* [TestMu AI Learning Hub](https://www.testmuai.com/learning-hub/)
* [TestMu AI on YouTube](https://www.youtube.com/@TestMuAI)
* [TestMu AI Newsletter](https://www.testmuai.com/newsletter/)

## LambdaTest is Now TestMu AI

On **January 12, 2026**, [LambdaTest evolved to TestMu AI](https://www.testmuai.com/lambdatest-is-now-testmuai/), the world's first fully autonomous **Agentic AI Quality Engineering Platform**.

Same team. Same infrastructure. Same customer accounts. All existing LambdaTest logins, scripts, capabilities, and integrations continue to work without change.

Find the new home for [LambdaTest](https://www.testmuai.com).

### How LambdaTest Evolved into TestMu AI

In 2017, we launched LambdaTest with a simple mission: make testing fast, reliable, and accessible. As LambdaTest grew, we expanded into Test Intelligence, Visual Regression Testing, Accessibility Testing, API Testing, and Performance Testing, covering the full depth of the testing lifecycle.

As software development entered the AI era, testing had to evolve, too. We rebuilt the architecture to be AI-native from the ground up, with autonomous agents that **plan, author, execute, analyze, and optimize tests** while keeping humans in the loop. The platform integrates with your repos, CI, IDEs, and terminals, continuously learning from every code change and development signal.

That evolution earned a new name: **TestMu AI**, built for an AI-first future of quality engineering. TestMu is not a new name for us. It is the name of our annual community conference, which has brought together 100,000+ quality engineers to discuss how AI would reshape testing, long before that became an industry norm.

What started as a high-performance cloud testing platform has transformed into an AI-native, multi-agent system powering a connected, end-to-end quality layer. That evolution defined a new identity: LambdaTest evolved into TestMu AI, built for an AI-first future of quality engineering.

## Support

Got a question? Email [support@testmuai.com](mailto:support@testmuai.com) or chat with us 24x7 from our chat portal.
