PSAT Extension features a dedicated settings page, where users can easily access and modify certain configuration settings, and also view system information.

<img width="1200" alt="PSAT Settings" src="images/settings/psat_v0.11.0_settings_2024_09_16.avif">

## Enabling Chrome DevTools Protocol in PSAT

One of the main purposes of PSAT is to help developers analyze and understand the usage of third-party cookies during browsing sessions. To achieve this, PSAT uses the Chrome DevTools Protocol (CDP) to debug and collect information about sites being loaded during a browsing session.

When users enable the CDP to troubleshoot their website, Chrome warns them that their session is being debugged. However, to avoid disrupting the user experience, activating CDP doesn't automatically reload other open tabs. Instead, PSAT offers a separate “Reload” button when CDP is turned on, allowing users to refresh tabs manually when needed.

PSAT allows the Enabling and Disabling of its debugging capabilities directly from the tool itself so that the extension can be enabled. Still, the debugging components can be turned on only when needed.


<img width="1200" alt="PSAT Enable CDP" src="images/settings/psat_v0.11.0_enabling_cdp_in_psat_2024_09_16.avif">

## Multi-tab Debugging

PSAT lets users control the number of tabs analyzed concurrently. To optimize performance and ensure smooth operation, the default setting allows analysis of one tab at a time. However, users who require simultaneous multiple-tab analysis can easily adjust this setting to meet their specific debugging needs.

<img width="1200" alt="PSAT Multitab" src="images/settings/psat_v0.11.0_multitab_debugging_2024_06_16.avif">

## PSAT Permissions

### Storage

The purpose of this tool is to help developers analyze the use of third-party cookies, as they get ready for changes in the Chrome browser, which will limit the use of unrestricted third-party cookies. To achieve this, the extension requires the appropriate permissions to leverage the Chrome DevTools Protocols to gather data regarding Cookies from network traffic.

### Tabs

The purpose of this tool is to help developers analyze and understand the usage of third-party cookies during browsing sessions, which may involve accessing multiple websites from different tabs.

### webNavigation

The purpose of this tool is to help developers analyze and understand the usage of third-party cookies during browsing sessions which encompass a sequence of web navigations

### webRequest

The purpose of this tool is to help developers analyze and understand the usage of third-party cookies during browsing sessions, and this requires gathering data about cookie-usage from different Chrome APIs as well as from the Chrome DevTools protocol.

### Cookies

The purpose of this tool is to help developers analyze and understand the usage of third-party cookies during browsing sessions, and this encompasses gathering and manipulating cookie-related data from different API sources.

### Unlimited Storage

This tool stores data temporarily as part of the processing necessary to shed light on third-party cookie usage, and help developers prepare for upcoming changes in the Chrome browser.

### Debugger

The purpose of this tool is to help developers analyze and debug cookie behaviors to transition to a more private web. To do this the tool requires to use the debugger to obtain information regarding cookie blocking reasons and cookie warnings.

### Management Justification

This tool helps developers analyze and understand the behavior of cookies on web pages, specifically as third-party cookies start getting blocked on Chrome.

The presence of other extensions managing cookies or related functionalities may interfere with the proper functioning of this tool. The management permission is used for debugging purposes by this tool to list active extension used by the user. This information can be copied by the user and shared through a GitHub issue which will be helpful for debugging.

### Host permission

The purpose of this tool is help users analyze and debug their use of cookies in preparation for the changes coming to Chrome limiting the unrestricted use of cookies on websites. To achieve this the tool leverages the Chrome DevTools protocol, and doing so requires the specified permissions.
