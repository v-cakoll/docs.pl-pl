---
title: "Porady: odczytywanie wartości z klucza rejestru w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f88401f6daa7a2108522496c845521474c22cc30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Porady: odczytywanie wartości z klucza rejestru w Visual Basic
`GetValue` Metody `My.Computer.Registry` obiekt może służyć do odczytania wartości w rejestrze systemu Windows.  
  
 Jeśli klucz "Software\MyApp" w poniższym przykładzie, nie istnieje, zwracany jest wyjątek. Jeśli `ValueName`, "Nazwa" nie istnieje w poniższym przykładzie, `Nothing` jest zwracany.  
  
 `GetValue` Metody można również określić, czy dana wartość istnieje w kluczu rejestru.  
  
 Gdy kod odczytuje rejestru z aplikacji sieci Web, bieżącego użytkownika jest określana przez uwierzytelniania i personifikacji, która jest zaimplementowana w aplikacji sieci Web.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>Odczytać wartości z klucza rejestru  
  
-   Użyj `GetValue` metody, określając ścieżkę i nazwę) można odczytać wartości z klucza rejestru. Poniższy przykład odczytuje wartość `Name` z `HKEY_CURRENT_USER\Software\MyApp` i wyświetla je w oknie komunikatu.  
  
     [!code-vb[VbResourceTasks#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_1.vb)]  
  
 W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense. Selektor wstawek kodu, znajduje się się w **systemu operacyjnego Windows > rejestru**. Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Aby określić, czy wartość istnieje w kluczu rejestru  
  
-   Użyj `GetValue` metody do pobierania wartości. Poniższy kod sprawdza, czy wartość istnieje i zwraca komunikat, jeśli jej nie ma.  
  
     [!code-vb[VbResourceTasks#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_2.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Rejestr zawiera najwyższego poziomu lub głównego kluczy, które są używane do przechowywania danych. Na przykład klucza głównego HKEY_LOCAL_MACHINE służy do przechowywania ustawień na poziomie komputera używane przez wszystkich użytkowników, podczas gdy HKEY_CURRENT_USER jest używany do przechowywania danych specyficznych dla poszczególnych użytkowników.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nazwa klucza jest `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Użytkownik nie ma uprawnień do odczytu klucze rejestru (<xref:System.Security.SecurityException>).  
  
-   Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uruchomić ten proces, używanemu zestawowi wymaga poziom uprawnień przyznanych przez <xref:System.Security.Permissions.RegistryPermission> klasy. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek, ze względu na niewystarczające uprawnienia. Podobnie użytkownik musi mieć odpowiednich list ACL tworzenia i zapisywania ustawień. Na przykład lokalnych aplikacji, które ma uprawnienia zabezpieczeń dostępu kodu może nie ma uprawnienia systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](https://msdn.microsoft.com/library/33tceax8).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.Win32.RegistryHive>  
 [Odczytywanie z oraz zapisywanie do rejestru](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
