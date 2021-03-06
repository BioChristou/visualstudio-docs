---
title: "Assigning Roles to a Test Controller and Test Agent for Automated Testing in Visual Studio | Microsoft Docs"
ms.date: "10/20/2016"
ms.topic: "conceptual"
helpviewer_keywords: 
  - "testing, walkthroughs, test controller and test agents"
  - "test agent, walkthrough"
  - "walkthroughs [Visual Studio ALM] testing"
  - "test controller, walkthrough"
  - "walkthroughs, test controller and test agents"
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
---
# Assign Roles to a Test Controller and Test Agent

This walkthrough demonstrates how to create and configure a test setting that uses a test controller and test agent to distribute testing across several machines using Visual Studio. In addition, this walkthrough demonstrates how to add diagnostic and data adapters to the test setting.

In this walkthrough, you will complete the following tasks:

-   Create a test setting.

-   Assign roles to a test controller and test agents.

-   Assign a diagnostic and data adapter to your test setting.

## Prerequisites

-   Create unit tests or coded UI tests to run with the test setting.

-   Install a test controller and test agents. For information about how to install a test controller and test agents, see [Install and configure test agents](../test/lab-management/install-configure-test-agents.md).

## To create and configure a test setting

1.  In Solution Explorer, right-click **Solution Items,** point to **Add**, and then choose **New Item**.

     The **Add New Item** dialog box appears.

2.  In the **Installed Templates** pane, choose **Test Settings**.

3.  In the **Name** box, type **TestSettingDistributedTestWalkthrough**.

4.  Choose **Add**.

     The new test TestSettingDistributedTestWalkthrough.testsettings file appears in Solution Explorer, under the **Solution Items** folder.

     The **Test Settings** dialog box is displayed. The **General** page is selected.

     You can now edit and save test settings values.

    > [!NOTE]
    > Each test settings that you create is listed as a choice for the **Select Active Test Settings** and **Edit Test Settings** options on the **Test** menu.

5.  Under **Name**, type the name for the test settings.

6.  Under **Description**, type **Distributed test settings**.

7.  Leave **Default naming scheme** selected.

## To assign roles to a test controller and test agents

1.  Choose **Roles**.

     The **Roles** page is displayed.

2.  To run your test remotely, use the **Test execution method** drop-down list and select **Remote execution**.

3.  In the **Controller** drop-down list, type the computer name of [your test controller](../test/lab-management/install-configure-test-agents.md).

    > [!NOTE]
    > If this is the first time that you are adding a controller, there are no controllers listed in the drop-down list. The list is populated by previous controllers that you have specified in other test settings.

4.  Under **Roles**, choose **Add**.

5.  In the highlighted row under the **Name** column, type **Distributed test**.

## To assign a diagnostic and data adapter to your test setting

1.  Choose **Data and Diagnostics**.

     The **Data and Diagnostics** page is displayed.

2.  Under **Role**, verify that the **Distributed test** role is selected.

3.  Under **Data and Diagnostic for select role**, select the **IntelliTrace** and **System Information** adapters.

     For information about these adapters and other adapters that you can use in a test setting, see [Configure unit tests](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4.  Choose **Hosts**.

5.  (Optional) If your machine is running under a 64-bit version of Microsoft Windows, and you compiled your test using the **Any CPU** configuration, use the **Run test in 32 bit or 64 bit process** drop-down list and select **Run tests in 64-bit process on 64-bit machine**.

    > [!TIP]
    > For maximum flexibility, you should compile your test projects with the **Any CPU** configuration. Then you can run on both 32-bit and 64-bit agents. There is no advantage to compiling test projects with the **64-bit** configuration.

6.  To save the new test settings, choose **Apply**.

7.  Choose **Close**.

8.  On the Test menu, select **Select Active Test Settings** and then choose **TestSettingDistributedTestWalkthrough.testsettings**.

9. Run your test as usual.

     When the test controller processes unit tests and coded UI tests, the test controller divides the tests into groups of 100 and sends them to a test agent machine. For example, if you have 250 unit tests and three test agents, the first 100 unit tests will be sent to agent1, the next 100 unit tests will be sent to agent2, and the remaining 50 unit tests will be sent to agent3.

## See also

- [Install and configure test agents](../test/lab-management/install-configure-test-agents.md)