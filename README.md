<p align=center>my handwritten notes on software engineering concepts</p>
<br><br>

<p align=center> 
    <a href=#dns>dns</a> • <a href=#http>http</a> • <a href=#git>git</a> 
</p>

# dns

> learnt from aws, wikipedia.

- domain name system. since 1980s. first, the SRI (the standford research institute) maintained a file named `hosts.txt` that mapped host names to numerical addresses of computers on the ARPANET.

- ip addresses are not human-memorizable, we like readable names or web addresses. that's where dns resolution comes in. to translate a web address like 'www.example.com' to its ip address like '1.2.3.4'.

- there's always a dns lookup followed by the actual protocol connection.

- who are those dns resolvers? they are the isp, public dns resolvers like google and cloudflare. there can also be resolvers in home or corporate networks, or local dns resolvers.

## how a dns is resolved

> wikipedia

- the iterative approach to resolving dns is mandated by rfc 1034.

- in practice, caching is used in dns servers to off-load the root servers. root name servers are actually involved in resolving a small fraction of all requests.

- and the resolution process starts with a query to one of the root servers. 

    - the root servers do not answer directly but respond with a referral to more authorititive servers (hence the name recursion). 

    - until it receives an authoritative answer or the FQDN (fully qualified domain name) such as www.wikipedia.org.

![](https://en.wikipedia.org/wiki/File:Example_of_an_iterative_DNS_resolver.svg)

## aws route53

- managed dns services like route 53 have advantages:

  - anycast network with redudant locations: redundancy across multiple server locations, hopefully closer to the user, make faster dns resolves.

  - lbr (location-based routing): based on end-users location you can give them an ip address closer to their region.

  - route53 monitor: to check if one region goes down, then route53 can respond by giving a different ip address.

  - route53 makes integrations with other aws services easier
    - elastic load-balancing
    - elastic beanstalk
    - cloudfront

## reverse dns lookup

- a reverse dns lookup is a query of the dns for domain names when the ip address is known.

## client lookup

- client applications like web browsers, email clients, etc actually asks the dns resolver in the local operating system!

# http

> learnt from mdn

- hypertext transfer protocol. designed in 1990s.

- an application-layer* protocol for transmitting hypermedia*.

- designed for communication between web browsers and web servers.

- stateless protocol: the server doesn't store any data between two requests. each request is understood separately.

- due to the extensibility of http, videos and images can be fetched too.

<sub>* hypermedia refers to plain text, images, videos, hyperlinks, audio altogether.</sub>

<sub>* application-layer refers to the OSI model.</sub>

## messages

- a client initiaites the message. such messages are called 'requests'. and the server returns a 'response'. for web-browsers, the server responds with html web pages.

- servers never inititate a request (although that's added nowadays).

### how the browser displays a webpage

- the browser sends a request to fetch a html document.

- then the browser parses the file, makes additional requests corresponding to execution script (aka javascript), layout information (aka css), and sub-resources contained within the page (such as images and videos).

- finally the web browser combines these resources to present a complete document - called a 'web page'

## headers

- http headers let the client and the server pass additional information with an http request or response.

- custom proprietary headers are used with an `x-` prefix. (but this is deprecated in june 2012, but still quite common.)

- headers can be grouped according to their contexts:
    - request headers:
        - contain more info about the resource to be fetched
        - or, contain more info about the client
        - e.g. ???
    - response headers:
        - hold additional info about the response
        - e.g. `server: apache`
    - representation headers
        - contain info about the body of the resource
        - e.g. mime type, encoding/compression.
    - payload headers
        - contain info about payload data
        - e.g. content-length

# hosting

- web hosting services allow users to publish their website or web application on the internet.

- users of a hosting service rent space on a physical server to store files and data necessary for their website to function.

- 3 types of web hosting are:

    - shared hosting: same cpu, ram, storage, bandwidth of a server will be utilized by multiple domains/users. however, other domains/users cannot access your files since they won't have file-system access to your directories. best to use if monthly visitors are <30k. low monthly fees. examples include 000webhost.com.

    - virtual private server (vps): partitions a server's computing resources in a way that provides to the user an abstraction of a dedicated server. best for a bit complex websites. requires some in-house technical expertise.

    - dedicated hosting: gives you exclusive access to the complete physical server. best for complex applications requiring large amount of processing power.

    - cloud: the latest iteration in web hosting and using compute resources.

# programming languages

- a programming language is a (human-readable) system of notation to write computer programs (or to specify instructions for a computer).

    - meaning, a language tries to be human-readable and provide a structured approach to specify computing processes such as: declaring a variable, defining a function, allocating memory, executing operations on the variable, etc.

    - notation? - the word 'notation' refers to a structured/standardized way to communicate concepts.
 
    - computer programs? - a program is a list of instructions that can be executed by a cpu.
    
    - instructions? - a computer's processor can only understand machine language - 0s and 1s. instructions written using a programming language is translated/compiled to machine language for the processor to execute.

# git

# operating systems

## how they work

## memory management, ipc, threads, concurrency, scheduling

# databases

## relational databases

## non relational databases

## concepts

## scaling and architecture

# caching

# web security 
see backend-dev/security

# software design and development patterns

# architectural patterns

# search engines, message broker

# containerization vs virtualization
