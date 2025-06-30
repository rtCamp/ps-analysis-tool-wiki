The IP Protection Geolocation Approach is designed to enhance user privacy by masking their true IP address, thus preventing its use for cross-site tracking. The fundamental goal is to balance this increased privacy with the need for websites to access general location information for essential functionalities. 

Rather than providing a precise location, the system offers an approximate, "coarse" geographical signal, acknowledging that IP-based geolocation is inherently imprecise. This approach aims to maintain key use cases like localized content and analytics while fundamentally improving privacy on the web.
## How It Works

The system operates by dividing the world into distinct geographic areas ("geos") and assigning users to one of these geos.

- *Defining Geographic Areas:* To ensure anonymity, each geographic area is defined to contain a large population of at least one million internet users. This means the physical size of these areas varies; they are smaller in densely populated regions and larger in sparse ones. The system is designed to respect national boundaries, so a user is always assigned a location within their original country.

- *Assigning Users:* A user is assigned to a geographic area based on their original, pre-proxy IP address. If a specific area doesn't have enough concurrent users to guarantee anonymity at any given moment, the user is defaulted to a larger, less granular region to maintain privacy.

- *Public Geolocation Data:* The IP-to-location mappings are shared publicly via a "geofeed" file. This file, which uses the format defined in RFC 8805, provides city-level assignments, allowing services to determine the generalized location corresponding to the privacy-protected IP address.

### Masked Domains
To balance privacy with web usability, IP Protection doesn't proxy all internet traffic. Instead, it uses a list-based approach centered on Masked Domains. 

You can check all the masked domains in PSAT extension by navigating to the "Masked Domains" under IP protection section, You can also search and filter the domains in the list.

<img src="images/ip-protection/psat_v1.0.0_ip_protection_masked_domains_2025_06_30.png" alt="Masked Domains in PSAT" width="1200" />

#### What Are Masked Domains?
Masked Domains are a specific list of domains (known as the Masked Domain List or MDL) for which IP masking is applied. This list is curated to include domains that are likely to be involved in cross-site tracking, such as those serving ads, performing analytics, or collecting user data for marketing

#### How Masked Domains Work?
The purpose is to surgically target potential trackers without disrupting the user's primary web experience. Traffic to a domain on this list is only sent through the privacy proxy when it's accessed in a *third-party context* (for example, a tracking script from `tracker.com` running on `news-website.com`). If you visit a masked domain directly (in a first-party context), it will still receive your real IP address. This ensures that websites continue to function correctly while preventing third-party observers from using your IP address to build a profile of your activity across different sites.

### Resources

- Google Chrome's IP Protection Proposal: [GitHub - GoogleChrome/ip-protection](https://github.com/GoogleChrome/ip-protection/blob/main/Explainer-IP-Geolocation.md)
- The Masked Domain List: [Masked Domain List](https://github.com/GoogleChrome/ip-protection/blob/main/Masked-Domain-List.md)
