---
title: 'Porady: usuwanie klucza rejestru w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.DeleteSetting
helpviewer_keywords:
- GetSetting function [Visual Basic]
- registry [Visual Basic], deleting values
- GetAllSettings function
- registry keys [Visual Basic], deleting
- registry [Visual Basic], deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cb98c02531bac133b9dc37a92f75d5c0418dc7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a>Porady: usuwanie klucza rejestru w Visual Basic
<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> i <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> metod można usunąć kluczy rejestru.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-delete-a-registry-key"></a>Aby usunąć klucz rejestru  
  
-   Użyj `DeleteSubKey` metodę, aby usunąć klucz rejestru. W tym przykładzie powoduje usunięcie klucza oprogramowania/TestApp w gałęzi CurrentUser. Zmień kod na odpowiedni ciąg lub go na podstawie informacji dostarczone przez użytkownika.  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 `DeleteSubKey` Metoda zwraca pusty ciąg, jeśli para klucza i wartości nie istnieje.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nazwa klucza jest `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Użytkownik nie ma uprawnień do usuwania kluczy rejestru (<xref:System.Security.SecurityException>).  
  
-   Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).  
  
-   Klucz rejestru jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Wywołania rejestru kończą się niepowodzeniem, jeśli nie są przyznawane albo wystarczające uprawnienia wykonawcze (<xref:System.Security.Permissions.RegistryPermission>) lub jeśli użytkownik nie ma dostępu (określone przez listy kontroli dostępu) do tworzenia lub zapisywania ustawień. Na przykład lokalnych aplikacji, które ma uprawnienia zabezpieczeń dostępu kodu może nie ma uprawnienia systemu operacyjnego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey>  
 [Bezpieczeństwo i rejestr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 [Odczytywanie z oraz zapisywanie do rejestru](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
