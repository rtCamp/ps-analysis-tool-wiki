The Chrome extension provides capabilities surfaced via the extension pop-up, the Side Panel, and as Devtools panel. The CLI implementation parses a sitemap provided as input and outputs a JSON file listing all cookies set while navigating through the URLs in the sitemap. Follow the following steps to get the extension installed in your browser. 

- Clone this Cookie Analysis Tool Repository
- `npm install` Install all dependencies

# Extension (from source)

- `npm run dev` or `npm run build` to generate a build in `/dist/extension`
- Turn on "Developer mode" in `chrome://extensions` to [load the unpacked extension](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/#load-unpacked)
- Click on the "Load Unpacked" button and upload the `dist/extension` folder



# Unpacked Extension (from zip file)

- Alternatively, you can download the extension zip file from the [latest release](https://github.com/GoogleChromeLabs/ps-analysis-tool/releases) and unzip it.
- Turn on "Developer mode" in `chrome://extensions` to [load the unpacked extension](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/#load-unpacked)
- Click the "Load unpacked" button and select the unzipped extension folder.



# CLI

- `npm run cli:build` to genrate a build in `/dist/cli`.
- Run the CLI, providing a URL or a sitemap as input.
  - E.g. `npm run cli -- -s https://example.com/sitemap_index.xml`.
  - E.g. `npm run cli -- -u https://bbc.com`.
- Please note that the dependency (Wappalyzer), which analyzes page technologies, may require permission to use its instance of Chromium. If this happens, you have the option to skip the technology analysis by using the `nt` flag for uninterrupted analysis of cookies.
  - E.g. `npm run cli -- -u https://bbc.com -nt`. 