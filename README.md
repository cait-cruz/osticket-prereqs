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

![image](https://github.com/user-attachments/assets/72eaf117-9712-4071-86da-f21f50667b07)
<br />

![image](https://github.com/user-attachments/assets/8cd57077-e6c9-41a2-9dc1-30a9a08c0a25)
<br/>

![image](https://github.com/user-attachments/assets/5783ec64-9fcc-4748-b136-5669d7dbaca6)
<br />

<h4>2. Prepare the VM</h4>
<ul>
    <li>Download and extract <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD" target="_blank">osTicket Installation Files</a>. The extracted folder should be named <strong>osTicket-Installation-Files</strong>.</li>
</ul>

![image](https://github.com/user-attachments/assets/eb484fdf-b680-401b-a4ad-ce1eb6a31217)
<br />

![image](https://github.com/user-attachments/assets/9f5c39c2-4edf-4871-a5c6-773c75fc80f2)
<br />

<h4>3. Install IIS and Required Modules</h4>
<ul>
    <li>Enable <strong>IIS (Internet Information Services)</strong> with <strong>CGI</strong>:</li>
    <ul>
        <li><strong>World Wide Web Services</strong> → <strong>Application Development Features</strong> → <strong>[X] CGI</strong></li>
    </ul> 
    <li>Install required IIS modules from the <strong>osTicket-Installation-Files</strong> folder:</li>
    <ul>
        <li><strong>PHP Manager for IIS</strong> (<code>PHPManagerForIIS_V1.5.0.msi</code>)</li>
        <li><strong>IIS Rewrite Module</strong> (<code>rewrite_amd64_en-US.msi</code>)</li>
    </ul>
</ul>

![image](https://github.com/user-attachments/assets/2fb02bee-518e-46c7-897d-3dcb03a5e88f)
<br />

![image](https://github.com/user-attachments/assets/a2275804-82aa-4a15-8f75-6bccb05c7297)
<br />

![image](https://github.com/user-attachments/assets/c8601844-cc58-4549-944f-56abc70500f0)
<br />

![image](https://github.com/user-attachments/assets/30d466b2-0849-478c-b75d-12fc0ac46909)
<br />

<h4>4. Install PHP and MySQL</h4>
<ul>
    <li>Create directory: <code>C:\PHP</code></li>
    <li>From the <strong>osTicket-Installation-Files</strong> folder, extract <strong>PHP 7.3.8</strong> into <code>C:\PHP</code>.</li>
    <li>From the <strong>osTicket-Installation-Files</strong> folder, install:</li>
    <ul>
        <li><strong>VC Redist</strong> (<code>VC_redist.x86.exe</code>)</li>
        <li><strong>MySQL 5.5.62</strong> (<code>mysql-5.5.62-win32.msi</code>) with "Standard" configuration and <strong>Username:</strong> root, and <strong>Password:</strong> root.</li>
    </ul>
</ul>

![image](https://github.com/user-attachments/assets/b0e6bdeb-5ff5-4485-bd66-5ca1bd31e547)
<br />

![image](https://github.com/user-attachments/assets/2a5130f2-0cad-4ec8-909a-025a407a9a53)
<br />

![image](https://github.com/user-attachments/assets/230f5ba2-aacd-4ae5-aba9-a5aeb8284683)
<br />

![image](https://github.com/user-attachments/assets/169f2415-8e7b-4cb2-9691-25497529af7e)
<br />

![image](https://github.com/user-attachments/assets/9878ab68-7814-419b-9e32-22fa04e722a7)
<br />

<h4>5. Configure IIS</h4>
<ul>
    <li>Open IIS as Administrator.</li>
    <li>Register <strong>PHP</strong> (<code>PHP Manager -> C:\PHP\php-cgi.exe</code>).</li>
    <li>Reload IIS (Stop & Start the server).</li>
</ul>

![image](https://github.com/user-attachments/assets/e59d2e11-e30c-440f-a600-ffce3539dd5a)
<br />

![image](https://github.com/user-attachments/assets/07d8e02f-6c86-49dc-9364-43e39fc4955e)
<br />

![image](https://github.com/user-attachments/assets/d27539c6-2963-46d1-8c3e-f2e47a2c72e0)
<br />

![image](https://github.com/user-attachments/assets/41cc3874-71b4-477a-b855-bf978c676cc4)
<br />

![image](https://github.com/user-attachments/assets/8dd0dcd0-adc7-4061-9ec6-b734e2c4e92a)
<br />

<h4>6. Install osTicket</h4>
<ul>
    <li>Extract <code>osTicket-v1.15.8.zip</code> and move the <strong>upload</strong> folder to <code>C:\inetpub\wwwroot</code>.</li>
    <li>Rename <strong>upload</strong> to <strong>osTicket</strong>.</li>
    <li>Reload IIS.</li>
    <li>Navigate to <strong>Sites → Default → osTicket</strong> and click <strong>Browse *:80</strong>. Notice that some extensions are not enabled.</li>
</ul>

![image](https://github.com/user-attachments/assets/6bec7392-a35b-4279-9875-be61c32eec50)
<br />

![image](https://github.com/user-attachments/assets/f1730c89-1f38-4c24-86e7-2a586f6c4475)
<br />

![image](https://github.com/user-attachments/assets/bb9cfe26-91bb-4856-8d42-8eac033e0dc9)
<br />

![image](https://github.com/user-attachments/assets/7bc58436-77a4-42d5-8fd3-21b55b6f83eb)
<br />

![image](https://github.com/user-attachments/assets/9c2cdbee-0ad7-4b39-a46e-efc509e07d04)
<br />

![image](https://github.com/user-attachments/assets/1806edf2-bcd2-44f4-9c10-de8b1836a464)
<br />

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

![image](https://github.com/user-attachments/assets/fa9ff071-a704-4ea7-8fbe-acaf834b4b4c)
<br />

![image](https://github.com/user-attachments/assets/3d651d26-58ae-46ea-a357-5e8b613dee70)
<br />

![image](https://github.com/user-attachments/assets/bb60423d-29a3-4d56-a9fc-449be127c67a)
<br />

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

![image](https://github.com/user-attachments/assets/8e03c193-49bf-481e-9065-f116653586b0)
<br />

![image](https://github.com/user-attachments/assets/c2859560-dd9f-436e-a7d8-2eab31dfa988)
<br />

![image](https://github.com/user-attachments/assets/f488a6ef-6db8-4fd3-963d-60e75ddb5a36)
<br />

![image](https://github.com/user-attachments/assets/d626dd3e-b43b-4fdc-a070-237b32068fba)
<br />

![image](https://github.com/user-attachments/assets/0109e49e-30fd-4549-91f3-affe34653127)
<br />

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

![image](https://github.com/user-attachments/assets/b56be149-c40c-4fd2-9c04-76ffde7b9044)
<br />

![image](https://github.com/user-attachments/assets/bb30ff48-d73e-4516-a9c5-86c788e6f1f3)
<br />

![image](https://github.com/user-attachments/assets/b076a59c-f1aa-4ee8-b69f-8f05de145618)
<br />

![image](https://github.com/user-attachments/assets/50754952-abcd-4aed-8248-f8edad9cf6b7)
<br />

![image](https://github.com/user-attachments/assets/65705e9b-4e2d-46c8-9d77-b6099beb569a)
<br />

![image](https://github.com/user-attachments/assets/3e412a22-c66f-4767-afa7-fccfe73ab71c)
<br />

<h4>10. Final Steps</h4>
<ul>
    <li>Access the <strong>Admin Panel</strong>: <a href="http://localhost/osTicket/scp/login.php">http://localhost/osTicket/scp/login.php</a></li>
    <li>User Portal: <a href="http://localhost/osTicket/">http://localhost/osTicket/</a></li>
</ul>
<hr>

<h3>🎉 Congratulations! osTicket is now installed and ready to use. 🎉</h3>
