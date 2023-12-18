The first component in PSAT's Privacy Sandbox DevTools panel corresponds to the area of Cookie Analysis.

As discussed in the Evaluation Enviroment section, PSAT can be configured to avoid using too much resources by restricting the tool to only analyze a single tab at a time. If that configuration optino is set, PSAT presents an `Analyze this tab` button to switch the focus of the tool to the current tab.

<img width="742" alt="PSAT Cookie Landing Page" src="images/cookie-analysis/analyze-this-tab.png">

Once the PSAT's focus has been switched to the current tab, we get to the Cookies Landing Page:

<img width="742" alt="PSAT Cookie Landing Page" src="images/cookie-analysis/cookie-landing-page.png">

The purpose of PSAT's cookie landing page is to provide information and insights regarding the behavior and distribution of cookies on web pages, while navigating across sites during browsing sessions.

Currently the cookie landing page provides a classification of observed cookies on a given page (total, first-party, third-party).

PSAT leverages, and contributes to, the [Open Cookie Database](https://github.com/jkwakman/Open-Cookie-Database), which is an open-source effort to describe and categorize cookies in the ecosystem. Using that DB, PSAT's provides a classification for some of the observed cookies, into the categories: Functional, Marketing, Analytics, and Uncategorized.

As PSAT continues to evolve rapidly, the cookie landing page will incorporate more information and insights about cookie usage and behaviors.
