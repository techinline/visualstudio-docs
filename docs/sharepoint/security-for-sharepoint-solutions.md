---
title: "Security for SharePoint Solutions | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "security [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, security"
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: 16
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Security for SharePoint Solutions
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incorporates the following features to help enhance the security of SharePoint applications.  
  
## Safe Control Entries  
 Every SharePoint project item created in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] has a **Safe Control Entries** property that represents a safe controls collection. Its **Safe** subproperty enables you to specify the controls that you consider secure. For more information, see [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) and [Specifying Safe Web Parts](http://go.microsoft.com/fwlink/?LinkId=177521).  
  
## AllowPartiallyTrustedCallers Attribute  
 By default, only applications that are fully trusted by the runtime code access security (CAS) system can access a shared managed code assembly. Marking a fully trusted assembly with the AllowPartiallyTrustedCallers attribute allows partially trusted assemblies to access it.  
  
 The AllowPartiallyTrustedCallers attribute is added to any SharePoint solution that is not deployed to the system global assembly cache ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). This includes sandboxed solutions or solutions deployed to the SharePoint application Bin directory. For more information, see [Version 1 Security Changes for the Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) and [Deploying Web Parts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
## Safe Against Script Property  
 *Script injection* is the insertion of potentially malicious code into controls or Web pages. To help protect SharePoint 2010 sites against script injection, contributors cannot view or edit Web parts or their properties by default. This behavior is controlled by a SafeControl attribute called SafeAgainstScript. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], set this attribute in a project item's **Safe Control Entries** subproperty **Safe Against Script**. For more information, see [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) and [How to: Mark Controls as Safe Controls](../sharepoint/how-to-mark-controls-as-safe-controls.md).  
  
## Vista and Windows 7 User Account Control  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] and [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporate a security feature known as User Account Control (UAC). To develop SharePoint solutions in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] on [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] and [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] systems, UAC requires that you run [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] as a system administrator. From the **Start** menu, open the shortcut menu for [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], and then choose **Run as administrator**.  
  
 To configure the [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] shortcut to always run as administrator, open its shortcut menu, choose **Properties**, choose the **Advanced** button in the **Properties** dialog box, and then select the **Run as administrator** check box.  
  
 For more information, see [Understanding and Configuring User Account Control in Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). and [Windows 7 User Account Control](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## SharePoint Permissions Considerations  
 To develop SharePoint solutions, you must have sufficient permissions to run and debug SharePoint solutions. Before you can test a SharePoint solution, take the following steps to ensure that you have the necessary permissions:  
  
1.  Add your user account as an Administrator on the system.  
  
2.  Add your user account as a Farm Administrator for the SharePoint server.  
  
    1.  In SharePoint 2010 Central Administration, choose the **Manage the farm administrators group** link.  
  
    2.  On the **Farm Administrators** page, choose the **New** menu option  
  
3.  Add your user account to the to the WSS_ADMIN_WPG group.  
  
## Additional Security Resources  
 For more information about security issues, see the following.  
  
### Visual Studio Security  
  
-   [Security and User Permissions](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [Security in Native and .NET Framework Code](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [Security in the .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### SharePoint Security  
  
-   [SharePoint Foundation Administration and Security](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [SharePoint Security Resource Center](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [Securing Web Parts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Improving Web Application Security: Threats and Countermeasures](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### General Security  
  
-   [MSDN Security Development Lifecycle](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## See Also  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Requirements for Developing SharePoint Solutions](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  