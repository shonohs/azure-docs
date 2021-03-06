---
title: Remove VMs from Azure Automation Change Tracking and Inventory
description: This article tells how to remove VMs from Change Tracking and Inventory.
services: automation
ms.subservice: change-inventory-management
ms.topic: conceptual
ms.date: 05/26/2021
---

# Remove VMs from Change Tracking and Inventory

When you're finished tracking changes on the VMs in your environment, you can stop managing them with the [Change Tracking and Inventory](overview.md) feature. To stop managing them, you will edit the saved search query `MicrosoftDefaultComputerGroup` in your Log Analytics workspace that is linked to your Automation account.

## Sign into the Azure portal

Sign in to the [Azure portal](https://portal.azure.com).

## To remove your VMs

1. In the Azure portal, launch **Cloud Shell** from the top navigation of the Azure portal. If you are unfamiliar with Azure Cloud Shell, see [Overview of Azure Cloud Shell](../../cloud-shell/overview.md).

2. Use the following command to identify the UUID of a machine that you want to remove from management.

    ```azurecli
    az vm show -g MyResourceGroup -n MyVm -d
    ```

3. In the Azure portal, navigate to **Log Analytics workspaces**. Select your workspace from the list.

4. In your Log Analytics workspace, select **Computer Groups** from the left-hand menu.

5. From **Computer Groups** in the right-hand pane, the **Saved groups** tab is shown by default..

6. From the table, click the icon **Run query** to the right of the item **MicrosoftDefaultComputerGroup** with the **Legacy category** value **ChangeTracking**.

7. In the query editor, review the query and find the UUID for the VM. Remove the UUID for the VM and repeat the steps for any other VMs you want to remove.

8. Save the saved search when you're finished editing it by selecting **Save > Save as function** from the top bar. When prompted, specify the following:

    * **Name**: ChangeTracking__MicrosoftDefaultComputerGroup
    * **Save as computer Group** is selected
    * **Legacy category**: ChangeTracking

>[!NOTE]
>Machines are still shown after you have unenrolled them because we report on all machines assessed in the last 24 hours. After removing the machine, you need to wait 24 hours before they are no longer listed.

## Next steps

To re-enable this feature, see [Enable Change Tracking and Inventory from an Automation account](enable-from-automation-account.md), [Enable Change Tracking and Inventory by browsing the Azure portal](enable-from-portal.md), [Enable Change Tracking and Inventory from a runbook](enable-from-runbook.md), or [Enable Change Tracking and Inventory from an Azure VM](enable-from-vm.md).