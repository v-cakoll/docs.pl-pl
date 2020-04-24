---
title: 'Instrukcje: odczytywanie wartości z klucza rejestru'
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

`GetValue` Metoda `My.Computer.Registry` obiektu może służyć do odczytywania wartości w rejestrze systemu Windows.  
  
 Jeśli klucz "Software\MyApp" w poniższym przykładzie nie istnieje, zgłaszany jest wyjątek. `ValueName`Jeśli w poniższym przykładzie nie istnieje, zwracana `Nothing` jest wartość "name" (nazwa).  
  
 Metody `GetValue` można również użyć do określenia, czy dana wartość istnieje w określonym kluczu rejestru.  
  
 Gdy kod odczytuje rejestr z aplikacji sieci Web, bieżący użytkownik jest określany przez uwierzytelnianie i personifikację, która jest zaimplementowana w aplikacji sieci Web.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>Odczytywanie wartości z klucza rejestru  
  
- Użyj `GetValue` metody, określając ścieżkę i nazwę) do odczytu wartości z klucza rejestru. Poniższy przykład odczytuje wartość `Name` z `HKEY_CURRENT_USER\Software\MyApp` i wyświetla ją w oknie komunikatu.  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się on w **systemie operacyjnym Windows > Registry**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Aby określić, czy wartość istnieje w kluczu rejestru  
  
- Użyj `GetValue` metody, aby pobrać wartość. Poniższy kod sprawdza, czy wartość istnieje i zwraca komunikat, jeśli nie.  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Rejestr zawiera klucze najwyższego poziomu (lub główne), które są używane do przechowywania danych. Na przykład klucz główny HKEY_LOCAL_MACHINE jest używany do przechowywania ustawień na poziomie komputera używanych przez wszystkich użytkowników, podczas gdy HKEY_CURRENT_USER jest używany do przechowywania danych specyficznych dla pojedynczego użytkownika.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa klucza to `Nothing` (<xref:System.ArgumentNullException>).  
  
- Użytkownik nie ma uprawnień do odczytu z kluczy rejestru (<xref:System.Security.SecurityException>).  
  
- Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 Aby uruchomić ten proces, zestaw wymaga poziomu uprawnień przyznany przez <xref:System.Security.Permissions.RegistryPermission> klasę. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień. Analogicznie, użytkownik musi mieć poprawne listy ACL do tworzenia lub zapisywania w ustawieniach. Na przykład aplikacja lokalna, która ma uprawnienie zabezpieczeń dostępu kodu, może nie mieć uprawnień systemu operacyjnego. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
