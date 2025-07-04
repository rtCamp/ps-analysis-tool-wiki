Welcome to the Privacy Sandbox Analysis Tool (PSAT) Wiki!

The [Privacy Sandbox initiative &#10548;](https://privacysandbox.com/) aims to create technologies that both protect people's privacy online and give companies and developers tools to build thriving digital businesses. The main goal of Privacy Sandbox is to provide in Chrome the functionality and user choice to enable the capabilities that keep online content and services freely accessible by everyone, while reducing cross-site tracking on behalf of users.

## Transitioning to a more privacy-preserving web

If you are website developer, or a developer of components used by websites, and you use third-party cookies to achieve your goals the good news is that, by moving away from using unpartitioned third-party cookies and take advantage of new privacy-preserving APIs, you can now achieve your technology goals while also protecting your users from privacy violations.

Transitioning to a more private web encompasses the following steps:

- [Audit your third-party cookie usage. &#10548;](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#audit)
- [Test for breakage. &#10548;](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#test)
- For cross-site cookies which store data on a per-site basis, like an embed, consider [Partitioned with CHIPS. &#10548;](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#partitioned)
- For cross-site cookies across a small group of meaningfully linked sites, consider [Related Website Sets. &#10548;](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#rws)
- For other third-party cookie use cases, [migrate to the relevant web APIs. &#10548;](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#migrate)

## The Privacy Sandbox Analysis Tool

The purpose of this tool is to help developers like you in making your sites/applications more robust in protecting the privacy of users. This wiki provides guidance on analyzing your critical user journeys and getting insights needed to implement changes, including:

1. How to set up an [**Evaluation Environment**](https://github.com/GoogleChromeLabs/ps-analysis-tool/wiki/Evaluation-Environment) that will help predict what is likely to happen when third-party cookies have been blocked.
1. How to identify specific aspects of the site that are likely to be affected, amongst other [**General debugging actions for Analysis**](https://github.com/GoogleChromeLabs/ps-analysis-tool/wiki/General-Debugging-Actions).
1. How to evaluate an existing component and/or user journey, to identify, triage and address issues, using various tools and resources, including ready-made step-by-step instructions for common [**Example Analysis Scenarios**](https://github.com/GoogleChromeLabs/ps-analysis-tool/wiki/Example-Analysis-Scenarios).
1. How to [**Find Help and Report Issues**](https://github.com/GoogleChromeLabs/ps-analysis-tool/wiki/Reporting-Issues-and-Learning-More) that are encountered during this process.

In addition, within relevant contexts, it includes prompts and pathways for you to contribute your own use cases, provide feedback and seek even more guidance.
