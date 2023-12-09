## HTTP is stateless

HTTP is a stateless protocol. That means that no information, or state, is saved anywhere between individual requests; each request from a client to a server is treated in isolation. This property of HTTP has played a crucial role in the design and functioning of web applications in terms of simplicity, scalability, and efficient resource utilization.

## The birth of cookies

In the early 1990s, a visionary developer named [Lou Montulli ](https://en.wikipedia.org/wiki/Lou_Montulli) working at Netscape, faced a significant challenge while creating an online shopping cart for a client company. The absence of a state management mechanism to save user selections as they navigated across web pages resulted in a bad online shopping experience.

To tackle the shopping cart problem, Lou adapted an existing technique, [magic cookies](https://en.wikipedia.org/wiki/Magic_cookie), which allowed data exchange between computer programs to maintain state during communications. This gave the browser the ability to remember the items users had selected, even as they explored different pages on the site. This work soon found its way into the fabric of the Netscape browser, and paved the way for what we know today as cookies.

[!IMPORTANT]  
Crucial information necessary for users to succeed.
