<p align="center">
  <img src="https://github.com/user-attachments/assets/a9e62984-6877-41d3-b24c-25d0460b9005" alt="Microsoft Azure Banner">
</p>

<h1>Network File Shares and Permissions Lab</h1>

<p>In this lab, I demonstrated how to set up and manage network file shares and configure different permissions for users in an Active Directory environment using Azure Virtual Machines. This lab allowed me to practice controlling access to resources based on group membership and verifying those permissions across multiple machines.</p>

<h2>Part 1: Creating File Shares and Configuring Permissions</h2>

<p><strong>Step 1: Connect to the Virtual Machines</strong></p>
<ul>
  <li>I turned on both <strong>DC-1</strong> and <strong>Client-1</strong> in the Azure Portal to ensure they were online.</li>
  <li>I connected to <strong>DC-1</strong> using my domain admin account: <strong>mydomain.com\pablo_davis</strong>.</li>
  <li>I connected to <strong>Client-1</strong> as a normal domain user (bam.wed) <strong>mydomain\<someuser></strong>.</li>
</ul>

<p><strong>Step 2: Create File Shares on DC-1</strong></p>
<ul>
  <li>On <strong>DC-1</strong>, I navigated to the C:\ drive and created 4 folders named: <strong>read-access</strong>, <strong>write-access</strong>, <strong>no-access</strong>, and <strong>accounting</strong>.</li>
  <li>Next, I configured the following permissions for each folder:</li>
  <ul>
    <li><strong>read-access:</strong> Group: <strong>Domain Users</strong>, Permission: <strong>Read</strong></li>
    <li><strong>write-access:</strong> Group: <strong>Domain Users</strong>, Permission: <strong>Read/Write</strong></li>
    <li><strong>no-access:</strong> Group: <strong>Domain Admins</strong>, Permission: <strong>Read/Write</strong></li>
    <li>I skipped setting up permissions for the <strong>accounting</strong> folder for now.</li>
  </ul>
</ul>

<p align="center">
  <img src="IMAGE_URL_HERE" alt="File Shares Configuration" width="80%">
</p>

<h2>Part 2: Testing File Share Access as a Normal User</h2>

<p><strong>Step 3: Attempt to Access File Shares from Client-1</strong></p>
<ul>
  <li>On <strong>Client-1</strong>, I navigated to the shared folder by typing <strong>\\dc-1</strong> in the run prompt.</li>
  <li>I tried accessing each of the folders I created:</li>
  <ul>
    <li>I was able to access the <strong>read-access</strong> folder but only had read permissions.</li>
    <li>I could both read and write in the <strong>write-access</strong> folder.</li>
    <li>I could not access the <strong>no-access</strong> folder because it was restricted to domain admins only.</li>
  </ul>
</ul>

<p align="center">
  <img src="IMAGE_URL_HERE" alt="Testing File Shares Access" width="80%">
</p>

<h2>Part 3: Creating a Security Group and Testing Folder Access</h2>

<p><strong>Step 4: Set Up the ACCOUNTANTS Security Group</strong></p>
<ul>
  <li>Back on <strong>DC-1</strong>, I opened Active Directory Users and Computers and created a security group called <strong>ACCOUNTANTS</strong>.</li>
  <li>I went back to the <strong>accounting</strong> folder on DC-1 and set the following permissions:</li>
  <ul>
    <li><strong>Group:</strong> <strong>ACCOUNTANTS</strong>, <strong>Permission:</strong> <strong>Read/Write</strong></li>
  </ul>
</ul>

<p align="center">
  <img src="IMAGE_URL_HERE" alt="Creating ACCOUNTANTS Security Group" width="80%">
</p>

<p><strong>Step 5: Test Access to the Accounting Folder as a Normal User</strong></p>
<ul>
  <li>On <strong>Client-1</strong>, I tried to access the <strong>accounting</strong> folder as a normal user (<strong>mydomain\<someuser></strong>), but access was denied as expected.</li>
</ul>

<p align="center">
  <img src="IMAGE_URL_HERE" alt="Testing Access Denied to Accounting Folder" width="80%">
</p>

<h2>Part 4: Granting Access to the ACCOUNTANTS Group</h2>

<p><strong>Step 6: Add the User to the ACCOUNTANTS Group</strong></p>
<ul>
  <li>I logged out of <strong>Client-1</strong> as <strong><someuser></strong>.</li>
  <li>Back on <strong>DC-1</strong>, I made <strong><someuser></strong> a member of the <strong>ACCOUNTANTS</strong> group.</li>
  <li>I logged back into <strong>Client-1</strong> as <strong><someuser></strong>.</li>
</ul>

<p><strong>Step 7: Test Access to the Accounting Folder Again</strong></p>
<ul>
  <li>After signing back into <strong>Client-1</strong>, I tried accessing the <strong>accounting</strong> share again at <strong>\\DC-1</strong> and verified that I now had <strong>Read/Write</strong> access to the folder as expected.</li>
</ul>

<p align="center">
  <img src="IMAGE_URL_HERE" alt="Testing Access to Accounting Folder After Group Addition" width="80%">
</p>

<h2>Conclusion</h2>

<p>By completing this lab, I gained experience in setting up file shares and managing permissions based on group membership in an Active Directory environment. This exercise reinforced the importance of using security groups to control access to sensitive resources and demonstrated how folder permissions can be applied to specific users and groups within a domain.</p>
