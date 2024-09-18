User-Agent (UA) reduction minimizes the identifying information shared in the User-Agent string, which may be used for passive fingerprinting. Web developers should review their site code for usage of the User-Agent string and implement the User-Agent Client Hints API if their site relies on parsing the User-Agent string to read the device model, platform version, or full browser version. 

The User-Agent Client Hints (UA-CH) API is a web standard that allows servers to request specific information about a user's browser and device, such as device model or operating system version, through an opt-in mechanism, enhancing user privacy compared to the traditional User-Agent string.

**Proposal**: [Public explanation for the proposed solution (WICG) &#10548;](https://wicg.github.io/ua-client-hints/)

**Public discussion**: [ublic questions and feedback about the proposal &#10548;](https://github.com/WICG/ua-client-hints/issues)

**Documentation**: [Developer documentation &#10548;](https://developers.google.com/privacy-sandbox/protections/user-agent)