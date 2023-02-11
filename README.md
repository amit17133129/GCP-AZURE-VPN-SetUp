# GCP-AZURE-VPN-SetUp


Hello guys, hope you all doing good. Back again with another article that will helps you to create a vpn setup with azure and gcp cloud.

## What is VPN connection ?
VPN stands for “Virtual Private Network” and describes the opportunity to establish a protected network connection when using public networks. VPNs encrypt your internet traffic and disguise your online identity. This makes it more difficult for third parties to track your activities online and steal data. The encryption takes place in real time.

## How does a VPN work?
A VPN hides your IP address by letting the network redirect it through a specially configured remote server run by a VPN host. This means that if you surf online with a VPN, the VPN server becomes the source of your data. This means your Internet Service Provider (ISP) and other third parties cannot see which websites you visit or what data you send and receive online. A VPN works like a filter that turns all your data into “gibberish”. Even if someone were to get their hands on your data, it would be useless.

## What are the benefits of a VPN connection?
A VPN connection disguises your data traffic online and protects it from external access. Unencrypted data can be viewed by anyone who has network access and wants to see it. With a VPN, hackers and cyber criminals can’t decipher this data.

### Secure encryption: 
To read the data, you need an encryption key . Without one, it would take millions of years for a computer to decipher the code in the event of a brute force attack . With the help of a VPN, your online activities are hidden even on public networks.

### Disguising your whereabouts : 
VPN servers essentially act as your proxies on the internet. Because the demographic location data comes from a server in another country, your actual location cannot be determined. In addition, most VPN services do not store logs of your activities. Some providers, on the other hand, record your behavior, but do not pass this information on to third parties. This means that any potential record of your user behavior remains permanently hidden.
      
### Access to regional content: 
Regional web content is not always accessible from everywhere. Services and websites often contain content that can only be accessed from certain parts of the world. Standard connections use local servers in the country to determine your location. This means that you cannot access content at home while traveling, and you cannot access international content from home. With VPN location spoofing , you can switch to a server to another country and effectively “change” your location.
      
### Secure data transfer: 
If you work remotely, you may need to access important files on your company’s network. For security reasons, this kind of information requires a secure connection. To gain access to the network, a VPN connection is often required. VPN services connect to private servers and use encryption methods to reduce the risk of data leakage.
      
## What kind of VPNs are there?
There are many different types of VPNs, but you should definitely be familiar with the three main types:

### SSL VPN
Often not all employees of a company have access to a company laptop they can use to work from home. During the corona crisis in Spring 2020, many companies faced the problem of not having enough equipment for their employees. In such cases, use of a private device (PC, laptop, tablet, mobile phone) is often resorted to. In this case, companies fall back on an SSL-VPN solution, which is usually implemented via a corresponding hardware box.

The prerequisite is usually an HTML-5-capable browser, which is used to call up the company’s login page. HTML-5 capable browsers are available for virtually any operating system. Access is guarded with a username and password.

### Site-to-site VPN
A site-to-site VPN is essentially a private network designed to hide private intranets and allow users of these secure networks to access each other’s resources.

A site-to-site VPN is useful if you have multiple locations in your company, each with its own local area network (LAN) connected to the WAN (Wide Area Network). Site-to-site VPNs are also useful if you have two separate intranets between which you want to send files without users from one intranet explicitly accessing the other.

Site-to-site VPNs are mainly used in large companies. They are complex to implement and do not offer the same flexibility as SSL VPNs. However, they are the most effective way to ensure communication within and between large departments.

### Client-to-Server VPN
Connecting via a VPN client can be imagined as if you were connecting your home PC to the company with an extension cable. Employees can dial into the company network from their home office via the secure connection and act as if they were sitting in the office. However, a VPN client must first be installed and configured on the computer.

This involves the user not being connected to the internet via his own ISP, but establishing a direct connection through his/her VPN provider. This essentially shortens the tunnel phase of the VPN journey. Instead of using the VPN to create an encryption tunnel to disguise the existing internet connection, the VPN can automatically encrypt the data before it is made available to the user.

This is an increasingly common form of VPN, which is particularly useful for providers of insecure public WLAN. It prevents third parties from accessing and compromising the network connection and encrypts data all the way to the provider. It also prevents ISPs from accessing data that, for whatever reason, remains unencrypted and bypasses any restrictions on the user’s internet access (for instance, if the government of that country restricts internet access).

The advantage of this type of VPN access is greater efficiency and universal access to company resources. Provided an appropriate telephone system is available, the employee can, for example, connect to the system with a headset and act as if he/she were at their company workplace. For example, customers of the company cannot even tell whether the employee is at work in the company or in their home office.

## Azure side configuration:
First thing we will do is to create azure resource group. In azure resource group is global. Everything will be configured inside the same resource group.

### Resource Group:
A resource group is a container that holds related resources for an Azure solution. The resource group can include all the resources for the solution, or only those resources that you want to manage as a group

<p align="center">
  <img width="1000" height="500" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*LZYt-31-OTyjrAUwdQ0MnQ.png">
</p>

Finally you can see that resource group is created with the name of az-gcp-rg.

### Virtual Network:
Azure Virtual Network (VNet) is the fundamental building block for your private network in Azure. VNet enables many types of Azure resources, such as Azure Virtual Machines (VM), to securely communicate with each other, the internet, and on-premises networks. While creating the Vnet you have to provide the following resources that is mentioned in the below image.

<p align="center">
  <img width="1000" height="600" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*d_budgXerR3w8JEGRbuvTw.png">
</p>

### Subnet:
A subnet is a range of IP addresses in the virtual network. You can divide a virtual network into multiple subnets for organization and security. Each NIC in a VM is connected to one subnet in one virtual network.

<p align="center">
  <img width="1000" height="150" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*kbWBzvzLSdtiqv4lecj2Rg.png">
</p>

<p align="center">
  <img width="1000" height="50" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*4Zr8QGGHv-XrlFstSV1BEw.png">
</p>

### Gateway Subnet:
The gateway subnet is part of the virtual network IP address range that you specify when configuring your virtual network. It contains the IP addresses that the virtual network gateway resources and services use. When you create the gateway subnet, you specify the number of IP addresses that the subnet contains.

The range of the gateway subnet should be the same of the subnet. Here i have given 10.0.2.0/27.

<p align="center">
  <img width="1000" height="500" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*_2YDS90CI_NS80ER1B-gKg.png">
</p>

Below you can see that the subnet and gateway subnet is created successfully in the same vnet.

<p align="center">
  <img width="1000" height="100" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*kCpCJde0caiOAC9mlpHsqQ.png">
</p>

### GCP side configuration:
Now lets navigate to GCP side to make the networking configurations. First we will create the VPC. While creating the VPC you have to give the below details as mentioned in the image. In GCP there is no cidr for VPC the cidr ranges applied on the subnet section only.

<p align="center">
  <img width="1000" height="800" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*VBysGe85NJqCHFO8eCqC1g.png">
</p>

Here you can see that the subnet will need the cidr ranges which i have given as 192.168.1.0/24.

<p align="center">
  <img width="1000" height="800" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*d4D1FxbUt4jqFXOshN565A.png">
</p>

I am allowing the firewall to be all traffic from the default firewall rules. Keep the dynamic routing mode as global.

<p align="center">
  <img width="1000" height="500" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*lYbAKk-t-vC-lLBIsIu8UQ.png">
</p>

Here you can see that the vpc is created successfully.

<p align="center">
  <img width="1000" height="100" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*4IT0kIQLfFk8AdTzJwI29Q.png">
</p>

### HA VPN Configuration:
The HA VPN gateway uses two tunnels, both tunnels to the single external IP address on the peer device. In Google Cloud, the REDUNDANCY_TYPE for this configuration takes the value SINGLE_IP_INTERNALLY_REDUNDANT . The following example provides 99.99% availability. While configuring the HA VPN you have to select the High-availbilty (HA) VPN.

<p align="center">
  <img width="1000" height="800" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*t5HFXWdTXnBK0XymhiglBQ.png">
</p>

When you on the below page while configuring the HA VPN you have to give the name of the VPN, the network name and the region in which you would like to create the HA VPN here i am taking the default region as us-east1.

<p align="center">
  <img width="1000" height="600" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*PjbGLUQtVtVgl4_nRvQ9EA.png">
</p>

After clicking on create and continue i will provide you the two interfaces as you can see below. These interface ip’s will be useful later.

```
interface 0: 35.242.3.33
interface 1: 35.220.0.218
```

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*4ZB_UqRciKsVurJ-kFNQHA.png">
</p>

## Azure side configuration:
### Public IP:
Now lets move to azure side to create the public ip address. Public IP addresses allow Internet resources to communicate inbound to Azure resources. Public IP addresses enable Azure resources to communicate to Internet and public-facing Azure services. The address is dedicated to the resource, until it’s unassigned by you. Here i am creating two public-ip addresses.

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*k1e7kC-H45LPuUyZc2PDPw.png">
</p>

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*AaOiL60NdQ8x45V39UZtuw.png">
</p>

As you can see below that the two public ip addresses created successfully. Below i have noted down the ip public ip addresses that we will be using later.

```
az-gcp-pip-01: 20.253.10.219
az-gcp-pip-02: 20.253.11.198
```

<p align="center">
  <img width="1000" height="100" src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*y3_Yn-m3iopl7o2qkGLb6w.png">
</p>

## GCP side configuration:
### Peer VPN Connection:
Now lets move to gcp side to create the peer vpn gateway. Cloud VPN securely connects your peer network to your Virtual Private Cloud (VPC) network through an IPsec VPN connection. Traffic traveling between the two networks is encrypted by one VPN gateway and then decrypted by the other VPN gateway. This action protects your data as it travels over the internet.

While creating Peer VPN gateway it will ask you to enter the vpn interface’s ip’s. We be moving towards two interfaces ip’s. You have to enter the public ip addresses which we created in azure.

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*c8KzMfZnLYBS5PyQEDfxUA.png">
</p>

### Cloud Routers:
Cloud Router is a fully distributed and managed Google Cloud service that uses the Border Gateway Protocol (BGP) to advertise IP address ranges. It programs custom dynamic routes based on the BGP advertisements that it receives from a peer.

While creating the cloud router you have to give the name of the cloud router, the google ASN (enter randomly) and click on create.

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*apGTs6b_6BuDr006uFaULg.png">
</p>

After creating cloud router we will be configuring the tunnels. Here we will be configuring the two tunnels. While configuring the tunnel you have to give the name of the tunnel, the IKE version and the pre shared key. Here the pre shared key wil be generated when you click on generate and copy. Note: Keep this pre-shared key with yourself. We will require this pre-shared key late while configuring the vpn in azure.

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*YNZiNS9uoget4wJrfIQAeA.png">
</p>

After configuring the tunnel you will seeing the below screen. You have to save the cloud VPN gateway IP addresses. We will require this ip addresses while configuring the BGP sessions.

```
Cloud VPN gateway IP 1: 35.242.3.33
Cloud VPN gateway IP 2: 35.220.0.218
```

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*h_yhaBvNmI8MOH7OKl9VHg.png">
</p>

## Azure side configuration:
Azure Virtual Network (VNet) is the fundamental building block for your private network in Azure. VNet enables many types of Azure resources, such as Azure Virtual Machines (VM), to securely communicate with each other, the internet, and on-premises networks.

While creating the virtual network gateway select the name of the virtual network gateway, the region in which you wanted to have this virtual network gateway and all the details as per below image.

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*d-5uTp8FXH3Byoe_ZCSOMQ.png">
</p>

Click on use existing to add the public ip addresses that we created earlier. Add the primary and secondary public ip addresses as mentioned below. Add the ASN number randomly. Enter the custo azure APIPA BGP address in the range of below ip address and click on review and create.

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*9Jm_Qd_hkwyxJ8Cto3EpQg.png">
</p>

Finally, we can see that virtual network gateway is created successfully.

<p align="center">
  <img width="1000" height="100" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*LTwUomlCvGvCbCDQqBqH4g.png">
</p>

### Local network gateway:
The local network gateway is a specific object that represents your on-premises location (the site) for routing purposes. You give the site a name by which Azure can refer to it, then specify the IP address of the on-premises VPN device to which you’ll create a connection.

Here while configuring the local network gateway we will add the gcp cloud vpn gateway ip 1 and ip2 respectively. Addresses spaces will be the same as we have given while creating the virtual network gateway. Make sure you will be the range of cidr as /32.

Click on advance and give the google ASN i.e. 65001 (remember we added this ASN while creating HA VPN in gcp) and BGPpeer IP address will be the same as what you enetered in the address spaces. Finally click on create.

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*VQNOXgR6QGm-bxdv7o0drQ.png">
</p>

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*mdTvA_8vwf0SNKXJy9ZQIA.png">
</p>

The same process you have to follow creating the second local network gateway. Remember we will be adding the second ip address from cloud VPN gateway.

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*KLuBhdAIGxym23SQ_xEhcQ.png">
</p>

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*S8_tJjDZX_YcIyzj5xm3jg.png">
</p>

Finally you can see that the two local gateway internet is created successfully.

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*7am2V3UejsPK1xdFPvDZew.png">
</p>

After creating the local network gateway we will be adding the connections inside the virtual network gateway. Navigate to virtual network gateway and click on connections. We will create the first connection. While configuring the first connection select the connection type as site-to-site(IPsec). Select the virtual network gateway that you created. Later select the first local network gateway while creating the first connection. Similarly, select the second local network gateway while configuring the second connection.
Add the pre-shared key that was created while configuring the tunnel in HA VPN on the GCP side. After enabling the BGP you will able to see primary and secondary custom BGP addresses.

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*7GXtxU722lAVBbLyDeX7OA.png">
</p>

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*LZIURZ--nxBmmbvxd0a1EQ.png">
</p>

Finally you can see below that connections are successfully created.

<p align="center">
  <img width="1000" height="100" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*2cs7vJEscw2QyVgSYoc9qQ.png">
</p>

## GCP side configuration:
On the GCP side we left at configuring the tunnels. Now we will be creating the BGP sessions of each tunnel. While configuring the BGP allocate the Peer ASN and BGP IPv4 addresses that we given while creating the virtual network gateway. In the similar fashion we have to configure the BGP session for second tunnel.

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*uvaVFtro32tlh6HSMWeTWg.png">
</p>

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*5tuz2qiH1bFEYB3vxcjVZQ.png">
</p>

As you can see the tunnel have BGP session established successfully.

<p align="center">
  <img width="1000" height="100" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*f9MU-jhV5BoKT6SDqYjepQ.png">
</p>

Now you have to create the virtual machines on the both the side i.e. azure and gcp. Make sure you creating the VM in the same network in which you made all the configurations earlier.

<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*aWW2yjRUbOH3iFPr2MTxAA.png">
</p>

As you can see that from the gcp compute instance console we can able to ping the private ip address of the azure vm.


<p align="center">
  <img width="1000" height="700" src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*aWW2yjRUbOH3iFPr2MTxAA.png">
</p>

Let’s move on the gcp side, you can see that from the azure vm console we can able to ping the private ip address of the gcp vm.

I hope you had liked this article and would help you while creating the gcp and azure vpn setup successfully.

<p align="center">
  <img width="1000" height="150" src="https://miro.medium.com/v2/resize:fit:280/0*Aan_vZZQfRV6xTMu">
</p>
