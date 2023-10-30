<h1>Azure sentinel tutorial map with live attack</h1>

<h2>Description</h2>
Project consists of creating a vulnerable virtual machine within azure and using sentinel to display geographical data of live attacks on a map. <br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Sentinel</b>

<h2>Program walk-through:</h2>

The initial phase entailed the establishment of a virtual machine (VM) within the Azure cloud infrastructure. Notably, the external firewall was intentionally deactivated to render the VM openly accessible, thereby increasing its susceptibility to potential intrusion attempts.

To commence this process, I initiated the creation of an Azure portal account and subsequently configured the virtual machine. All pre-existing rules were removed, and a new inbound rule was introduced to permit unrestricted incoming traffic. This action was taken with the express purpose of making the VM conspicuously discoverable and, consequently, more vulnerable to security threats.

<img src="https://imgur.com/WpRFgEE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Subsequent to this, the next step involved the creation of a designated repository in Azure, designated as a "Log Analytics Workspace." This repository would serve as the primary repository for aggregating logs pertaining to failed login attempts originating from the VM.

<img src="https://imgur.com/GdjzYFK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Following the establishment of the Log Analytics Workspace, a connection was established between this repository and the virtual machine in question. This connection facilitated the acquisition of the VM's IP address, which was then used for remote desktop access.

<img src="https://imgur.com/86s7OtV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

To delve deeper into the security event data, the Event Viewer utility was employed to analyse logs, thereby revealing pertinent information about login attempts.

<img src="https://imgur.com/xZeiPJr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

In tandem, the implementation of Azure Sentinel, a Microsoft-native Security Information and Event Management (SIEM) solution, was carried out. Azure Sentinel was strategically integrated into the architecture to facilitate the comprehensive analysis and correlation of attack data originating from diverse sources.

To extract critical information, including IP addresses, from the Windows logs, PowerShell scripts were deployed within the virtual machine. Subsequently, this information was transmitted to a third-party application via a custom Application Programming Interface (API) key obtained from ipgeolocation.io. This API key enabled the precise geolocation data to be appended to the information and transmitted back to the virtual machine, thereby enhancing the context of the logs.

<img src="https://imgur.com/VfccwR6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Further enhancement of the security posture was achieved through the creation of a tailored log within the Log Analytics Workspace. This custom log was instrumental in bringing together the geographical data gathered from the virtual machine and its associated logs.

<img src="https://imgur.com/UynTZfh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

The culmination of this undertaking involved the design and configuration of a geographical map that visually represented the geolocation data pertaining to failed login attempts. This was achieved by generating a new query within the Azure Sentinel platform and subsequently incorporating it into the map visualization. The resultant map vividly illustrated the geographical distribution of failed login attempts originating from various locations.


<img src="https://imgur.com/45W2dZz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br /> This project underlines the global prevalence of cyber threats and the paramount significance of robust security measures. As evidenced by the discovery of over 7,000 failed login attempts in Cambodia, cyber attacks are an omnipresent and persistent concern worldwide. This sobering statistic serves as a stark reminder that organisations and individuals must remain vigilant in safeguarding their digital assets. Configuring and maintaining effective firewalls is a pivotal step towards fortifying the security posture, as it acts as the first line of defence against unauthorised access and malicious activities. The project's findings emphasize the imperative of continuous vigilance and proactive security strategies in an era where cyber threats transcend geographical 



