---
title: "Adding an MFC Class"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a96b67f-40bf-43d4-8872-2f8dfc5404f1
caps.latest.revision: 11
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# Adding an MFC Class
To add classes derived from Microsoft Foundation Class (MFC) library classes to your project, use the **Add Class** command available from [Class View](assetId:///8d7430a9-3e33-454c-a9e1-a85e3d2db925). Specify the name of the new class, select the base class, and select the ID of the dialog box with which it is associated (if any). The code wizard creates a header file and an implementation file and adds them to your project.  
  
> [!NOTE]
>  You can add MFC classes to an ATL COM application if you initially [created the application with MFC support](../VS_visualcpp/MFC-Support-in-ATL-Projects.md). You can also add MFC classes to Win32 projects that have MFC support.  
  
### To add an MFC class to your project  
  
1.  From Class View, right-click the project name. Click **Add** and then click **Add Class** to open the [Add Class](../VS_visualcpp/Add-Class-Dialog-Box.md) dialog box.  
  
2.  In the Templates pane, select **MFC Class** and press the **Add** button.  
  
3.  Define the settings for the new class in the [MFC Class Wizard](../VS_visualcpp/MFC-Add-Class-Wizard.md) dialog box.  
  
4.  Click **Finish** to close the wizard and view the new class in Class View. You can also view the files created by the wizard in **Solution Explorer**.  
  
## See Also  
 [Adding Functionality with Code Wizards](../VS_visualcpp/Adding-Functionality-with-Code-Wizards--C---.md)   
 [Adding a Class](../VS_visualcpp/Adding-a-Class--Visual-C---.md)   
 [Class Overview](../VS_visualcpp/Class-Library-Overview.md)