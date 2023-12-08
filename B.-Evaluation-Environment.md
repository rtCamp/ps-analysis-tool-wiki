Preparing the environment for analyzing and debugging the behavior of cookies and storage APIs during browsing sessions encompasses two aspects: (1) access to Chrome instances with and without Privacy Sandbox APIs enabled and restricted use of 3P cookies; and (2) install PSAT.

## Spinning Chrome Instances from Command Line

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

## Installing PSAT from Chrome Web Store

PSAT is available in the [Chrome Web Store](https://chromewebstore.google.com/detail/privacy-sandbox-analysis/ehbnpceebmgpanbbfckhoefhdibijkef). To install, simply go to the linked store listing and click on `Add to Chrome`. 

<div align='left'>
<img width="742" align="center" alt="PSAT on Chrome Web Store" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/b664c5ed-a858-447c-9481-ef816d05b353">
</div>


## Installation from the PSAT zip file

Go to the `Releases` Section in the PSAT github repo: bit.ly/psat-repo

<img width="742" alt="Install from zip file, step one" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/2350fc22-c60e-49e2-9e3b-149cb78ebc30">

Select the latest version from the available tags:

<img width="742" alt="Install from zip file, step two" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/4dd56d99-46eb-4cad-8f4d-28d672062436">

Expand the “Assets” dropdown, and click on the file named “extension-v*.*.zip” to download the extension.

<img width="742" alt="Install from zip file, step three" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/c1184b95-bc92-4ac3-8ea1-882e8e4485e7">

Go to `chrome://extensions` in the browser you want PSAT to be installed on, turn on `Developer mode`to [load the unpacked extension](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/#load-unpacked), click the "Load unpacked" button, and select the unzipped extension folder.

<img width="742" alt="Screenshot 2023-12-07 at 10 45 00 AM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/0b0c2a99-81ee-4433-a93e-98cfbd02a3ea">


## PSAT installation from source code 

If you need to debug the extension or submit improvements, you can download the source code and run it locally.

- Clone this Privacy Sandbox Analysis Tool Repository
- Run `npm install` to install all dependencies
- `npm run dev` or `npm run build` to generate a build in `/dist/extension`
- Turn on "Developer mode" in `chrome://extensions` to [load the unpacked extension](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/#load-unpacked)
- Click on the "Load Unpacked" button and upload the `dist/extension` folder

## Extension settings

PSAT can be configured to focus on the analysis of a single tab, or allow any number of open tabs. The recommended approach is to analyze browsing sessions from a single tab perspective, or a very small number of tabs, as doing so minimizes the amount of resources consumed by PSAT. 

To configure this capability of PSAT:

<img width="742" alt="Screenshot 2023-12-07 at 11 03 01 AM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/888f43b9-3820-488d-a174-c7f3aa0c1200">

And the select the appropiate option:

<img width="742" alt="Screenshot 2023-12-07 at 10 54 33 AM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/693f831c-c520-46e7-a218-5217ea9aa8ba">
























