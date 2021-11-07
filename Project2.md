Google   2001:4860:4860:8888 And/or 2001:4860:4860:8844
Facebook 2a03:2880:2130:cf05:face:b00c::1.Faceb00c.
Tesla    199.66.11.62

 What Is Subnetting?
Subnetting is the process of stealing bits from the HOST part of an IP address in order to divide the larger network into smaller sub-networks called subnets. After subnetting, we end up with NETWORK SUBNET HOST fields. We always reserve an IP address to identify the subnet and another one to identify the broadcast subnet address. 

In the following sections you will find out how all this is possible.

Why Use Subnetting?
Here are three reasons why you may want to use subnetting:

Conservation of IP addresses: Imagine having a network of 20 hosts. Using a Class C network will waste a lot of IP addresses (254-20=234). Breaking up large networks into smaller parts would be more efficient and would conserve a great amount of addresses.

Reduced network traffic: The smaller networks that created the smaller broadcast domains are formed, hence less broadcast traffic on network boundaries.

Simplification: Breaking large networks into smaller ones could simplify fault troubleshooting by isolating network problems down to their specific existence.

How to Subnet (or the Concept of Subnetting Explained)
To better understand the concept of subnetting, imagine a network with a total of 256 addresses (a Class C network). One of these addresses is used to identify the network address and another one is used to identify the broadcast address on the network. Therefore, we are left with 254 addresses available for addressing hosts.

If we take all these addresses and divide them equally into 8 different subnets we still keep the total number of original addresses, but we have now split them into 8 subnets with 32 addresses in each. Each new subnet needs to dedicate 2 addresses for the subnet and broadcast address within the subnet.

The result is that we eventually come up with 8 subnets, each one possessing 30 subnet addresses available for hosts. You can see that the total amount of addressable hosts is reduced (240 instead of 254) but better management of addressing space is gained. 

Now that we have subnet mask explained, I'll now use a couple of examples to help explain how an IP address subnet mask can be calculated as clearly as possible, but first, here is a quick explanation of “What is a subnet mask?” An IP subnet mask is a number used for defining a range of IP addresses that are available within a network. 

How to Subset a Class C Address Using the Binary Method
It can be helpful to know how to be your own subnet mask calculator. Subset a Class C address with the binary method by following these four steps (which will be explained in more detail below):

Convert to binary.

Calculate the subset address.

Find host range.

Calculate the total number of subsets and the hosts per subnet.

We will use a Class C address, which takes 5 bits from the Host field for subnetting and leaves 3 bits for defining hosts as shown in figure 1 below. Having 5 bits available for defining subnets means that we can have up to 32 (2^5) different subnets.

It should be noted that in the past using subnet zero (00000---) and all-ones subnet (11111---) was not allowed. This is not true nowadays. Since Cisco IOS Software Release 12.0 the entire address space including all possible subnets is explicitly allowed.

Subnetting
Let's use IP address 192.168.10.44 with subnet mask 255.255.255.248 or /29.

Step 1: Convert to Binary
Subnetting
Step 2: Calculate the Subnet Address
To calculate the IP Address Subnet you need to perform a bit-wise AND operation (1+1=1, 1+0 or 0+1 =0, 0+0=0) on the host IP address and subnet mask. The result is the subnet address in which the host is situated.

Subnetting
Step 3: Find Host Range
We know already that for subnetting this Class C address we have borrowed 5 bits from the Host field. These 5 bits are used to identify the subnets. The remaining 3 bits are used for defining hosts within a particular subnet.

The Subnet address is identified by all 0 bits in the Host part of the address. The first host within the subnet is identified by all 0s and a 1. The last host is identified by all 1s and a 0. The broadcast address is the all 1s. Now, we move to the next subnet and the process is repeated the same way. 

The following diagram clearly illustrates this process:

Subnetting
Step 4: Calculate the Total Number of Subnets and
Hosts Per Subnet
Knowing the number of Subnet and Host bits we can now calculate the total number of possible subnets and the total number of hosts per subnet. We assume in our calculations that all-zeros and all-ones subnets can be used. The following diagram illustrates the calculation steps.

Subnetting
How to Subset a Class C Address
Using the Fast Way
Now let's see how to subnet the same Class C address using a faster method. Let's again use the IP address 192.168.10.44 with subnet mask 255.255.255.248 (/29). 

The steps to perform this task are the following:

Total number of subnets: Using the subnet mask 255.255.255.248, number value 248 (11111000) indicates that 5 bits are used to identify the subnet. To find the total number of subnets available simply raise 2 to the power of 5 (2^5) and you will find that the result is 32 subnets. Note that if subnet all-zeros is not used then we are left with 31 subnets and if also all-ones subnet is not used then we finally have 30 subnets.

Hosts per subnet: 3 bits are left to identify the host therefore the total number of hosts per subnet is 2 to the power of 3 minus 2 (1 address for subnet address and another one for the broadcast address)(2^3-2) which equals to 6 hosts per subnet.

Subnets, hosts and broadcast addresses per subnet: To find the valid subnets for this specific subnet mask you have to subtract 248 from the value 256 (256-248=8), which is the first available subnet address. Actually the first available one is the subnet-zero which we explicitly note. Next subnet address is 8+8=16, next one is 16+8=24 and this goes on until we reach value 248. 

10.10.10.0 is in Class A
A= net.0.0.0 or /8 
subnet mask= 255.0.0.0
Host portion=x.10.10.0

192.168.0.0 is in Class C
C= net.net.net.0 or /24  
subnet mask= 255.255.255.0
Host portion=x.x.x.0


172.168.1.0 is in Class B
B= net.net.0.0 or  /16 
 subnet mask= 255.255.0.0
Host portion=x.x.1.0
