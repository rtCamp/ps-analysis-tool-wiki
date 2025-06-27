The Protected Audience API is a privacy-preserving technology that allows advertisers to show targeted ads without tracking user behavior across different websites. This approach eliminates the need for third-party cookies and prevents cross-site tracking, enhancing user privacy.

The Protected Audience API works by creating “interest groups” based on user interactions with specific websites or content. These interest groups are stored on the user's device, not on a central server. When a user visits a website that participates in the API, the browser checks for relevant interest groups and selects ads accordingly. This process happens locally, without sharing user data with third parties, thus enhancing privacy.

### Key Features
- **Interest Groups**: Websites can add users to interest groups based on their interactions. For example, if a user frequently visits a sports website, they might be added to a "sports" interest group.

- **Ad Selection**: When a user visits a participating website, the browser selects ads from the interest groups stored on the user's device. This selection is done without sharing user data with advertisers or third parties.

- **Privacy**: The API is designed to protect user privacy by keeping interest groups on the user's device and not sharing personal data with advertisers.

- **Transparency**: Users can view and manage their interest groups through browser settings, allowing them to opt-out of interest-based advertising if they choose.

### Benefits
- **Enhanced Privacy**: By eliminating third-party cookies and cross-site tracking, the Protected Audience API enhances user privacy.

- **Targeted Advertising**: Advertisers can still show relevant ads to users based on their interests without compromising privacy.

- **User Control**: Users have control over their interest groups and can manage their preferences easily.

## Interest Groups

An interest group is a collection of users who share a common interest, similar to a remarketing list, each interest group has an owner, which is typically an advertiser, publisher, or ad tech platform.

Interest groups allow advertisers to target ads to users who have previously shown interest in their products or services, without relying on third-party cookies

When a user visits a website, the website can ask the user's browser to add the user to an interest group. 

The browser stores this information locally on the user's device. When the user visits a website that participates in the Protected Audience API, that stored information can be analyzed by the Interest group tab.

It will list out interest groups as you perform actions on specific elements, for example, if you click on e-commerce site and clicked/searched for a shoe, it will trigger an action that will add an interest group in your browser

<img alt="PSAT Protected Audience - Interest Groups" src="images/private-advertising/protected-audience/psat_v0.14.1_interest_groups_2025_04_24.png" width="1200" />

The tab shows that list of interest groups along with useful information such as event time, access type, name, owner, and expiration time. You can also filter based on the similar categories.

## Ad Units

### Prebid
The PSAT extension is an essential tool for publishers, ad operations professionals, and anyone working with Prebid. It offers a transparent window into the complex world of header bidding, directly in your browser. When you visit a website with Prebid-enabled ads, the extension populates with a wealth of actionable data.

[SCREENSHOT]

When you visit the site using prebid and check the Ad unit from the PSAT extension, you will instantly see ad unit codes, sizes, and active bidders, with the ability to filter by each bidder for focused analysis.

### PAAPI
The Protected Audience API allows publishers to conduct on-device ad auctions in the user's browser. This means that when a user visits a website with an ad unit that's configured to use the Protected Audience API, the browser will run an auction to determine which ad to display.

<img alt="PSAT Protected Audience - Ad Units" src="images/private-advertising/protected-audience/psat_v0.14.0_ad_unit_2025_04_09.png" width="1200" />

The tab shows a list of ad units along with Ad unit Code, container size, bidders, you can also click on ad unit to focus and get detailed information in a popup. We can also filter ad units based on bidders.

## Auctions

### Prebid
A Prebid auction is a process that allows a website's ad space to be offered to many advertisers simultaneously, creating a competitive, real-time marketplace. It is managed by a piece of code called Prebid.js located in the website's header.

[SCREENSHOT]

The Auctions tab in the PSAT extension provides a granular, real-time log of the entire Prebid auction lifecycle. Track every ad unit from initialization to completion, monitoring key events like bid requests and wins. Powerful filtering options also allow you to instantly sort the data by event type, specific bidders, or bid CPM to quickly debug and analyze auction performance.

### PAAPI
An auction is a process where an ad space seller (like a website publisher) makes ad space available for bidding, and advertisers (buyers) compete to have their ad displayed.
This all happens within the user's browser, preserving privacy.

The Auctions tab gives detailed information for each Ad Unit and for every event, so users can understand the auction process better.

<img alt="PSAT Protected Audience - Auctions" src="images/private-advertising/protected-audience/psat_v0.14.1_auctions_2025_04_24.png" width="1200" />

The detailed information includes event time, name, interest group origin, interest group name, bid amount, bid currency, and component seller.

The auctions are listed for each cycle and the auction events are listed as the auction make progresses. 

You can also filter the auction process for particular event, interest group owner, group name, bid (amount), bid currency and component seller.

When you click and peculiar Ad Unit or auction event, you can view raw data in JSON format at footer panel. 

## Bids

### Prebid
A bid is a formal offer from an advertiser or their representative (known as a "bidder" or "demand partner") to purchase a specific ad impression on a publisher's website or app. Essentially, it's the price an advertiser is willing to pay to display their ad to a particular user at a specific moment.

These bids are the fundamental currency of the Prebid auction, a process also known as header bidding. This system allows publishers to offer their ad inventory to multiple bidders simultaneously, fostering competition and maximizing revenue.

[SCREENSHOT]

In the extension's Prebid tab, you can view detailed bid information, including event time, bidder, bid value (CPM), currency, ad unit code, ad container size, and ad type. You can also identify bidders who did not participate in the auction and filter by any of these parameters for easier analysis.

### PAAPI
In the Protected Audience API, bids are a crucial component of the ad auction process. bids in the Protected Audience API are the way advertisers express their interest in showing an ad to a user within a privacy-preserving, on-device auction environment.

<img alt="PSAT Protected Audience - Bids" src="images/private-advertising/protected-audience/psat_v0.14.1_bids_2025_04_24.png" width="1200" />

The Bids section contains two subsections, Received Bids and No Bids

The first section of Received Bids show list of bidders along with information such as event time, bid value, currency, Ad Unit, Ad Container Size, Media Type. You can also filter using the bidder using the same information.

#### No Bids
[SCREENSHOT]
The second section No Bids show list of bidders along with information of no bid.

#### Timeline

[SCREENSHOT]

The Timeline is a diagnostic feature in the Privacy Sandbox Analysis Tool (PSAT) that provides developers with a sequential, visual breakdown of the events related to the Privacy Sandbox APIs.

### Prebid Utilities 
Prebid utilities are fundamental concepts and tools, primarily related to the Prebid.js library, that AdOps professionals and developers use to configure, debug, and manage header bidding.

#### 1. Config
This is the central configuration object in Prebid.js, managed primarily through the `pbjs.setConfig()` function. It controls the overall behavior of the Prebid auction

- **Prebid Config (`pbjs.setConfig`)** This is a single, powerful function used to set a wide range of options for the auction. It's the primary way to define rules and behaviors. Key configuration options include:
   - `priceGranularity`: Defines the increments of bid prices (e.g., $0.10 increments). This is crucial for how bids are passed to the ad server.
   - `bidderTimeout`: Sets the maximum time (in milliseconds) that Prebid will wait for bidders to respond before closing the auction.
   - `enableSendAllBids`: By default, Prebid only sends the winning bid to the ad server. Setting this to true sends all bids, which is useful for analytics but can create issues with URL length limits.
   - `debug`: When set to true, it enables verbose logging in the browser's console, showing detailed information about the auction, bids, and configurations.

##### example:
```javascript
pbjs.setConfig({
  priceGranularity: "medium",
  bidderTimeout: 700,
  debug: true
});
```
 - **Bidder Sequence** By default, all bid requests are sent to bidders simultaneously (asynchronously). However, a publisher might want to control the order in which requests are sent.
   - `bidderSequence`: This setting in `setConfig` allows you to specify a sequence. For example, you might want a high-performing bidder to get the request first, and then send requests to others. This is an advanced and rarely used feature, as it can reduce the benefits of a parallel auction.

##### example:
```javascript
pbjs.setConfig({
  bidderSequence: "sequential"
});
```
 - **Installed Modules** Prebid.js is modular. Your Prebid build file only includes the modules you need (e.g., specific bidder adapters, user ID modules).
   - `pbjs.getConfig('modules')`: This function returns a list of all installed modules, which can be useful for debugging and ensuring that the necessary components are loaded.
 - **Bidder Settings** This allows publishers to set specific configurations that apply to all bidders or to a particular bidder. This is a powerful way to customize behavior without changing the ad units themselves.
   - `pbjs.bidderSettings`: This is an object where you can define rules. For example, you can set a standard bid adjustment (e.g., to account for currency differences) for a specific bidder.

##### example: (Adjusting a specific bidder's bids up by 10%):
```javascript
pbjs.bidderSettings = {
  appnexus: {
    bidCpmAdjustment: function(bidCpm) {
      return bidCpm * 1.1;
    }
  }
};
```
 - **User IDs (from a config perspective)** This refers to how User ID modules are configured within the `setConfig` object. These modules fetch user IDs from various identity providers (like The Trade Desk's Unified ID, ID5, etc.) and make them available to bidders to improve user matching and increase bid values, especially in a post-cookie world.
##### example:
```javascript
pbjs.setConfig({
  userSync: {
    userIds: [{
      name: "id5Id",
      params: {
        partner: 1234
      },
      storage: {
        type: "cookie",
        name: "id5id.1234",
        expires: 90
      }
    }]
  }
});
```
 - **User Sync** This is a critical configuration that controls how and when Prebid.js synchronizes user IDs with demand partners. When a bidder doesn't win an auction, they may still want to "sync" their cookie with the user's browser.

   - The `userSync` object within `setConfig` controls this behavior. You can enable or disable it, and control which methods are used (e.g., `iframe` or `image` pixels). A proper user sync configuration is vital for increasing bidder participation and revenue.

 - **Prebid Server Config (`s2sConfig`)** This is used to configure "Server-to-Server" (S2S) header bidding, where the auction is run on an external server (a Prebid Server) instead of the user's browser (client-side). This reduces the amount of work the browser has to do.
   - `s2sConfig`: This object, passed into `setConfig`, tells Prebid.js which bidders should be called via the Prebid Server. It includes the server's endpoint URL, a timeout, and a list of S2S bidders.

#### Events
The Events Log is a dedicated tab that serves as a diagnostic tool by providing a clean, searchable, and sortable list of all warnings and errors that occur during a Prebid auction. It features a prominent count of total issues for a quick health check and allows users to efficiently find and analyze specific problems to debug the auction process.

#### Tools
These tools typically offer a centralized tab or panel with features that give you direct control over the auction on any live webpage. Key features in these advanced tools often include:
 - **Shortcut to GAM Console:** Provides a direct link to the associated Google Ad Manager (GAM) console, saving time by removing the need to search for it manually.
 - **Bid CPM Override:** A powerful testing utility that allows you to manually change the CPM value of any bid. This can be used to simulate a winning bid from a specific partner to ensure your ad server line items are configured correctly.

#### UserID
This refers to the **UserID** Module itself. It's a framework within Prebid that allows publishers to integrate various identity solutions. In a world where third-party cookies are disappearing, these modules are critical. They fetch user identifiers from different providers and attach them to the bid requests, allowing bidders to recognize the user and bid more accurately. Each ID solution (e.g., Unified ID 2.0, RampID, ID5) has its own submodule that can be included in the Prebid build.

#### Namespace
In JavaScript, a namespace is a global variable that holds all the functions and data for a library to avoid conflicts with other scripts on the page. For Prebid.js, the default namespace is `pbjs`. All Prebid commands start with this prefix (e.g., `pbjs.addAdUnits`, `pbjs.requestBids`). While it can be changed during the build process, `pbjs` is the universally recognized standard.

#### Version
This is simply the version number of the Prebid.js library file running on the page. Different versions have different features, bug fixes, and supported modules.
  - pbjs.version: You can type this directly into the browser console to check the exact version of Prebid.js that is currently loaded. This is one of the first things to check when debugging, as outdated versions can be the source of many problems.

## Worklet Breakpoints

The Worklet Breakpoints tab will enable you to set breakpoints directly within the Protected Audience API's worklet code, facilitating debugging and a deeper understanding of the auction process. Additionally, you will be able to use event listener breakpoints (located in the DevTools Sources tab under Event Listener) to pause execution within the event handler code after an ad auction event has occurred.

You will be able to set breakpoints for following events:

- Bidder Phase start
- Bidder Reporting Phase Start
- Seller Scoring Phase Start
- Seller Reporting Phase Start

> [!NOTE]
> These PSAT breakpoints are currently just for informational purposes, guiding users to set them using the DevTools interface. They are planned to become fully functional in future PSAT releases.

### References
- [Google's Privacy Sandbox](https://privacysandbox.com/)
- [Protected Audience API](https://developer.chrome.com/docs/privacy-sandbox/protected-audience/)
- [WebKit's Privacy-Preserving Advertising](https://webkit.org/blog/12345/privacy-preserving-advertising/)
- [Mozilla's Privacy-First Advertising](https://www.mozilla.org/en-US/privacy/advertising/)
- [W3C's Privacy and Advertising Working Group](https://www.w3.org/groups/wg/paw/)