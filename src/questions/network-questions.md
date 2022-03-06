---
title: Network Questions
layout: layouts/page.njk
permalink: /questions/network-questions/index.html
---

* Traditionally, why has it been better to serve site assets from multiple domains?
   - https://developer.mozilla.org/en-US/docs/Glossary/Domain_sharding 
   - browser limits the number of active connections for each domain
   - so to enable concurrent downloads of assets exceeding the limit, **domain sharding** splits content across multiple domains
   - "When multiple domains are used to serve multiple assets, browsers are able to download more resources simultaneously, resulting in a faster page load time and improved user experience."
   - However, domain sharding has the problem of cost of extra DNS lookups for each domain and the overhead of establishing each TCP connection.
* Do your best to describe the process from the time you type in a website's URL to it finishing loading on your screen.
```
Let us suppose that you type the URL www.quora.com

Step 1 --> DNS Resolution, Get the ip address of the URL.

To Get the IP address for http://www.quora.com, the steps are
a) System checks the browser cache. Browser caches the DNS data for some time.
b) If IP address[DNS data for http://www.quora.com] is not found in browser cahe, system will check the OS cache. [in windows gethostbyname system call is made]
c) If IP address[DNS data for http://www.quora.com] is not found in OS cache, then request continues to DNS cache maintained by the router.
d) If DNS data for http://www.quora.com is not found then seach moves to next level where DNS cache of your Internet Service Provider.
e) If the DNS data is not found in ISP's DNS cache, then ISP's DNS server perform DNS query to search for the required DNS data.


Step 2>> Once browser gets the IP address it opens TCP connection and sends HTTP request to the web server.

Step 3>> The web server will handle the request [it happens in multiple steps] and send the HTTP response to the client/browser.

Step 4>> The browser parse the HTML docuemnt and render it.


This is basically summary of what happend when we type an URL and hit enter.

For more detail you can refer this link :-
http://igoro.com/archive/what-really-happens-when-you-navigate-to-a-url/
```
* What are the differences between Long-Polling, Websockets and Server-Sent Events?
    - Ajax Polling: A client **repeatly initiates requests**, Making repeated requests to server wastes resources as each new incoming connection must be established
    - Long Polling: server elects to **hold a client connection open** for as long as possible, and deliver the data after data becomes available or timeout threshold has been reached. When the response is received, the client can initiate a new request.
    - Websocket: WebSocket is a computer communication **protocol** which provides full-duplex communication channels over a single TCP connection. WebSockets keeps the connection open, allowing messages to be passed back and forth between the client and the server.
    - Server Sent Events: Server-Sent Events are a **one-way** communication channel where events flow **from server to client only**
    - https://medium.com/system-design-blog/long-polling-vs-websockets-vs-server-sent-events-c43ba96df7c1
* Explain the following request and response headers:
  * Diff. between Expires, Date, Age and If-Modified-...
      - Expires The Expires HTTP header contains the date/time after which the **response is considered expired**.
      - Date: contains the date and time at which the message was originated.
      - Age: contains the time in seconds the object was in a **proxy cache**.  If it is Age: 0, it was probably fetched from the origin server;
  * Do Not Track
  * Cache-Control - **instructions control** caching in browsers and shared caches (e.g. Proxies, CDNs).
  * Transfer-Encoding - encoding to transfer the payload body
  * ETag
     - entity tag
     - identifier for a specific version of a resource
     - If the resource at a given URL changes, a new Etag value must be generated
     - web server does not need to resend a full response if the content was not changed
  * X-Frame-Options - indicate whether or not a browser should be **allowed to render** a page in a <frame>, <iframe>, <embed> or <object>
* What are HTTP methods? List all HTTP methods that you know, and explain them.
* What is domain pre-fetching and how does it help with performance?
    - attempt to **resolve** domain names **before** resources get **requested**.
* What is a CDN and what is the benefit of using one?
    - https://www.cloudflare.com/learning/cdn/cdn-benefits/
    - **a group of servers** around the globe, speed up content delivery on the web
    - The servers in a CDN temporarily **store webpage content** like images, HTML, JavaScript, and video. 
    - four important benefits: better performance(reduction in load time), increased reliability(failover to backup server), cost savings(reduction in server bandwidth costs), and resilience against cyber attacks(DoS and DDoS attack).
