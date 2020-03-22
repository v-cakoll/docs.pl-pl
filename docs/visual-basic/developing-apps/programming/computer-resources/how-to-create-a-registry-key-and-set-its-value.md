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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349200"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Porady: tworzenie klucza rejestru i określanie jego wartości w Visual Basic

Metoda `CreateSubKey` `My.Computer.Registry` obiektu może służyć do tworzenia klucza rejestru.

## <a name="procedure"></a>Procedura

### <a name="to-create-a-registry-key"></a>Aby utworzyć klucz rejestru

- Użyj `CreateSubKey` metody, określając, który gałąź umieścić klucz pod, jak również nazwę klucza. W `Subkey` przypadku przypadku przypadku nie jest rozróżniana wielkość liter. W tym przykładzie `MyTestKey` tworzy klucz rejestru w obszarze HKEY_CURRENT_USER.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Aby utworzyć klucz rejestru i ustawić w nim wartość

1. Użyj `CreateSubkey` metody, określając, który gałąź umieścić klucz pod, jak również nazwę klucza. W tym przykładzie `MyTestKey` tworzy klucz rejestru w obszarze HKEY_CURRENT_USER.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. Ustaw wartość za `SetValue` pomocą metody. W tym przykładzie ustawia wartość ciągu. "MyTestKeyValue" do "Jest to wartość testowa".

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a>Przykład

W tym przykładzie `MyTestKey` utworzy klucz rejestru w obszarze `MyTestKeyValue` `This is a test value`HKEY_CURRENT_USER a następnie ustawi wartość ciągu na .

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a>Niezawodne programowanie

Sprawdź strukturę rejestru, aby znaleźć odpowiednią lokalizację dla klucza. Na przykład można otworzyć klucz HKEY_CURRENT_USER\Oprogramowanie bieżącego użytkownika i utworzyć klucz o nazwie firmy. Następnie dodaj wartości rejestru do klucza firmy.

Podczas odczytywania rejestru z aplikacji sieci Web bieżący użytkownik zależy od uwierzytelniania i personifikacji zaimplementowanych w aplikacji sieci Web.

Bezpieczniejsze jest zapisywanie danych w<xref:Microsoft.Win32.Registry.CurrentUser>folderze użytkownika ( )<xref:Microsoft.Win32.Registry.LocalMachine>zamiast do komputera lokalnego ( ).

Podczas tworzenia wartości rejestru, należy zdecydować, co zrobić, jeśli ta wartość już istnieje. Inny proces, być może złośliwy, może już stworzył wartość i mieć do niej dostęp. Po umieszczeniu danych w wartości rejestru dane są dostępne dla innego procesu. Aby temu zapobiec, <xref:Microsoft.Win32.RegistryKey.GetValue%2A> użyj tej metody. `Nothing` Zwraca, jeśli klucz jeszcze nie istnieje.

Przechowywanie wpisów tajnych, takich jak hasła, w rejestrze jako zwykłego tekstu, nie jest bezpieczne, nawet jeśli klucz rejestru jest chroniony listami kontroli dostępu (listami kontroli dostępu).

Następujące warunki mogą spowodować wyjątek:

- Nazwa klucza jest `Nothing` <xref:System.ArgumentNullException>( ).

- Użytkownik nie ma uprawnień do tworzenia<xref:System.Security.SecurityException>kluczy rejestru ( ).

- Nazwa klucza przekracza limit 255<xref:System.ArgumentException>znaków ( ).

- Klucz jest zamknięty<xref:System.IO.IOException>( ).

- Klucz rejestru jest tylko<xref:System.UnauthorizedAccessException>do odczytu ( ).

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Aby uruchomić ten proces, zestaw wymaga poziomu <xref:System.Security.Permissions.RegistryPermission> uprawnień przyznanego przez klasę. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień. Podobnie użytkownik musi mieć poprawne listy ACL do tworzenia lub zapisywania do ustawień. Na przykład aplikacja lokalna, która ma uprawnienie zabezpieczeń dostępu do kodu, może nie mieć uprawnień systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [Podstawy zabezpieczeń dostępu do kodu](../../../../framework/misc/code-access-security-basics.md).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md)
