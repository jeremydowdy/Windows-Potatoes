# Windows-Potatoes


This document is for **educational purposes** only and is not intended to promote or facilitate malicious activity. _**By accessing this information, you acknowledge and agree that you are solely responsible for your actions and any potential consequences.**_

**Introduction:**

Hot, Rotten, Lonely, Juicy, Rogue, Sweet, Generic potatoes. There are a lot of different potatoes used to escalate privileges from Windows Service Accounts to Hot, Rotten, Lonely, Juicy, Rogue, Sweet, Generic potatoes.

There are a lot of different potatoes used to escalate privileges from Windows Service Accounts to NT AUTHORITY/SYSTEM 

NT AUTHORITY/SYSTEM is a built-in Windows account with the highest level of privileges, often referred to as the system account. It has extensive access rights and is used by the operating system for critical system-level processes and services.

Privilege escalation vulnerabilities in Windows systems can pose significant security risks. Understanding and mitigating these vulnerabilities is crucial for system administrators and security professionals. This document explores various "potato" techniques used for Windows privilege escalation, providing an overview of their mechanics, limitations, and mitigation strategies.

_**Important Note:**_

_While exploring these techniques, it is essential to follow responsible disclosure practices and adhere to ethical guidelines. Avoid exploiting vulnerabilities in production environments without explicit authorization._

Potato Techniques:

**1. Hot Potato:**

Overview: Exploited a local NBNS (NetBIOS Name Service) spoofing vulnerability (patched in MS16-075 and MS16-077) to relay NTLM authentication and achieve SYSTEM privileges. The NetBIOS Name Service is responsible for resolving NetBIOS names to IP addresses on a local network. ocal NBNS spoofing could be used as a technique in attacks such as man-in-the-middle attacks, where an attacker intercepts and potentially modifies the communication between two parties. Understanding and securing against such vulnerabilities is crucial for maintaining the integrity and security of a local network. Security measures like encryption, secure network configurations, and monitoring for suspicious activities are important in protecting against potential threats.

Limitations: Not applicable to modern Windows versions. 

Mitigation: Apply security patches mentioned above and disable unnecessary services like NetBIOS.

**2. Rotten Potato:**

Overview: Abused RPC (Remote Procedure Call) communication and CoGetInstanceFromIStorage API to impersonate SYSTEM privileges.

Here's a brief overview of how RPC works:
Client sends a request: The client program sends a request for a particular procedure to the remote server.
Marshalling: The parameters of the procedure and other necessary information are packaged into a message (marshalled) so that they can be transmitted over the network. Network communication: The marshalled message is sent from the client to the server over the network. 
Unmarshalling: The server receives the message, unpacks the parameters (unmarshals), and executes the requested procedure.
Server sends a response: The server sends the result of the procedure back to the client.
Unmarshalling on the client side: The client receives the response, unpacks the result (unmarshals), and continues its execution.
RPC abstracts away the complexities of network communication, allowing developers to build distributed systems more easily. Examples of RPC frameworks include CORBA (Common Object Request Broker Architecture), gRPC (a modern, open-source RPC framework developed by Google), and Microsoft's DCOM (Distributed Component Object Model). Each of these provides a way for programs to communicate and invoke procedures across a network.

Limitations: Patch addressed in Windows 10 1809 and Windows Server 2019 onwards.

Mitigation: Update systems to supported versions and restrict DCOM communication.

**3. Lonely Potato:**

Overview: Similar to Rotten Potato, but without relying on meterpreter.

Meterpreter is a post-exploitation framework that is part of the Metasploit penetration testing framework. Metasploit is a widely used open-source tool for developing, testing, and executing exploits against remote targets. It provides a comprehensive environment for penetration testers, security researchers, and ethical hackers to assess and enhance the security of computer systems. Meterpreter is designed to be injected into a target system after a successful exploitation. Once injected, it provides a powerful command and control interface, allowing the attacker to interact with the compromised system. Meterpreter can be used to perform various post-exploitation activities, such as:
File system manipulation: Navigate through the file system, upload or download files, delete or execute files, etc.
Privilege escalation: Attempt to escalate privileges on the compromised system to gain higher access levels.
System reconnaissance: Gather information about the target system, including network configurations, running processes, user accounts, etc.
Network exploration: Perform network discovery and gather information about other systems on the network.
Keylogging and screenshot capture: Capture keystrokes and take screenshots of the user's desktop.
Pivoting: Use the compromised system as a pivot point to attack other systems within the same network.
Run additional payloads: Execute additional exploits or payloads on the compromised system..

Limitations: Deprecated and superseded by Juicy Potato.

Mitigation: Same as for Rotten Potato.

**4. Juicy Potato:**

Overview: Leveraged Background Intelligent Transfer Service (BITS) and COM servers to exploit the same vulnerability as Rotten Potato.
Background Intelligent Transfer Service (BITS) is a Windows service designed to facilitate seamless file transfers between computers on a network in a background, asynchronous manner. Its primary applications include supporting Windows Update, Windows Defender, and various Microsoft software, ensuring the efficient and inconspicuous downloading of updates without significant impact on system performance. BITS exhibits resilient transfer capabilities, enabling downloads to pause and resume seamlessly, even in the event of system restarts or temporary network disconnections. Additionally, it allows for bandwidth throttling, offering configuration options to limit network bandwidth usage, ensuring that other applications can function smoothly without disruption. On the other hand, Component Object Model (COM) Servers serve the purpose of providing a platform-independent, distributed, and object-oriented system for creating binary software components that can collaborate and communicate. By fostering an object-oriented approach, COM allows developers to encapsulate functionality within objects, exposing a well-defined interface. Its interoperability features facilitate seamless interaction among components written in different programming languages, promoting code reuse and modularity. Furthermore, COM supports distributed computing, enabling components to be located on different machines and communicate over a network, contributing to a flexible and scalable software architecture.

Limitations: Patch addressed in Windows 10 1809 and Windows Server 2019 onwards.

Mitigation: Same as for Rotten Potato.

**5. Rogue Potato:**

Overview: Targets the OXID resolution process in DCOM to achieve remote code execution with SYSTEM privileges.
In the Distributed Component Object Model (DCOM), the Object Exporter Identification (OXID) resolution process is a crucial mechanism for locating and identifying objects within a distributed system. When a client requests a remote object, the OXID resolution process comes into play. The client communicates with the Object Locator, which is responsible for resolving the requested OXID to the actual network location of the corresponding object. The process involves querying the OXID table to find the pertinent information about the object, such as its location and interfaces. This resolution allows DCOM to establish a connection to the remote object, ensuring that method invocations and communication can occur seamlessly across the distributed environment. The OXID resolution process is fundamental in facilitating the transparency and interoperability necessary for distributed computing in a COM-based architecture.

Limitations: Requires a controlled machine on port 135 and may not work against fully patched systems.

Mitigation: Keep systems updated, restrict inbound traffic on port 135, and monitor for suspicious activity.

**6. Sweet Potato:**

Overview: A collection of various potato techniques, including weaponized Juicy Potato, PrintSpoofer, and EfsRpc exploits.

Limitations: Each included technique has its own limitations and patches.

Mitigation: Apply necessary patches based on the specific techniques used.

**7. Generic Potato:**

Overview: A modified version of Sweet Potato supporting HTTP and named pipe impersonation for local privilege escalation. 
HTTP Impersonation and Named Pipe Impersonation are security mechanisms utilized in Windows environments for handling authentication and inter-process communication. HTTP impersonation, commonly employed in web applications, allows a server to temporarily adopt the security context of an authenticated client when processing HTTP requests. This ensures that actions performed by the server, such as accessing resources, are executed with the proper permissions based on the client's credentials. On the other hand, Named Pipe Impersonation is associated with inter-process communication, specifically using named pipes. It enables a server process to assume the security context of a client, facilitating secure actions on behalf of the client during communication. This is particularly relevant in scenarios involving Windows services or applications where a server needs to execute operations with the permissions of a connected client, maintaining the principle of least privilege. Both mechanisms contribute to the overall security of Windows systems by ensuring proper access control and user context management during communication and application execution.

Limitations: Requires specific conditions like SeImpersonatePrivilege and might be patched in newer versions.

Mitigation: Keep systems updated, restrict unnecessary privileges, and monitor for unauthorized access attempts.

**Conclusion:**

While potato techniques have played a role in privilege escalation attacks, most have been patched in recent Windows versions. Understanding these techniques can help security professionals stay informed and implement effective mitigation strategies. Remember, ethical practices and responsible disclosure are crucial when dealing with vulnerabilities.

**Additional Resources:**

Jorge Lajara: https://jlajara.gitlab.io/Potatoes_Windows_Privesc

SANS Institute: https://www.sans.org/webcasts/dive-into-windows-user-kernel-mode-exploit-mitigations/

Microsoft Security Response Center: https://www.microsoft.com/en-us/msrc

CERT Division: https://www.sei.cmu.edu/about/divisions/cert/
