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

![image](https://github.com/user-attachments/assets/a80a6a89-80b5-4309-80b9-3a15c9154224)

![image](https://github.com/user-attachments/assets/8689fda8-0c0c-4d18-81be-9f86be28490a)

<h4>3. Install IIS and Required Modules</h4>
<ul>
    <li>Enable <strong>IIS (Internet Information Services)</strong> with <strong>CGI</strong>:</li>
    <ul>
        <li><strong>World Wide Web Services</strong> → <strong>Application Development Features</strong> → <strong>[X] CGI</strong></li>
<br />
        
![image](https://github.com/user-attachments/assets/b926d937-2485-4c16-b00e-7663ec3b55f9)   
    </ul> 
    <li>Install required IIS modules from the <strong>osTicket-Installation-Files</strong> folder:</li>
    <ul>
        <li><strong>PHP Manager for IIS</strong> (<code>PHPManagerForIIS_V1.5.0.msi</code>)</li>
        <li><strong>IIS Rewrite Module</strong> (<code>rewrite_amd64_en-US.msi</code>)</li>
    </ul>
</ul>

![image](https://github.com/user-attachments/assets/78ff2b0a-1188-42a7-a13e-8caeab9fde96)

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

![image](https://github.com/user-attachments/assets/b27f7dce-2c9f-4e65-8a27-270d8001b96f)

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

![image](https://github.com/user-attachments/assets/1db5fa2e-705b-4fbd-9875-8245496c4174)

![image](https://github.com/user-attachments/assets/4c96f4ef-7468-4c50-ad40-3a805e54b56c)

![image](https://github.com/user-attachments/assets/6d12df4f-27c1-43a7-b7c5-3dc9263a1018)


<h4>6. Install osTicket</h4>
<ul>
    <li>Extract <code>osTicket-v1.15.8.zip</code> and move the <strong>upload</strong> folder to <code>C:\inetpub\wwwroot</code>.</li>
    <li>Rename <strong>upload</strong> to <strong>osTicket</strong>.</li>
</ul>

![image](https://github.com/user-attachments/assets/0847e51e-ed3c-48fe-aa07-16982bee782f)

![image](https://github.com/user-attachments/assets/77bed335-8217-4ebf-8b46-9652f3883feb)

![image](https://github.com/user-attachments/assets/602a2b63-e8f0-4af1-8ea5-031ddf1744ab)

![image](https://github.com/user-attachments/assets/6a23c269-b7bf-4205-a3d7-f29631b69b08)

![image](https://github.com/user-attachments/assets/a7ffd109-478b-478b-a2c8-1860e35b9f2d)

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

![image](https://github.com/user-attachments/assets/33aba18d-4a2e-4d3e-a55f-a2162a2a9479)

![image](https://github.com/user-attachments/assets/761c8ff3-2304-46ac-a819-0776f333437e)

<h4>8. Configure osTicket</h4>
<ul>
    <li>Rename <code>C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php</code> to <code>ost-config.php</code>.</li>
    <li>Adjust <strong>permissions</strong>:</li>
    <ul>
        <li><strong>Disable inheritance</strong> → <strong>Remove All</strong>.</li>
        <li><strong>New Permissions</strong> → <strong>Everyone → All</strong>.</li>
        <li>Enable <strong>Full Control.</strong></li>
    </ul>
<br />
    
![image](https://github.com/user-attachments/assets/f7717dc8-7f29-4aaa-b019-9885be0c5a58)

![image](https://github.com/user-attachments/assets/0a4a4755-b1f8-430d-9fcc-29c35695ba9e)

![image](https://github.com/user-attachments/assets/ec61adb5-6c62-42ba-962e-ce93b839d13c)

![image](https://github.com/user-attachments/assets/b85cb4aa-d038-42bd-ab84-ab2a1913556f)

![image](https://github.com/user-attachments/assets/0e7da184-d9d9-453f-b9fd-a34b4df81b64)

![image](https://github.com/user-attachments/assets/250628c3-4df4-416f-8c23-412f970adb7b)

![image](https://github.com/user-attachments/assets/2f240fd8-038b-469e-a996-36556fa30fd0)

![image](https://github.com/user-attachments/assets/3e862079-87e1-4d9c-906e-68aa64c89e91)

<h4>9. Configure Database</h4>
<ul>
    <li>Install <strong>HeidiSQL</strong> from the <strong>osTicket-Installation-Files</strong> folder.</li>
    <li>Open <strong>HeidiSQL</strong> → Create a new session (<code>root/root</code>).</li>
    <li>Create a database named <strong>osTicket</strong>.</li>
</ul>
<br />

![image](https://github.com/user-attachments/assets/bc5e828a-86b6-4e3a-b2d2-cf855b8eb8f1)

![image](https://github.com/user-attachments/assets/6e59e53e-6ce9-4e24-a934-c6487536018e)

![image](https://github.com/user-attachments/assets/d316e745-4fc3-4dcb-b483-970f64b61f90)

![image](https://github.com/user-attachments/assets/a449ed44-9289-48c5-b863-09c72e5bd321)

![image](https://github.com/user-attachments/assets/ebe5051e-9b92-4acd-b70a-1f3ccf9bc3cf)

<h4>10. Final Steps</h4>
<li>Continue <strong><a href="http://localhost/osTicket/scp/login.php">osTicket setup</a></strong> in the browser:</li>
    <ul>
        <li>Helpdesk Name</li>
        <li>Default email</li>
        <li>Admin User</li>
    </ul>

![image](https://github.com/user-attachments/assets/bdec70f5-685a-41f0-b08e-444c89723093)

<li>Finalize <strong>osTicket installation</strong> in the browser:</li>
    <ul>
        <li><strong>MySQL Database:</strong> <code>osTicket</code></li>
        <li><strong>MySQL Username:</strong> <code>root</code></li>
        <li><strong>MySQL Password:</strong> <code>root</code></li>
        <li>Click <strong>Install Now!</strong></li>
    </ul>

![image](https://github.com/user-attachments/assets/ddfda481-a6f4-4380-8d27-7b28f02f41e5)

<br />    
<p>Access the <strong>Admin Panel</strong>: <a href="http://localhost/osTicket/scp/login.php">http://localhost/osTicket/scp/login.php</a></p>
<p>User Portal: <a href="http://localhost/osTicket/">http://localhost/osTicket/</a></p>

<hr>

<h3>🎉 Congratulations! osTicket is now installed and ready to use. 🎉</h3>
