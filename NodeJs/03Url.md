A URL, or Uniform Resource Locator, is essentially the web address you type into your browser's address bar to access a specific webpage or file on the internet. It's like a street address for the digital world, providing precise directions to where you want to go online.

Here's a simple breakdown of what a URL consists of:

- **Protocol**: This part of the URL tells your browser how to access the resource. Common protocols are HTTP (Hypertext Transfer Protocol) for unsecured web pages and HTTPS (HTTP Secure) for secure web pages.
- **Domain Name**: This is the name of the website you're visiting, such as `google.com` or `example.org`. It's what you remember and type into your browser.
- **Subdomain**: Sometimes, you'll see a part of the domain name before the main domain, like `www` in `www.google.com`. This is optional and can be used for different purposes, such as directing users to specific sections of a website.
- **Path**: This is the specific page or file within the website you're looking for, such as `/about` in `www.example.com/about`. It helps navigate to different sections of the website.
- **Parameters**: These are additional pieces of information sent to the server, usually starting with a question mark (`?`) and followed by key-value pairs, like `?page=2` in a URL. They can be used for various purposes, such as passing data to the server or filtering results.

In essence, a URL is a unique identifier that tells your browser where to find the information you're looking for on the internet. It's made up of several parts, each serving a specific purpose in directing you to the right content.

A domain name is a unique address that people type into their web browsers to access a specific website. It is essentially the name of a website, similar to how a store name identifies a physical store. For example, `walmart.com` is the domain name for Walmart's online presence. Unlike IP addresses, which are numeric and difficult for humans to remember, domain names are designed to be easily recognizable and memorable, making it easier for users to find and access websites [4].

The structure of a domain name is composed of several parts, including:

- **Top-Level Domain (TLD)**: This is the last part of the domain name, such as `.com`, `.org`, `.net`, etc. TLDs indicate the general purpose of the website or the type of organization it represents. For instance, `.com` is used for commercial entities, `.org` for non-profit organizations, and `.edu` for educational institutions [1][3].
- **Second-Level Domain (SLD)**: This is the part of the domain name that comes before the TLD. For example, in `walmart.com`, `walmart` is the SLD. The SLD is often the name of the organization or entity that owns the domain [1].
- **Subdomains**: These are optional parts of the domain name that can be added to create different sections of a website. For example, `developer.mozilla.org` is a subdomain of `mozilla.org` [1].

Domain names are crucial for the internet infrastructure because they provide a human-readable address for any web server available on the internet. Without domain names, websites would be identified by their IP addresses, which are difficult for people to remember and remember [1][4].

To obtain a domain name, you must purchase it from a domain registrar. The domain name must be unique and not infringe on any trademarks or copyrights. It's also beneficial to choose a domain name that can serve as your brand name or include keywords relevant to your business or the content of your website. This helps with search engine optimization and makes the domain name more meaningful to users [3].

In summary, a domain name is the address used to access a website on the internet, consisting of a SLD, TLD, and optionally, subdomains. It is a critical component of the internet infrastructure, making websites easily accessible and memorable for users.

Query parameters are key-value pairs appended to the end of a URL to provide additional information or instructions to the web server when making requests. They are introduced after the path of the URL with a question mark (?) and are separated by an ampersand (&) if there are multiple parameters. These parameters can be used for various purposes such as sorting, filtering, or customizing the data received by an application.

For example, in the URL `https://example.com/path?name=Branch&products=[Journeys,Email,Universal%20Ads]`, `name=Branch` and `products=[Journeys,Email,Universal%20Ads]` are query parameters. The first parameter instructs the server to customize the page based on the 'name' field, and the second parameter filters products based on the 'products' list [0].

Query parameters are widely used in:

- **API requests**: To filter, sort, or customize the data received by mobile apps or web applications.
- **Deep linking**: To pass information to an app to open a specific in-app screen.
- **Search functionality**: To pass search queries to the app’s server or API.
- **Tracking and attribution**: To track user interactions and measure campaign effectiveness [0].

For instance, in a weather API request like `curl GET /surfreport/beachId?days=3&units=metric&time=1400`, `days=3`, `units=metric`, and `time=1400` are query parameters used to sort the surf report retrieved from the API into results from the next three days, display results in metric units, and display results at a specific time [1].

Query parameters allow efficient sorting and filtering of data pulled from APIs, saving computational resources and bandwidth by avoiding unnecessary data processing or user search. While path parameters indicate where to look, query parameters describe how to look, thus enhancing the functionality and efficiency of API requests [1][2].

```javascript
const http = require("http");
const fs = require("fs");
const url = require("url");

const myServer = http.createServer((req, res) => {
  const log = `${Date.now()}: New Req Received \n`;
  if (req.url === "/favicon.ico") return;
  const myUrl = url.parse(req.url, true);

  console.log(myUrl);
  fs.appendFile("log.txt", log, (err) => {
    res.end("Hello From Server");
  });
});

myServer.listen(8000, () => console.log("Server is running on port 8000"));
```
