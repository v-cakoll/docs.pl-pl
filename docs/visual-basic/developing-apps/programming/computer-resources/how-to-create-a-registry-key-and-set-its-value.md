---
title: 'Porady: tworzenie klucza rejestru i określanie jego wartości w Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: 4f74d41aa8055e26f5a707829449ddd310ff576f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Porady: tworzenie klucza rejestru i określanie jego wartości w Visual Basic
`CreateSubKey` Metody `My.Computer.Registry` obiekt może służyć do tworzenia klucza rejestru.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-create-a-registry-key"></a>Aby utworzyć klucz rejestru  
  
-   Użyj `CreateSubKey` metody, wskazujące, której hive można umieścić klucz w obszarze, a także nazwę klucza. Parametr `Subkey` nie jest rozróżniana wielkość liter. W tym przykładzie jest tworzony klucz rejestru `MyTestKey` w gałęzi HKEY_CURRENT_USER.  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Utwórz klucz rejestru i ustawić wartość w nim  
  
1.  Użyj `CreateSubkey` metody, wskazujące, której hive można umieścić klucz w obszarze, a także nazwę klucza. W tym przykładzie jest tworzony klucz rejestru `MyTestKey` w gałęzi HKEY_CURRENT_USER.  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
2.  Ustaw wartość z `SetValue` metody. W tym przykładzie wartość ciągu. "MyTestKeyValue" do "Jest wartość testu".  
  
     [!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest tworzony klucz rejestru `MyTestKey` w gałęzi HKEY_CURRENT_USER, a następnie ustawia wartość ciągu `MyTestKeyValue` do `This is a test value`.  
  
 [!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Sprawdź, czy struktura rejestru można znaleźć odpowiedniej lokalizacji dla klucza. Na przykład można otworzyć klucza HKEY_CURRENT_USER\Software bieżącego użytkownika i Utwórz klucz o nazwie firmy. Następnie dodaj odpowiednie wartości rejestru do klucza w firmie.  
  
 Podczas odczytywania rejestru z aplikacji sieci Web, bieżącego użytkownika zależy od uwierzytelniania i personifikacji wdrożone w aplikacji sieci Web.  
  
 Jest bardziej bezpieczne można zapisać danych do folderu użytkownika (<xref:Microsoft.Win32.Registry.CurrentUser>), a nie na komputerze lokalnym (<xref:Microsoft.Win32.Registry.LocalMachine>).  
  
 Po utworzeniu wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje. Inny proces, możliwe, że złośliwe jeden mogły już zostać utworzone wartość i jest do niego dostęp. Po umieszczeniu danych w wartości rejestru, dane są dostępne do innego procesu. Aby tego uniknąć, należy użyć <xref:Microsoft.Win32.RegistryKey.GetValue%2A> metody. Zwraca `Nothing` Jeśli klucz jeszcze nie istnieje.  
  
 Nie jest bezpieczny do przechowywania kluczy tajnych, takie jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy kontroli dostępu (listy kontroli dostępu).  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nazwa klucza jest `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Użytkownik nie ma uprawnień do tworzenia kluczy rejestru (<xref:System.Security.SecurityException>).  
  
-   Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).  
  
-   Klucz jest zamknięta (<xref:System.IO.IOException>).  
  
-   Klucz rejestru jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uruchomić ten proces, używanemu zestawowi wymaga poziom uprawnień przyznanych przez <xref:System.Security.Permissions.RegistryPermission> klasy. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek, ze względu na niewystarczające uprawnienia. Podobnie użytkownik musi mieć odpowiednich list ACL tworzenia i zapisywania ustawień. Na przykład lokalnych aplikacji, które ma uprawnienia zabezpieczeń dostępu kodu może nie ma uprawnienia systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>  
 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>  
 [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [Podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md)
