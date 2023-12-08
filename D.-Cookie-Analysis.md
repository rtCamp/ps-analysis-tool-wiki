### Cookies Landing Page

Click on the Cookies component in PSAT's landing page, which will open the Cookies landing page. As discussed above, PSAT can be configured to avoid using too much resources by restricting the tool to only analyze a single tab at a time. If that configuration setting is set, PSAT presents an `Analyze thus tab` button to switch the focus of the tool to the current tab. 

<img width="742" alt="Screenshot 2023-12-07 at 5 19 35 PM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/1c7d3973-a0c5-4a7a-bac2-8b6b70920373">

The Cookies landing page:

<img width="1532" alt="Screenshot 2023-12-07 at 5 25 30 PM" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/a92fd0eb-d3e8-42df-ba17-13ef8c206403">


#### A note on _Cookie Accepted_ Column

>Of all the cookies that a site attempts to set, the browser will accept some, and some will be rejected, in a 3PCD instance of Chrome (depending on whether they’re third-party or first-party cookies).
>
>The `Cookie Accepted` column of the _PSAT_ cookie table indicates this piece of information by adding a check icon (*✓*) next to the cookies that were accepted by the browser. Other cookies that don’t have this indicator, _have not been accepted by the browser_ and _are not set_.
>
>For this reason, such cookies won’t be displayed under _Applications > Cookies_ in _Chrome Developer Tools_, since that displays the current state of the application and all the cookies that are actually set (accepted) and available for use.
>
>In contrast, `PSAT` is obviously interested in displaying cookies that are not set and not in use, for the purpose of analysis and repair.
>
>This is expected behavior, but sometimes it is a source of confusion because of the apparent disparity between the information displayed under _Application > Cookies_ and the _PSAT_ extension.


### Frame Overlays

Frame overlays make it easy to associate third-party cookies with embedded iframes. To use it:

1. Create a report with the extension
1. Go to the DevTools Privacy Sadbox tab
1. Click on the icon on the side of the Cookies section on the right sidebar to activate the functionality
1. Pass the mouse over the website's iframe to get quick info about it 

<img width="937" alt="Google Chrome showing the Frames Overlay with the PSAT Extension" src="https://github.com/GoogleChromeLabs/ps-analysis-tool/assets/506089/82ab33ab-9e19-4fc3-b80f-33805b089756">

