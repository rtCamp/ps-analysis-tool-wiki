## PSAT's Cookies Landing Page

Click on the Cookies component in PSAT's landing page, which will open the Cookies landing page. As discussed above, PSAT can be configured to avoid using too much resources by restricting the tool to only analyze a single tab at a time. If that configuration setting is set, PSAT presents an `Analyze thus tab` button to switch the focus of the tool to the current tab. 

<img width="742" alt="Screenshot 2023-12-07 at 5 19 35 PM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/1c7d3973-a0c5-4a7a-bac2-8b6b70920373">

The Cookies landing page:

<img width="742" alt="Screenshot 2023-12-07 at 5 25 30 PM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/a92fd0eb-d3e8-42df-ba17-13ef8c206403">


### A note on _Cookie Accepted_ Column

>Of all the cookies that a site attempts to set, the browser will accept some, and some will be rejected, in a 3PCD instance of Chrome (depending on whether they’re third-party or first-party cookies).
>
>The `Cookie Accepted` column of the _PSAT_ cookie table indicates this piece of information by adding a check icon (*✓*) next to the cookies that were accepted by the browser. Other cookies that don’t have this indicator, _have not been accepted by the browser_ and _are not set_.
>
>For this reason, such cookies won’t be displayed under _Applications > Cookies_ in _Chrome Developer Tools_, since that displays the current state of the application and all the cookies that are actually set (accepted) and available for use.
>
>In contrast, `PSAT` is obviously interested in displaying cookies that are not set and not in use, for the purpose of analysis and repair.
>
>This is expected behavior, but sometimes it is a source of confusion because of the apparent disparity between the information displayed under _Application > Cookies_ and the _PSAT_ extension.


### Frame Overlays

Frame overlays make it easy to associate third-party cookies with embedded iframes. To use it:

1. Create a report with the extension
1. Go to the DevTools Privacy Sadbox tab
1. Click on the icon on the side of the Cookies section on the right sidebar to activate the functionality
1. Pass the mouse over the website's iframe to get quick info about it 

<img width="742" alt="Google Chrome showing the Frames Overlay with the PSAT Extension" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/82ab33ab-9e19-4fc3-b80f-33805b089756">


## General Debugging Actions

Analyzing websites for potential breakages is not a trivial process, as there are many factors to consider and lots of information to be grasped. This section describes various factors that can be considered during a site analysis.

### **Authentication**

Some functionality of a site can be tested without authentication and/or login requirements, while others require users to have an account of some sort and be properly authenticated. Both scenarios must be analyzed.

### **Desktop/Mobile**

Tests/analysis must be performed on both desktop and mobile, if and only if the mobile version of the site is entirely different.

### **Top–level navigation**

Quite often, top-level navigation happens *invisibly* to you when you only look at the URL bar, e.g. through server-side 301 redirects.

To see top-level navigation without the added noise of other requests. Toggle the “Doc” filter in the network panel as shown below, then look at the origin of the request URL to see if it is cross-site with the one that is in the URL bar.

![](https://lh5.googleusercontent.com/6P9RVjbKERsgDM2JGUjDq03-IeUvgReoQxVjLoSfk99R6oi4GQgyNB9D_-QORhZ_VRMhLl7Lti8_mWET97w7UAzghw37PVYWb1uMk3mLNxc9y2_Az1a90zY9qj8JTTQJthAZjqpHuri5MZzukVAXwr6iBhMRJMxErvR1nlalq7cUXXGcWTF7qI1F1fwjfjXIvmDAZmPVGKnJbLOGlrNmfUquOacEgK-SIJv58g)

### **JS/Network errors**

Lack of 3PC access can very frequently cause errors to be thrown in DevTools. One example is the bug “Nintendo - sign-in doesn't work”, where a 3P request to [accounts.nintendo.com](http://accounts.nintendo.com/) throws a 403 without the right cookies attached.

![](https://lh6.googleusercontent.com/aToiHmXtzmRh8NDYRwFbjI2kcUzDcUtB7vtVHq_pCC8hyiNyPtvI3cqsd742h5mIDf_SIMoEwEoK9Mv94w1hSmicpwmvZXuewy7cEGDbgMhenlzwZl_w-flt5ROdMox0LhmCuq0FXbkFvk-lW9vFkwyY3Vb_MIDFwG6o4Lq9pTLrjyzxSOfV4KveatVKIuHvmoihhfNzWBjbVWySBF3PO8a06_YFXD-UaEpVVA)

### **Partitioned storage**

A reported bug on “S-Bahn München status page” reported by https://www.s-bahn-muenchen.de/fahren/betriebslage, where lack of partitioned storage throws an error on the `localStorage` getter. Through the JS exception chain, we can actually see the origin of the file that ran this code, and derive that this could be the 3rd party in this case.

![](https://lh6.googleusercontent.com/znBDHSuyEGse0gP0SQHU4jJiVUy_3p7iGqSF7D0aL527ePlOQT5bQCgqdxb1_SouLxY5WMO2Od9oDymBpp3s4UU10QIc-VZVpRIXd7shsmkwPbf4ltVQsz90ZxiHhrNdCDmFmYhGWBUx7XaXHooV93aURc0PMt_NnRbtHAofkr5YeoUyhnKCRxFK4Cy0LAIAl5nTkdCQ9caJaTqfvhUeb5NdLHPvXgvoQE2hCw)

### **Cross-site requests in the network tab**

Sometimes sites send 3P network requests without the right cookies, but those requests don’t fail. They could just return a 200 because the user not being logged in isn’t considered an error state for them. Here, it’s helpful to search the network DevTools panel for “3rd-party requests” only by checking the corresponding checkbox. There might be a lot of noise here, e.g., calls to ads servers, but also some useful information. This is especially useful if you have some repeatable way of triggering the breakage on the site, e.g., by clicking on a login button or similar. Unless the site is using JS-based cookie access through `document.cookie`, there should be an outgoing network request at that moment.

### **Authenticated embeds**

Sometimes embedded iframes can appear to be part of the 1P experience on the website. To detect them, it can be helpful to use the DOM inspector in DevTools (starting with the UI that isn’t loading or is showing an error to the user) to figure out if it’s really an iframe. Then, the source of that iframe is likely the 3P that is involved and it’s often an “auth embeds” use case that can be solved with `requestStorageAccess`, or even CHIPS if there’s no top-level navigation.

An example of this is Mindbody Inc. which serves embedded iframes for website owners to allow their customers to book appointments. This iframe looks a lot like it’s part of the website, but reveals itself in the inspector.

![](https://lh5.googleusercontent.com/S8TAjyBXswXkrV_wnXHt2YbDzFQMqjGca97z4-8KoT9Uaonw8MyjN_SR4fCERH4cdz5NarXkabljsde5Y_A1PtMkK3xRAOzptnx1bB8PjxneQc5FyB6V4Nzp5odXrhdMUcQwnfG1adhBW5fLF1HHnfZDXQwuX8nZW87tr_9IO7QsLB4banjcv5gVnqJNNKH1aepPAtq-VMkc1ZYdxUlY-eHKlkfkQ3swWGfkYQ)

### **Checking for known breakages: GSI v2**

GSI v2 is a legacy library from Google Identity that is integrated with plenty of sites and, unfortunately, relies on cross-site cookies to work. This is a very common source of failure and is especially likely when the user-facing breakage is “can not log in”. There are some tips for identifying whether GSI v2 is in use here.

### **DOM Storage usage**

Some sites are not trying to use cookies, but instead `LocalStorage` or Quota Storage like `IndexedDB`. These can often be spotted by observing exceptions being thrown, see [Look at JS/Network errors](https://docs.google.com/document/d/1SlFMWZx8YPDqgMRQi1mjR69v1mUvVDORMfQgKisS0FU/edit?resourcekey=0-A2dMtm454TShDq4mPHTQYg#bookmark=id.24lfqsh6zaqj).
