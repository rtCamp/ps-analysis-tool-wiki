The Privacy Sandbox Analysis Tool (PSAT) is a tool that helps developers understand and manage cookies to prepare for changes to improve privacy for users on the web. It provides several features to help you:

- **Identify third-party cookies**: PSAT can help you identify third-party cookies being set on your site, which can be affected by third-party cookies deprecation.
- **Report breakages**: PSAT CLI provides a way for you to easily report breakages that you find in the Privacy Sandbox, which can help to improve the ecosystem.

## Installing and Running PSAT

PSAT offers three straightforward installation methods:

### 1. Chrome Web Store Installation

- Visit the PSAT [extension page](https://chromewebstore.google.com/detail/privacy-sandbox-analysis/ehbnpceebmgpanbbfckhoefhdibijkef) on the Chrome Web Store. 
- Click the "Add to Chrome" button.
- Grant the necessary permissions when prompted.

![PSAT Extension Page](https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/330792/60f9e403-8627-44bc-a0a3-b8db3026432f)

#### Extension settings

PSAT analyses only one tab at a time by default to ensure minimum system usage. Otherwise, analysis can be resource-intensive depending on hardware limitations and the total number of open tabs at a time.

However, you can change this behavior under **Extension options > Total number of allowed tabs to be processed together:** and choose **No Restriction**

1. You can find the extension settings in the extension details:

![PSAT Extension details](https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/330792/17d15053-60be-4e58-bb40-b2a5150b1533)

2. Go to "Extension options"

![Extension details panel](https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/330792/003f08da-5a27-4c56-b734-f3b53b9f6843)

3. Select the Behavior that you prefer:

<img width="771" alt="settings PSAT" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/330792/11f2bbdb-59c7-4c15-8aa8-586c59d9a66f">


### 2. Installation from the PSAT zip file

This option is an alternative if you want to install a specific version. You can find it in our repository.

- You can download the extension zip file from the [release list](https://github.com/GoogleChromeLabs/ps-analysis-tool/releases) and unzip it.
- Turn on "Developer mode" in `chrome://extensions` to [load the unpacked extension](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/#load-unpacked)
- Click the "Load unpacked" button and select the unzipped extension folder.

### 3. PSAT Source code installation

If you need to debug the extension or submit improvements, you can download the source code and run it locally.

- Clone this Privacy Sandbox Analysis Tool Repository
- Run `npm install` to install all dependencies
- `npm run dev` or `npm run build` to generate a build in `/dist/extension`
- Turn on "Developer mode" in `chrome://extensions` to [load the unpacked extension](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/#load-unpacked)
- Click on the "Load Unpacked" button and upload the `dist/extension` folder

## Utilizing PSAT

Once PSAT is successfully installed, you can access its functionalities through the Chrome extension pop-up or the DevTools panel.

### Chrome Extension Pop-up:

- Access the URL that you want to analyze
- Locate the PSAT extension icon on the right side of the browser toolbar and click on it.
- Initiate the analysis process by clicking the "Analyze this tab" button.
- PSAT will present a detailed list of all cookies encountered in the specific URL Address.

### DevTools Panel:

1. Access the URL that you want to analyze
1. Launch Chrome DevTools.
1. Navigate to the "Private Sandbox" tab.
1. Go to the cookies section at the right sidebar
1. Commence the analysis by clicking the "Analyze this tab" button.
1. PSAT will display a comprehensive list of all cookies set through the URL provided.

## PSAT main functionalities

Based on version `0.3.2` We will list three main functionalities, but more functionalities are planned to be included in future versions. The features are:
- PSAT Landing Page
- Cookie Data Manipulation and Analysis
- Frame overlay

### PSAT Landing Page

The features and capabilities of this tool help you (developers) transition towards a more private web, by shedding light on data and context as you implement privacy-preserving solutions to the features and capabilities of your websites and apps. The main functional areas of the tool are as follows. 

<img width="937" alt="Privacy Sandbox Analysis tool landing page" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/4352e62f-832b-4cce-800f-41a767e1bcc3">

### Cookie Data Manipulation and Analysis

DevTools provides access to lots of information regarding every functional aspect of the browser, including cookies. This extension expands the capabilities of DevTools and provides additional ways to slice and dice cookie data, making it easier for everyone to understand the behaviors of cookies in different scenarios.

<img width="937" alt="Cookies Data Manipulation Panel" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/e20cb6d0-f682-4c20-98c7-3b5e69be32df">

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

<img width="937" alt="Google Chrome showing the Frames Overlay with the PSAT Extension" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/82ab33ab-9e19-4fc3-b80f-33805b089756">


## Build and Run PSAT's CLI

PSAT CLI is another alternative to analyze your website. You can use a terminal to scan an entire sitemap to create a more extensive report. I will create a webpage with a similar structure to the Chrome extension. Including an option to download a CSV file.

- Clone this Privacy Sandbox Analysis Tool Repository
- Run `npm install` to install all dependencies
- `npm run cli:build` to generate a build in `/dist/cli`.
- Run the CLI, providing a URL or a sitemap as input.
  - E.g. `npm run cli -- -s https://example.com/sitemap_index.xml`.
  - E.g. `npm run cli -- -u https://bbc.com`.
  - Please note that the dependency (Wappalyzer), which analyzes page technologies, may require permission to use its instance of Chromium. If this happens, you have the option to skip the technology analysis by using the `nt` flag for the uninterrupted analysis of cookies.
  - E.g. `npm run cli -- -u https://bbc.com -nt`.

Once you create a report with the CLI, as in the image below, you will notice that a list with affected cookies will be listed in a different table. This is another advantage of using the CLI that allows quick access to the affected cookies.

![PSAT CLI](https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/330792/39a7f797-c381-41cd-a0fd-e07ed36d97df)

## Reporting

This tool provides capabilities to make it easy for users to report breakages, and connect with existing Privacy Sandbox feedback and bug reporting channels. As you leverage the capabilities of the tool to analyze and debug your critical user journeys, you can report breakages or questions about your use cases and directly send them to the proper feedback channel. This way you would get answers to your issues, and will contribute to our collective effort to ensure the ecosystem is ready for a world without 3P cookies as we know them today.

<img width="937" alt="Reporting section with the PSAT Chrome Extension" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/67aff95d-4c9e-4eb9-b429-7a1b4c8c46d7">
