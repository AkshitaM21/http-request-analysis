# HTTP Request Analysis Report

## Overview

This report analyzes the HTTP request/response cycle for the Wikipedia homepage using Chrome Developer Tools (Network tab). The analysis includes request details, response headers, DNS lookup, TCP connection, TLS handshake, Time To First Byte (TTFB), and the relationship between DNS, TCP/IP, HTTPS, and HTTP.



## Website Information

- **Website:** Wikipedia
- **URL:** https://www.wikipedia.org/
- **Request Method:** GET
- **Status Code:** 200 OK
- **Protocol:** HTTPS
- **Remote Address:** 103.102.166.224:443

### Explanation

- **GET** requests data from a server.
- **200 OK** indicates the request was successful.
- **HTTPS** ensures secure communication through encryption.
- **Port 443** is the standard port used by HTTPS.



## Response Headers Analysis

### Content-Type: text/html

Indicates that the server returned an HTML document.

### Content-Length: 30635

Specifies the size of the response body in bytes.

### Content-Encoding: gzip

The content is compressed before transmission to reduce bandwidth usage and improve loading speed.

### Cache-Control: s-maxage=86400, must-revalidate, max-age=3600

Controls browser and proxy caching behavior to improve performance.

### Accept-Ranges: bytes

Allows downloading portions of a file instead of the entire file.

### ETag

A unique identifier used for cache validation.

### Last-Modified

Shows when the resource was last updated on the server.

### Date

Represents the time at which the response was generated.


## Timing Breakdown

| Activity | Time |
|-----------|---------|
| Queueing | 10.57 ms |
| Stalled | 13.84 ms |
| DNS Lookup | 72.21 ms |
| Initial Connection | 86.75 ms |
| SSL/TLS Handshake | 43.55 ms |
| Request Sent | 0.50 ms |
| Waiting for Server Response (TTFB) | 82.78 ms |
| Content Download | 37.17 ms |
| Total Time | 304.22 ms |


## Time To First Byte (TTFB)

**TTFB = 82.78 ms**

TTFB measures the time between sending a request and receiving the first byte of the response from the server. Lower TTFB values generally indicate better server responsiveness.


## How DNS, TCP/IP, TLS, and HTTP Work Together

### Step 1: DNS Lookup

When the URL is entered into the browser, DNS converts the domain name into an IP address.

Example:

www.wikipedia.org → 103.102.166.224

DNS Lookup Time:

72.21 ms



### Step 2: TCP Connection

After obtaining the IP address, the browser establishes a TCP connection with the server.

TCP ensures:

- Reliable communication
- Error checking
- Ordered delivery of packets

Connection Time:

86.75 ms



### Step 3: TLS Handshake

Because HTTPS is used, a TLS handshake occurs before data exchange.

TLS provides:

- Authentication
- Encryption
- Secure communication

TLS Handshake Time:

43.55 ms



### Step 4: HTTP Request

The browser sends an HTTP request:

GET / HTTP/1.1
Host: www.wikipedia.org

The server receives the request and processes it.



### Step 5: HTTP Response

The server returns:

HTTP/1.1 200 OK

along with the HTML content and response headers.


### Step 6: Content Download and Rendering

The browser downloads the content and renders the webpage.

Download Time:

37.17 ms



## HTTP vs HTTPS

| HTTP | HTTPS |
|--------|--------|
| Not encrypted | Encrypted |
| Uses Port 80 | Uses Port 443 |
| Less secure | More secure |
| No TLS handshake | Uses TLS handshake |
| Vulnerable to interception | Protected against interception |

This request used HTTPS, which is why the TLS handshake was observed.



## Conclusion

The Wikipedia homepage was successfully loaded through an HTTPS GET request. The browser first performed a DNS lookup, established a TCP connection, completed a TLS handshake, sent the HTTP request, and received a 200 OK response from the server. The complete request-response cycle took approximately 304.22 ms, with a Time To First Byte (TTFB) of 82.78 ms. This analysis demonstrates how DNS, TCP/IP, TLS, and HTTP work together to securely deliver web content.



## Evidence

Screenshots included in the repository:

1. Network Tab Overview
2. Headers Tab
3. Timing Tab
