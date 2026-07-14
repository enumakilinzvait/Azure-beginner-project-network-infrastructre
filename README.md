# Azure-beginner-project-network-infrastructer

# Azure Fundamentals: Implementing Network Security Groups (NSGs)

 INTRO

Sometimes you have to get your hands dirty and adding motion is even better. So welcome to PAIN and prepare the surface area to receive a lot of errors, but fear thee less its just the beginning. SO today we are gonna look at a proper netowrk infrastructre u see the one where u join an organization and they hand you laptopt already configured . Yeaaah its not magic you are gonna see how its done


JUST ANY WORKING BRAIN IS DOABLE

- Basic understanding of cloud computing
- An Azure account (free trial available)
- Basic knowledge of command-line interface (CLI)

WEAPONS AT HAND
Azure cli (the terminal used in scripting

Before we begin create aresoure group head on search bar and type "resource group" 
      input name
      region that is closest to you
      finnaly your subscription
and before you ask a resource is just as the name implies a file for where you put organize your reosurces in the cloud

 Quests

Quests1: Create a Virtual Network and Subnet

PATH 1 TO COMPLETE QUEST 1

1. Log in to the [Azure Portal](https://portal.azure.com/).
2. Navigate to "Create a resource" and select "Virtual Network".
3. Configure the virtual network:
    - Name: pick any - name must be unique
    - Address space: `10.0.0.0/16` in most time they choose this for you as th only option
    - Subnet name: pick any dont ask CHATGPT:)
    - Subnet address range: `10.0.1.0/24`
4. Review and create the virtual network.
   So now you have created your first virtual network a literal network witout even piulling cables 

MOVE ON TO THE NEXT and relax do it slowly do not rush 

Quest 2: Launch an Azure Virtual Machine
Now you already have network but for what it needs a machine to run on it to see if it works 

THY PATH 2

1. Search bar ( virtual machine)
2. Configure the VM:
    - Name: a uniqe name like as long as its not GPT guyssss :)
    - Region: Select a region now here when selecting regions to ensure compatibility select on the same region of the resoruce group you created it beocmes esier when connecting all of them
    - Image: Windows Server 2019 Datacenter even the azure editon is fine
    - Size: B1s (Basic)
    - Authentication type: Password
    - Username: 'bubble'
    - Password: Choose a strong password not your birthday date
    - Do not immediately press review=create relaxx click next on the networking section
    - network section choose the virtual network with its subnets you created on first quest
3. Review and create the virtual machine.


QUEST 3: Create a Network Security Group (NSG)

PATH 3
I know you are asking wy are putting another firewall here on the secuirty group and we but one on the virtual network well think again today i will teach how to slap firewalls anywhere and everywhere. Ever heard of the term reaping where thy did not sow exaclty this is why we slap them everywhere.

if you did on the virtual netowrk is still okay no worries

1. Navigate to "Create a resource" and select "Network Security Group".
2. Configure the NSG:
    - Name: `myNSG`
    - Region: Same as the VM region
3. Review and create the NSG.

STOP SAYING YOU ARE TIRED WE HAVE JUST BEGUN

Quest 4: Configure Inbound and Outbound Security Rules

Remember when we said that security groups are statefull well it was not just a bluff this  they actuly are this inbound rules and otubound rules allow return traffic automatically so even setting the inbound rules is okay but its different when setting up Network ACLs in eg. AWS 

1. Navigate to the newly created NSG `myNSG`.
2. Under "Settings", click on "Inbound security rules".
I know you have seen the RDP protocol part do not despair remember when someone ssays they are working from home in most cases this waht they utilise. Since you have seen the notification telling you it dangerous to set the Remote Desk Protocol to allow any ip to access we are shifting it to only your IP address
3. Add an inbound rule to allow RDP (port 3389) from your IP address:
    - Source: IP Addresses
    - Source IP address: Your IP address now you can ask GPT:)
    - Destination: Any
    - Destination port ranges: 3389
    - Protocol: TCP
    - Action: Allow
    - Priority: 1000
    - Name: `Allow-RDP`
4. Under "Settings", click on "Outbound security rules".
5. Ensure the default outbound rule allows all outbound traffic.



Quest 5: Associate NSG with the VM's Network Interface

PATH 5
You will find that you already associated them in the previosu quests if you did not rush the process and read carefuly
1. Navigate to the "Network interfaces" section in the Azure Portal.
2. Select the network interface associated with `myVM`.
3. Under "Settings", click on "Network security group".
4. Associate the network interface with the NSG `myNSG`.

##Expected conclusion:
 YOU NAILED IT

## Conclusion

By completing these exercises, you have successfully set up an Azure VM, created a Network Security Group, configured security rules, and associated the NSG with your VM. These skills are essential for securing Azure resources and managing network traffic effectively.
