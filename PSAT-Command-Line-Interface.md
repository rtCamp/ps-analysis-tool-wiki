The PSAT CLI is an alternative way to run analysis on your website. You can use a terminal to scan a given URL or an entire sitemap to create a more extensive report. The CLI creates a local site showing information similar to PSAT's extension.

<img width="1200" alt="PSAT Cookie Filters" src="images/psat-cli/psat_v0.11.0_cli_landing_page_2024_09_12.png">

The sidebar section can help you navigate through various reports. The main section will help you identify all the cookies that are being used by a site.

Within the CLI Dashboard, you'll find the following sections: "Categories" and "Blocked Reasons.".

### Prerequisites

For the best performance of the PSAT CLI, it's recommended to use **Node.js version 18.1 or later.** To easily manage different Node.js versions, we recommend installing Node.js via [NVM (Node Version Manager)](https://github.com/nvm-sh/nvm#installing-and-updating). For detailed installation instructions, please refer to the official NVM documentation.

#### Installing and Using the Required Node.js Version using NVM

1. **Install the Node.js version specified in `.nvmrc` which is Node 18:**
   ```bash
   nvm install 18
   ```
2. **Use the installed Node.js version:**
   ```bash
   nvm use 18
   ```
3. **Verify Node.js installation:** Run `node --version` to confirm the correct version is being used.

### Getting Started with PSAT CLI

To leverage the PSAT CLI's capabilities, you can either choose to install it as a node package or clone the repository and build it locally.

#### Installing PSAT CLI as package

To install the [PSAT CLI from Node](https://www.npmjs.com/package/@google-psat/cli), follow these steps:

1. **Install the PSAT CLI:** Run `npm i -g @google-psat/cli` to install the PSAT CLI globally.
2. **Run the CLI Audit:** Execute `psat https://example.com` followed by the URL you want to analyze.
3. **Help Command:** Use the `psat --help` command to view all available options.

The PSAT CLI is now installed, and it's ready to use. You can learn more about CLI options from the node package [README](https://github.com/GoogleChromeLabs/ps-analysis-tool/blob/main/packages/cli/README.md). The CLI will generate a report and store it in the `/out/` directory by default.

<img idth="1200" alt="PSAT's npm page" src="images/psat-cli/psat_v0.9.0_npm_home_page_2024_06_30.png">

#### Clone and Build Locally

To install the PSAT CLI locally, follow these steps:

1. **Clone the Privacy Sandbox Analysis Tool Repository.**
2. **Install Dependencies:** Run `npm install` to set up all required dependencies.
3. **Build Generation:** Execute `npm run build:all` to build CLI locally.
4. **Running the CLI:** Start the analysis by specifying a URL, a sitemap URL, a CSV file of the URL set, or a path to a sitemap file.

The CLI provides the following options as a source to create a report:

- Analyze a specific URL: `npm run cli https://example.com` or `npm run cli -- -u https://example.com`.
- Analyze CSV or XML sitemap from URL : `npm run cli -- -s https://example.com/sitemap_index.xml`.
- Analyze CSV for XML sitemap from file path : `npm run cli -- -f /path/to/urlset.csv`.

To customize and change the behavior of the analysis of those reports, the CLI also supports options:

  - Make PSAT reports available in different languages for user convenience: `npm run cli -- -u https://example.com -l ja`.
  - Limit the number of URLs to analyze from a specific sitemap or CSV: `npm run cli -- -f /path/to/sitemap.xml -n 10`
  - Export the report to a specific folder without creating a dashboard URL: `npm run cli -- -u https://example.com -o <path-to-dir>` or `npm run cli -- -u https://example.com --out-dir <path-to-dir>`.
  - GDPR banners are accpeted by default, you can ignore them by using `-i` flag : `npm run cli -- -u https://example.com -i`.
  - If your machine is processing any long task or a specific cookie is set after a particular time you can set a waiting time in milliseconds for the report being generated: `npm run cli -- -u https://example.com --wait 50000`
  - If your machine has a high number of cores, you can set the number of tabs to open in parallel during sitemap or CSV analysis: `npm run cli -- -s https://example.com/sitemap.xml -c 5`, by default it opens 3 tabs.
  - If you want to run the CLI in non-headless mode, you can use the `-d` flag: `npm run cli -- -u https://example.com -d`.
  - Want to see detailed information about what the CLI is doing? Use the `-v` flag. This enables verbose mode, showing you each step as it happens. Here's an example with a sample URL: `npm run cli -- -u https://example.com -v`
  - If you want to run the CLI in quiet mode, you can use the `-q` flag: `npm run cli -- -u https://example.com -q`.

> [!IMPORTANT]
> When using a URL with multiple parameters joined by ampersands (&), surround the entire URL with double quotes (") to avoid errors, the quote ensures that it treats entire URL as string. For example: `npm run cli -- -u "https://example.com?param1=value1&param2=value2"`.

### CLI Use Cases

The PSAT CLI is not just a command-line version of the PSAT Extension; it's a versatile tool enabling various use cases:

- **Comprehensive Site Analysis:** Aggregated evaluation of entire sites (via sitemap.xml).
- **Pre-analysis Site Evaluation:** Offers guidance on scope and prioritization for site evaluation.
- **Integration into CI Pipeline:** Seamlessly incorporate PSAT CLI in CI pipelines to detect issues related to the blocking of third-party cookies.
- **Cookie Differential Analysis:** Compare site functionality with and without cookies to identify potential breakages.
- List the Blocked cookies' reasons to guide developers in solving those issues.
- Help developers by allowing them to download detailed reports.

### CLI Options

For a detailed understanding of the CLI options, you can use the `npm run cli -- --help` or `psat --help` command:

```bash
$ npm run cli -- --help

> ps-analysis-tool@1.0.0 cli
> node packages/cli/dist/main.js --help

Usage: npm run cli [website-url] -- [options]

CLI to test a URL for 3p cookies.

Options:
  -V, --version               output the version number
  -u, --url <url>             The URL of a single site to analyze
  -s, --source-url <url>      The URL of a sitemap or CSV to analyze
  -f, --file <path>           The path to a local file (CSV or XML sitemap) to analyze
  -n, --number-of-urls <num>  Limit the number of URLs to analyze (from sitemap or CSV)
  -d, --display               Flag for running CLI in non-headless mode (default: false)
  -v, --verbose               Enables verbose logging (default: false)
  -o, --out-dir <path>        Directory to store analysis data (JSON, CSV, HTML) without launching the dashboard
  -i, --ignore-gdpr           Ignore automatically accepting the GDPR banner if present (default: false)
  -q, --quiet                 Skips all prompts; uses default options (default: false)
  -c, --concurrency <num>     Number of tabs to open in parallel during sitemap or CSV analysis (default: 3)
  -w, --wait <num>            Number of milliseconds to wait after the page is loaded before generating the report (default: 20000)
  -l, --locale <language>     Locale to use for the CLI, supported: en, hi, es, ja, ko, pt-BR (default: "en")
  -h, --help                  Display help for command

To learn more, visit our wiki: https://github.com/GoogleChromeLabs/ps-analysis-tool/wiki.
```

### CLI Output

PSAT offers a Command-line Interface (CLI) for users to interact with its functionalities. When users run PSAT commands through the CLI, they receive outputs in various formats depending on the parameters they use in the specific commands they've executed.

The following are two major outputs:

#### PSAT Dashboard

The PSAT dashboard is a locally run HTML application that processes the results from a JSON file for analysis and gives cookies results. It is served in the `/out/` directory; you can open it in any browser to get an interactive dashboard, just like the PSAT extensions panel. Due to the limitations mentioned in the discrepancy section, the PSAT CLI dashboard does not include all details.

<img idth="1200" src="images/psat-cli/psat_v0.11.0_cli_command_execution_2024_09_12.png" alt="PSAT CLI Command" />

#### Export Files

You can export analysis data as CSV or JSON files. These file formats store the data in a structured way that allows you to import it into other software tools like spreadsheets or data analysis programs. This allows for further customization and analysis of the PSAT results beyond what the dashboards might offer.

<img idth="1200" src="images/psat-cli/psat_v0.11.0_cli_download_button_2024_09_12.png" alt="PSAT Export Files" />

>[!NOTE]
>When exporting files without a specified output directory (using the `--out-dir` flag), relative paths are used. If the path doesn't exist, it will be created.

The exported reports contain the following files:

- **cookies-issues.csv** : The file contains a list of all the cookies that have been blocked, either in request or response.
- **cookies.csv** : The file contains a list of all the cookies that are created by the site, either by first-party or third-party frames.
- **report.csv** : The file contains an overall report of the cookies and their count based on various categories, domains, blocked cookies, etc.
- **report.json** : The file contains data for cookie data in a JSON format.
- **report.html** : The file contains the resume of the report in HTML format, similar to the Cookies' insight page.

### GDPR
The PSAT CLI can accept the GDPR banner if it is present on the site by default this feature is useful when analyzing websites that require user consent to access cookies. By accepting the GDPR banner, the CLI can analyze the site without any interruptions, providing a comprehensive report on the cookies used. If you want to disable this feature, you can use the `-i` flag.

PSAT identifies the common code libraries that power those cookie banners. If it recognizes one, it can automatically click "accept" for you, so you can get a detailed cookie report without having to interact with the site.

If PSAT doesn't automatically accept your site's GDPR banner, please [report](https://github.com/GoogleChromeLabs/ps-analysis-tool/issues/new?assignees=&labels=&projects=&template=feature-request.md&title=) the specific library that's causing the issue. The PSAT team can then add it to their detection list for a smoother experience in the future.

### Discrepancy between CLI and extension

The PSAT browser extension and the CLI tool both capture valuable insights, but they operate in different environments, leading to potential discrepancies. Understanding these differences will help you make informed decisions about choosing the appropriate tool based on the testing objectives and desired testing depth.

The following are three key reasons for discrepancies:

#### 1. Environment

The CLI tool utilizes a browser with the third-party cookie phase-out enabled. While the extension relies on Chrome settings for third-party cookies. This difference in environment can lead to discrepancies in website behavior, contributing to discrepancies.

#### 2. Duration

The CLI tool adopts a concise approach by launching a website and monitoring it for a brief period of 20 seconds. This short duration may not capture the complete set of cookies if certain scripts or functionalities take longer to load or execute, which may cause discrepancies. Using the flag `--wait` the developer can set a different waiting time.

#### 3. User Interactions

Unlike the PSAT extension, the CLI tool does not emulate user interactions during website monitoring. The lack of user interactions may impact how websites handle cookies, as certain cookies may load after user actions.

#### 4. Arm64 processor

Users with Mac Silicon processors should use the recommended version of node `18.20.0`, lower versions may impact report performance causing discrepancies in the final result. If you are using a old version of node the CLI will warning your with the following message:

```bash
  Degraded performance warning:
  Launching Chrome on Mac Silicon (arm64) from an x64 Node installation results in
  Rosetta translating the Chrome binary, even if Chrome is already arm64. This would
  result in huge performance issues. To resolve this, you must run Puppeteer with
  a version of Node built for arm64.
```

To fix it update the node version to the recommended version and run the report again.