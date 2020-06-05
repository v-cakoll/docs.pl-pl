---
title: 'Instrukcje: tworzenie klucza rejestru i określanie jego wartości'
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
ms.openlocfilehash: b51a14e5e9c69078330f5b2161f74cff8e4da332
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363451"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Porady: tworzenie klucza rejestru i określanie jego wartości w Visual Basic

`CreateSubKey`Metoda `My.Computer.Registry` obiektu może służyć do tworzenia klucza rejestru.

## <a name="procedure"></a>Procedura

### <a name="to-create-a-registry-key"></a>Aby utworzyć klucz rejestru

- Użyj `CreateSubKey` metody, określając gałąź, w której ma zostać umieszczony klucz, a także nazwę klucza. W parametrze `Subkey` nie jest rozróżniana wielkość liter. W tym przykładzie klucz rejestru jest tworzony `MyTestKey` w obszarze HKEY_CURRENT_USER.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Aby utworzyć klucz rejestru i ustawić w nim wartość

1. Użyj `CreateSubkey` metody, określając gałąź, w której ma zostać umieszczony klucz, a także nazwę klucza. W tym przykładzie klucz rejestru jest tworzony `MyTestKey` w obszarze HKEY_CURRENT_USER.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. Ustaw wartość za pomocą `SetValue` metody. Ten przykład ustawia wartość ciągu. "MyTestKeyValue" do "jest to wartość testowa".

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a>Przykład

W tym przykładzie klucz rejestru jest tworzony `MyTestKey` w obszarze HKEY_CURRENT_USER a następnie ustawia wartość ciągu `MyTestKeyValue` na `This is a test value` .

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a>Niezawodne programowanie

Sprawdź strukturę rejestru, aby znaleźć odpowiednią lokalizację klucza. Na przykład możesz chcieć otworzyć HKEY_CURRENT_USER klucz \Software bieżącego użytkownika i utworzyć klucz z nazwą swojej firmy. Następnie Dodaj wartości rejestru do klucza firmy.

Podczas odczytywania rejestru z aplikacji sieci Web bieżący użytkownik zależy od uwierzytelniania i personifikacji zaimplementowanego w aplikacji sieci Web.

Bardziej bezpieczne jest zapisanie danych do folderu użytkownika (), <xref:Microsoft.Win32.Registry.CurrentUser> a nie na komputerze lokalnym ( <xref:Microsoft.Win32.Registry.LocalMachine> ).

Podczas tworzenia wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje. Inny proces, prawdopodobnie złośliwy, mógł już utworzyć wartość i uzyskać do niej dostęp. Po umieszczeniu danych w wartości rejestru, dane są dostępne dla drugiego procesu. Aby tego uniknąć, należy użyć <xref:Microsoft.Win32.RegistryKey.GetValue%2A> metody. Zwraca `Nothing` , jeśli klucz jeszcze nie istnieje.

Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy ACL (Access Control List).

Następujące warunki mogą spowodować wyjątek:

- Nazwa klucza to `Nothing` ( <xref:System.ArgumentNullException> ).

- Użytkownik nie ma uprawnień do tworzenia kluczy rejestru ( <xref:System.Security.SecurityException> ).

- Nazwa klucza przekracza limit 255 znaków ( <xref:System.ArgumentException> ).

- Klucz jest zamknięty ( <xref:System.IO.IOException> ).

- Klucz rejestru jest tylko do odczytu ( <xref:System.UnauthorizedAccessException> ).

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Aby uruchomić ten proces, zestaw wymaga poziomu uprawnień przyznany przez <xref:System.Security.Permissions.RegistryPermission> klasę. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień. Analogicznie, użytkownik musi mieć poprawne listy ACL do tworzenia lub zapisywania w ustawieniach. Na przykład aplikacja lokalna, która ma uprawnienie zabezpieczeń dostępu kodu, może nie mieć uprawnień systemu operacyjnego. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../../framework/misc/code-access-security-basics.md).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [Odczytywanie z rejestru i zapisywanie w nim](reading-from-and-writing-to-the-registry.md)
- [Podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md)
