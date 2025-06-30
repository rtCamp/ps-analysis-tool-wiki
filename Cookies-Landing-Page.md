The first component in the PSAT Privacy Sandbox DevTools panel corresponds to the **Cookie Analysis** area. You will notice an interactive landing page that provides insights into the cookies observed during your Browse sessions.

<img width="1200" alt="PSAT Cookie Landing Page" src="images/cookie-analysis/cookie-landing-page/psat_v1.0.0_cookies_landing_page_2025_06_30.png">

The purpose of the PSAT cookie landing page is to provide information and insights regarding the behavior and distribution of cookies on web pages as you navigate across sites during Browse sessions.

The PSAT cookie landing page has a navigation menu in the top-right corner for easy access to different sections.

<img width="1200" src="images/cookie-analysis/cookie-landing-page/psat_v1.0.0_cookies_landing_page_navigation_2025_06_30.png" alt="PSAT Cookie Landing Page Navigation">

The Cookie Insights page categorizes observed cookies on a given page by total, first-party, and third-party.

The cookie landing page features interactive sections for cookie classification and blocked reasons. Clicking on a classification will navigate you to the corresponding section of the cookie table and automatically filter the results to display only the cookies associated with that selection.

<img width="1200" src="images/cookie-analysis/cookie-landing-page/psat_v1.0.0_cookies_landing_page_mapped_sections_2025_06_30.png" alt="PSAT Cookie Landing Page mapped sections.">

PSAT leverages and contributes to the [Open Cookie Database &#10548;](https://github.com/jkwakman/Open-Cookie-Database), an open-source effort to describe and categorize cookies in the ecosystem. Using that database, PSAT provides a classification for some of the observed cookies into the following categories: Functional, Marketing, Analytics, and Uncategorized.

As PSAT evolves rapidly, the cookie landing page will incorporate more information and insights about cookie usage and behavior.

## Cookie Exemptions

The Cookie Insights page now displays a dedicated section for “Cookie Exemptions,” similar to the existing “Blocked Cookies” section. This section lists the exempt cookies and provides details about the reason for their exemption.

Some cookies are exempt from blocking for specific technical reasons or are based on user actions, such as when a user explicitly allows third-party cookies. PSAT leverages the Chrome DevTools Protocol (CDP) to access this information and provide you with transparency.

PSAT has introduced a dedicated “Cookie Exemptions” section on the cookie landing page that displays information about exempt cookies.

<img width="1200" src="images/cookie-analysis/cookie-landing-page/psat_v1.0.0_cookie_landing_exemptions_2025_06_30.png" alt="Cookie Exemptions" />

By knowing why certain cookies are exempt, you gain valuable context about how websites function and how your cookie preferences interact with those functions.

## Filtering Data

The data on the Cookie Insights page can be filtered. Enabling the filter in the top-left corner allows the user to change the context of the report, listing only data from a specific scope or cookie category.

<img width="1200" alt="PSAT Cookies Landing Page Filtering Data" src="images/cookie-analysis/cookie-landing-page/psat_v1.0.0_cookies_landing_page_with_filtering_2025_06_30.png">

Once a filter is applied, the report will only display the cookies that match the selected criteria.