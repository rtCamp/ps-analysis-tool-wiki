## What is Evaluation Environment?

An evaluation environment is a controlled testing space designed to isolate the PSAT extension and its interaction with third-party cookies. This environment provides a clean slate, simulating a browser with no prior history or existing cookies.

### Why is it important to have an evaluation environment?

**Isolation**: This environment is completely isolated from your browsing data, like browsing history and cookies. It's like having a newly installed browser without any past activity, ensuring the integrity of the testing process.

**Accuracy**: By removing external factors like browsing history and cookies, the evaluation environment allows PSAT to focus solely on how third-party cookies function. This reduces the chances of misleading results caused by unrelated browsing activity.

**Precision**: The controlled environment minimizes distractions and extraneous data, allowing for more precise identification of any issues related to third-party cookies.

### How to set up an evaluation environment for PSAT?

Preparing the environment for analyzing and debugging the behavior of cookies and storage APIs during browsing sessions encompasses two aspects: (1) access to Chrome instances with and without Privacy Sandbox APIs enabled and restricted use of third-party cookies; and (2) install PSAT.

## Prerequisites

- The PSAT extension only works with **Chrome version 113 or newer**. You can see what version of Chrome you're using by going to this address in your browser: `chrome://settings/help`.
For the best experience, make sure you keep Chrome updated to the latest version.

- To improve your PSAT debugging experience, please disable Chrome's preloading feature. Navigate to `chrome://settings/performance#speed` and uncheck "Preload Pages".

## Spinning Chrome Instances from Command Line

PSAT's repository includes a set of custom commands streamlining the setup process, by creating ephemeral instances of Chrome for testing with specific configurations. To install these commands, run the following in your terminal:

### Installation

Run the following command

1. Download the PSAT Launcher script:

```bash
curl -s -f -L "https://raw.githubusercontent.com/GoogleChromeLabs/ps-analysis-tool/launcher-update/bin/install.sh" -o "install.sh"
chmod +x install.sh
```
2. Install the PSAT Launcher script:
```bash
./install.sh
```
3. To finalize the installation, close and reopen your terminal. or run source `~/.bashrc` or `~/.zshrc` depending on your shell.

eg:
```bash
source "/Users/myuser/bin/chrome_launcher.sh"
```
4. To verify the installation, run the following command in your terminal:
```bash
chrome-pat-ps
```
It should open a new chrome window with the PSAT extension installed and the Privacy Sandbox APIs enabled.

Following options are available to you for installing the PSAT Launcher script:

1. **Override the installation channel**: You can specify a different Chrome channel (Stable, Beta, Dev, Canary) by using the `--chrome-channel` option.

2. **Override the Chrome version**: If you want to install a specific version of Chrome, use the `--chrome-version` option with the desired version number (e.g., 128).

3. **Override the PSAT version**: To install a specific version of the PSAT extension, use the `--psat-version` option with the desired version tag (e.g., v0.14.1).

4. **Uninstall the script**: If you want to remove all files created by this script, use the `--uninstall` option.

5. **Display help message**: Use the `--help` option to see the usage instructions and available options.

```bash
./install.sh --help               
Usage: ./install.sh [OPTIONS]

Options:
  --chrome-channel CHANNEL    Override the installation channel (Stable, Beta, Dev, Canary)
  --chrome-version VER        Override the Chrome version to be installed (specific milestone number, e.g., 128)
  --psat-version VER          Override the PSAT version to be installed
  --uninstall                 Remove all files created by this script and exit
  --help                      Display this help message and exit

Examples:
  ./install.sh --chrome-channel Beta
  ./install.sh --chrome-version 128
  ./install.sh --psat-version v0.14.1
```

Once the installation is completed you can use the following commands:

- `chrome-default`: Opens a Chrome instance with default settings.
- `chrome-3pcd`: Opens a Chrome instance with Third-Party Cookies blocked.
- `chrome-default-ps`: Opens a Chrome instance with Third-party cookies enabled and PSAT installed.
- `chrome-3pcd-ps`: Opens a Chrome instance with Third-Party Cookies blocked enabled and the Privacy Sandbox extension installed.
- `chrome-pat` : Opens a Chrome instance with Private Advertising Testing enabled.
- `chrome-pat-ps` : Opens a Chrome instance with Private Advertising Testing enabled and the Privacy Analysis Tool extension installed.

#### Updating the PSAT Launcher script

To keep the Chrome Launcher script current with the latest PSAT Extension, simply rerun the installation command:

1. Open your terminal.
2. Run the following command: 
```bash
curl -s -f -L "https://raw.githubusercontent.com/GoogleChromeLabs/ps-analysis-tool/launcher-update/bin/install.sh" -o "install.sh"
chmod +x install.sh
```
3. To finalize the update, close and reopen your terminal.

PSAT offers three straightforward installation methods:

## Installing PSAT from Chrome Web Store

PSAT is available in the [Chrome Web Store. &#10548;](https://chromewebstore.google.com/detail/privacy-sandbox-analysis/ehbnpceebmgpanbbfckhoefhdibijkef) To install, simply go to the linked store listing and click on `Add to Chrome`.

<img width="1200" alt="PSAT on Chrome Web Store" src="images/evaluation-environment/psat_v0.13.0_chrome_store_2025_03_24.png">

## Installation from the PSAT zip file

Go to the `Releases` Section in the PSAT GitHub repo: [bit.ly/psat-repo](https://bit.ly/psat-repo)

<img width="1200" alt="Install from zip file, step one" src="images/evaluation-environment/psat_v0.13.0_psat_repository_2025_03_24.png">

Select the latest version from the available tags:

<img width="1200" alt="Install from zip file, step two" src="images/evaluation-environment/psat_v0.13.0_download_zip_2025-03-24.png">

Expand the “Assets” dropdown, and click on the file named “extension-v*.*.zip” to download the extension.

<img width="1200" alt="Install from zip file, step three" src="images/evaluation-environment/psat_v0.13.0_download_zip_2025-03-24.png">

Go to `chrome://extensions` in the browser you want PSAT to be installed on, turn on `Developer mode`to [load the unpacked extension &#10548;](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/#load-unpacked), click the "Load unpacked" button, and select the unzipped extension folder.

<img width="1200" alt="Chrome Settings page, step four" src="images/evaluation-environment/psat_v0.13.0_chrome_extension_settings_2025-03-25.png">

## PSAT installation from source code

If you need to debug the extension or submit improvements, you can download the source code and run it locally.

- Clone this Privacy Sandbox Analysis Tool Repository
- Run `npm install` to install all dependencies
- `npm run ext:dev` or `npm run ext:build` to generate a build in `/dist/extension`
- Turn on "Developer mode" in `chrome://extensions` to [load the unpacked extension &#10548;](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics/#load-unpacked)
- Click on the "Load Unpacked" button and upload the `dist/extension` folder
