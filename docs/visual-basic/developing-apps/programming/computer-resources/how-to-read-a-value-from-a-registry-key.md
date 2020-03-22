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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345615"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Porady: odczytywanie wartości z klucza rejestru w Visual Basic

Metoda `GetValue` `My.Computer.Registry` obiektu może służyć do odczytywania wartości w rejestrze systemu Windows.  
  
 Jeśli klucz "Software\MyApp" w poniższym przykładzie nie istnieje, zostanie zgłoszony wyjątek. Jeśli `ValueName`, "Nazwa" w poniższym przykładzie, nie istnieje, `Nothing` jest zwracany.  
  
 Metoda `GetValue` może również służyć do określenia, czy dana wartość istnieje w określonym kluczu rejestru.  
  
 Gdy kod odczytuje rejestr z aplikacji sieci Web, bieżący użytkownik jest określany przez uwierzytelnianie i personifikację zaimplementowane w aplikacji sieci Web.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>Aby odczytać wartość z klucza rejestru  
  
- Użyj `GetValue` metody, określając ścieżkę i nazwę), aby odczytać wartość z klucza rejestru. W poniższym przykładzie odczytuje wartość `Name` i `HKEY_CURRENT_USER\Software\MyApp` wyświetla ją w oknie komunikatu.  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **rejestrze > systemu operacyjnego Windows**. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Aby ustalić, czy wartość istnieje w kluczu rejestru  
  
- Użyj `GetValue` metody, aby pobrać wartość. Poniższy kod sprawdza, czy wartość istnieje i zwraca komunikat, jeśli nie.  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Rejestr zawiera klucze najwyższego poziomu lub katalogu głównego, które są używane do przechowywania danych. Na przykład klucz główny HKEY_LOCAL_MACHINE służy do przechowywania ustawień na poziomie komputera używanych przez wszystkich użytkowników, podczas gdy HKEY_CURRENT_USER służy do przechowywania danych specyficznych dla poszczególnych użytkowników.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa klucza jest `Nothing` <xref:System.ArgumentNullException>( ).  
  
- Użytkownik nie ma uprawnień do odczytu<xref:System.Security.SecurityException>z kluczy rejestru ( ).  
  
- Nazwa klucza przekracza limit 255<xref:System.ArgumentException>znaków ( ).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 Aby uruchomić ten proces, zestaw wymaga poziomu <xref:System.Security.Permissions.RegistryPermission> uprawnień przyznanego przez klasę. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień. Podobnie użytkownik musi mieć poprawne listy ACL do tworzenia lub zapisywania do ustawień. Na przykład aplikacja lokalna, która ma uprawnienie zabezpieczeń dostępu do kodu, może nie mieć uprawnień systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [Podstawy zabezpieczeń dostępu do kodu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
