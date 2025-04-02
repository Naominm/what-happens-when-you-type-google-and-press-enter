# What happens when you type google.com in your browser and press enter.
When you type google.com or any other url in your browser and press enter a lot of things happen.

## DNS Lookup
At first a request is sent to the Domain Name system. The browser seek to translate a the human friendly domain name such as www.google.com to an IP address, the language of computers. a query is sent to a DNS server, which acts like a phoneBook for the internet, fetching the corresponding IP address for Googles server.

Servers communicate with IP addresses and not a domain name thats why the domain name needs to be translated.

### How does the lookup process work?

## Browser looks IP In Cache
To make the lookup process fast the DNS information is heavily cached. First the browser itself catches it for a short period of time and if its not in the browser cache, the browser asks the operating system for it. The OS itself has a cache for it which also keeps the answer for a short period of time.

If the OS doesn't have it, it makes a query out to the internet to a DNS Resolver.This sets off a chain of request until the IP address is resolved.

Now finally the browser has the IP address of the  server.

## TCP connection with the server
Next, the browser establishes a TCP (Transmission Control Protocol/Internet Protocol)  connection with the server using the IP address it got for it. TCP establishes a reliable connection between your machine and Google's server, ensuring data integrity and order. IP on the other hand is responsible for routing the data packets to the correct destination.

Now, there is a handshake involved in establishing a TCP connection. IT takes several network round trips for this to complete. To keep the loading process fast, Modern browsers use something called a keep alive connection to try and establish a TCP connection to the server as much as possible.

### Firewall
Before the packets venture further, they encounter the firewall-a security system ensuring that only safe and authorized traffic is allowed through. The firewall scrutinizes the packets based on predefined rules before permitting them onward.

#### Https

One more thing, If the Protocol is HTTPS the process of establishing a connection is even more involved. It Requires a complicated process called SSL/TLS handshake to establish an encrypted connection between the server.

This handshake is expensive and the browser use tricks like SSL session resumption to try to lower the cost.

Finally the browser sends a HTTP request to the server over the established TCP connection.

So, As we thread into a secure domain (https), a Secure Socket Layer (SSL) or its successor Transport Layer security (TLS) ensure a secure connection by encrypting the data transferred between your browser and Google's server, safeguarding against eavesdropping.

Eavesdropping is the act of secretly or stealthily listening to the private conversation or communications of others without their consent in order to gather information.


#### Http
Http itself is a very simple protocol. The server processes the request and send back a response.

The browser receives the response and renders html content.

### Load Balancer
Arriving at Google's premises, a load balancer warmly welcomes the packets. Its job is to distribute incoming network traffic across several servers to ensure no single server becomes overwhelmed with too much traffic. This way it ensures a seamless user experience.

### Web Server
Post load balancing, the  web server takes the stage , handling the HTTP request. It decides what action is needed, often communicating with an application server to process the request further.

### Application Server
The application server is the brain behind the operation, executing the necessary business logic, interacting with the database, and preparing the HTTP response to be sent back to your browser.

### Database
To fulfill your request, the application server might need to fetch or store data. It interacts with the database, where the database, where data is stored, retrieved, and managed, ensuring that your search query is successfully executed.

### Rendering
The HTTP response makes its way back through the channels, reaching your browser which then rerenders the HTML, CSS and JS to display the webpage we all know and love as Google.

