Welcome to the Privacy Sandbox Analysis Tool (PSAT) Wiki!

The [Privacy Sandbox initiative](https://privacysandbox.com/) aims to create technologies that both protect people's privacy online and give companies and developers tools to build thriving digital businesses. The main goal of Privacy Sandbox is to reduce cross-site tracking while still enabling the functionality that keeps online content and services freely accessible by everyone. Deprecating and removing third-party cookies encapsulates the challenge, as they enable critical functionality across sign-in, fraud protection, advertising, and generally the ability to embed rich, third-party content in your sites—but at the same time they're also the key enablers of cross-site tracking.

## Preparing for the end of third-party cookies

If your site uses third-party cookies it's time to take action as we approach their deprecation. Chrome plans to disable third-party cookies for 1% of users from Q1 2024 to facilitate testing, and then ramp up to 100% of users from Q3 2024.  

Getting ready for Privacy Sandbox encompasses following a set of key steps o ensure you're prepared for your site to run without third-party cookies:

- [Audit your third-party cookie usage](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#audit).
- [Test for breakage](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#test).
- For cross-site cookies which store data on a per site basis, like an embed, consider [Partitioned with CHIPS](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#partitioned).
- For cross-site cookies across a small group of meaningfully linked sites, consider [Related Website Sets](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#rws).
- For other third-party cookie use cases, [migrate to the relevant web APIs](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#migrate).

## The Privacy Sandbox Analysis Tool

The purpose of this tool is to empower developers like you in making your sites/applications ready for the upcoming deprecation of 3rd Party Cookies (3PC) and unpartitioned storage on Chrome as part of the [Privacy Sandbox](https://privacysandbox.com/) initiative. This wiki outlines a testing/evaluation methodology that will guide you in analyzing your scenarios and the necessary insights needed to implement changes.

This wiki contains different pages to help in this process of identifying and evaluating the impact of the upcoming changes related to cookies:

1. How to set up an [**Evaluation Environment**](https://github.com/GoogleChromeLabs/ps-analysis-tool/wiki/Evaluation-Environment) that will help predict what is likely to happen once the deprecation comes into effect.
1. How to identify specific aspects of the site that are likely to be affected, amongst other [**General debugging actions for Analysis**](https://github.com/GoogleChromeLabs/ps-analysis-tool/wiki/General-debugging-actions).
1. How to evaluate an existing component and/or user journey, to identify, triage and address issues, using various tools and resources, including ready-made step-by-step instructions for common [**Example Analysis Scenarios**](https://github.com/GoogleChromeLabs/ps-analysis-tool/wiki/Example-analysis-scenarios).
1. How to [**Find Help and Report Issues**](https://github.com/GoogleChromeLabs/ps-analysis-tool/wiki/Reporting-Issues-and-Learning-More) that are encountered during this process.

In addition, within relevant contexts, it includes prompts and pathways for you to contribute your own use cases, provide feedback and seek even more guidance.
