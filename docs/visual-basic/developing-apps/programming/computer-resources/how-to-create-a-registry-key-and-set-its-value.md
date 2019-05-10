---
title: 'Instrukcje: Utwórz klucz rejestru i określanie jego wartości w języku Visual Basic'
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
ms.openlocfilehash: 5c286c240c405fc2d01b267bb4395701ec091c8a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620694"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Instrukcje: Utwórz klucz rejestru i określanie jego wartości w języku Visual Basic
`CreateSubKey` Metody `My.Computer.Registry` obiekt może służyć do tworzenia klucza rejestru.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-create-a-registry-key"></a>Aby utworzyć klucz rejestru  
  
- Użyj `CreateSubKey` metody, wskazujące, której hive, umieszcza klucz w obszarze, a także nazwę klucza. Parametr `Subkey` nie jest rozróżniana wielkość liter. W tym przykładzie tworzy klucz rejestru `MyTestKey` w gałęzi HKEY_CURRENT_USER.  
  
     [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Utwórz klucz rejestru i wartości w nim  
  
1. Użyj `CreateSubkey` metody, wskazujące, której hive, umieszcza klucz w obszarze, a także nazwę klucza. W tym przykładzie tworzy klucz rejestru `MyTestKey` w gałęzi HKEY_CURRENT_USER.  
  
     [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]  
  
2. Ustaw wartość z `SetValue` metody. W tym przykładzie ustawia wartość ciągu. "MyTestKeyValue" do "To jest wartość testu".  
  
     [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tworzy klucz rejestru `MyTestKey` w gałęzi HKEY_CURRENT_USER, a następnie ustawia wartość ciągu `MyTestKeyValue` do `This is a test value`.  
  
 [!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Zbadaj strukturę rejestru w celu znalezienia odpowiedniej lokalizacji dla klucza. Na przykład można otworzyć klucza HKEY_CURRENT_USER\Software bieżącego użytkownika, a następnie utworzyć klucz z nazwą Twojej firmy. Następnie dodaj wartości rejestru do klucza Twojej firmy.  
  
 Podczas odczytywania rejestru z aplikacji sieci Web, bieżącego użytkownika zależy od uwierzytelniania i personifikacji zaimplementowane w aplikacji sieci Web.  
  
 Bezpieczniej jest do zapisywania danych do folderu użytkownika (<xref:Microsoft.Win32.Registry.CurrentUser>), a nie na komputerze lokalnym (<xref:Microsoft.Win32.Registry.LocalMachine>).  
  
 Kiedy tworzysz wartość rejestru, musisz zdecydować, co należy zrobić, jeśli ta wartość już istnieje. Inny proces, fałszywy, być może już utworzył wartość i masz do niego dostęp. Dane są umieszczane w wartości rejestru, dane są dostępne dla innego procesu. Aby tego uniknąć, należy użyć <xref:Microsoft.Win32.RegistryKey.GetValue%2A> metody. Zwraca `Nothing` Jeśli klucz jeszcze nie istnieje.  
  
 Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze jako zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy kontroli dostępu (list usługi Access Control).  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa klucza jest `Nothing` (<xref:System.ArgumentNullException>).  
  
- Użytkownik nie ma uprawnień do tworzenia kluczy rejestru (<xref:System.Security.SecurityException>).  
  
- Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).  
  
- Klucz jest zamknięty (<xref:System.IO.IOException>).  
  
- Klucz rejestru jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uruchomić ten proces, zestaw wymaga poziom uprawnień przyznanych przez <xref:System.Security.Permissions.RegistryPermission> klasy. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek ze względu na niewystarczające uprawnienia. Podobnie użytkownik musi mieć prawidłowe listy ACL dla tworzenia zmiennej czy zapisujemy do ustawienia. Na przykład lokalnych aplikacji, które ma uprawnienia zabezpieczeń dostępu kodu ma uprawnienie systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md)
