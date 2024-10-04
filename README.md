<p align="center">
  <img src="https://github.com/user-attachments/assets/a9e62984-6877-41d3-b24c-25d0460b9005" alt="Microsoft Azure Banner">
</p>

<h1>Network Security Groups (NSGs) and Inspecting Network Protocols</h1>

<p>This lab demonstrates how to create virtual machines, inspect network traffic using WireShark, and configure Network Security Groups (NSGs) on Microsoft Azure.</p>

<h2>Part 1: Creating Virtual Machines</h2>

1. Go to the <a href="https://portal.azure.com/">Azure Portal</a>.
2. Create a Resource Group.
3. Create a Windows 10 VM:
    - Select the Resource Group you created.
    - Let Azure create a new Virtual Network (VNet) and Subnet.
4. Create a Linux (Ubuntu) VM:
    - Select the same Resource Group and VNet as the Windows 10 VM.
    - Authentication: Username/Password.
5. Ensure both VMs are in the same VNet and Subnet.

<p align="center">
  <!-- Add Image Example -->
  <img src="https://github.com/user-attachments/assets/your-image-link.png" alt="Creating Virtual Machines" width="80%">
</p>

<h2>Part 2: Observing ICMP Traffic</h2>

1. Install Microsoft Remote Desktop (Mac users).
2. Connect to your Windows 10 VM using Remote Desktop.
3. Install WireShark on your Windows 10 VM.
4. Start a packet capture in WireShark and filter for ICMP traffic.
5. Ping your Ubuntu VM from the Windows 10 VM using its private IP.
6. Observe the ICMP traffic in WireShark.
7. Ping a public website (e.g., google.com) and observe the traffic.

<p align="center">
  <!-- Add Image Example -->
  <img src="https://github.com/user-attachments/assets/your-image-link.png" alt="Observing ICMP Traffic" width="80%">
</p>

<h2>Part 3: Configuring Network Security Groups (NSGs)</h2>

1. Start a continuous ping from your Windows 10 VM to your Ubuntu VM.
2. In Azure, disable inbound ICMP traffic in the NSG for the Ubuntu VM.
3. Observe the ICMP traffic and ping activity in WireShark.
4. Re-enable ICMP traffic in the NSG and observe the restored traffic.
5. Stop the ping activity.

<h2>Part 4: Observing Protocol Traffic</h2>

- **SSH Traffic:** 
  - Capture SSH traffic in WireShark.
  - SSH from the Windows 10 VM to the Ubuntu VM using its private IP.
  - Observe the traffic in WireShark as you interact with the SSH session.
  
- **DHCP Traffic:** 
  - Filter for DHCP traffic in WireShark.
  - Run `ipconfig /renew` in the Windows 10 VM and observe the traffic.

- **DNS Traffic:** 
  - Filter for DNS traffic in WireShark.
  - Use `nslookup` to query DNS for google.com and disney.com.

- **RDP Traffic:** 
  - Filter for RDP traffic in WireShark.
  - Observe continuous traffic due to the live RDP session.

<h2>Conclusion</h2>

<p>By completing this lab, you've learned how to create VMs, inspect network traffic, and manage NSGs using Azure. You've also explored key network protocols such as ICMP, SSH, DHCP, DNS, and RDP using WireShark.</p>

<p align="center">
  <!-- Add Conclusion Image -->
  <img src="https://github.com/user-attachments/assets/your-image-link.png" alt="Conclusion Image" width="80%">
</p>
