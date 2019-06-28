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

## How does compression work
## Virtual memory
## Cache
## Asymmetric cryptography 
## HTTP/2 & HTTPS
## HDD, SSD, DRAM
## Wifi
## Pros & cons of NoSQL
## Node.js
## CDN
## Infrastructure as code
## MV* Pattern