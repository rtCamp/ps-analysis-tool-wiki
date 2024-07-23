Welcome to the Privacy Sandbox Analysis Tool (PSAT) Wiki!

The [Privacy Sandbox initiative](https://privacysandbox.com/) aims to create technologies that protect people's privacy online and give companies and developers tools to build thriving digital businesses. The main goal of Privacy Sandbox is to reduce cross-site tracking while still enabling the functionality that keeps online content and services freely accessible by everyone. The new Privacy Sandbox APIs are introduced to allow for more privacy-preserving solutions for critical functionality across the web, such as sign-in, fraud protection, advertising, and, generally, the ability to embed rich, third-party content.

## Preparing for a privacy-preserving web

Chrome is introducing a new feature that allows users to make informed choices about their privacy settings, applicable across their browsing experience. It's still crucial for developers to adopt privacy-preserving technologies. The Privacy Sandbox APIs are available and improved, offering alternatives to third-party cookies. 

- [Audit your third-party cookie usage](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#audit).
- [Test for breakage](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#test).
- For cross-site cookies which store data on a per site basis, like an embed, consider [Partitioned with CHIPS](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#partitioned).
- For cross-site cookies across a small group of meaningfully linked sites, consider [Related Website Sets](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#rws).
- For other third-party cookie use cases, [migrate to the relevant web APIs](https://developers.google.com/privacy-sandbox/blog/cookie-countdown-2023oct#migrate).

## The Privacy Sandbox Analysis Tool

This tool aims to empower developers to prepare their sites/applications for privacy-preserving web, identify third-party cookies, and implement alternatives with the new [Privacy Sandbox](https://privacysandbox.com/) APIs. This wiki outlines a testing/evaluation methodology that will guide you in analyzing your scenarios and the necessary insights needed to implement changes.

This wiki contains different pages to help in this process of identifying and evaluating the impact of the upcoming changes related to cookies:

1. How to set up an [**Evaluation Environment**](https://github.com/GoogleChromeLabs/ps-analysis-tool/wiki/Evaluation-Environment) that will help predict what is likely to happen once the deprecation comes into effect.
2. How to identify specific aspects of the site that are likely to be affected, amongst other [**General debugging actions for Analysis**](https://github.com/GoogleChromeLabs/ps-analysis-tool/wiki/General-debugging-actions).
3. How to evaluate an existing component and/or user journey, to identify, triage and address issues, using various tools and resources, including ready-made step-by-step instructions for common [**Example Analysis Scenarios**](https://github.com/GoogleChromeLabs/ps-analysis-tool/wiki/Example-analysis-scenarios).
4. How to [**Find Help and Report Issues**](https://github.com/GoogleChromeLabs/ps-analysis-tool/wiki/Reporting-Issues-and-Learning-More) that are encountered during this process.

In addition, within relevant contexts, it includes prompts and pathways for you to contribute your use cases, provide feedback, and seek even more guidance.
