# the Complexities of the Internet 

## Domain Name System (DNS)

- The internet is addressed through **IP** (Internet Protocol) and the DNS serves as a sort of Yellow Pages for the internet.

- All webpages have a unique IP address, and the **Domain Name System** is like an address book that matches domain name to IP address.

- When a **URL** (uniform resource locator) is typed into your browser, your machine sends a out a DNS request to locate the corresponding IP address.


<p align="center">
  <img src="https://sw.nohold.net/CiscoSB/Images/3775_1.png">
</p>



## Steps of a DNS Request

- When you enter a URL into your web browser, the DNS request will first be sent to a **recursive name server**. The recursive name server is typically operated by your ISP (internet service provider).
- A recursive name server would be like a phone operator looking into a phone book on behalf of the requesting party. Further, in the recursive case, last names have a seperate phone book and first names have another phone book, making the process categoristically recursive. 
- The recursive name sevrer can also be operated by other sources, such as [Google](https://developers.google.com/speed/public-dns/).
- A recursive name server might have the IP address your looking for already *cached*, but if not it will search 13 root servers which manage requests for **top level domains** (TLD).
- TLDs include .com, .net, .org, and more.

<p align="center">
  <img src="http://atelier.inf.unisi.ch/~dalsat/sai/projects/2015/media/images/internet/www_domain_top.jpg">
</p>

- The TLD server will then contact **authoratative name servers** that contain authoratative lists of IP addresses under the specified top level domain.
- Authoratative name servers are updated every time someone buys and registers a new domain name.
- Once the specific domain name to IP address mapping is found, the infomation is sent back to the recursive name server (hopefully this clears up why the process is recursive 😉).
- To save time in the future both the recursive name server and your own machine will cache (save) the DNS entry (record).



#### Interesting Side Note

Hackers can get into your DNS cache and change the records to point seemingly inoccuous website to malicious ones. As such, it is a good preventative measure to clear your DNS cache from time to time.



Here's the command on Mac and other Unix machines:

`sudo killall -HUP mDNSResponder;sudo killall mDNSResponderHelper;sudo dscacheutil -flushcache`


#### More Resources
- [Cisco Blog on the Difference Between Recursive and Authotative Name Servers](https://umbrella.cisco.com/blog/2014/07/16/difference-authoritative-recursive-dns-nameservers/)


