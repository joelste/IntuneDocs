---
# required metadata

title: Configure iOS software update policies in Microsoft Intune - Azure | Microsoft Docs
description: In Microsoft Intune, create or add a configuration policy to restrict when software updates are automatically installed on iOS devices managed or supervised by Intune. You can choose the date and time when updates aren't installed. You can also assign this policy to groups, users, or devices, and check for any installation failures. 
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/24/2018
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer:
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configure iOS update policies in Intune

Software update policies let you force supervised iOS devices to automatically install the latest available OS update. This feature is only available for supervised devices. When configuring a policy, you can add the days and times when you don't want devices to install an update. 

The device checks in with Intune about every 8 hours. If an update is available, and it's not during a restricted time, then the device downloads and installs the latest OS update. There isn't any user interaction needed to update the device. The policy doesn't prevent a user from updating the OS manually.

This feature supports devices running iOS 10.3 and later.

## Configure the policy
1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **All services**, filter on **Intune**, and select **Microsoft Intune**.
3. Select **Software updates** > **Update policies for iOS** > **Create**.
4. Enter a name and description for the policy.
5. Select **Settings**. 

    Enter the details for when iOS devices aren't forced to install the latest updates. These settings create a restricted timeframe. You can configure the **Days** of the week, the **Time zone**, the **Start time**, the **End time**, and whether to **Delay visibility of software update (days)** to enter users. You can select a delay range of software updates from 1 to 90 days. To opt-out of setting a software update delay, enter 0. These update settings will only apply to supervised iOS devices.

6. Select **OK** to save your changes. Select **Create** to create the policy.

The profile is created and shown in the policy list. Apple MDM doesn't allow you to force a device to install updates by a certain time or date. 

## Change the restricted times for the policy

1. In **Software updates**, select **Update policies for iOS**.
2. Choose an existing policy > **Properties**.
3. Update the restricted time:

    1. Choose the days of the week
    2. Choose the time zone that this policy is applied
    3. Enter the start and end time for the blacklisted hours

    > [!NOTE]
    > If the **Start time** and **End time** are both set to 12am, then the maintenance time check is turned off.

## Assign the policy to users

Existing policies are assigned to groups, users, or devices. When assigned, the policy is applied.

1. In **Software updates**, select **Update policies for iOS**.
2. Choose an existing policy > **Assignments**. 
3. Select the Azure Active Directory groups, users, or devices to include or exclude from this policy.
4. Choose **Save** to deploy the policy to your groups.

The devices used by the users targeted by the policy are evaluated for update compliance. This policy also supports userless devices.

## Monitor device installation failures
<!-- 1352223 -->
**Software updates** > **Installation failures for iOS devices** shows a list of supervised iOS devices targeted by an update policy, attempted an update, and couldn't be updated. For each device, you can view the status on why the device hasn't been automatically updated. Healthy, up-to-date devices aren't shown in the list. "Up-to-date" devices include the latest update that the device itself supports.

