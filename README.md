<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
<p>This tutorial guides you through installing <strong>osTicket</strong>, a popular open-source support ticket system, on an <strong>Azure Virtual Machine</strong> running <strong>Windows 10</strong>.</p>
<br />

<h2>Environments and Technologies Used</h2>

- <strong>Microsoft Azure</strong> - Cloud platform for deploying the virtual machine.
- <strong>Windows 10</strong> – Operating system for the VM.
- <strong>Internet Information Services (IIS)</strong> – Web server for hosting osTicket.
- <strong>PHP 7.3.8</strong> – Required for running osTicket.
- <strong>MySQL 5.5.62</strong> – Database management system for osTicket.
- <strong>HeidiSQL</strong> – Database administration tool.
<br />

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
<br />

<h2>List of Prerequisites</h2>

<p>Before starting this tutorial, ensure you have:</p>

- An <strong>Azure account</strong> to create the virtual machine.
- <strong>Remote Desktop Protocol (RDP)</strong> client to access the VM.
- A basic understanding of <strong>IIS, PHP, and MySQL</strong>.
<br />

<h2>Installation Steps</h2>

<h4>1. Create an Azure Virtual Machine</h4>
<ul>
    <li>Deploy a <strong>Windows 10 VM</strong> in <strong>Azure</strong> with <strong>4 vCPUs</strong>.</li>
    <li><strong>VM Name:</strong> <code>osticket-vm</code></li>
    <li><strong>Username:</strong> <code>labuser</code></li>
    <li><strong>Password:</strong> <code>osTicketPassword1!</code></li>
    <li>Connect to the VM using <strong>Remote Desktop (RDP)</strong>.</li>
</ul>

<h4>2. Prepare the VM</h4>
<ul>
    <li>Download and extract <a href="https://osticket.com/" target="_blank">osTicket Installation Files</a>. The extracted folder should be named <strong>osTicket-Installation-Files</strong>.</li>
</ul>

<h4>3. Install IIS and Required Modules</h4>
<ul>
    <li>Enable <strong>IIS (Internet Information Services)</strong> with <strong>CGI</strong>:</li>
    <ul>
        <li><strong>World Wide Web Services</strong> → <strong>Application Development Features</strong> → <strong>[X] CGI</strong></li>
    </ul>
    <li>Install required IIS modules from the <strong>osTicket-Installation-Files</strong> folder:</li>
    <ul>
        <li><a href="#">PHP Manager for IIS</a> (<code>PHPManagerForIIS_V1.5.0.msi</code>)</li>
        <li><a href="#">IIS Rewrite Module</a> (<code>rewrite_amd64_en-US.msi</code>)</li>
    </ul>
</ul>

<h4>4. Install PHP and MySQL</h4>
<ul>
    <li>Create directory: <code>C:\PHP</code></li>
    <li>Extract <strong>PHP 7.3.8</strong> into <code>C:\PHP</code>.</li>
    <li>Install:</li>
    <ul>
        <li><a href="#">VC Redist</a> (<code>VC_redist.x86.exe</code>)</li>
        <li><a href="#">MySQL 5.5.62</a> (<code>mysql-5.5.62-win32.msi</code>) with <strong>root/root</strong> credentials.</li>
    </ul>
</ul>

<h4>5. Configure IIS</h4>
<ul>
    <li>Open IIS as Administrator.</li>
    <li>Register <strong>PHP</strong> (<code>PHP Manager -> C:\PHP\php-cgi.exe</code>).</li>
    <li>Reload IIS (Stop & Start the server).</li>
</ul>

<h4>6. Install osTicket</h4>
<ul>
    <li>Extract <code>osTicket-v1.15.8.zip</code> and move the <strong>upload</strong> folder to <code>C:\inetpub\wwwroot</code>.</li>
    <li>Rename <strong>upload</strong> to <strong>osTicket</strong>.</li>
    <li>Reload IIS.</li>
    <li>Navigate to <strong>Sites → Default → osTicket</strong> and click <strong>Browse *:80</strong>.</li>
</ul>

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

<h4>8. Configure osTicket</h4>
<ul>
    <li>Rename <code>C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php</code> to <code>ost-config.php</code>.</li>
    <li>Adjust <strong>permissions</strong>:</li>
    <ul>
        <li><strong>Disable inheritance</strong> → <strong>Remove All</strong>.</li>
        <li><strong>New Permissions</strong> → <strong>Everyone → All</strong>.</li>
    </ul>
    <li>Continue <strong>osTicket setup</strong> in the browser:</li>
    <ul>
        <li><strong>Helpdesk Name</strong></li>
        <li><strong>Default email</strong></li>
    </ul>
</ul>

<h4>9. Configure Database</h4>
<ul>
    <li>Install <a href="#">HeidiSQL</a> from the <strong>osTicket-Installation-Files</strong> folder.</li>
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

<h4>10. Final Steps</h4>
<ul>
    <li>Access the <strong>Admin Panel</strong>: <a href="http://localhost/osTicket/scp/login.php">http://localhost/osTicket/scp/login.php</a></li>
    <li>User Portal: <a href="http://localhost/osTicket/">http://localhost/osTicket/</a></li>
    <li><strong>Clean up:</strong></li>
    <ul>
        <li>Delete <code>C:\inetpub\wwwroot\osTicket\setup</code>.</li>
        <li>Set <code>C:\inetpub\wwwroot\osTicket\include\ost-config.php</code> to <strong>Read-Only</strong>.</li>
    </ul>
</ul>

<p>🎉 <strong>Congratulations! osTicket is now installed and ready to use.</strong> 🎉</p>
