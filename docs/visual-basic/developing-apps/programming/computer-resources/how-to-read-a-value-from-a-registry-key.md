---
title: 'Instrukcje: Odczytywanie wartości z klucza rejestru w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: bc71dd2e3a78454236b2f6f30c2d51aa596e5b8c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840188"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Instrukcje: Odczytywanie wartości z klucza rejestru w Visual Basic
`GetValue` Metody `My.Computer.Registry` obiekt może służyć do odczytywania wartości w rejestrze systemu Windows.  
  
 Jeśli nie ma klucza "Software\MyApp" w poniższym przykładzie, jest zgłaszany wyjątek. Jeśli `ValueName`, "Name" nie istnieje w poniższym przykładzie, `Nothing` jest zwracana.  
  
 `GetValue` Metodę można również określić, czy danej wartości istnieje w kluczu rejestru.  
  
 Gdy kod odczytuje rejestru z aplikacji sieci Web, bieżącego użytkownika jest określane przez uwierzytelnianie i personifikacji, który jest implementowany w aplikacji sieci Web.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>Aby odczytać wartości z klucza rejestru  
  
-   Użyj `GetValue` metody, określając ścieżkę i nazwę) można odczytać wartości z klucza rejestru. Poniższy przykład odczytuje wartość `Name` z `HKEY_CURRENT_USER\Software\MyApp` i wyświetla go w oknie komunikatu.  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu, znajduje się w **systemu operacyjnego Windows > rejestru**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Aby określić, czy wartość istnieje w kluczu rejestru  
  
-   Użyj `GetValue` metodę, aby pobrać wartość. Poniższy kod sprawdza, czy wartość istnieje i zwraca komunikat, jeśli nie jest.  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Rejestr zawiera najwyższego poziomu lub główne klucze, które są używane do przechowywania danych. Na przykład klucz główny HKEY_LOCAL_MACHINE służy do przechowywania ustawień maszyn na poziomie używanych przez wszystkich użytkowników, podczas gdy HKEY_CURRENT_USER służy do przechowywania danych specyficznych dla poszczególnych użytkowników.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nazwa klucza jest `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Użytkownik nie ma uprawnień do odczytu klucze rejestru (<xref:System.Security.SecurityException>).  
  
-   Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uruchomić ten proces, zestaw wymaga poziom uprawnień przyznanych przez <xref:System.Security.Permissions.RegistryPermission> klasy. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek ze względu na niewystarczające uprawnienia. Podobnie użytkownik musi mieć prawidłowe listy ACL dla tworzenia zmiennej czy zapisujemy do ustawienia. Na przykład lokalnych aplikacji, które ma uprawnienia zabezpieczeń dostępu kodu ma uprawnienie systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
