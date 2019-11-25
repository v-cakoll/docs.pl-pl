---
title: 'Porady: odczytywanie wartości z klucza rejestru'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 73c32aefe06a68bb42fcb5f4615da0927e57e892
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345615"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Porady: odczytywanie wartości z klucza rejestru w Visual Basic

The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.  
  
 If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown. If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.  
  
 The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.  
  
 When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>To read a value from a registry key  
  
- Use the `GetValue` method, specifying the path and name) to read a value from registry key. The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 This code example is also available as an IntelliSense code snippet. In the code snippet picker, it is located in **Windows Operating System > Registry**. For more information, see [Code Snippets](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>To determine whether a value exists in a registry key  
  
- Use the `GetValue` method to retrieve the value. The following code checks whether the value exists and returns a message if it does not.  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 The registry holds top-level, or root, keys that are used to store data. For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- The name of the key is `Nothing` (<xref:System.ArgumentNullException>).  
  
- The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).  
  
- The key name exceeds the 255-character limit (<xref:System.ArgumentException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class. If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges. Similarly, the user must have the correct ACLs for creating or writing to settings. For example, a local application that has the code access security permission might not have operating system permission. For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
