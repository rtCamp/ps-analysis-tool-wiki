The Chrome extension provides capabilities surfaced via the extension pop-up and as Devtools panel. The CLI implementation parses a sitemap provided as input and outputs a JSON file listing all cookies set while navigating through the URLs in the sitemap. Follow the following steps to get the extension installed in your browser. 

## Installing and Running PSAT

### Build PSAT from source

- Clone this Privacy Sandbox Analysis Tool Repository
- Run `npm install` to install all dependencies
- `npm run dev` or `npm run build` to generate a build in `/dist/extension`
- Turn on "Developer mode" in `chrome://extensions` to [load the unpacked extension](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/#load-unpacked)
- Click on the "Load Unpacked" button and upload the `dist/extension` folder


### Install PSAT from zip file

- Alternatively, you can download the extension zip file from the [latest release](https://github.com/GoogleChromeLabs/ps-analysis-tool/releases) and unzip it.
- Turn on "Developer mode" in `chrome://extensions` to [load the unpacked extension](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/#load-unpacked)
- Click the "Load unpacked" button and select the unzipped extension folder.

### Build and Run PSAT's CLI

- Clone this Privacy Sandbox Analysis Tool Repository
- Run `npm install` to install all dependencies
- `npm run cli:build` to genrate a build in `/dist/cli`.
- Run the CLI, providing a URL or a sitemap as input.
  - E.g. `npm run cli -- -s https://example.com/sitemap_index.xml`.
  - E.g. `npm run cli -- -u https://bbc.com`.
  - Please note that the dependency (Wappalyzer), which analyzes page technologies, may require permission to use its instance of Chromium. If this happens, you have the option to skip the technology analysis by using the `nt` flag for uninterrupted analysis of cookies.
  - E.g. `npm run cli -- -u https://bbc.com -nt`. 


## PSAT Landing Page

The features and capabilities of this tool help you (developers) with the transition towards a more private web, by shedding light on data and context as you go about implementing privacy-preserving solutions to the features and capabilities of your websites and apps. The main functional areas of the tool are the following. 

<img width="937" alt="Screenshot 2023-10-04 at 3 34 36 PM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/4352e62f-832b-4cce-800f-41a767e1bcc3">


## Cookie Data Manipulation and Analysis

DevTools provides access to lots of information regarding every functional aspect of the browser, including cookies. This extension expands a bit the capabilities of DevTools and provides additional ways to slice and dice cookie data, making it easier for everyone to understand the behaviors of cookies in different scenarios.

<img width="937" alt="Screenshot 2023-08-21 at 1 41 13 PM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/e20cb6d0-f682-4c20-98c7-3b5e69be32df">


## Frame Overlays

Frame overlays make it easy to associate third-party cookies with embedded iframes.

<img width="937" alt="Screenshot 2023-10-04 at 3 32 03 PM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/82ab33ab-9e19-4fc3-b80f-33805b089756">

## Knowledge Access Points

The final goal of this tool is to make it easy to understand the role of 3P cookies on critical user journeys all the relevant aspects of Privacy Sandbox and the phasing out of 3P cookies. As you use the tool to analyze and debug your use cases, you will encounter links to documentation and other sources of information to support your learning and understanding as you navigate the transition to a more private web. 

## Reporting

This tool provides capabilities to make it easy for users to report breakages, and connect with existing Privacy Sandbox feedback and bug reporting channels. As you leverage the capabilities of the tool to analyze and debug your critical user journeys, you can report breakages or questions about your use cases and directly send them to the proper feedback channel. This way you would get answers to your issues, and will contribute to our collective effort to ensure the ecosystem is ready for a world without 3P cookies as we know them today.

<img width="937" alt="Screenshot 2023-10-10 at 4 02 12 PM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/67aff95d-4c9e-4eb9-b429-7a1b4c8c46d7">
