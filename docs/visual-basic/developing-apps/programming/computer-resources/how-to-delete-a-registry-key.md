---
title: 'Instrukcje: Usuwanie klucza rejestru w Visual Basic'
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
ms.openlocfilehash: 226dc22f42783bec11eb1ddc38f270477bb0fbab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633966"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a>Instrukcje: Usuwanie klucza rejestru w Visual Basic
<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> i <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> metody służy do usuwania kluczy rejestru.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-delete-a-registry-key"></a>Aby usunąć klucz rejestru  
  
-   Użyj `DeleteSubKey` metodę, aby usunąć klucza rejestru. W tym przykładzie usuwa klucz oprogramowania/TestApp w gałęzi CurrentUser. Możesz zmienić w kodzie na odpowiedni ciąg lub jego opierają się na informacjach dostarczonych przez użytkownika.  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 `DeleteSubKey` Metoda zwraca pusty ciąg, jeśli para klucza i wartości nie istnieje.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nazwa klucza jest `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Użytkownik nie ma uprawnień do usuwania kluczy rejestru (<xref:System.Security.SecurityException>).  
  
-   Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).  
  
-   Klucz rejestru jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Wywołania rejestru kończyć się niepowodzeniem, jeśli nie są przyznawane albo wystarczające uprawnienia środowiska wykonawczego (<xref:System.Security.Permissions.RegistryPermission>) lub jeśli użytkownik nie ma prawidłowy dostęp (zgodnie z ustaleniami listy ACL), tworzenia i zapisywania ustawień. Na przykład lokalnych aplikacji, które ma uprawnienia zabezpieczeń dostępu kodu ma uprawnienie systemu operacyjnego.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [Bezpieczeństwo i rejestr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
