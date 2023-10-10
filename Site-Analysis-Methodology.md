# **Introduction**

The upcoming deprecation of 3P cookies will potentially have an impact on many websites. This document outlines a methodology for analyzing sites in search of potential breakages caused by these changes. This methodology leverages tooling capabilities provided by Chrome, Chrome DevTools, and the Privacy Sandbox Analysis extension.

# **Methodology Summary**

The goal of the methodology is to provide a systematic approach to help developers to ensure their websites and applications experience the minimum number of disruptions as they navigate the transition to a world without third-party (3P) cookies and unpartitioned storage. The methodology encompasses a set of distinct yet interconnected components:

1. **Evaluation environment.** A controlled environment is set up to emulate the state of the platform once 3P cookies and unpartitioned storage are deprecated. This is achieved by leveraging various Chrome Release Channels (e.g. Chrome Canary, Chrome Beta) which enable the implementation of the new capabilities of Chrome, and essential developer tools such as Chrome DevTools and the Privacy Sandbox Analysis extension, which enable developers to delve deep into network requests, scrutinize cookies, and detect reported errors.

2. **Testing Scope.** A primary goal of this methodology is to narrow down the evaluation space so developers can focus systematically on specific aspects of their sites and applications:

    1. **3P Technologies**: Evaluate all third-party technologies to discern their dependency on 3P cookies and the potential fallout from their deprecation.

    2. **1P Features**: Thoroughly review essential first-party features and CUJs.

3. **QA/Testing Steps**. Testing sequences for different components or user journeys. For instance, in checkout flows, validate the cart functionality and payment processing; if discrepancies or issues arise, follow a specific process to identify, triage, and address them.

4. **Reporting**. Aggregated data reports presented via dashboards, providing clarity and insights to strategic decision-making on addressing the transition to Privacy Sandbox.

# **How to Test**

## **Evaluation Environment**

**▶️** Screencast: [Prepare Testing Environment](https://www.youtube.com/watch?v=EjbV4sUot4M)

To fully evaluate the potential impact of Privacy Sandbox changes on Chrome, we can leverage different Chrome Release versions (Stable, Canary, Beta, Dev).  Set up your evaluation environments by following the instructions below.

1. Download or update to the latest version of Google Chrome [Release Channels](https://support.google.com/chrome/a/answer/9027636?hl=en&ref_topic=9023245&sjid=8170039632193365418-AP), both Stable and versions which have implemented the restrictions and new capabilities that will be generally available after 3PCD: Chrome Canary, Chrome Beta, Chrome Dev.

2. Start Chrome versions with the relevant command line arguments:

*Linux OS*

```
google-chrome --test-third-party-cookie-phaseout --enable-features="FirstPartySets,StorageAccessAPI,StorageAccessAPIForOriginExtension,PageInfoCookiesSubpage,PrivacySandboxFirstPartySetsUI"
```
        
*Mac OS*

```        
open /Applications/Google\ Chrome.app --args --test-third-party-cookie-phaseout --enable-features="FirstPartySets,StorageAccessAPI,StorageAccessAPIForOriginExtension,PageInfoCookiesSubpage,PrivacySandboxFirstPartySetsUI"
```        

*Windows OS*

```        
"\Program Files\Google\Chrome\Application\chrome.exe" --test-third-party-cookie-phaseout --enable-features="FirstPartySets,StorageAccessAPI,StorageAccessAPIForOriginExtension,PageInfoCookiesSubpage,PrivacySandboxFirstPartySetsUI"
```
        
3. Consider using a new Chrome profile for a clean testing environment, or deactivate browser plugins/extensions that might interfere with cookies.

4. Enable Storage Partitioning (available in all release channels)
    - Go to chrome://flags#third-party-storage-partitioning
    - Select “Enable”
    - Restart your browser


https://lh5.googleusercontent.com/iSv0ZkoxWo9yhuXsCV8JfJxELEZt_JEikEILCZNHko5c_Rj5Zp8FU4DUhunZ9xE8n2sdqRfbNxb9LiCDJglQ7eAIwmbt-cbm_f5K9_om11iDgJJ3Rz0yRyI9i9Zw6YC1jAmweWp-qLeXBSEh8wN2ZYNRSG7S0k16-kSPKbfkWhtjg6U4iJfwFchwPxmy5WUOxgDnK2ybWyt1R8gKgiaQM9_TWBbQQ6SfEgTEAg

1. Run tests on the different Chrome versions (Stable, Canary with 3PCD enabled)
    - In this methodology, we use the following naming convention
        - **Chrome Browser Open**: refers to the chrome instance with 3P cookie functionality available
        - **Chrome Browser Private**: refers to the chrome instance with 3P cookie and storage access APIs secured

2. During testing with 3P cookies blocked, turn cookies on an off via the URL bar
    - Click the small “eye” icon in the URL bar
    - Click on “site not working” -> “Allow cookies”

## **Analyzing Cookies with DevTools**

**▶️Screencast**: [[Analyzing site with DevTools](https://www.youtube.com/watch?v=_FErYRFIXHA)](https://www.youtube.com/watch?v=_FErYRFIXHA).

DevTools is a powerful debugging companion to Chrome providing a myriad of vantage points to observe the operational execution of sites running on the browser. DT provides visibility to all data about cookies. To get to it some access points are:

1. **Open Chrome Developer Tools**: Right-click on the webpage and select "Inspect" or press Ctrl+Shift+I (Windows/Linux) or Cmd+Option+I (Mac) to open the Developer Tools.
2. **Navigate to the Network Tab**: In the Developer Tools window, navigate to the "Network" tab.
3. **Perform the Action**: Interact with the website, such as clicking a button, submitting a form, or navigating to a new page.
4. **Observe Network Activity**: In the "Network" tab, you'll see a list of network requests made by the webpage. Look for entries related to cookies, which might have a "Set-Cookie" header in the response or other relevant information.
5. **Inspect Cookies**: Click on a network request entry to view its details. Look for the "Headers" tab, which should include information about cookies, including those being added or modified as a result of the action you performed.

You can learn more about DevTools [[here](https://developer.chrome.com/docs/devtools/)](https://developer.chrome.com/docs/devtools/).  We will leverage DT capabilities when performing the tests on specific CUJs as described below.

## **Privacy Sandbox Analysis CLI**

**▶️Screencast**: Analyzing sites with PSAT CLI.

The PSA CLI provides access to functionality similar to the PSA Extension, and makes it accessible through the command line. The CLI enables the following use cases:

- Aggregated analysis of full site (i.e. sitemap.xml)
- Site evaluation pre-analysis ⇒ Guidance on scope and prioritization
- CLI for CI: Integrate the PSA CLI into your CI pipeline and detect potential areas of issues related to 3PCD
- Testing for breakages by executing two access runs, with and without cookies being blocked, and provide a “cookie differential” analysis

The current version of the CLI is limited as it does not include yet an extensive automated interaction model to ensure that aspects such as Cookie Consent Banners are accounted for when exercising CUJs. But we are making progress quickly to remove this limitation. Stay tuned!

## **Analyzing Cookies with PSA DevTools Extension**

**▶️Screencast**: Analyzing sites with PSAT.

The Privacy Sandbox Analysis Tool (PSAT) is a Chrome DevTools extension to assist developers in the analysis and debugging of cookie, storage, and PS API usage during Browsing Sessions. In the future, the extension will be also available on the Chrome Store (TODO: https://developer.chrome.com/docs/webstore/publish/).

- Download and install PSAT, which is being developed as an open source project and you can access the project [[here](https://github.com/GoogleChromeLabs/ps-analysis-tool).
- Load the website on the evaluation environment (i.e. Chrome Stable, Chrome Canary)
- Open DevTools:
    - On Mac : Command(⌘) + Option(⌥) + C
    - Windows, Linux, ChromeOS: Control(⌃) + Shift(⇧) + C
- Click on the “Privacy Sandbox” Tab
- Click on the *Cookies > Site Frame*
- Open filters by clicking on the Filter icon
- Add filters
    - ***E.g. Scope: Third Party*** (filters list to show all 3P cookies)
    - ***E.g. Cookie Accepted: False*** (filters list to show all cookies that were not set)

# **General Debugging Actions**

**The term “Breakage”** refers to functionality that is available to the user on the site but does not work as advertised (e.g. a “login” button not logging in, a video not loading, the site reporting an error at any point). Breakages frequently occur in one of the following situations:

- When users are signing up, signing in, or managing various aspects of their account
- When the site is integrating with another site in some way, e.g. by showing an embedded video from a video hosting service, hosting an embedded feedback form, or forwarding a payment request to an external payment provider. Some of these third-party integrations
    
    might be hard to spot, since sites want their user experience to be seamless
    
- A site notifying the user that the browser or cookie settings are “not supported”

Analyzing websites for potential breakages is not a trivial process, as there are many factors to take into account, and lots of information to be grasped. This section describes various factors that can be considered during a site analysis.

## **Authentication**

Some of the functionality of a site can be tested without authentication and/or login requirements, while others do require users to have an account of some sort and be properly authenticated. Both scenarios must be analyzed.

## **Desktop/Mobile**

Tests/analysis must be performed on both desktop and mobile, if and only if the mobile version of the site is entirely different.

## **Top–level navigations**

Quite often, top-level navigations happen *invisibly* to you when you only look at the URL bar, e.g. through server-side 301 redirects.

To see top-level navigations without the added noise of other requests, toggle the “Doc” filter in the network panel as shown below, then look at the origin of the request URL to see if it is cross-site with the one that is in the URL bar

https://lh5.googleusercontent.com/6P9RVjbKERsgDM2JGUjDq03-IeUvgReoQxVjLoSfk99R6oi4GQgyNB9D_-QORhZ_VRMhLl7Lti8_mWET97w7UAzghw37PVYWb1uMk3mLNxc9y2_Az1a90zY9qj8JTTQJthAZjqpHuri5MZzukVAXwr6iBhMRJMxErvR1nlalq7cUXXGcWTF7qI1F1fwjfjXIvmDAZmPVGKnJbLOGlrNmfUquOacEgK-SIJv58g

## **JS/Network errors**

Lack of 3PC access can very frequently cause errors to be thrown in DevTools. One example is the bug “Nintendo - sign-in doesn't work”, where a 3P request to [accounts.nintendo.com](http://accounts.nintendo.com/) throws a 403 without the right cookies attached.

https://lh6.googleusercontent.com/aToiHmXtzmRh8NDYRwFbjI2kcUzDcUtB7vtVHq_pCC8hyiNyPtvI3cqsd742h5mIDf_SIMoEwEoK9Mv94w1hSmicpwmvZXuewy7cEGDbgMhenlzwZl_w-flt5ROdMox0LhmCuq0FXbkFvk-lW9vFkwyY3Vb_MIDFwG6o4Lq9pTLrjyzxSOfV4KveatVKIuHvmoihhfNzWBjbVWySBF3PO8a06_YFXD-UaEpVVA

## **Partitioned storage**

A reported bug on “S-Bahn München status page” reported by https://www.s-bahn-muenchen.de/fahren/betriebslage, where lack of partitioned storage throws an error on the localStorage getter. Through the JS exception chain we can actually see the origin of the file that ran this code, and derive that this could be the 3rd party in this case.

https://lh6.googleusercontent.com/znBDHSuyEGse0gP0SQHU4jJiVUy_3p7iGqSF7D0aL527ePlOQT5bQCgqdxb1_SouLxY5WMO2Od9oDymBpp3s4UU10QIc-VZVpRIXd7shsmkwPbf4ltVQsz90ZxiHhrNdCDmFmYhGWBUx7XaXHooV93aURc0PMt_NnRbtHAofkr5YeoUyhnKCRxFK4Cy0LAIAl5nTkdCQ9caJaTqfvhUeb5NdLHPvXgvoQE2hCw

## **Cross-site requests in the network tab**

Sometimes sites send 3P network requests without the right cookies, but those requests don’t fail. They could just return a 200 because the user not being logged in isn’t considered an error state for them. Here, it’s helpful to search the network DevTools panel for “3rd-party requests” only by checking the corresponding checkbox. There might be a lot of noise here, e.g. calls to ads servers, but also some useful information. This is especially useful if you have some repeatable way of triggering the breakage on the site, e.g. by clicking on a login button or similar. Unless the site is using JS-based cookie access through document.cookie, there should be an outgoing network request at that moment.

## **Authenticated embeds**

Sometimes embedded iframes can appear to be part of the 1P experience on the website. To detect them, it can be helpful to use the DOM inspector in DevTools (starting with the UI that isn’t loading or is showing an error to the user) to figure out if it’s really an iframe. Then, the source of that iframe is likely the 3P that is involved and it’s often an “auth embeds” use case that can be solved with requestStorageAccess, or even CHIPS if there’s no top-level navigation.

An example of this is Mindbody Inc. which serves embedded iframes for website owners to allow their customers to book appointments. This iframe looks a lot like it’s part of the website, but reveals itself in the inspector.

https://lh5.googleusercontent.com/S8TAjyBXswXkrV_wnXHt2YbDzFQMqjGca97z4-8KoT9Uaonw8MyjN_SR4fCERH4cdz5NarXkabljsde5Y_A1PtMkK3xRAOzptnx1bB8PjxneQc5FyB6V4Nzp5odXrhdMUcQwnfG1adhBW5fLF1HHnfZDXQwuX8nZW87tr_9IO7QsLB4banjcv5gVnqJNNKH1aepPAtq-VMkc1ZYdxUlY-eHKlkfkQ3swWGfkYQ

## **Checking for known breakages: GSI v2**

GSI v2 is a legacy library from Google Identity that is integrated with a lot of sites and, unfortunately, relies on cross-site cookies to work. This is a very common source of failure and is especially likely when the user-facing breakage is “can not log in”. There are some tips for identifying whether GSI v2 is in use here.

## **DOM Storage usage**

Some sites are not trying to use cookies, but instead LocalStorage or Quota Storage like IndexedDB. These can often be spotted by observing exceptions being thrown, see [[Look at JS/Network errors.](https://docs.google.com/document/d/1SlFMWZx8YPDqgMRQi1mjR69v1mUvVDORMfQgKisS0FU/edit?resourcekey=0-A2dMtm454TShDq4mPHTQYg#bookmark=id.24lfqsh6zaqj)](https://docs.google.com/document/d/1SlFMWZx8YPDqgMRQi1mjR69v1mUvVDORMfQgKisS0FU/edit?resourcekey=0-A2dMtm454TShDq4mPHTQYg#bookmark=id.24lfqsh6zaqj)

# **Analysis Scenarios and Critical User Journeys**

This section describes the analysis/debugging of Critical User Journeys (CUJs) which are commonly implemented in sites across verticals. Each of these CUJs represents a testing scenario to be checked for potential 3PCD breakages.

## **Analytics Tracking ✅**

This scenario encompasses a website use of analytics providers (e.g. Google Analytics, others) for tracking user behavior. We want to verify user activity/events on 3P analytics service platforms are being captured properly. The goal of this demo is to show details that are part of this scenario, and show you how to analyze the behavior and determine if there are failures.

### **How the Demo Works**

In this demo, we have two distinct sites running on [[domain A](https://domain-aaa.com/analytic)](https://domain-aaa.com/analytic) and [[domain B](https://domain-bbb.com/analytics)](https://domain-bbb.com/analytics) respectively, both of which are using an analytics service delivered from Domain C, which uses the third-party cookies.

When a visitor accesses site A, an analytics service hosted on domain C assigns a unique identifier to that visitor. This identifier tracks any subsequent visits by the same individual. Should this visitor later browse site B, which also utilizes the analytics service served from domain C, they will be identified using the third-party cookie that was set during their initial visit to site A. This cross-domain identification is possible because the third-party cookie from domain C remains consistent and can be accessed irrespective of whether the visitor is on site A or site B.

After Third-Party Cookies Deprecation, when a user visits site A the analytics service from domain C will no longer be able to store the cookie in the user’s browser, and therefore the user will not be tracked upon his visit to site B.

The following sequence diagram shows these behaviors before and after third-party cookie deprecation.

https://lh6.googleusercontent.com/80Ke31JZ4pqKXjmXumJU2vYERRauyHZR4QYEjF_n1Mbv1pkGW3H4NXy2VKbOmjMH4frp3V4CauoJSut_fgiptHWNWpMXSm2YXDYiNsljGIlBrBunR6RUukEe02XM9w36Nu85ak2JtkpvCYDAD5fcbh7I9dB7Z2rqcQqdOhlsCAORMDFDvHukUmEhIeY3fkmnqvbbggtwb0UiJp-i90hQatTy3dlD9Q0Vx3dhgw

### **Debugging the Scenario**

1. **Setup Testing Environment**
    1. Set up your testing environment (as described [[here](https://docs.google.com/document/d/1SlFMWZx8YPDqgMRQi1mjR69v1mUvVDORMfQgKisS0FU/edit?resourcekey=0-A2dMtm454TShDq4mPHTQYg#bookmark=id.5g3v3cb5xogv)](https://docs.google.com/document/d/1SlFMWZx8YPDqgMRQi1mjR69v1mUvVDORMfQgKisS0FU/edit?resourcekey=0-A2dMtm454TShDq4mPHTQYg#bookmark=id.5g3v3cb5xogv)) with two instances of Google Chrome browser: one simulating third-party cookie deprecation (Chrome Private) and the other using the default settings (Chrome Open).
2. **Open Developer Tools in both instances**
    1. On both browsers, open Chrome DevTools (on Mac: Cmd-Option-i, Linux: Ctrl-Shift-i)
    2. It is important to open DevTools first, to ensure capturing all the network interactions as the demo pages load
3. **Adjust Network Tab Settings**
    1. In the network tab, enable “Preserve Log” and “Disable Cache” in both instances of Google Chrome.
    2. This asks the browser to persist the information on network requests, so that we can go back to them if needed as we analyze our scenarios
4. **Navigate and interact with the website**
    1. Open the site https://domain-aaa.com/analytics in both instances
    2. Click the button “Click Me”.
    3. This mimics the actions that cause the analytics tracker to record eventdata on cookies.
5. **Analyze the Cookies in the Application Tab**
    1. Go to the “Application” tab in the DevTools in the default Chrome instance and the instance simulating third-party cookie deprecation.
    2. Navigate to the “Cookies” section and select the frame ([[domain-aaa.com](http://domain-aaa.com/)](http://domain-aaa.com/)) to view the cookies in both instance of Google Chrome
    3. Note the cookies present from domains other than [[domain-aaa.com](http://domain-aaa.com/)](http://domain-aaa.com/), in our case it will be [[domain-ccc.com](http://domain-ccc.com/)](http://domain-ccc.com/) in both instances of Chrome.
6. **Compare the cookies**
    1. Identify the cookie that is set in Chrome Open but absent in Chrome Private.
    2. Identify the network request which sets the cookie in the Chrome Open instance, and track that request in the Chrome Private instance
7. **Navigate to the other domain**
    1. Open the site https://domain-bbb.com/analytics in both instances
    2. Click the button “Click Me”.
    3. Proceed with Step 5 and 6 to determine why Domain B was able to identify the visitor in one instance and it could not when simulating third-party cookie deprecation.

At this point, we debugged the scenario which is common for implementations of analytics providers, and learned how to detect potential failures. This demo can be extrapolated to other analytics providers which also use cookies as the state mechanism to implement their capabilities.

If you are a 3P provider, or if you are checking if the 3P analytics providers on your site are working, then you can map the process  outlined in this demo to your scenario.

## **E-commerce: Cross-domain Shopping Cart ✅**

This scenario goes through the workings of an e-commerce setup that leverages a third-party service for cart management across multiple domains. The goal of the demo is to illustrate how third-party cookies are used to maintain cart continuity across different first-party domains, and provide a detailed overview of how to analyze this kind of scenario and determine if there are potential failures.

### **How the Demo Works**

We have two separate e-commerce sites hosted on [[domain A](http://domain-aaa.com/)](http://domain-aaa.com/) and [[domain B](http://domain-bbb.com/)](http://domain-bbb.com/), both using  a third-party e-commerce service hosted on [[domain C](http://domain-ccc.com/)](http://domain-ccc.com/).

When a visitor shops on domain A, items added to the cart are stored by the third-party e-commerce service on domain C using a third-party cookie. This cookie acts as a memory bank for the cart items irrespective of which first-party domain the visitor is on. Therefore, if the visitor subsequently navigates to domain B, the items they added to the cart on domain A are still visible in their cart.

This behavior will be affected with the deprecation of third-party cookies. When a visitor shops on domain A, domain C's service will not be able to store the cart information using a third-party cookie, and therefore cart information from domain A cannot be carried over.

The following sequence diagram shows the cart behavior with cookies enabled:

https://lh4.googleusercontent.com/9ieLJRVZ4-5hcDHrUjiH2jjbjl8WehSru7_7WcLrvw5_djRh4YAJu4pV0d0xuIQQiHS5pz3JDbggBOfvqnLhzlSDIRrrwHoCOVV7CT2Pn_DKII2xIIeBZ32Ablo05ljSaHvIbeV20eS0sVYq0ALPCQerJ7htcGJo6HQaYUzhFKIT4gZxFSmxIKQ-V_l9CmSxduMBKUvT-XzxlPOInPHTzRVX-DQW9bIkkRDTEQ

And this one, shows the behavior of the scenario when third-party are not available:

https://lh5.googleusercontent.com/62Tujj1x1LHAlzeUNhTklyFyHZriHLhOTtkENP0I0hIl7dU00vQivUQkYLtYbWEIMHdRTpUxWY9F_7g-CxzIldwGSZZ-hXHwFIU3woarm5g_1lO8zvEz4EeKdHmX4-uchl2DO9AxtbfobCN4BqPRVfpBEPS8GkGlb61cCAKfiOUMVvxeaAhlLnb-1y5Stv4_iVYv_2adID7jljLky9LJLRKs-AVpoDUPKE_jPg

We can observe in the diagrams how blocked cookies will ruin the shopping experience for the user across multiple domains. Read on to learn how we debug this kind of scenario.

### **Debugging the Scenario**

1. **Setup Testing Environment**
    1. Set up your testing environment (as described [[here](https://docs.google.com/document/d/1SlFMWZx8YPDqgMRQi1mjR69v1mUvVDORMfQgKisS0FU/edit?resourcekey=0-A2dMtm454TShDq4mPHTQYg#bookmark=id.5g3v3cb5xogv)](https://docs.google.com/document/d/1SlFMWZx8YPDqgMRQi1mjR69v1mUvVDORMfQgKisS0FU/edit?resourcekey=0-A2dMtm454TShDq4mPHTQYg#bookmark=id.5g3v3cb5xogv)) with two instances of Google Chrome browser: one simulating third-party cookie deprecation (Chrome Private) and the other using the default settings (Chrome Open).
2. **Open Developer Tools**
    1. On both browsers, open Chrome DevTools (on Mac: Cmd-Option-i, Linux: Ctrl-Shift-i)
    2. It is important to open DevTools first, to ensure capturing all the network interactions as the demo pages load
3. **Adjust Network Tab Settings**
    1. On both browsers, go to the network tab and enable "Preserve Log" and "Disable Cache" in both instances of Google Chrome.
    2. This asks the browser to persist the information on network requests, so that we can go back to them if needed as we analyze our scenarios
4. **Navigate to the first domain**
    1. On both browsers, open the site [**https://domain-aaa.com/**](https://domain-aaa.com/)
    2. Interact with the products and add them to the cart.
    3. This mimics what you would do while online shopping on any site.
5. **Analyze the Cookies in the Application Tab**
    1. Go to the "Application" tab in the DevTools in both Chrome instances.
    2. Navigate to the "Cookies" section and select the frame ([[domain-aaa.com](http://domain-aaa.com/)](http://domain-aaa.com/)) to view the cookies set for that domain.
    3. Note the cookies present from domains other than [[domain-aaa.com](http://domain-aaa.com/)](http://domain-aaa.com/). In our scenario, particularly note cookies from [[domain-ccc.com](http://domain-ccc.com/)](http://domain-ccc.com/).
6. **Compare the behavior of the cookies**
    1. Identify the cookie that is set in Chrome Open but absent in Chrome Private.
    2. On Chrome Open, right-click on the identified cookie and select “Show Requests with this Cookie” from the context menu to access information about the network request that initiated the cookie-setting in the default Chrome instance. Take note of th
    3. On Chrome Private, the same cookie identified will not be present (blocked).
    4. Go to the Network tab and search for “[[domain-ccc.com](http://domain-ccc.com/)](http://domain-ccc.com/)”, and click on the network request named “add-to-cart”
    5. Click on the Cookies tab, and nothing will be shown, as the cookie was blocked by Chrome Private. On Chrome Open, if configured via settings to block 3P cookies, you will observe the cookies that domain C attempted to set, highlighted indicating that the operation was rejected.
7. **Navigate to the second domain**
    1. Open the site [**https://domain-bbb.com/**](https://domain-bbb.com/) in both Chrome instances.
    2. Observe the cart contents and the count icon.
    3. Return to the "Application" tab in both Chrome instances and navigate to the "Cookies" section, this time selecting the frame ([[domain-bbb.com](http://domain-bbb.com/)](http://domain-bbb.com/)).
    4. Make note of cookies, especially those from [[domain-ccc.com](http://domain-ccc.com/)](http://domain-ccc.com/).
    5. Compare the cookies between the two instances similarly as in Step 6 to understand discrepancies, if any.

By this stage, you've debugged the sequence that represents the behavior of many e-commerce and analytics solutions relying on third-party cookies, and gaining a clear insight into how third-party cookies function (and the implications when they don't) equips you to address potential issues as an e-commerce website operator.

If you are a 3P provider, or if you are checking if the 3P e-commerce providers on your site are working, then you can map the process outlined in this demo to your scenario.

## **Single Sign-On (SSO) Services ✅**

This scenario demonstrates how a third-party Single Sign-On (SSO) service enables users to log in seamlessly across multiple websites, using third-party cookies to maintain their logged-in state. Our goal is to demonstrate the process by focusing on the specific details of how data flows through third-party cookies. We will evaluate the SSO functionality and identify any possible issues or problems.

### **How the Demo Works**

This demo showcases two separate sites operating on [[domain A](https://domain-aaa.com/)](https://domain-aaa.com/) and [[domain B](https://domain-bbb.com/)](https://domain-bbb.com/). Both these sites rely on an SSO service located on [[domain C](https://domain-ccc.com/)](https://domain-ccc.com/), which utilizes third-party cookies for its operation.

When a user accesses [[domain A](http://domain-aaa.com/)](http://domain-aaa.com/) and logs in using their email, they are redirected to the SSO service on [[domain C](http://domain-ccc.com/)](http://domain-ccc.com/). This service then sets a third-party cookie containing the user's email, marking them as logged in. As the user later navigates to [[domain B](http://domain-bbb.com/)](http://domain-bbb.com/), this site communicates with [[domain C](http://domain-ccc.com/)](http://domain-ccc.com/), checking the presence and validity of the third-party cookie to ascertain the user's logged-in status.

Thanks to the third-party cookie set by [[domain C](http://domain-ccc.com/)](http://domain-ccc.com/), both domain A and domain B can recognize and maintain the user's logged-in state seamlessly. The user does not have to log in again on domain B, as the SSO service on domain C confirms their status through the third-party cookie.

However, post Third-Party Cookies Deprecation, the behavior will change. When the user first visits domain A and logs in, the domain C cannot set a third-party cookie. Consequently, when the user transitions to domain B, the site won't recognize the user's logged-in status as the third-party cookie is absent. This absence disrupts the seamless cross-domain login experience previously facilitated by third-party cookies.

The provided sequence diagrams effectively visualizes this behavior both before and after the deprecation of third-party cookies.

https://lh6.googleusercontent.com/MLPmYfI2pz3ZjnIz4-E_h0UV0UTG6P4SmoSvf0hNNzu4LybN0hDtagqKQ-nhwhX1YXRFjHfqqMNo4AWj-RQ8nD1YSeJmUX1btpwV7mLaIrfzm19sQDOgspvfQFf1lGWSeR1n1EuHBiyKOhLgyF7AcfLApbl2pmm4UhXQov3UNADEErR8KT9ed12ULCWZhAjPxw4PyBuWeby0Llm6NfmFEUwd1wq4d_xvup5bFA

https://lh3.googleusercontent.com/s6sp2pV5XkJWzJLAS3q95jV-ZBagtyf8Gpw3PuDKoZJGcie7yaHfbeTP1d1KG3ZupXuidXnA-EtA71lDSadIa0wbMoowXP_fnR2D5YO2Ee3KIE2kg_NHqJWk2jopkc_pvw3YaqfDSnQTb-QL3eVyf802l6uvblnDFUVNCuycluhChIgw7BTfSg0duY5kn9L7l8dQ-s8gtd7FeCrf4BnkUgEHTF__fhtp6rqgKw

### **Debugging the Scenario**

1. **Setup Testing Environment**
    1. Set up your testing environment (as described [[here](https://docs.google.com/document/d/1SlFMWZx8YPDqgMRQi1mjR69v1mUvVDORMfQgKisS0FU/edit?resourcekey=0-A2dMtm454TShDq4mPHTQYg#bookmark=id.5g3v3cb5xogv)](https://docs.google.com/document/d/1SlFMWZx8YPDqgMRQi1mjR69v1mUvVDORMfQgKisS0FU/edit?resourcekey=0-A2dMtm454TShDq4mPHTQYg#bookmark=id.5g3v3cb5xogv)) with two instances of Google Chrome browser: one simulating third-party cookie deprecation (using flags) and the other using the default settings.
2. **Open Developer Tools in both instances**
3. **Adjust Network Tab Settings**
    1. In the network tab, enable "Preserve Log" and "Disable Cache" in both instances of Google Chrome.
4. **Visit the First Domain**
    1. Open the site [**https://domain-aaa.com/**](https://domain-aaa.com/) in both instances.
    2. Input your email and initiate the Single Sign-On process.
5. **Analyze the Cookies in the Application Tab**
    1. Go to the “Application” tab in the DevTools in both the default browser instance and the one simulating third-party cookie deprecation.
    2. Navigate to the “Cookies” section and select the frame (**[[domain-aaa.com](http://domain-aaa.com/)](http://domain-aaa.com/)**) to view the cookies.
    3. Note the presence of the cookie from [**[domain-ccc.com](http://domain-ccc.com/)**](http://domain-ccc.com/) (our SSO service) in both instances of the browser.
6. **Compare the Cookies**
    1. Examine the cookies set in the default browser instance and compare them with the ones in the instance simulating third-party cookie deprecation.
    2. Identify which cookies, if any, are missing from the latter instance.
7. **Navigate to the Other Domain**
    1. Open [**https://domain-bbb.com/**](https://domain-bbb.com/) in both instances.
    2. Observe the user's logged-in status.
    3. Go back to the “Application” tab in the DevTools, and under the “Cookies” section, now select the frame (**[[domain-bbb.com](http://domain-bbb.com/)](http://domain-bbb.com/)**). Check for the presence of the cookie from [**[domain-ccc.com](http://domain-ccc.com/)**](http://domain-ccc.com/) in both instances of the browser.
    4. Identify discrepancies between the two instances regarding login status and the presence of the third-party cookie.

By now, you should have a clearer understanding of how third-party cookies are used for Single Sign-On (SSO) processes across multiple domains. If you're working on implementing or testing an SSO service, this debugging scenario can be quite useful. It can help developers and testers validate their SSO implementations and prepare them for any upcoming third-party cookie deprecation. By following the process outlined in this demo, you can easily map it to your specific use case.

## **Embedded Content ✅**

▶️ [[Screencast](https://youtu.be/gHh1B3QqKXg?si=83uI5p47rt1tgX1D)](https://youtu.be/gHh1B3QqKXg?si=83uI5p47rt1tgX1D)  ✍️ [[Video Transcript](https://docs.google.com/document/d/1ExunW3_LDqkTfe7UQCoA8Ch-bOO_Tx0v/edit)](https://docs.google.com/document/d/1ExunW3_LDqkTfe7UQCoA8Ch-bOO_Tx0v/edit)

This scenario goes through the workings of embedded content platforms, such as video streaming, which operate across multiple top-level domains utilizing third-party cookies and local storage for retaining user session and preferences. The primary objective of this demo is to provide details on how to analyze this kind of scenario and determine if there are potential breakages.

### **How the Demo Works**

We have two independent websites on [[domain A](http://domain-aaa.com/)](http://domain-aaa.com/) and [[domain B](http://domain-bbb.com/)](http://domain-bbb.com/). Both host embedded video content through a third-party streaming service residing on [[YouTube.com](http://youtube.com/)](http://youtube.com/)

When a user engages with a video on domain A and adjusts certain playback preferences, these are recorded by the third-party streaming service on YouTube via third-party cookies (i.e. for user session) and local storage (i.e. for preferences). These storage mechanisms allow YouTube embeds to maintain consistency, no matter which first-party domain the user navigates to. As a result, when the user transitions to domain B, the preferences set on domain A, such as volume level or playback speed, persist.

This seamless experience breaks with the deprecation of third-party cookies. When a user adjusts video settings on domain A, YouTube's service will not be able to remember those preferences using a third-party cookie or local storage. Consequently, as the user navigates to domain B, the customized settings from domain A will not be replicated, leading to a disjointed user experience.

The following sequence diagram illustrates the behavior of embedded content as described above, when cookies are available:

https://lh6.googleusercontent.com/Xd2-sjtVSvE9M2Qb-hyd41C9MbnL8hhEKs--ifhDNt0-iJLy8aiGH3BH7Dd5hm9fFiKO01F0f6E2h_2V8gUO1VfXYbAGIijvAN6vUuX31we9mVXcglHFReYmPYFgWwiYVSJFFcD6XfsesDGTyBFnbA9U-gO3u9IXSEdoXM4WNmzegRn6xJcCFuJK8qAl-ETDG9aflTJ1I2kz3qsLQdyDbhhfFlzfUx_9kr3R8A

And the following sequence diagram illustrates the behavior of the embedded content when third-party cookie deprecation changes are in place:

https://lh4.googleusercontent.com/N0D17habfNXaIbkUraD0TJYFcSjhtwNSVUggV1SZzVIqTUGjpcnAJGebAyN0oka7GTyE_RMAjcVZjf-S0a1iIWlqyyw1-odjo3P11f92jhMBCFXvKAmyC969adnffXmYxPEGyoHBqINMdSGRSWV_MG2S3HlX8HaqlxcSLKppkT0jUm4zGCcLCqCYLjn6OQhk4X3O8iaGBIi9XiD-3cLj_KBCwtuoXeNl2Tzbvg

### **Debugging the Scenario**

1. **Setup Testing Environment**
    1. Prepare your testing environment (as described [[here](https://docs.google.com/document/d/1SlFMWZx8YPDqgMRQi1mjR69v1mUvVDORMfQgKisS0FU/edit?resourcekey=0-A2dMtm454TShDq4mPHTQYg#bookmark=id.5g3v3cb5xogv)](https://docs.google.com/document/d/1SlFMWZx8YPDqgMRQi1mjR69v1mUvVDORMfQgKisS0FU/edit?resourcekey=0-A2dMtm454TShDq4mPHTQYg#bookmark=id.5g3v3cb5xogv)). Ensure you have two distinct instances of Google Chrome:
        - **Chrome Private**: Simulating third-party cookie deprecation.
        - **Chrome Open**: Running on default settings.
    2. In both instances, navigate to [[YouTube.com](http://youtube.com/)](http://youtube.com/) and log in using an account.
2. **Open Developer Tools**
    1. Launch Chrome DevTools in both browsers. For Mac users, press **Cmd-Option-i** and for Linux users, press **Ctrl-Shift-i**.
    2. It's crucial to initialize DevTools prior to browsing to capture all network interactions as pages load.
3. **Adjust Network Tab Settings**
    1. In the network tab of both browsers, activate the "Preserve Log" and "Disable Cache" options.
    2. These settings ensure the persistence of network request logs for post-analysis.
4. **Navigate to the embedded video site:**
    1. In **Chrome Private**, access https://domain-aaa.com/embedded-video.
    2. Initiate the YouTube video player by pressing play and ensure the video streams seamlessly.
    3. In a new tab (with DevTools active), visit https://domain-bbb.com/embedded-video.
    4. Play the video. Alter a setting (e.g., muting the audio) and observe if preferences from the previous site (domain A) persist.
    5. If the preferences are not consistently maintained across navigation, proceed to the next steps to investigate the reasons.
    6. In **Chrome Open**, follow the aforementioned sub-steps.
5. **Inspect Network Activity**:
    1. In **Chrome Private**, filter out the network traffic associated with the YouTube player using the search function in the Network tab.
    2. Click on the request beginning with “player?key=XXXXXXX”.
    3. Access the “Cookies” tab for this specific request and activate “show filtered out request cookies”.
    4. In **ChromeOpen**, repeat these sub-steps. Notice that in this instance, the cookies are transmitted to the third-party site, unlike **Chrome Private**.
6. **Check YouTube History**:
    1. In **Chrome Private**, review your YouTube viewing history.
    2. Note that videos from domains A and B *shouldn't* be listed as YouTube can't identify the user due to missing session cookies (as we figured out in step 5).
    3. In **Chrome Open**, repeat the review process. This time, videos from both domains *should* be cataloged since the session is identifiable.
7. **Inspect Local Storage**:
    1. Use developer tools to inspect local storage associated with the YouTube frame in both browser instances.
    2. For **Chrome Open**, the settings must be consistent across all tabs for [[youtube.com](http://youtube.com/)](http://youtube.com/).
    3. Contrastingly, in **Chrome Private**, the local storage reveals not just the origin ([[youtube.com](http://youtube.com/)](http://youtube.com/)) but the top-level site (domain A or B) as well, causing potential discrepancies in user experiences.
8. **Analyze Additional Breakages**:
    1. In the **Chrome Open** instance, a "watch later" option should be visible. Its absence in the **Chrome Private** instance hints that YouTube cannot identify the logged-in user.

By now, you've thoroughly explored and debugged the scenario that illustrates how embedded content, like YouTube videos, relies on third-party cookies and/or storage APIs (e.g. localStorage)  to provide a seamless user experience. You have gained an understanding of the intricacies of how third-party cookies operate, and the challenges that arise when they're deprecated. You can apply a similar approach to investigate potential breakages on any embedded content on yoursite.  If you are an embedded content provider or are evaluating the effectiveness of such third-party content integrations on your platform, you can tailor the methodology from this demo to fit your specific situation.

## **Further Scenarios ✅**

At this point we have pursued in depth analyses of several CUJs commonly found across a wide range of sites, and it is likely that your site has at least one of them. There are many other scenarios commonly found  across the web ecosystem. This methodology will continue expanding on the set of considered scenarios as we create examples and run analyses on them. These scenarios include:

### **Creating an Account**

This scenario focuses on the process of account creation, which is a critical feature for many websites. Given the reliance on third-party cookies, both sign-up and sign-in flows are susceptible to disruptions. To ensure comprehensive testing, all available sign-up providers, such as Google, Facebook, Twitter, and Apple, should be examined. Additionally, the conventional email sign-in method should not be overlooked. Once signed in, it's crucial to log out and attempt the sign-in process once more to validate consistency and reliability.

### **Third-party Authentication**

Many websites incorporate third-party OAuth services like Google and Facebook for streamlined user authentication. Testing this kind of scenario encompasses thoroughly evaluating the third-party login mechanism, including things like:

1. Ensuring that upon pressing the "Login" button (say, "Login with Google"), an authentication popup emerges or a redirection to the third-party service happens seamlessly.
2. Observing the authentication behavior when loading the site on Chrome Private, leveraging the "Network" tab within developer tools to oversee all network requests during the authentication phase.
3. After successfully granting permissions and navigating through the login sequence, confirm that users are smoothly redirected back to the originating website.
4. Moving across different web pages or even refreshing the site should not alter the user's authenticated state, ensuring sustained connectivity.

### **Personalization/Recommendations (e.g., Amazon Recommendations)**

Personalization or recommendation services aim to curate and tailor user experiences on websites by suggesting content, products, or other items based on individual user behaviors, preferences, and histories. Such services can significmantly enhance user engagement, increase conversion rates, and foster loyalty. For example, on e-commerce platforms like Amazon, when a user browses through products, the platform provides recommendations based on the user's past interactions, viewing patterns, and purchases.

If a user explores an Amazon product on a third-party site with an Amazon affiliate link, a third-party cookie might track this interaction. When the user later visits Amazon, they could be presented with recommendations related to this previously-viewed product.

### **Content Delivery Networks (CDNs)**

A Content Delivery Network (CDN) is a system of distributed servers that work together to deliver content (like web pages, images, videos, scripts, and more) to users based on their geographic locations. By caching and storing content at multiple locations around the world, CDNs help reduce the distance between the user and the content, thus speeding up content delivery and ensuring high availability and performance.

Third-party cookies can be used to track user behavior across multiple sites that use the same CDN. This aggregated data can help CDN providers make informed decisions about content caching, server optimizations, and traffic management.

CDNs can tailor the delivery of content based on user profiles, preferences, or behaviors stored in third-party cookies. For instance, a CDN can deliver region-specific content or ads based on a user's browsing history.

In some scenarios, CDNs may rely on third-party cookies to determine if a user has access to specific content, especially in ecosystems where authentication is managed by a third party.

# **Reporting Breakages ✅**

We have outlined a general, yet useful, methodology to approach the analysis of sites in search of potential breakages due to the deprecation of 3P cookies and upcoming changes to Web Storage APIs. By applying this methodology to your specific use cases, you can unearth potential issues and get ready for a successful transition to a more private web.

### **Found an Issue or Breakage?**

Your findings are invaluable! Should you encounter any breakages or issues, make sure to reach out and share with us your findings. By reporting them you will be able to receive help to address the breakage, and  you will be helping others in the web platforms who may experience the same breakage.

Before reporting, please gather information about the breakage and its context to help the training and debugging process. Once you have done that, you can report breakages on the public [[PS Dev Support repository](https://github.com/GoogleChromeLabs/privacy-sandbox-dev-support/)](https://github.com/GoogleChromeLabs/privacy-sandbox-dev-support/), or on [[Google’s tracker](https://goo.gle/report-3pc-broken)](https://goo.gle/report-3pc-broken).

Please also report any bugs/issues with the

[[PS Analysis Tool](https://github.com/GoogleChromeLabs/ps-analysis-tool/issues/new?assignees=&labels=&projects=&template=bug_report.md&title=)](https://github.com/GoogleChromeLabs/ps-analysis-tool/issues/new?assignees=&labels=&projects=&template=bug_report.md&title=)

, and also request features for the

[[PS Analysis Tool](https://github.com/GoogleChromeLabs/ps-analysis-tool/issues/new?assignees=&labels=&projects=&template=feature-request.md&title=)](https://github.com/GoogleChromeLabs/ps-analysis-tool/issues/new?assignees=&labels=&projects=&template=feature-request.md&title=)

in support of use cases that would help in the analysis and debugging of sites.