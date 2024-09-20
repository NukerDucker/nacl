# <u>NaCl Sandbox - Homework</u>
## 02 - Introduction to Internet and Basic Network
##### 67011178 Nuker (Com-Inter)

---
**1. Three Terminologies**
- ISP : **Internet Service Provider** is companies that provides internet access to consumers. In Thailand, examples include True, AIS, and Dtac.
- API : Acts as a bridge between systems, making it easier for applications, such as web services, to interact and exchange data.
- Port : Ports enable multiple services to run on a single server, each identified by a unique port number. 
---

**2. K-FIGHT vs K-NEXT**
- Same Subnet ? :
- Could devices communicate between these two? 
---

**3. Why DNS not IP?**
- DNS Blocking: DNS is like the phonebook of the internet .Blocking DNS means preventing users from accessing specific websites. It’s easier to implement because DNS operates at the domain level.
- IP Blocking: prevents direct access to the website's server. However, many websites use shared IPs, so blocking an IP can affect other websites hosted on the same server
---
**4.Explore Network infrastructure**
- Network Layout in Place:
The home network I have at my house uses the **fiber optic in the living room as the basis.** The main router connects upstairs through the living room. Upstairs, there is an Ethernet connection **to the switch in the hallway on the second floor.** The switch spreads connections **to both the second-floor master bedroom and the guest bedroom.** Further ahead, it leads **to the third floor, where my room and another guest bedroom are.**
I have a secondary router in my room, which connects the following:
  - TV
  - PC
  - Server - hosts Jellyfin and Minecraft. The server is port-forwarded, enabling external access to these services.
  
  **Improvable**
**Increased Security in Port Forwarding :**
My port fowarding method expose my network to some kind of security risks. To fix this, setting up a VPN for remote access without opening directly to the internet would be much more secure. Another alternative is Cloudflare Tunnel, which also securely connects external traffic to internal services with no exposure of home IP

    **Pi-hole:**
    Pi-hole is a DNS-based ad-blocker that blocks unwanted ads and trackers across all devices.

    **Wi-Fi Coverage and Performance:**

    A mesh network would ensure better Wi-Fi coverage across all floors. This will go a long way in eliminating dead zones and assure consistent performance.
---
**5. Network Diagram**
    **a.How many end-devices are present in the network?** 
    End-devices are devices that accesses the network. 
```
Marketing Department:
- Laptop 1 (192.168.1.100)
- Laptop 2 (192.168.1.101)
- Laptop 3 (192.168.1.102)
- Server 3 (192.168.1.200)
- Server 4 (192.168.1.201)
  
Financial Department:
- PC 1 (10.1.1.13)
- PC 2 (10.1.1.12)
- PC 3 (10.1.1.13)
  
Server Room:
  - Server 1 (10.1.1.91)
  - Server 2 (10.1.1.92)
  
Total number of end-devices: 10
```

**b. What impact will an issue on Router 1 have on the network?**
- Internet access for the entire network would be down, since Router 1 is the only gateway to the Internet.
- Inter-department communication may also be disrupted if Router 1 handles routing between subnets.
- Internal communication within subnets will still work fine.
  
**c. What happen if there is an issue with Access Point 1**
- **Laptops communicating with each other:** ___**No.**___ If Access Point 1 fails, the laptops in the Marketing Department won't be able to communicate with each other via Wi-Fi, as this is their only point of connection.

- **Accessing Server 3 and Server 4**: ___**No.**___ Since Server 4 is connected via Wi-Fi through the same access point, it will also be unreachable. Server 3, which is wired to Switch 4, may still be operational, but the laptops won't be able to access it because Access Point 1 is down.
  
**d. Can the Financial Department access data from Server 3, which is located in the Marketing Department?**
- ___**Yes**___, the Financial Department can access data from Server 3 located in the Marketing Department.
- This access is possible because **Router 2** connects both subnets, enabling cross-subnet communication.
- 
**e. If Router 1 (with the DHCP Server) goes down, will devices with an IP still work? Could new devices connect to the router?**
- **Devices that already have an IP address:** These devices can still use their current IP and communicate within the network as long as their IP address doesn't expire.
- **New devices:** New devices trying to connect won't get an IP address because the DHCP server (on Router 1) is down. Without an IP, they can't join the network unless you manually give them one.