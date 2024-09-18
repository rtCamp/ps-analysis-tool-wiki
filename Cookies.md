## HTTP is Stateless

HTTP is a stateless protocol. That means that no information, or state, is saved anywhere between individual requests; each request from a client to a server is treated in isolation. This property of HTTP has played a crucial role in the design and functioning of web applications in terms of simplicity, scalability, and efficient resource utilization.

## The Birth of Cookies

In the early 1990s, a visionary developer named [Lou Montulli &#10548;](https://en.wikipedia.org/wiki/Lou_Montulli) working at Netscape, faced a significant challenge while creating an online shopping cart for a client company. The absence of a state management mechanism to save user selections as they navigated across web pages resulted in a bad online shopping experience.

To tackle the shopping cart problem, Lou adapted an existing technique, [magic cookies &#10548;](https://en.wikipedia.org/wiki/Magic_cookie), which allowed data exchange between computer programs to maintain state during communications. This gave the browser the ability to remember the items users had selected, even as they explored different pages on the site. This work soon found its way into the fabric of the Netscape browser, and paved the way for what we know today as cookies.

> **Key**: An HTTP cookie is a mechanism for an origin server to send state information to a user agent and for the user agent to return the state information to the origin server. Cookies enable the stateless HTTP protocol to transmit saved state information.

Cookies emerged as a transformative element, revolutionizing how websites interacted with users and laid the foundation for modern web personalization and user experience.

## Third-party Cookie and User Privacy

Cookies are associated with a specific domain. When a web server sets a cookie, it includes the [web origin &#10548;](https://web.dev/same-site-same-origin/) as part of the cookie's metadata.

Third-party or cross-site cookies, are cookies set or sent from a domain different from the top-level site being accessed by the user.

Cookies facilitate tracking because they are persistent across user agent sessions and can be shared between sites. They are not the only mechanism servers can use to track users across HTTP requests, but is certainly one of the most widely used to do that.

Site owners and developers can avoid compromising their user's privacy by not using **unpartitioned third-party cookies**, that is, cookies set by third-party entities on a site, which can then be accessed by those entities across site boundaries. To enable site owners and developers to achieve this, Chrome has introduced features that allow users to control the behavior of third-party cookies in their Chrome instance, and also various privacy-preserving capabilities and APIs which can be used to implement all CUJs in privacy-preserving ways.
