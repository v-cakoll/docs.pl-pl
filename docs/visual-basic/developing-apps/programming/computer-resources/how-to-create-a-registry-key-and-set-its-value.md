---
title: 'Porady: tworzenie klucza rejestru i określanie jego wartości'
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
ms.openlocfilehash: 459c4b3f971009ee4b6b669c55bc058db0826595
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349200"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Porady: tworzenie klucza rejestru i określanie jego wartości w Visual Basic

Metoda `CreateSubKey` obiektu `My.Computer.Registry` może służyć do tworzenia klucza rejestru.

## <a name="procedure"></a>Procedura

### <a name="to-create-a-registry-key"></a>Aby utworzyć klucz rejestru

- Użyj metody `CreateSubKey`, określając gałąź, w której ma zostać umieszczony klucz, a także nazwę klucza. W `Subkey` parametru nie jest rozróżniana wielkość liter. Ten przykład tworzy klucz rejestru `MyTestKey` w obszarze HKEY_CURRENT_USER.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Aby utworzyć klucz rejestru i ustawić w nim wartość

1. Użyj metody `CreateSubkey`, określając gałąź, w której ma zostać umieszczony klucz, a także nazwę klucza. Ten przykład tworzy klucz rejestru `MyTestKey` w obszarze HKEY_CURRENT_USER.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. Ustaw wartość za pomocą metody `SetValue`. Ten przykład ustawia wartość ciągu. "MyTestKeyValue" do "jest to wartość testowa".

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a>Przykład

Ten przykład tworzy klucz rejestru `MyTestKey` w obszarze HKEY_CURRENT_USER, a następnie ustawia wartość ciągu `MyTestKeyValue` na `This is a test value`.

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a>Skuteczne programowanie

Sprawdź strukturę rejestru, aby znaleźć odpowiednią lokalizację klucza. Na przykład możesz chcieć otworzyć HKEY_CURRENT_USER klucz \Software bieżącego użytkownika i utworzyć klucz z nazwą swojej firmy. Następnie Dodaj wartości rejestru do klucza firmy.

Podczas odczytywania rejestru z aplikacji sieci Web bieżący użytkownik zależy od uwierzytelniania i personifikacji zaimplementowanego w aplikacji sieci Web.

Bardziej bezpieczne jest zapisanie danych do folderu użytkownika (<xref:Microsoft.Win32.Registry.CurrentUser>), a nie na komputerze lokalnym (<xref:Microsoft.Win32.Registry.LocalMachine>).

Podczas tworzenia wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje. Inny proces, prawdopodobnie złośliwy, mógł już utworzyć wartość i uzyskać do niej dostęp. Po umieszczeniu danych w wartości rejestru, dane są dostępne dla drugiego procesu. Aby temu zapobiec, użyj metody <xref:Microsoft.Win32.RegistryKey.GetValue%2A>. Zwraca `Nothing`, jeśli klucz jeszcze nie istnieje.

Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy ACL (Access Control List).

Następujące warunki mogą spowodować wyjątek:

- Nazwa klucza jest `Nothing` (<xref:System.ArgumentNullException>).

- Użytkownik nie ma uprawnień do tworzenia kluczy rejestru (<xref:System.Security.SecurityException>).

- Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).

- Klucz jest zamknięty (<xref:System.IO.IOException>).

- Klucz rejestru jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).

## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework

Aby uruchomić ten proces, zestaw wymaga poziomu uprawnień przyznany przez klasę <xref:System.Security.Permissions.RegistryPermission>. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień. Analogicznie, użytkownik musi mieć poprawne listy ACL do tworzenia lub zapisywania w ustawieniach. Na przykład aplikacja lokalna, która ma uprawnienie zabezpieczeń dostępu kodu, może nie mieć uprawnień systemu operacyjnego. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../../framework/misc/code-access-security-basics.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Podstawowe informacje o zabezpieczeniach dostępu kodu](../../../../framework/misc/code-access-security-basics.md)
