### Methodology

Analyzing and Debugging Cookies with PSAT encompasses the following steps:

<div align='left'>
<img width="960" alt="Screenshot 2023-12-07 at 9 56 55 AM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/55e12372-f25a-435c-9810-9dcff05415ef">
</div>

## Preparing the environment

Preparing the environment for analyzing and debugging the behavior of cookies and storage APIs during browsing sessions encompasses two aspects: (1) access to Chrome instances with and without Privacy Sandbox APIs enabled and restricted use of 3P cookies; and (2) install PSAT.

### Spinning Chrome Instances from Command Line

PSAT's repository includes a set of custom commands streamlining the setup process, by creating ephemeral instances of Chrome with specific configurations. To install these commands, run the following in your terminal:

```bash
curl -sL https://rt.cx/psat | bash
```

The commands you can use are:

- `chrome-default`: Opens a Chrome instance with default settings.
- `chrome-3pcd`: Opens a Chrome instance with Third-Party Cookie Deprecation (3PCD) enabled.
- `chrome-default-ps`: Opens a Chrome instance with default settings and the Privacy Sandbox extension installed.
- `chrome-3pcd-ps`: Opens a Chrome instance with 3PCD enabled and the Privacy Sandbox extension installed.
PSAT offers three straightforward installation methods:

### Installing PSAT from Chrome Web Store

PSAT is available in the [Chrome Web Store](https://chromewebstore.google.com/detail/privacy-sandbox-analysis/ehbnpceebmgpanbbfckhoefhdibijkef). To install, simply go to the linked store listing and click on `Add to Chrome`. 

<div align='left'>
<img width="742" align="center" alt="PSAT on Chrome Web Store" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/b664c5ed-a858-447c-9481-ef816d05b353">
</div>


### Installation from the PSAT zip file

Go to the `Releases` Section in the PSAT github repo: bit.ly/psat-repo

<img width="742" alt="Install from zip file, step one" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/2350fc22-c60e-49e2-9e3b-149cb78ebc30">

Select the latest version from the available tags:

<img width="742" alt="Install from zip file, step two" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/4dd56d99-46eb-4cad-8f4d-28d672062436">

Expand the “Assets” dropdown, and click on the file named “extension-v*.*.zip” to download the extension.

<img width="742" alt="Install from zip file, step three" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/c1184b95-bc92-4ac3-8ea1-882e8e4485e7">

Go to `chrome://extensions` in the browser you want PSAT to be installed on, turn on `Developer mode`to [load the unpacked extension](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/#load-unpacked), click the "Load unpacked" button, and select the unzipped extension folder.

<img width="742" alt="Screenshot 2023-12-07 at 10 45 00 AM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/0b0c2a99-81ee-4433-a93e-98cfbd02a3ea">


### PSAT installation from source code 

If you need to debug the extension or submit improvements, you can download the source code and run it locally.

- Clone this Privacy Sandbox Analysis Tool Repository
- Run `npm install` to install all dependencies
- `npm run dev` or `npm run build` to generate a build in `/dist/extension`
- Turn on "Developer mode" in `chrome://extensions` to [load the unpacked extension](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/#load-unpacked)
- Click on the "Load Unpacked" button and upload the `dist/extension` folder

### Extension settings

PSAT can be configured to focus on the analysis of a single tab, or allow any number of open tabs. The recommended approach is to analyze browsing sessions from a single tab perspective, or a very small number of tabs, as doing so minimizes the amount of resources consumed by PSAT. 

To configure this capability of PSAT:

<img width="742" alt="Screenshot 2023-12-07 at 11 03 01 AM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/888f43b9-3820-488d-a174-c7f3aa0c1200">

And the select the appropiate option:

<img width="742" alt="Screenshot 2023-12-07 at 10 54 33 AM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/693f831c-c520-46e7-a218-5217ea9aa8ba">


## PSAT Extension Pop-up

- Access the URL that you want to analyze
- Locate the PSAT extension icon on the right side of the browser toolbar and click on it.
- Initiate the analysis process by clicking the "Analyze this tab" button.
- PSAT will present a detailed list of all cookies encountered in the specific URL Address.

## PSAT's Privacy Sandbox Panel in DevTools

DevTools provides a very large set of powerful capabilities enabling the understanding and debugging of every functional aspect of web development, including cookies and all storage APIs. PSAT expands DevTools with additional features to support tackling the deprecation of unrestricted 3P cookies, and the adoption of new privacy-preserving building blocks (i.e. Chrome APIs).

To access PSAT:

1. Access the URL that you want to analyze
1. Launch Chrome DevTools.
1. Navigate to the "Private Sandbox" tab.
1. Go to the cookies section at the right sidebar
1. Commence the analysis by clicking the "Analyze this tab" button.
1. PSAT will display a comprehensive list of all cookies set through the URL provided.

### PSAT Landing Page

PSAT features and capabilities aim at supporting developers transition towards a more private web, by shedding light on cookie usage, and the new building blocks available for implementing privacy-preserving solutions for features and capabilities of websites and apps. PSAT's landing paghe in DevTools reflects this goal:

<img width="742" alt="Screenshot 2023-12-07 at 5 07 13 PM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/9a38dace-5ee1-423b-8fae-98942533d03f">

On the left there are four sections corresponding to the main technical components of Privacy Sandbox: Cookies, Site Boundaries, Private Advertising, and Tracking Protection. Each of these sections corresponds to a feature area of PSAT, which are being developed progressively. 

### Cookies Landing Page

Click on the Cookies component in PSAT's landing page, which will open the Cookies landing page. As discussed above, PSAT can be configured to avoid using too much resources by restricting the tool to only analyze a single tab at a time. If that configuration setting is set, PSAT presents an `Analyze thus tab` button to switch the focus of the tool to the current tab. 

<img width="742" alt="Screenshot 2023-12-07 at 5 19 35 PM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/1c7d3973-a0c5-4a7a-bac2-8b6b70920373">

The Cookies landing page:

<img width="1532" alt="Screenshot 2023-12-07 at 5 25 30 PM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/a92fd0eb-d3e8-42df-ba17-13ef8c206403">


#### A note on _Cookie Accepted_ Column

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
- Run the CLI by providing a URL, sitemap url, CSV file of URL set or a path to sitemap file as input.
  - E.g. to analyze specific URL: `npm run cli -- -u https://bbc.com`.
  - E.g. to analyze all URLs from sitemap: `npm run cli -- -s https://example.com/sitemap_index.xml`.
  - E.g. to analyze set of URLs through CSV file: `npm run cli -- -c /path/to/urlset.csv`.
  - E.g. to analyze specific XML sitemap file: `npm run cli -- -p /path/to/sitemap.xml`.
  - Please note that the dependency (Wappalyzer), which analyzes page technologies, may require permission to use its instance of Chromium. If this happens, you have the option to skip the technology analysis by using the `nt` flag for the uninterrupted analysis of cookies.
  - E.g. `npm run cli -- -u https://bbc.com -nt`.

Once you create a report with the CLI, as in the image below, you will notice that a list with affected cookies will be listed in a different table. This is another advantage of using the CLI that allows quick access to the affected cookies.

![PSAT CLI - small](https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/330792/10329cc9-9362-4c8c-8092-e5770c882c7f)

## Reporting

This tool provides capabilities to make it easy for users to report breakages, and connect with existing Privacy Sandbox feedback and bug reporting channels. As you leverage the capabilities of the tool to analyze and debug your critical user journeys, you can report breakages or questions about your use cases and directly send them to the proper feedback channel. This way you would get answers to your issues, and will contribute to our collective effort to ensure the ecosystem is ready for a world without 3P cookies as we know them today.

<img width="937" alt="Reporting section with the PSAT Chrome Extension" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/67aff95d-4c9e-4eb9-b429-7a1b4c8c46d7">
