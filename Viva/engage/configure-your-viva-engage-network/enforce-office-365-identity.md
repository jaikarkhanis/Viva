---
title: "Enforce Office 365 identity for Viva Engage users"
description: "When you enforce Office 365 identity in Viva Engage, all Viva Engage users use their Office 365 credentials to sign in to Viva Engage."
f1.keywords:
- CSH
ms.author: v-bvrana
author: Starshine89
manager: pamgreen
ms.date: 11/01/2023
audience: Admin
ms.topic: article
ms.service: viva
ms.subservice: viva-engage
ms.localizationpriority: medium
ms.custom: 
- Adm_Yammer
- fwlink from UI
search.appverid:
- MET150
- MOE150
- YAE150
ms.assetid: 008f940b-6bec-47fc-bcc6-9c6133467562
---

# Enforce Microsoft 365 identity for Viva Engage users

As Viva Engage becomes a core service for your organization, users want to sign in seamlessly, like any other Microsoft 365 service. If you want to streamline user management, we suggest that you maintain a single identity for all Microsoft 365 users. You can achieve both of these goals by enforcing Microsoft 365 identity in Viva Engage. By enforcing Microsoft 365 identity in Viva Engage and configuring password hash sync, pass-through authentication, or [Microsoft Entra ID](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9#BK_Federated), admins can achieve single sign-on (SSO) capabilities for all services in Microsoft 365, including Viva Engage.
  
## How enforcing Microsoft 365 identities in Viva Engage works

The following flowchart shows what happens when a user logs in to Viva Engage.
  
:::image type="content" source="../../media/engage/admin/enforce-o365-id.png" alt-text="Flowchart shows what happens when user signs in when Microsoft 365 identity is enforced, they sign in with their Microsoft 365 identity.":::
  
A user's sign-in experience when Microsoft 365 identity is and isn't enforced for Viva Engage:
  
1. A user tries to sign in to Viva Engage, and is presented with a sign-in dialog box.
    
2. The user enters their email address.
    
3. If Microsoft 365 identity is enforced, the user signs in with their Microsoft 365 identity. If the customer has implemented the federated identity model in Microsoft 365, the user signs in with single-sign-on.
    
4. If Microsoft 365 identity isn't enforced, the user signs in with their Office 365 identity only if their email address corresponds to an Office 365 account.
    
5. When Microsoft 365 identity isn't enforced, the user signs in with their Viva Engage identity (email and password), if their email address doesn't correspond to an Office 365 account.
    
The following table compares the user sign-in behavior when Microsoft 365 identity is enforced or not enforced. Office 365 identity isn't enforced by default. 
  
| Is Microsoft 365 identity enforced? | Is there an Office 365 account for that user's email address? | What happens when the user logs in: |
|:-----|:-----|:-----|
|Yes  |Yes  |The user is prompted to sign in with their Microsoft 365 identity.  |
|No  |Yes  |The user is prompted to sign in with their Microsoft 365 identity.  |
|No  |No  |The user is prompted to sign in with their Viva Engage identity (email and password).  |
   
<a name="StartEnforcing"> </a>
## Start enforcing Microsoft 365 identity in Viva Engage

It takes just a few steps to start enforcing Microsoft 365 identities in Viva Engage. However, turning on this setting can accidentally disrupt users' access to Viva Engage. So before you begin, do the following to make sure your Viva Engage users can continue working smoothly:
  
- **Make sure all current Viva Engage users have a corresponding Office 365 identity.** When you enforce Microsoft 365 identities for Viva Engage, any user without a corresponding Microsoft 365 identity is locked out of Viva Engage. So before you begin, make sure that all of your current Viva Engage users have corresponding Microsoft 365 identities. To ensure that users have the correct identities, go to the data export page in the Viva Engage admin center and export all users. Compare that list to the list of users in Microsoft 365 and make any needed changes.
    
- **Tell your users about this change.** We strongly recommend that you tell users that you're switching to enforcing Microsoft 365 identities, because it can disrupt their day-to-day usage of Viva Engage. See the following sample email for suggested text.
    
You must be a global administrator on Office 365 who was synchronized to Viva Engage on Microsoft 365.
  
### To start enforcing Microsoft 365 identity in Viva Engage
  
1. In the Yammer admin center, go to the **Network Admin** section, and choose **Security Settings**.
    
2. In the Security Settings page, go to the **Office 365 Identity Enforcement** section and select **Enforce Office 365 identity**. 
    
    You must be a global administrator to see this section. 
    
    :::image type="content" source="../../media/engage/admin/enforce-o365-settings.png" lightbox="../../media/engage/admin/enforce-o365-settings.png" alt-text="Screenshot that shows the Enforce Office 365 identity in Viva Engage checkbox in the Viva Engage Security Setting page. You must be a global administrator to see this setting.":::
  
3. A confirmation message asks you to select the most appropriate level of enforcement: 
    
   - **Committed Enforcement**:  Choose this option if all of your Viva Engage users already have a Microsoft Entra ID account.
    
     > [!IMPORTANT]
     > This change cannot be reversed. Your users will no longer be able to sign in using their Viva Engage usernames and passwords. 
  
   - **Temporary 7-Day Enforcement**: Choose this option if you're testing the enforcement of Microsoft 365 identity on your network, and may need to revert it back. After you save this change, a temporary enforcement period of seven days begins, and your users can't sign in using their Viva Engage usernames and passwords. After seven days, your network is automatically committed to Microsoft 365 identity enforcement.
    
     :::image type="content" source="../../media/a0927cc2-eafa-4ace-a939-a3fa27be943b.png" alt-text="Screenshot of confirmation dialog box that shows the Enforcement level for Microsoft 365 sign-in.":::
  
4. Optionally, you can automatically sign out all current users to ensure that everyone using the Viva Engage service has signed in with their Microsoft 365 identities. To sign out all current users, select the **Log out all users** checkbox. If you choose this option, we recommend that you communicate this change to your users by using the following sample email.
    
   *Subject Line: [Action Required] Log back in to Viva Engage* 
    
   *Hi,* 
    
   *This email is to let you know that [ORGANIZATION'S NAME] is making changes to the way we all access Viva Engage. If you're currently working on Viva Engage, we may temporarily interrupt you by logging you out. This action is necessary for us to securely configure Microsoft 365 sign-in for Viva Engage.* 
    
   *You can resume your work immediately by logging in to Viva Engage using your Microsoft 365 username and password.*
    
   *We've made this change so that you can access all of Office 365 with a single identity. If you're unable to sign in using your Microsoft 365 username and password, let your network administrator know.* 
    
   *Thank You,* 
    
   *[SIGNATURE]* 
    
5. If you're ready to start enforcing this setting, select **Okay**. Go to the Security Settings page where the **Enforce Office 365 identity in Viva Engage** checkbox is now selected. 
    
   > [!NOTE]
   > You can also select [Start blocking users who don't have Viva Engage licenses](../manage-viva engage-users/manage-viva engage-licenses-in-office-365.md#StartBlocking) to ensure that only users with Viva Engage licenses can login to Viva Engage.
  
6. Choose **Save** to save all your settings on the page.
    
## Stop enforcing Office 365 identity in Viva Engage
<a name="StopEnforcing"> </a>

> [!IMPORTANT]
> You can only stop enforcing Microsoft 365 identities in Viva Engage when you are in the temporary 7-day enforcement period. 
  
When you stop enforcing Microsoft 365 identities in Viva Engage:
  
- Any users already logging into Viva Engage with their Microsoft 365 identities are unaffected by this change.
    
- Other users can join your network by signing up with their work email and verifying it.
    
If you no longer want to enforce Microsoft 365 identities, use the following steps to stop. You must be a global administrator to perform these steps.
  
**To stop enforcing Microsoft 365 identity in Viva Engage**
  
1. In Viva Engage, go to the **Network Admin** section, and choose **Security Settings**.
    
2. In the Security Settings page, go to the **Office 365 Identity Enforcement** section and clear the **Enforce Office 365 identity** checkbox. 
    
   You see a confirmation message so you can verify that you're ready to stop enforcing Office 365 identity.
    
   :::image type="content" source="../../media/09162001-6581-41f9-b558-27673366c2a8.png" alt-text="Screenshot of confirmation dialog box to stop enforcing Microsoft 365 identities in Viva Engage. Viva Engage SSO restarts if it was previously configured. Users who normally log into Viva Engage with Microsoft 365 identities aren't affected.":::
  
3. Select **Okay** to confirm your choice. 
    
   The Security Settings page shows the **Enforce Office 365 identity in Yammer** checkbox cleared.
    
4. Choose **Save** to save your settings on the page.
    
## FAQ
<a name="FAQ"> </a>

#### Once Office 365 Identity Enforcement is set to 'Committed Enforcement', why can't I revert it back?

When an organization commits to enforcing Microsoft 365 identity and has one Microsoft 365 tenant associated with a single Viva Engage tenant, connected groups are enabled for the network. In this configuration, whenever a group is created in Viva Engage, a connected Microsoft 365 group is also created. Users can then take advantage of tools connected to the group like SharePoint, Planner, and OneNote. At this point, reverting the **Enforce Office 365 Identity** setting is disruptive to the user experience, as users who sign in with their user names and passwords can no longer access these connected resources.
  
#### How will this change impact guest and external users?

Guests and external users are unaffected and follow the sign-in settings and requirements of their home network.
  
#### How long does it take for this setting to be applied?

Enforce Office 365 Identity is applied immediately after you select the setting.
  
#### We use the same ADFS configuration in Viva Engage and Microsoft 365. Should we sign out users during the transition?

Yes. Sign-out ensures all users who sign on afterward are connected to their Microsoft 365 identity. Microsoft 365 identity connects users to lifecycle management, which provides a consistent experience with things like Microsoft 365 suite navigation.
  
#### What is the experience for users being logged-out when enforcing Microsoft 365 identities?

Users are signed out of their web and mobile sessions immediately and must sign in again to all their devices and browser sessions using their Microsoft 365 identity configuration and credentials.
  
<a name='q-how-can-i-audit-and-clean-up-viva-engage-users-when-compared-to-office-365-and-azure-ad'></a>

#### How can I audit and clean up Viva Engage users when compared to Microsoft 365 and Microsoft Entra ID?

You can audit Viva Engage users in networks connected to Microsoft 365 and take appropriate actions based on it. See more information and examples in [How to audit Viva Engage users in networks connected to Microsoft 365](../manage-viva-engage-users/audit-users-connected-to-office-365.md).
