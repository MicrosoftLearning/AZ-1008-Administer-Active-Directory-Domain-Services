---
lab:
    title: 'Exercise – Configure Security Settings'
    module: 'Guided Project – Administer Active Directory Domain Services'
---
In this exercise, you configure settings related to security including disabling NTLM authentication for domain accounts, auditing account management activity, and denying log on as a service for members of a security group.

This exercise should take approximately **10** minutes to complete. <!-- update with estimated duration -->

## Restrict NTLM Authentication

In this task, you restrict NTLM authentication. To complete this task, perform the following steps in TAILWIND-DC1:

1.  From the Tools menu of the Server Manager console, open the Group Policy Management console.
2.  In the Group Policy Management console, expand the tailwindtraders.internal forest, the Domains folder, and the tailwindtraders.internal domain. Then expand Group Policy Objects.
3.  Right-click **Default Domain Controller Policy** and click **Edit**.
4.  Navigate to Computer Configuration\\Policies\\Windows Settings\\Security Settings\\Local Policies\\Security Options.
5.  Select and double-click **Network security: Restrict NTLM: NTLM authentication in this domain**.
6.  Click the **Define this policy setting** check box.
7.  Select the value **Deny all** and click **OK**.
8.  Click **Yes** in the Confirm Setting Change dialog box.
9.  Close the Group Policy Management Editor.

## Audit User Account Management in Sydney

In this task, you enable auditing of User Account Management in the Sydney OU. To complete this task, perform the following steps in TAILWIND-DC1:

1.  From the Tools menu of the Server Manager console, choose Group Policy Management Console.
2.  In the Group Policy Management Console, expand the Tailwindtraders.internal domain.
3.  Navigate to the Sydney OU, right-click and select **Create a GPO in this domain, and link it here...**.
4.  Name the new GPO `SydneyOUPolicy`.
5.  Click **OK**
6.  Right-click SydneyOUPolicy and select **Edit**.
7.  Browse to Computer Configuration\\Policies\\Windows Settings\\Security Settings\\Advanced Audit Policy Configuration\\Audit Policies\\Account Management.
8.  Select and double-click **Audit User account management**.
9.  Click the **Configure the following audit events** check box.
10.  Select the **Success** and **Failure** values and click **OK**.
11.  Close the Group Policy Management Editor

## Deny Log On As a Service

In this task, you configure the Deny Log On As A Service security option. To complete this task, perform the following steps in TAILWIND-DC1:

1.  From the Tools menu of the Server Manager console, open the Group Policy Management console.
2.  Expand Tailwindtraders.internal domain.
3.  Browse to the Sydney OU and right-click SydneyOUPolicy. Select **Edit**.
4.  Browse to Computer Configuration\\Policies\\Windows Settings\\Security Settings\\Local Policies\\User Rights Assignment.
5.  Select and double-click the **Deny Log on as a service** policy.
6.  Select the **Define this policy** setting.
7.  Click **Add User or Group**.
8.  Click **Browse**, click **Advanced**, and then click **Find now**.
9.  Select **Sydney Administrators** group.
10. Click **OK** until dialogue boxes are closed (it may require four or five acknowledgements).
