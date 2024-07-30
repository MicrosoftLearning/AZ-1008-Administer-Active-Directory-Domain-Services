---
lab:
    title: 'Exercise – Configure Domain Controller Operations'
    module: 'Guided Project – Administer Active Directory Domain Services'
---
In this exercise, you promote a server to domain controller, transfer a FSMO role to the new domain controller, create a site, and add a subnet to the site.

## Install Active Directory Domain Services (AD DS) and promote to Domain Controller

In this task, you promote member server TAILWIND-MBR1 to become a domain controller in the TAILWINDTRADERS domain. To complete this task, perform the following steps:

1.  Sign in to TAILWIND-MBR1 as TAILWINDTRADERS\\Administrator with the password: `Pa55w.rdPa55w.rd`.
2.  In Server Manager, select the Manage menu and then select **Add Roles and Features**.
3.  On the Before you begin page of the Add Roles and Features wizard, click **Next**.
4.  On the Select installation type page, select **Role-based or feature-based installation** and click **Next**.
5.  On the Select destination server page, choose **Select a server from the server pool**, ensure TAILWIND-MBR1 is selected and click **Next**.
6.  On the Select server roles page, select the **Active Directory Domain Services** checkbox. This opens the Add features page. Select **Add Features**. Click **Next**.
7.  On the Select features page, click **Next**.
8.  On the Active Directory Domain Services page, click **Next**.
9.  On the Confirm installation selections page, click **Install**. Depending on the speed of the computer, installation may take several minutes. When the installation completes, click **Close**.
10. On the Server manager menu, select the notification icon next to the flag in the top right corner (as shown in the screenshot).

    ![Screenshot of the server manager menu with the alert icon displayed.](./Media/server-manager-menu.png)
13. On the menu that opens when you select the notification icon, select **Promote this server to a domain controller**. This will start the Active Directory Domain Services Configuration Wizard.
14. On the Deployment Configuration page, select **Add a domain controller to an existing domain** and ensure that the domain name is set to **tailwindtraders.internal**.
15. You must re-authenticate the administrator account. Select **Change**. Enter `Administrator` for the user name and `Pa55w.rdPa55w.rd` for the password. Click **OK**. Click **Next**.
16. On the Domain Controller options page, accept the default settings and provide the Directory Services Restore Mode (DSRM) password. To do this, enter the following password twice: `Pa55w.rdPa55w.rd`. Click **Next**.
17. On the DNS Options page, click **Next**.
18. On the Additional Options page, click **Next**.
19. On the Paths page, click **Next**.
20. On the Review Options page, click **Next**.
21. On the Prerequisites Check page, click **Install**. The installation will take several minutes depending on the speed of the virtual machine. The virtual machine will restart.
22. When the virtual machine restarts, sign in as `tailwindtraders\administrator` with the password you configured for the default administrator account (`Pa55w.rdPa55w.rd`)

## Transfer Flexible Single Master Operations Roles

In this task, you transfer the RID Master role from TAILWIND-DC1 to TAILWIND-MBR1. To complete this task, perform the following steps:

1.  On TAILWIND-MBR1, under **Tools** open Active Directory Users and Computers.<br>
2.  In the navigation pane, right-click Active Directory Users and Computers, point to **All Tasks**, and then select **Operations Masters**.
3.  On the RID tab, select **Change**, select **Yes**, and then click **OK**.
4.  Click **Close** to close the Operations Masters dialog box.

## Create an Active Directory site and configure a subnet for that site

In this task, you create an Active Directory site and configure a subnet associated with that site. To complete this task, perform the following steps:

1.  On TAILWIND-DC1, sign in as `tailwindtraders\administrator` with the password you configured for the default administrator account (`Pa55w.rdPa55w.rd`).
2.  Open Active Directory Sites and Services from the Tools menu.
3.  Right-click Sites, select **New site**, and type `Sydney` as the site name.
4.  For the Link Name, select DEFAULTIPSITELINK and click **OK** twice.
5.  Expand the **Sites** folder.
6.  Right-click **Subnets** and select **New Subnet**.
7.  As the Prefix, type `172.16.1.0/24`, select **Sydney** as site name and click **OK**.
8.  Close Active Directory Sites and Services.
