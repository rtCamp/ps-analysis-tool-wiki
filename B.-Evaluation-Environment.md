## **Chrome**

**▶️** Screencast: [Prepare Testing Environment](https://www.youtube.com/watch?v=EjbV4sUot4M)

To fully evaluate the potential impact of Privacy Sandbox changes on Chrome, we can leverage different Chrome Release versions (Stable, Canary, Beta, Dev).  Set up your evaluation environments by following the instructions below.

1. Download or update to the latest version of Google Chrome [Release Channels](https://support.google.com/chrome/a/answer/9027636?hl=en&ref_topic=9023245&sjid=8170039632193365418-AP), both Stable and versions which have implemented the restrictions and new capabilities that will be generally available after 3PCD: Chrome Canary, Chrome Beta, Chrome Dev.

2. Start Chrome versions with the relevant command line arguments:

**Linux OS**

```
google-chrome --test-third-party-cookie-phaseout --enable-features="FirstPartySets,StorageAccessAPI,StorageAccessAPIForOriginExtension,PageInfoCookiesSubpage,PrivacySandboxFirstPartySetsUI"
```
        
**Mac OS**

```        
open /Applications/Google\ Chrome.app --args --test-third-party-cookie-phaseout --enable-features="FirstPartySets,StorageAccessAPI,StorageAccessAPIForOriginExtension,PageInfoCookiesSubpage,PrivacySandboxFirstPartySetsUI"
```        

**Windows OS**

```        
"\Program Files\Google\Chrome\Application\chrome.exe" --test-third-party-cookie-phaseout --enable-features="FirstPartySets,StorageAccessAPI,StorageAccessAPIForOriginExtension,PageInfoCookiesSubpage,PrivacySandboxFirstPartySetsUI"
```
        
3. Consider using a new Chrome profile for a clean testing environment, or deactivate browser plugins/extensions that might interfere with cookies.

4. Enable Storage Partitioning (available in all release channels)

    - Go to chrome://flags#third-party-storage-partitioning
    - Select “Enable”
    - Restart your browser


![](https://lh5.googleusercontent.com/iSv0ZkoxWo9yhuXsCV8JfJxELEZt_JEikEILCZNHko5c_Rj5Zp8FU4DUhunZ9xE8n2sdqRfbNxb9LiCDJglQ7eAIwmbt-cbm_f5K9_om11iDgJJ3Rz0yRyI9i9Zw6YC1jAmweWp-qLeXBSEh8wN2ZYNRSG7S0k16-kSPKbfkWhtjg6U4iJfwFchwPxmy5WUOxgDnK2ybWyt1R8gKgiaQM9_TWBbQQ6SfEgTEAg)

5. Run tests on the different Chrome versions (Stable, Canary with 3PCD enabled)
    - In this methodology, we use the following naming convention
        - **Chrome Browser Open**: refers to the chrome instance with 3P cookie functionality available
        - **Chrome Browser Private**: refers to the chrome instance with 3P cookie and storage access APIs secured

6. During testing with 3P cookies blocked, turn cookies on and off via the URL bar
    - Click the small “eye” icon in the URL bar
    - Click on “site not working” -> “Allow cookies”

## **DevTools**

▶️ **Screencast**: [Analyzing site with DevTools](https://www.youtube.com/watch?v=_FErYRFIXHA)

DevTools is a powerful debugging companion to Chrome providing a myriad of vantage points to observe the operational execution of sites running on the browser. DT provides visibility to all data about cookies. To get to it some access points are:

1. **Open Chrome Developer Tools**: Right-click on the webpage and select "Inspect" or press Ctrl+Shift+I (Windows/Linux) or Cmd+Option+I (Mac) to open the Developer Tools.
2. **Navigate to the Network Tab**: In the Developer Tools window, navigate to the "Network" tab.
3. **Perform the Action**: Interact with the website, such as clicking a button, submitting a form, or navigating to a new page.
4. **Observe Network Activity**: In the "Network" tab, you'll see a list of network requests made by the webpage. Look for entries related to cookies, which might have a "Set-Cookie" header in the response or other relevant information.
5. **Inspect Cookies**: Click on a network request entry to view its details. Look for the "Headers" tab, which should include information about cookies, including those being added or modified as a result of the action you performed.

You can learn more about DevTools [here](https://developer.chrome.com/docs/devtools/).  We will leverage DT capabilities when performing the tests on specific CUJs as described below.

## **PSAT: CLI**

▶️ **Screencast**: PSAT: CLI.

The PSA CLI provides access to functionality similar to the PSA Extension, and makes it accessible through the command line. The CLI enables the following use cases:

- Aggregated analysis of the full site (i.e. sitemap.xml)
- Site evaluation pre-analysis ⇒ Guidance on scope and prioritization
- CLI for CI: Integrate the PSA CLI into your CI pipeline and detect potential areas of issues related to 3PCD
- Testing for breakages by executing two access runs, with and without cookies being blocked, and providing a “cookie differential” analysis

The current version of the CLI is limited as it does not include yet an extensive automated interaction model to ensure that aspects such as Cookie Consent Banners are accounted for when exercising CUJs. But we are making progress quickly to remove this limitation. Stay tuned!

## **PSAT: Extension**

**▶️ Screencast**: PSAT.

The Privacy Sandbox Analysis Tool (PSAT) is a Chrome DevTools extension to assist developers in the analysis and debugging of cookie, storage, and PS API usage during Browsing Sessions.

- Download and install PSAT, which is being developed as an open-source project and you can access the project [here](https://github.com/GoogleChromeLabs/ps-analysis-tool).
- Load the website on the evaluation environment (i.e. Chrome Stable, Chrome Canary)
- Open DevTools:
    - On Mac : Command(⌘) + Option(⌥) + C
    - Windows, Linux, ChromeOS: Control(⌃) + Shift(⇧) + C
- Click on the “Privacy Sandbox” Tab
- Click on the *Cookies > Site Frame*
- Open filters by clicking on the Filter icon
- Add filters
    - ***E.g. Scope: Third Party*** (filters list to show all 3P cookies)
    - ***E.g. Cookie Accepted: False*** (filters list to show all cookies that were not set)