The PSAT CLI is an alternative way to run analyses on your website. You can use a terminal to scan a given URL, or an entire sitemap to create a more extensive report. The CLI creates a local site showing similar information as PSAT's extension.

<img width="742" alt="PSAT Cookie Filters" src="images/psat-cli/cli-cookies-landing-page.png">

### Getting Started with PSAT CLI

To leverage the PSAT CLI's capabilities, follow these steps:

1. **Clone the Privacy Sandbox Analysis Tool Repository.**
2. **Install Dependencies:** Run `npm install` to set up all required dependencies.
3. **Build Generation:** Execute `npm run cli:build` to create a build located at `/dist/cli`.
4. **Running the CLI:** Launch the CLI by inputting a URL, sitemap URL, CSV file of URL set, or a path to a sitemap file.
  - Analyze a specific URL: `npm run cli -- -u https://bbc.com`.
  - Analyze URLs from a sitemap: `npm run cli -- -s https://example.com/sitemap_index.xml`.
  - Analyze URLs from a CSV file: `npm run cli -- -c /path/to/urlset.csv`.
  - Analyze a specific XML sitemap file: `npm run cli -- -p /path/to/sitemap.xml`.
  - **Note:** Wappalyzer, used for page technology analysis, may request permission for its Chromium instance. To bypass technology analysis, use the `nt` flag: `npm run cli -- -u https://bbc.com -nt`.

### CLI Use Cases

The PSAT CLI is not just a command-line version of the PSAT Extension; it's a versatile tool enabling various use cases:

- **Comprehensive Site Analysis:** Aggregated evaluation of entire sites (via sitemap.xml).
- **Pre-analysis Site Evaluation:** Offers guidance on scope and prioritization for site evaluation.
- **Integration into CI Pipeline:** Seamlessly incorporate PSAT CLI in CI pipelines to detect issues related to third-party cookie deprecation (3PCD).
- **Cookie Differential Analysis:** Compare site functionality with and without cookies to identify potential breakages.

### CLI Options

For a detailed understanding of the CLI options, you can use the `npm run cli -- --help` command:

```bash
$ npm run cli -- --help

> ps-analysis-tool@0.4.1 cli
> node dist/cli/index.js --help

Usage: index [options]

CLI to test a URL for 3p cookies

Options:
  -V, --version               output the version number
  -u, --url <value>           URL of a site
  -s, --sitemap-url <value>   URL of a sitemap
  -c, --csv-path <value>      Path to a CSV file with a set of URLs
  -p, --sitemap-path <value>  Path to a sitemap saved in the file system
  -ul, --url-limit <value>    Number of URLs to analyze
  -nh, --no-headless          Flag for running Puppeteer in non-headless mode
  -np, --no-prompts           Flag for skipping all prompts (Default options will be used)
  -nt, --no-technology        Flag for skipping technology analysis
  -h, --help                  Display help for command

```
