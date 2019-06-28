## 1. PNG vs JPG vs Bitmap vs GIF

|                                                                                             | PNG                                   | JPG(=JPEG)                                                 | BMP                     | GIF                                                                   |
| ------------------------------------------------------------------------------------------- | ------------------------------------- | ---------------------------------------------------------- | ----------------------- | --------------------------------------------------------------------- |
| Name                                                                                        | Portable Networks Graphic             | Joint Photographic Experts Group                           | Bitmap                  | Graphics Interchange Format                                           |
| Compression ratio (file size)                                                               | 10-30%                                | 10:1 ~ 100:1                                               | 1:1 (large)             | 4:1 ~ 10:1                                                            |
| Loseless (compressed but no loss in quality) vs Lossy (more compressed and loss in quality) | Loseless                              | Lossy                                                      | Loseless                | Loseless                                                              |
| Support transparency (alpha)                                                                | O                                     | X                                                          | O                       | O (partially)                                                         |
| Color depths in bits (indexed vs direct palette)                                            | 48  (= 281,474,976,710,656 colors)    | 24 (= 16,777,216 colors)                                   | 24 / indexed AND direct | 8 (= 256 colors) / indexed                                            |
| Animation                                                                                   | X                                     | X                                                          | X                       | O                                                                     |
| Used for                                                                                    | Recommended for static graphics/icons | Photographs (small size, fairly good quality, many colors) | Almost nothing          | Logos, line drawings, and other simple images that need to be small.  |

More useful info
- http://ist.uwaterloo.ca/~anderson/images/GIFvsJPEG/compression_rates.html
- https://superuser.com/questions/53600/jpeg-vs-png-vs-bmp-vs-gif-vs-svg
- https://www.techsmith.com/blog/jpg-vs-png/

## OSI
The OSI (Open Systems Interconnection) Model is:
> a **conceptual model that standardises the communication of a computing system** without regard to its internal structure

> a tool used by IT professionals to **model or trace flow of data transfer in networks.**

### Why is it good anyways
- **can divide large data exchange process** in smaller segments (layers).
- standardized network components -> can do **multiple vendor development**

### Layers
![OSI Model](./OSI-model.jpg)

#### 7. Application layer
- End-user interacts with this layer
- **Examples**: anything that an end-user can directly use for a network connection.
    - network protocols directly provided to the user: **`telnet`, `ftp`, `tftp`** commands on cli
    - more broadly said: web browsers, mail services

#### 6. Presentation layer
- formats the data to be presented to the application layer
- **translate data from a format** used by the application layer into a common format at the sending station, then **translate the common format** to a format known to the application layer at the receiving station
- **Examples**: format conversions and encryption / decryption
    - image formats: **PNG, GIF, JPEG**... 
        > **The focus of this layer is having a common ground to present data between applications.** Billions of image files are transferred every day. Each of these files contains an image that ultimately will be displayed or stored on a computer. However, each image file must be the proper specified file format. This way, the application that reads the image file understands the type of data and the format contained in it. 
    - text formats: ASCII, UNICODE...
    - audio formats: WAV, MP3, AIFF...
    - even HTML, Javascript, ... 
        > file formats are **'translated'**(or interpreted, by a web browser) to display images and text, and play audio.
    - password encrpytion on data
    - more broadly said: HTTP(S)

#### 5. Session layer
- maintainins communication by establishing, managing and terminating sessions between devices
- **Examples**:  
    - TCP/IP Sockets: you know they establish sessions.
    - NETBIOS: allows applications on separate computers to communicate over a local area network. (strictly an API, not a protocol. One protocol for this is NETBIOS over TCP/IP)

#### 4. Transport layer
- decides information sent at a time
- provides **reliable** process to **deliver** & **recover** data.
- **Examples**: 
    - TCP(Transmission control protocol) ([three-way handshake](https://9oelm.github.io/2018-05-12--Three-way-handshake-in-TCP-&-ACK-and-SYN-flood-attack/)). **Sequence number identifies the order of the bytes**  sent from each computer so that the data can be reconstructed in order, regardless of any packet reordering, or packet loss. **Acknowledgement**  are sent with a sequence number by the receiver of data to tell the sender that **data has been received to the specified byte.**   
    - UDP(User datagram protocol): speed over quality

#### 3. Network layer
- moves packets from source to destination
- routers work on this level -> IP address is also at this level
- **Example**: 
    > When you message your friend, **this layer assigns source and destination IP addresses to the data segments.** Your IP address is the source, and your friend’s is the destination. It finds **the best path** for delivery too.

#### 2. Data link layer
- organises **bits into frames** and ensures hop to hop delivery
- switches at this level -> Adds **sender and receiver MAC addresses** to the data packet to form a frame (switches vs routers: **switch** is designed to connect computers within a network (local area network, LAN), while a **router** is designed to connect multiple networks together (wide area network, WAN))
- enables frames to be transported via local media (e.g. copper wire, optical fiber, or air), done@device's Network Interface Card

#### 1. Physical layer
-  transmission of data through a medium (a real, physical wire, electrical, light, or radio signal)

### Mnemonic
> **A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing

### Illustrations from [Plixer.com](https://www.plixer.com/blog/network-monitoring/network-layers-explained) to grasp the concept in seconds

![OSI layers 1](./osi-layers-1.PNG)
![OSI layers 2](./osi-layers-2.PNG)
![OSI layers 3](./osi-layers-3.PNG)

More useful info
- https://medium.com/@madhavbahl10/osi-model-layers-explained-ee1d43058c1f
- https://www.plixer.com/blog/network-monitoring/network-layers-explained/

## HTTP/2
### Goal of HTTP/2
- **reduce latency** by enabling full request, response multiplexing
- **minimize protocol overhead** via efficient compression of HTTP header fields
- add support for request prioritization and server push

### HTTP/2 vs HTTP/1.x
- **HTTP/2 does not modify the application semantics of HTTP** in any way. All the core concepts, such as HTTP methods, status codes, URIs, and header fields, remain in place. 
- Instead, **HTTP/2 modifies how the data is formatted** (framed) and **transported** between the client and server

### SPDY and HTTP/2
- Google started to develop **SPDY** in 2009 to address performance issues of HTTP/1.1 and **brought a good result** after a while 
- HTTP-WG(Working group) started working on HTTP/2 based on SPDY, and was accepted as a de facto global standard for web in 2015, surpassing SPDY which is now obsolete. 

### Performance problems in HTTP/1.x solved in HTTP/2
- clients **need to use multiple connections** to achieve concurrency and reduce latency; 
- **does not compress request and response headers**, causing unnecessary network traffic; 
- **does not allow effective resource prioritization**, resulting in poor use of the underlying TCP connection;

More useful info 
- https://developers.google.com/web/fundamentals/performance/http2/

## HTTPS
It enforces three things: privacy, integrity, and authentication
### 1. **Privacy** 
> Encrypting data such that anything in-between your browser and the website cannot read your traffic.

- Anybody can see what you are looking into over HTTP.

### 2. **Integrity**
> Ensuring that the data received on either end has not been altered unknowingly along the way.

- Plain, unencrypted messages can be caught in the middle, modified, and sent to the receiver (man-in-the-middle attack). 

### 3. **Authentication**
Proving that the website your browser is talking to is who they say they are.

- HTTPS, via **SSL certificates**, ensures you are connected exactly with the receiver you would expect.

More useful info
- https://www.howtogeek.com/181767/htg-explains-what-is-https-and-why-should-i-care/
- https://strongarm.io/blog/how-https-works/
- https://howhttps.works/

## Symmetric & Asymmetric cryptography 
### Symmetric cryptography
- There is **only one key** to encrypt and decrypt
- It's like putting the message in a box and locking the box with a key. **Only the person that has a copy of the key can open the box** and read the message. 
- More technically, HTTPS uses SSL (Secure Socket Layer) with RSA algorithm to encrypt data.
- **The key must be kept private.** You should not share the key in plain text, or send it with the box.
- **Problem with symmetric keys**: hard to share. And this brings us to asymmetric keys.

### Asymmetric cryptography
- You got **2 keys**
- One is **public**, the other **private**.
- **Public key** can be shared anywhere.
    ```
    A sends its public key to B
    B sends a message back, encrypting it with the public key
    A decrypts the message with his private key
    ```
- Only the private key can open a box locked with the public key pair.

> The server generates two large prime numbers, and multiplies them together. This is called the "public key". This key is made available to any client which wishes to transmit data securely to the server. The client uses this "public key" to encrypt data it wishes to send. Now because this is an asymmetric algorithm, the public key cannot be used to decrypt the transmitted data, only encrypt it. In order to decrypt, you need the original prime numbers, and only the server has these (the "private key"). On receiving the encrypted data, the server uses its private key to decrypt the transmission.

> In the case of you browsing the web, your browser gives the server its public key. The server uses this key to encrypt data to be sent to your browser, which then uses its private key to decrypt.

### The HTTPS (SSL/TLS) handshake
The **negotiation** between a browser and a server, is called "the handshake".

1. **[CLIENT HELLO]** CLIENT **sends a list of SSL/LTS versions and encryption algorithms (called cypher suite)** that it can work with the server.
2. **[SERVER HELLO 1]** SERVER **chooses the best SSL/TLS version and encryption algorithm** based on its preferences.
3. **[SERVER HELLO 2]** SERVER replies with its certificate (includes public key)
4. **[Client Key Exchange 1]** CLIENT verifies legitimacy of the certificate.
5. **[Client Key Exchange 2]** CLIENT generates a **pre-master key**, encrypts it with the public key, a**nd sends it back to SERVER. The **pre-master key is a random byte string that enables both the client and the server to compute the secret key to be used for encrypting subsequent message.**
6. **[Change Cypher spec 1]** SERVER decrypts with its private key to get the **pre-master key**.
7. **[Change Cypher spec 2]** SERVER and CLIENT both generate the same 'shared secret' to use for subsequent messaging
8. **["Finished"]** CLIENT sends **"finished" message encrypted with the secret key**. SERVER decrypts it. 
9. **["Finished"]** SERVER sends **"finished" message encrypted with the secret key**. CLIENT decrypts it.
10. The SERVER and CLIENT can now exchange messages **that are symmetrically encrypted with the shared secret key.**

### Illustration from [SSL.com](https://www.ssl.com/article/ssl-tls-handshake-overview/) to help
![SSL Handshake](./ssl-handshake.png)

More useful info
- https://stackoverflow.com/questions/3968095/how-does-https-provide-security
- https://www.ibm.com/support/knowledgecenter/en/SSFKSJ_7.1.0/com.ibm.mq.doc/sy10660_.htm
- https://howhttps.works/the-handshake/
- https://medium.com/@kasunpdh/ssl-handshake-explained-4dabb87cdce

## SSL and TLS
> TLS is the new name for SSL. **Namely, SSL protocol got to version 3.0; TLS 1.0 is "SSL 3.1".** TLS versions currently defined include TLS 1.1 and 1.2. Each new version adds a few features and modifies some internal details. We sometimes say "SSL/TLS".

More useful info
- https://stackoverflow.com/questions/3690734/difference-between-ssl-tls
- https://security.stackexchange.com/questions/5126/whats-the-difference-between-ssl-tls-and-https

## How could SSL/TLS not be safe
**IMPORTANT**: as of [**February 2019, TLS v1.3 (state-of-art protocol) is no longer safe.**](https://www.nccgroup.trust/us/about-us/newsroom-and-events/blog/2019/february/downgrade-attack-on-tls-1.3-and-vulnerabilities-in-major-tls-libraries/) More easily said: NOTHING IS SAFE. 

- All SSL versions: vulnerable
- TLS 1.0: vulnerable
- TLS 1.1: vulnerable
- TLS 1.2: vulnerable
- TLS 1.3: now vulnerable.

Some known vulnerabilities: [POODLE](https://en.wikipedia.org/wiki/POODLE), [BEAST](https://en.wikipedia.org/wiki/Transport_Layer_Security#BEAST_attack), [CRIME](https://en.wikipedia.org/wiki/CRIME), [BREACH](https://en.wikipedia.org/wiki/BREACH), [Heartbleed](http://heartbleed.com/)

More useful info
- https://kb.iweb.com/hc/en-us/articles/230268628-SSL-TLS-issues-POODLE-BEAST-SWEET32-attacks-and-the-End-of-SSLv3-OpenSSL-Security-Advisory
- https://www.acunetix.com/blog/articles/tls-ssl-cipher-hardening/
- https://www.zdnet.com/article/new-tls-encryption-busting-attack-also-impacts-the-newer-tls-1-3/
- https://kinsta.com/blog/tls-1-3/
- https://www.nccgroup.trust/us/about-us/newsroom-and-events/blog/2019/february/downgrade-attack-on-tls-1.3-and-vulnerabilities-in-major-tls-libraries/
- https://securityboulevard.com/2019/02/security-researchers-discloses-vulnerabilities-in-tls-libraries-and-the-downgrade-attack-on-tls-1-3/

## How does compression work? What's lossy and loseless compression?
### Compression


### Loseless compression
- Exploits statistical redundancy to represent data **without losing any information**
- For **example**, an image with same red pixels: "red pixel, red pixel, ..." -> "279 red pixels"

### Lossy compression
- Drops unimportant details to save storage
- **Examples**: JPEG, DVD, Blu-ray

More useful info
- https://stackoverflow.com/questions/16469410/data-compression-algorithms
- https://superuser.com/questions/132303/how-does-file-compression-work


## Wifi: WEP, WPA, WPA2, WPA3


More useful info
- https://en.wikipedia.org/wiki/Wi-Fi_Protected_Access

## Virtual memory
## Cache
## HDD, SSD, DRAM
## Pros & cons of NoSQL
## Node.js
## CDN
## Infrastructure as code
## MV* Pattern
