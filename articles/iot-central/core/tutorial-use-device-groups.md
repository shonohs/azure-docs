---
title: Tutorial - Use device groups in your Azure IoT Central application | Microsoft Docs
description: Tutorial - Learn how to use device groups to analyze telemetry from  devices in your Azure IoT Central application.
author: dominicbetts
ms.author: dobett
ms.date: 11/16/2020
ms.topic: tutorial
ms.service: iot-central
services: iot-central
---

# Tutorial: Use device groups to analyze device telemetry

This article describes how to use device groups to analyze device telemetry in your Azure IoT Central application.

A device group is a list of devices that are grouped together because they match some specified criteria. Device groups help you manage, visualize, and analyze devices at scale by grouping devices into smaller, logical groups. For example, you can create a device group to list all the air conditioner devices in Seattle to enable a technician to find the devices for which they're responsible.

In this tutorial, you learn how to:

> [!div class="checklist"]
> * Create a device group
> * Use a device group to analyze device telemetry

## Prerequisites

Before you begin, you should complete the [Create an Azure IoT Central application](./quick-deploy-iot-central.md) and [Add a simulated device to your IoT Central application](./quick-create-simulated-device.md) quickstarts to create the **Sensor Controller** device template to work with.

## Create simulated devices

Before you create a device group, add at least five simulated devices based on the **Sensor Controller** device template to use in this tutorial:


:::image type="content" source="media/tutorial-use-device-groups/simulated-devices.png" alt-text="Screenshot showing five simulated sensor controller devices":::

For four of the simulated sensor devices, use the **Manage device** view to set the customer name to *Contoso* and select **Save**.

:::image type="content" source="media/tutorial-use-device-groups/customer-name.png" alt-text="Screenshot that shows how to set the Customer Name cloud property":::

## Create a device group

1. Select **Device groups** on the left pane to navigate to device groups page.

1. Select **+ New**.

1. Name your device group *Contoso devices*. You can also add a description. A device group can only contain devices from a single device template. Choose the **Sensor Controller** device template to use for this group.

1. To customize the device group to include only the devices belonging to **Contoso**, select **+ Filter**. Select the **Customer Name** property, the **Equals** comparison operator, and **Contoso** as the value. You can add multiple filters and devices that meet **all** the filter criteria are placed in the device group. The device group you create is accessible to anyone who has access to the application, so anyone can view, modify, or delete the device group.

    > [!TIP]
    > The device group is a dynamic query. Every time you view the list of devices, there may be different devices in the list. The list depends on which devices currently meet the criteria of the query.

1. Choose **Save**.

:::image type="content" source="media/tutorial-use-device-groups/device-group-query.png" alt-text="Screenshot that shows the device group query configuration":::

> [!NOTE]
> For Azure IoT Edge devices, select Azure IoT Edge templates to create a device group.

## Analytics

You can use **Analytics** with a device group to analyze the telemetry from the devices in the group. For example, you can plot the average temperature reported by all the Contoso environmental sensors.

To analyze the telemetry for a device group:

1. Choose **Analytics** on the left pane.

1. Select the **Contoso devices** device group you created. Then add both the **Temperature** and **Humidity** telemetry types:

    :::image type="content" source="media/tutorial-use-device-groups/create-analysis.png" alt-text="Screenshot that shows the telemetry types selected for analysis":::

    Use the gear-wheel icons next to the telemetry types to select an aggregation type. The default is **Average**. Use **Group by** to change how the aggregate data is shown. For example, if you split by device ID you see a plot for each device when you select **Analyze**.

1. Select **Analyze** to view the average telemetry values:

    :::image type="content" source="media/tutorial-use-device-groups/view-analysis.png" alt-text="Screenshot that shows average values for all the Contoso devices":::

    You can customize the view, change the time period shown, and export the data.

## Clean up resources

[!INCLUDE [iot-central-clean-up-resources](../../../includes/iot-central-clean-up-resources.md)]

## Next steps

Now that you've learned how to use device groups in your Azure IoT Central application, here is the suggested next step:

> [!div class="nextstepaction"]
> [How to create telemetry rules](tutorial-create-telemetry-rules.md)
