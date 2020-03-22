---
title: 'Porady: usuwanie klucza rejestru'
ms.date: 07/20/2015
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
ms.openlocfilehash: f38301a3a717a35b98e55804d6435d046bbbbab4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345656"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a>Porady: usuwanie klucza rejestru w Visual Basic

I <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> metody mogą być używane do usuwania kluczy rejestru.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-delete-a-registry-key"></a>Aby usunąć klucz rejestru  
  
- Użyj `DeleteSubKey` tej metody, aby usunąć klucz rejestru. W tym przykładzie usuwa klucz Software/TestApp w currentuser hive. Można to zmienić w kodzie na odpowiedni ciąg lub polegać na informacjach dostarczonych przez użytkownika.  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Metoda `DeleteSubKey` zwraca pusty ciąg, jeśli para klucz/wartość nie istnieje.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa klucza jest `Nothing` <xref:System.ArgumentNullException>( ).  
  
- Użytkownik nie ma uprawnień do usuwania kluczy rejestru (<xref:System.Security.SecurityException>).  
  
- Nazwa klucza przekracza limit 255<xref:System.ArgumentException>znaków ( ).  
  
- Klucz rejestru jest tylko<xref:System.UnauthorizedAccessException>do odczytu ( ).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 Wywołania rejestru nie powiedzie się, jeśli nie<xref:System.Security.Permissions.RegistryPermission>udzielono wystarczających uprawnień w czasie wykonywania ( ) lub jeśli użytkownik nie ma poprawnego dostępu (określonego przez listy ACL) do tworzenia lub zapisywania w ustawieniach. Na przykład aplikacja lokalna, która ma uprawnienie zabezpieczeń dostępu do kodu, może nie mieć uprawnień systemu operacyjnego.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [Bezpieczeństwo i rejestr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
