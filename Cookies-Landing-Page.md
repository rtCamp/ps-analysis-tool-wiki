The first component in PSAT's Privacy Sandbox DevTools panel corresponds to the area of Cookie Analysis.

As discussed in the Evaluation Environment section, PSAT can be configured to avoid using too many resources by restricting the tool to analyze only a single tab at a time. If that configuration option is set, PSAT presents an `Analyze this tab` button to switch the tool's focus to the current tab.

<img width="1200" alt="PSAT Cookie Landing Page - Analyze this tab" src="images/cookie-analysis/cookie-landing-page/psat_v0.11.0_analyze_this_tab_2024_09_16.avif">

Once the PSAT's focus has been switched to the current tab, we get to the Cookies Landing Page:

<img width="1200" alt="PSAT Cookie Landing Page" src="images/cookie-analysis/cookie-landing-page/psat_v0.11.0_cookies_landing_page_2024_09_16.avif">

The purpose of PSAT's cookie landing page is to provide information and insights regarding the behavior and distribution of cookies on web pages while navigating across sites during browsing sessions.

The PSAT Cookie landing page has a navigation menu in the top-right corner for easy access to different sections.

<img width="1200" src="images/cookie-analysis/cookie-landing-page/psat_v0.11.0_cookies_landing_page_navigation_2024_09_16.avif" alt="PSAT Cookie Landing Page Navigation">

The cookie insights page categorizes observed cookies on a given page (total, first-party, third-party).

The cookie landing page features interactive sections for cookie classification and blocked reasons. Clicking on a classification will navigate you to the corresponding section of the cookie table and automatically filter the results to display only the cookies associated with that selection.

<img width="1200" src="images/cookie-analysis/cookie-landing-page/psat_v0.11.0_cookies_landing_page_mapped_sections_2024_09_16.avif" alt="PSAT Cooking Landing Page mapped sections.">

PSAT leverages and contributes to the [Open Cookie Database &#10548;](https://github.com/jkwakman/Open-Cookie-Database), which is an open-source effort to describe and categorize cookies in the ecosystem. Using that DB, PSAT's provides a classification for some of the observed cookies, into the categories: Functional, Marketing, Analytics, and Uncategorized.

As PSAT evolves rapidly, the cookie landing page will incorporate more information and insights about cookie usage and behaviors.

## Cookie Exemptions

The Cookie Insights page will now display a dedicated section for “Cookie Exemptions,” similar to the existing “Blocked cookies” section. This section will list the exempt cookies and provide details about the reason for the exemption.

Some cookies are exempt from blocking for specific technical reasons or based on user actions, such as when a user explicitly allows third-party cookies. The PSAT leverages Chrome DevTools Protocols (CDP) to access this information and provide you with transparency.

PSAT has introduced a dedicated “Cookie Exemptions” section on the Cookie Lading page, displaying information about exempt cookies.

<img width="1200" src="images/cookie-analysis/cookie-landing-page/psat_v0.11.0_cookie_landing_exemptions_2024_09_16.avif" alt="Cookie Exemptions" />

By knowing why certain cookies are exempt, you gain valuable context about how websites function and how your cookie preferences interact with those functions.

## Detecting Potential Breakages

PSAT helps developers analyze website behaviors in environments where the user has blocked the use of unrestricted third-party cookies and identify components/libraries with known issues caused by this blocking. The cookie landing page, with an expansion toggle, details of broken features, and possible migration guides, provides information about these breakages.

PSAT currently detects the following libraries; you can test their working on respective [demos &#10548;](https://domain-aaa.com/)

- Google Sign-In (GSI)
- Google Identity Services (GIS)
- Facebook Like
- Facebook Comment
- Disqus Comment
- Jetpack Comment
- Jetpack Like

<img width="1200" alt="PSAT Breakage Detection" src="images/cookie-analysis/cookie-landing-page/psat_v0.11.0_known_breakages_2024_09_16.avif">

## Filtering Data

The data on the Cookies Insights page can be filtered. Enabling the filter at the top-left allows the user to change the context of the report, listing only data from a specific scope or cookie category.

<img width="1200" alt="PSAT Cookies Landing Page Filtering Data" src="images/cookie-analysis/cookie-landing-page/psat_v0.11.0_cookies_landing_page_with_filtering_2024_09_16.avif">

Once the filter is applied, the report will only display the cookies that fit on those selected filters.
