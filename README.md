# Windows-Potatoes


This document is for **educational purposes** only and is not intended to promote or facilitate malicious activity. _**By accessing this information, you acknowledge and agree that you are solely responsible for your actions and any potential consequences.**_

**Introduction:**

Privilege escalation vulnerabilities in Windows systems can pose significant security risks. Understanding and mitigating these vulnerabilities is crucial for system administrators and security professionals. This document explores various "potato" techniques used for Windows privilege escalation, providing an overview of their mechanics, limitations, and mitigation strategies.

_**Important Note:**_

_While exploring these techniques, it is essential to follow responsible disclosure practices and adhere to ethical guidelines. Avoid exploiting vulnerabilities in production environments without explicit authorization._

Potato Techniques:

**1. Hot Potato (Deprecated):**

Overview: Exploited a local NBNS spoofing vulnerability (patched in MS16-075 and MS16-077) to relay NTLM authentication and achieve SYSTEM privileges.
Limitations: Not applicable to modern Windows versions.
Mitigation: Apply security patches mentioned above and disable unnecessary services like NetBIOS.

**2. Rotten Potato (Deprecated):**

Overview: Abused RPC communication and CoGetInstanceFromIStorage API to impersonate SYSTEM privileges.
Limitations: Patch addressed in Windows 10 1809 and Windows Server 2019 onwards.
Mitigation: Update systems to supported versions and restrict DCOM communication.

**3. Lonely Potato (Deprecated):**

Overview: Similar to Rotten Potato, but without relying on meterpreter.
Limitations: Deprecated and superseded by Juicy Potato.
Mitigation: Same as for Rotten Potato.

**4. Juicy Potato (Deprecated):**

Overview: Leveraged Background Intelligent Transfer Service (BITS) and COM servers to exploit the same vulnerability as Rotten Potato.
Limitations: Patch addressed in Windows 10 1809 and Windows Server 2019 onwards.
Mitigation: Same as for Rotten Potato.

**5. Rogue Potato:**

Overview: Targets the OXID resolution process in DCOM to achieve remote code execution with SYSTEM privileges.
Limitations: Requires a controlled machine on port 135 and may not work against fully patched systems.
Mitigation: Keep systems updated, restrict inbound traffic on port 135, and monitor for suspicious activity.

**6. Sweet Potato:**

Overview: A collection of various potato techniques, including weaponized Juicy Potato, PrintSpoofer, and EfsRpc exploits.
Limitations: Each included technique has its own limitations and patches.
Mitigation: Apply necessary patches based on the specific techniques used.

**7. Generic Potato:**

Overview: A modified version of Sweet Potato supporting HTTP and named pipe impersonation for local privilege escalation.
Limitations: Requires specific conditions like SeImpersonatePrivilege and might be patched in newer versions.
Mitigation: Keep systems updated, restrict unnecessary privileges, and monitor for unauthorized access attempts.

**Conclusion:**

While potato techniques have played a role in privilege escalation attacks, most have been patched in recent Windows versions. Understanding these techniques can help security professionals stay informed and implement effective mitigation strategies. Remember, ethical practices and responsible disclosure are crucial when dealing with vulnerabilities.

**Additional Resources:**

Jorge Lajara: https://jlajara.gitlab.io/Potatoes_Windows_Privesc

SANS Institute: https://www.sans.org/webcasts/dive-into-windows-user-kernel-mode-exploit-mitigations/

Microsoft Security Response Center: https://www.microsoft.com/en-us/msrc

CERT Division: https://www.sei.cmu.edu/about/divisions/cert/
