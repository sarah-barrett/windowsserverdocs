---
title: Edit an AppLocker Policy
description: "Windows Server Security"
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: security-applocker
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df5a618f-141a-4435-b496-13274b7bd7e5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
---
# Edit an AppLocker Policy

>Applies To: Windows Server&reg; 2016, Windows Server&reg; 2012 R2, Windows Server&reg; 2012

This topic describes the steps you need to perform to modify an AppLocker policy in Windows Server 2012 and Windows 8.

You can edit an AppLocker policy by adding, changing, or removing rules. However, you cannot create a new version of the policy by importing additional rules. To modify an AppLocker policy that is in production, you should use Group Policy management software that allows you to version Group Policy Objects (GPOs). If you have created multiple AppLocker policies and need to merge them to create one AppLocker policy, you can either manually merge the policies or use the Windows PowerShell cmdlets for AppLocker. You cannot automatically merge policies by using the AppLocker snap-in. You must create one rule collection from two or more policies. The AppLocker policy is saved in XML format, and the exported policy can be edited with any text or XML editor. For information about merging policies, see [Merge AppLocker Policies Manually](policies/merge-applocker-policies-manually.md) or [Merge AppLocker Policies by Using Set-applockerPolicy](policies/merge-applocker-policies-by-using-set-applockerpolicy.md).

There are two methods you can use to edit an AppLocker policy:

-   [Editing an AppLocker policy by using Group Policy](#BKMK_EditAppPolinGPO)

-   [Editing an AppLocker policy by using the Local Security Policy snap-in](#BKMK_EditAppLolNotinGPO)

## <a name="BKMK_EditAppPolinGPO"></a>Editing an AppLocker policy by using Group Policy
The steps to edit an AppLocker policy distributed by Group Policy include the following:

### Step 1: Use Group Policy management software to export the AppLocker policy from the GPO
AppLocker provides a feature to export and import AppLocker policies as an XML file. This allows you to modify an AppLocker policy outside your production environment. Because updating an AppLocker policy in a deployed GPO could have unintended consequences, you should first export the AppLocker policy to an XML file. For the procedure to do this, see [Export an AppLocker Policy from a GPO](policies/export-an-applocker-policy-from-a-gpo.md).

### Step 2: Import the AppLocker policy into the AppLocker reference computer or the computer you use for policy maintenance
After exporting the AppLocker policy to an XML file, you should import the XML file onto a reference computer so that you can edit the policy. For the procedure to import an AppLocker policy, see [Import an AppLocker Policy from Another Computer](policies/import-an-applocker-policy-from-another-computer.md).

> [!CAUTION]
> Importing a policy onto another computer will overwrite the existing policy on that computer.

### Step 3: Use AppLocker to modify and test the rule
AppLocker provides ways to modify, delete, or add rules to a policy by modifying the rules within the collection.

-   For the procedure to modify a rule, see [Edit AppLocker Rules](rules/edit-applocker-rules.md).

-   For the procedure to delete a rule, see [Delete an AppLocker Rule](rules/delete-an-applocker-rule.md).

-   For procedures to create rules, see:

    -   [Create a Rule That Uses a Publisher Condition](rules/create-a-rule-that-uses-a-publisher-condition.md)

    -   [Create a Rule That Uses a Path Condition](rules/create-a-rule-that-uses-a-path-condition.md)

    -   [Create a Rule That Uses a File Hash Condition](rules/create-a-rule-that-uses-a-file-hash-condition.md)

    -   [Enable the DLL Rule Collection](rules/enable-the-dll-rule-collection.md)

-   For steps to test an AppLocker policy, see [Test and Update an AppLocker Policy](test-and-update-an-applocker-policy.md).

-   For procedures to export the updated policy from the reference computer back into the GPO, see [Export an AppLocker Policy to an XML File](policies/export-an-applocker-policy-to-an-xml-file.md) and [Import an AppLocker Policy into a GPO](policies/import-an-applocker-policy-into-a-gpo.md).

### Step 4: Use AppLocker and Group Policy to import the AppLocker policy back into the GPO
For procedures to export the updated policy from the reference computer back into the GPO, see [Export an AppLocker Policy to an XML File](policies/export-an-applocker-policy-to-an-xml-file.md) and [Import an AppLocker Policy into a GPO](policies/import-an-applocker-policy-into-a-gpo.md).

> [!CAUTION]
> You should never edit an AppLocker rule collection while it is being enforced in Group Policy. Because AppLocker controls what files are allowed run, making changes to a live policy can create unexpected behavior. For information about testing policies, see [Test and Update an AppLocker Policy](test-and-update-an-applocker-policy.md).

> [!NOTE]
> If you are performing these steps by using Microsoft Advanced Group Policy Management (AGPM), check out the GPO before exporting the policy.

## <a name="BKMK_EditAppLolNotinGPO"></a>Editing an AppLocker policy by using the Local Security Policy snap-in
The steps to edit an AppLocker policy distributed by using the Local Security Policy snap-in include the following tasks.

### Step 1: Import the AppLocker policy
On the computer where you maintain policies, open the AppLocker snap-in from the Local Security Policy snap-in. If you exported the AppLocker policy from another computer, use AppLocker to import it onto the computer.

After exporting the AppLocker policy to an XML file, you should import the XML file onto a reference computer so that you can edit the policy. For the procedure to import an AppLocker policy, see [Import an AppLocker Policy from Another Computer](policies/import-an-applocker-policy-from-another-computer.md).

> [!CAUTION]
> Importing a policy onto another computer will overwrite the existing policy on that computer.

### Step 2: Identify and modify the rule to change, delete, or add
AppLocker provides ways to modify, delete, or add rules to a policy by modifying the rules within the collection.

-   For the procedure to modify a rule, see [Edit AppLocker Rules](rules/edit-applocker-rules.md).

-   For the procedure to delete a rule, see [Delete an AppLocker Rule](rules/delete-an-applocker-rule.md).

-   For procedures to create rules, see:

    -   [Create a Rule That Uses a Publisher Condition](rules/create-a-rule-that-uses-a-publisher-condition.md)

    -   [Create a Rule That Uses a Path Condition](rules/create-a-rule-that-uses-a-path-condition.md)

    -   [Create a Rule That Uses a File Hash Condition](rules/create-a-rule-that-uses-a-file-hash-condition.md)

    -   [Enable the DLL Rule Collection](rules/enable-the-dll-rule-collection.md)

### Step 3: Test the effect of the policy
For steps to test an AppLocker policy, see [Test and Update an AppLocker Policy](test-and-update-an-applocker-policy.md).

### Step 4: Export the policy to an XML file and propagate it to all targeted computers
For procedures to export the updated policy from the reference computer to targeted computers, see [Export an AppLocker Policy to an XML File](policies/export-an-applocker-policy-to-an-xml-file.md) and [Import an AppLocker Policy from Another Computer](policies/import-an-applocker-policy-from-another-computer.md).

## Additional resources

-   For steps to perform other AppLocker policy tasks, see [Administer AppLocker](administer-applocker.md).


