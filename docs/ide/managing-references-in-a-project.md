---
title: "Managing references in a project | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.ProjectPropertiesReferencePaths"
  - "cs.ProjectPropertiesReferencePaths"
helpviewer_keywords: 
  - "Visual C# projects, references"
  - "referencing objects, project references"
  - "external component references"
  - "referencing namespaces"
  - "Visual Basic projects, references"
  - "referencing components, external components"
  - "Web references, types of project references"
  - "namespaces [Visual Studio], referencing"
  - "COM components, referencing"
  - "objects [Visual Studio], referencing"
ms.assetid: 05d1c51b-44f3-4973-8a11-6c919b08ad62
caps.latest.revision: 54
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Managing references in a project
Before you write code against an external component or connected service, your project must first contain a reference to it. A reference is essentially an entry in a project file that contains the information that Visual Studio needs to locate the component or the service.  

 To add a reference, right click on the References node in Solution Explorer and choose **Add Reference**. For more information, see [How to: Add or Remove References By Using the Reference Manager](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).  

 ![Add a reference in Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_reference.png "vs2015_cpp_add_reference")  

 You can make a reference to the following types of components/services:  

-   Windows Store app references  

-   .NET Framework class libraries or assemblies  

-   COM components  

-   Other assemblies or class libraries of projects in the same solution  

-   XML Web services  

## Windows Store App References  

### Project References  
 Universal Windows Platform (UWP) projects that target Windows 10 can create references to other UWP projects in the solution, or to Windows Store projects or binaries that target [!INCLUDE[win81](../debugger/includes/win81_md.md)], provided that these projects do not use APIs that have been deprecated in Windows 10. For more information, see [Move from Windows Runtime 8 to UWP](https://docs.microsoft.com/en-us/windows/uwp/porting/w8x-to-uwp-root).  

 If you choose to retarget [!INCLUDE[win81](../debugger/includes/win81_md.md)] projects to Windows 10, see [Port, Migrate, and Upgrade Visual Studio Projects](../porting/port-migrate-and-upgrade-visual-studio-projects.md)  

### Extension SDK References  
 Visual Basic, C#, C++ and JavaScript Windows Store projects that target the Universal Windows Platform (UWP) can reference Extension SDKs that target [!INCLUDE[win81](../debugger/includes/win81_md.md)], as long as these Extension SDKs do not use APIs that have been deprecated in Windows 10. Please check the Extension SDK vendor site to find out whether it can be referenced by Windows Store projects that target UWP.  

 If you determine that the Extension SDK being referenced by your app is not supported, then you need to perform the following steps:  

1.  Look at the name of the project that is causing the error. The platform your project is targeting is noted in parentheses next to the project name. For example, **MyProjectName (Windows 8.1)** means that your project **MyProjectName** is targeting platform version [!INCLUDE[win81](../debugger/includes/win81_md.md)].  

2.  Go to the site of the vendor who owns the unsupported Extension SDK and install the version of the Extension SDK with dependencies that are compatible with the version of the platform your project is targeting.  

    > [!NOTE]
    >  One way to find out whether an Extension SDK has dependencies on other Extension SDKs is to restart Visual Studio, create a new C# Windows Store project, right-click on the project and choose **Add Reference**, go to the **Windows** tab, go to the **Extensions** sub-tab, select the Extension SDK and look at the right pane in the **Reference Manager**. If it has dependencies, they will be listed there.  

    > [!IMPORTANT]
    >  If your project is targeting Windows 10, and the Extension SDK installed in the previous step has a dependency on the Microsoft Visual C++ Runtime Package, the version of Microsoft Visual C++ Runtime Package that is compatible with Windows 10 is v14.0 and is installed with Visual Studio.  

3.  If the Extension SDK you installed in the previous step has dependencies on other Extension SDKs, go to the site(s) of the vendor(s) who own the dependencies and install the versions of these dependencies that are compatible with the version of the platform your project is targeting.  

4.  Restart Visual Studio and open your app.  

5.  Right-click on the **References** node in the project that caused the error and choose **Add Reference**  

6.  Click the **Windows** tab and then the **Extensions** sub-tab, then uncheck the checkboxes for the old Extension SDKs and check the checkboxes for the new Extension SDKs. Click **OK**.  

## Adding a Reference at Design Time  
 When you make a reference to an assembly in your project, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] searches for the assembly in the following locations:  

-   The current project directory. (You can find these assemblies by using the **Browse** tab.)  

-   Other project directories in the same solution. (You can find these assemblies on the **Projects** tab.)  

> [!NOTE]
>  All projects contain an implied reference to mscorlib. Visual Basic projects contain an implied reference to `Microsoft.VisualBasic`.  
>   
>  All projects in Visual Studio contain an implied reference to `System.Core`, even if `System.Core` is removed from the list of references.  

## References to Shared Components at Run Time  
 At run time, components must be either in the output path of the project or in the Global Assembly Cache (GAC). If the project contains a reference to an object that is not in one of these locations, you must copy the reference to the output path of the project when you build the project. The <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> property indicates whether this copy has to be made. If the value is **True**, the reference is copied to the project directory when you build the project. If the value is **False**, the reference is not copied.  

 If you deploy an application that contains a reference to a custom component that is registered in the GAC, the component will not be deployed with the application, regardless of the <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> setting. In earlier versions of [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], you could set the <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> property on a reference to ensure that the assembly was deployed. Now, you must manually add the assembly to the \Bin folder. This puts all custom code under scrutiny, reducing the risk of publishing custom code with which you are not familiar.  

 By default, the <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> property is set to **False** if the assembly or component is in the global assembly cache or is a framework component. Otherwise, the value is set to **True**. Project-to-project references are always set to **True**.  

## Referencing a Project or Assembly That Targets a Different Version of the .NET Framework  
 You can create applications that reference projects or assemblies that target a different version of the .NET Framework. For example, you could create an application that targets the [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] that references an assembly that targets [!INCLUDE[dnprdnext](../ide/includes/dnprdnext_md.md)]. If you create a project that targets an earlier version of the [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], you cannot set a reference in that project to a project or assembly that targets the [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] or .NET Framework version 4.  

 For more information, see [Targeting a Specific .NET Framework Version](../ide/targeting-a-specific-dotnet-framework-version.md).  

## Project-to-Project References  
 Project-to-project references are references to projects that contain assemblies; you create them by using the **Project** tab. Visual Studio can find an assembly when given a path to the project.  

 When you have a project that produces an assembly, you should reference the project and not use a file reference (see below). The advantage of a project-to-project reference is that it creates a dependency between the projects in the build system. The dependent project will be built if it has changed since the last time the referencing project was built. A file reference does not create a build dependency, so it is possible to build the referencing project without building the dependent project, and the reference can become obsolete. (That is, the project can reference a previously built version of the project.) This can result in several versions of a single DLL being required in the bin directory, which is not possible. When this conflict occurs, you will see a message such as "Warning: the dependency 'file' in project 'project' cannot be copied to the run directory because it would overwrite the reference 'file.'". For more information, see [Troubleshooting Broken References](../ide/troubleshooting-broken-references.md) and [How to: Create and Remove Project Dependencies](../ide/how-to-create-and-remove-project-dependencies.md).  

> [!NOTE]
>  A file reference instead of a project-to-project reference is created if the target version of the .NET Framework of one project is version 4.5, and the target version of the other project is version 2, 3, 3.5, or 4.0.  

## File References  
 File references are direct references to assemblies outside the context of a Visual Studio project; you create them by using the **Browse** tab of the **Reference Manager**. Use a file reference when you just have an assembly or component and don't have the project that creates it as output.  

## See Also  
 [Troubleshooting Broken References](../ide/troubleshooting-broken-references.md)   
 [How to: Add or Remove References By Using the Reference Manager](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
