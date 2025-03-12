<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
<p>This tutorial guides you through installing <strong>osTicket</strong>, a popular open-source support ticket system, on an <strong>Azure Virtual Machine</strong> running <strong>Windows 10</strong>.</p>

<h2>Environments and Technologies Used</h2>

- <strong>Microsoft Azure</strong> - Cloud platform for deploying the virtual machine.
- <strong>Windows 10</strong> – Operating system for the VM.
- <strong>Internet Information Services (IIS)</strong> – Web server for hosting osTicket.
- <strong>PHP 7.3.8</strong> – Required for running osTicket.
- <strong>MySQL 5.5.62</strong> – Database management system for osTicket.
- <strong>HeidiSQL</strong> – Database administration tool.

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

<p>Before starting this tutorial, ensure you have:</p>

- An <strong>Azure account</strong> to create the virtual machine.
- <strong>Remote Desktop Protocol (RDP)</strong> client to access the VM.
- A basic understanding of <strong>IIS, PHP, and MySQL</strong>.

<h2>Installation Steps</h2>

<h4>1. Create an Azure Virtual Machine</h4>
<ul>
    <li>Deploy a <strong>Windows 10 VM</strong> in <strong>Azure</strong> with <strong>4 vCPUs</strong>.</li>
    <li><strong>VM Name:</strong> <code>osticket-vm</code></li>
    <li><strong>Username:</strong> <code>labuser</code></li>
    <li><strong>Password:</strong> <code>osTicketPassword1!</code></li>
    <li>Connect to the VM using <strong>Remote Desktop (RDP)</strong>.</li>
</ul>

![Screenshot 2025-03-11 161749](https://github.com/user-attachments/assets/6a7ded3f-1730-45a4-8a7e-6abd1ef38f47)

![Screenshot 2025-03-11 161830](https://github.com/user-attachments/assets/8f37aad8-bc0d-44e9-a828-526188b3aa64)

![Screenshot 2025-03-11 161853](https://github.com/user-attachments/assets/5b95bcb6-cd49-47c0-bb3e-a335f153d501)

<h4>2. Prepare the VM</h4>
<ul>
    <li>Download and extract <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD" target="_blank">osTicket Installation Files</a>. The extracted folder should be named <strong>osTicket-Installation-Files</strong>.</li>
</ul>

![image](https://github.com/user-attachments/assets/8439fb71-6d84-4f8b-82e4-5c371d5e6ea5)

![image](https://github.com/user-attachments/assets/8b04ee27-0ce6-4720-83c3-ae32b5bd5074)

<h4>3. Install IIS and Required Modules</h4>
<ul>
    <li>Enable <strong>IIS (Internet Information Services)</strong> with <strong>CGI</strong>:</li>
    <ul>
        <li><strong>World Wide Web Services</strong> → <strong>Application Development Features</strong> → <strong>[X] CGI</strong></li>

![421612319-931ca6f6-27cc-4044-80d0-e839b6ac023a](https://github.com/user-attachments/assets/6550950a-491e-4618-9fe7-f099bd14b063)   
    </ul> 
    <li>Install required IIS modules from the <strong>osTicket-Installation-Files</strong> folder:</li>
    <ul>
        <li><strong>PHP Manager for IIS</strong> (<code>PHPManagerForIIS_V1.5.0.msi</code>)</li>
        <li><strong>IIS Rewrite Module</strong> (<code>rewrite_amd64_en-US.msi</code>)</li>
    </ul>
</ul>

![image](https://github.com/user-attachments/assets/e39acf21-043c-4684-8044-4f3b28cdb543)

![image](https://github.com/user-attachments/assets/d732f709-f6d1-4813-b5c4-9c8b4668a628)

<h4>4. Install PHP and MySQL</h4>
<ul>
    <li>Create directory: <code>C:\PHP</code></li>
    <li>From the <strong>osTicket-Installation-Files</strong> folder, extract <strong>PHP 7.3.8</strong> into <code>C:\PHP</code>.</li>
    <li>From the <strong>osTicket-Installation-Files</strong> folder, install:</li>
    <ul>
        <li><strong>VC Redist</strong> (<code>VC_redist.x86.exe</code>)</li>
        <li><strong>MySQL 5.5.62</strong> (<code>mysql-5.5.62-win32.msi</code>) with "Standard" configuration and <strong>Password:</strong> root.</li>
    </ul>
</ul>

![image](https://github.com/user-attachments/assets/eb97123f-3138-4f36-97c3-ed5d96bac41f)

![Annotation 2025-03-12 002147](https://github.com/user-attachments/assets/035b3d74-a263-467b-8218-ad5d6ccd6042)

![Annotation 2025-03-12 002346](https://github.com/user-attachments/assets/136c7147-0cea-4607-bec8-0d5da3dbcf31)

![image](https://github.com/user-attachments/assets/ae630e8a-e04c-4464-b897-e59d4db4288f)

![image](https://github.com/user-attachments/assets/f952c719-4ca1-4987-af28-b3d2be6098ab)

<h4>5. Configure IIS</h4>
<ul>
    <li>Open IIS as Administrator.</li>
    <li>Register <strong>PHP</strong> (<code>PHP Manager -> C:\PHP\php-cgi.exe</code>).</li>
    <li>Reload IIS (Stop & Start the server).</li>
</ul>

![image](https://github.com/user-attachments/assets/ea909478-a2de-4f3a-9691-f6db4a47da33)

![image](https://github.com/user-attachments/assets/83a022b5-1f33-4897-8330-7b64499816dc)

![image](https://github.com/user-attachments/assets/719a3f55-6d80-47d1-b889-02d54e60a718)

![image](https://github.com/user-attachments/assets/b1967e41-7966-4403-bfd2-51f24bd62228)

![image](https://github.com/user-attachments/assets/ae8497ae-e1db-4850-9183-e498bca94f8e)

<h4>6. Install osTicket</h4>
<ul>
    <li>Extract <code>osTicket-v1.15.8.zip</code> and move the <strong>upload</strong> folder to <code>C:\inetpub\wwwroot</code>.</li>
    <li>Rename <strong>upload</strong> to <strong>osTicket</strong>.</li>
    <li>Reload IIS.</li>
    <li>Navigate to <strong>Sites → Default → osTicket</strong> and click <strong>Browse *:80</strong>. Notice that some extensions are not enabled.</li>
</ul>

![image](https://github.com/user-attachments/assets/a35333e7-d456-4a04-aa2c-e98293076fbc)

![image](https://github.com/user-attachments/assets/fd785f6a-456c-4b70-8dc8-691349c6b95c)

![image](https://github.com/user-attachments/assets/e3f37272-7abb-4aec-9d26-f2013e209562)

![image](https://github.com/user-attachments/assets/edfaa3d2-32b7-4016-876a-833f262644be)

![image](https://github.com/user-attachments/assets/35f02e12-7446-4771-a4aa-218b3b950ddc)

![image](https://github.com/user-attachments/assets/d826cfd3-4024-40fa-8cd9-01794d969fa8)

<h4>7. Enable PHP Extensions</h4>
<ul>
    <li>In IIS, navigate to <strong>osTicket → PHP Manager</strong> → <strong>Enable or disable an extension</strong>.</li>
    <li>Enable:</li>
    <ul>
        <li><code>php_imap.dll</code></li>
        <li><code>php_intl.dll</code></li>
        <li><code>php_opcache.dll</code></li>
    </ul>
    <li>Refresh the osTicket site.</li>
</ul>

![image](https://github.com/user-attachments/assets/76dc683b-a4f3-4550-b5c4-28ec986f1bad)

![image](https://github.com/user-attachments/assets/d619da65-3184-4c68-8d26-5e054e530477)

![image](https://github.com/user-attachments/assets/3f8b2d80-722c-4e19-92d6-e7e5e2003b19)

<h4>8. Configure osTicket</h4>
<ul>
    <li>Rename <code>C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php</code> to <code>ost-config.php</code>.</li>
    <li>Adjust <strong>permissions</strong>:</li>
    <ul>
        <li><strong>Disable inheritance</strong> → <strong>Remove All</strong>.</li>
        <li><strong>New Permissions</strong> → <strong>Everyone → All</strong>.</li>
        <li>Enable <strong>Full Control.</strong></li>
    </ul>
    <li>Continue <strong>osTicket setup</strong> in the browser:</li>
    <ul>
        <li>Helpdesk Name</li>
        <li>Default email</li>
        <li>Admin User</li>
    </ul>
</ul>

![image](https://github.com/user-attachments/assets/d73c753a-6816-44fa-9198-f28ce5c25c02)

![image](https://github.com/user-attachments/assets/7a8bf157-c239-464b-b2ff-f726ce83c583)

![image](https://github.com/user-attachments/assets/3369a7a5-858e-45d3-adbb-791296307900)

![image](https://github.com/user-attachments/assets/723f5ded-b04f-4cd0-8e7b-10c18bea1106)

![image](https://github.com/user-attachments/assets/0758b945-7657-4109-983f-09e83aca8dd6)

<h4>9. Configure Database</h4>
<ul>
    <li>Install <strong>HeidiSQL</strong> from the <strong>osTicket-Installation-Files</strong> folder.</li>
    <li>Open <strong>HeidiSQL</strong> → Create a new session (<code>root/root</code>).</li>
    <li>Create a database named <strong>osTicket</strong>.</li>
    <li>Finalize <strong>osTicket installation</strong> in the browser:</li>
    <ul>
        <li><strong>MySQL Database:</strong> <code>osTicket</code></li>
        <li><strong>MySQL Username:</strong> <code>root</code></li>
        <li><strong>MySQL Password:</strong> <code>root</code></li>
        <li>Click <strong>Install Now!</strong></li>
    </ul>
</ul>

![image](https://github.com/user-attachments/assets/445dfe8b-e5eb-44fc-8087-8752386ba174)

![image](https://github.com/user-attachments/assets/a0ba7fa2-ef13-4895-8377-8af94bc0899e)

![image](https://github.com/user-attachments/assets/2c1c2b1b-0f1c-48b4-b482-717f88a2278c)

![image](https://github.com/user-attachments/assets/04c4ec51-3b34-4ff9-92c6-f9c3b646fddf)

![image](https://github.com/user-attachments/assets/d2c8c472-87d0-47a0-abd0-515133fd7e13)

![image](https://github.com/user-attachments/assets/994cc398-5df4-4edd-b09d-40f7778ce97a)

<h4>10. Final Steps</h4>
<ul>
    <li>Access the <strong>Admin Panel</strong>: <a href="http://localhost/osTicket/scp/login.php">http://localhost/osTicket/scp/login.php</a></li>
    <li>User Portal: <a href="http://localhost/osTicket/">http://localhost/osTicket/</a></li>
</ul>
<hr>

<h3>🎉 Congratulations! osTicket is now installed and ready to use. 🎉</h3>
