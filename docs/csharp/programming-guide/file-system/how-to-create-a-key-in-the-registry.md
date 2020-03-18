---
title: Jak utworzyć klucz w rejestrze - Przewodnik po programowaniu C#
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 16974db950a3a460416cfb917147439707e1d007
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635447"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a>Jak utworzyć klucz w rejestrze (Przewodnik programowania C#)
W tym przykładzie dodaje parę wartości, "Nazwa" i "Izabela", do rejestru bieżącego użytkownika, w kluczu "Nazwy".  
  
## <a name="example"></a>Przykład  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Skopiuj kod i `Main` wklej go do metody aplikacji konsoli.  
  
- Zamień `Names` parametr na nazwę klucza, który istnieje bezpośrednio w HKEY_CURRENT_USER węźle rejestru.  
  
- Zamień `Name` parametr na nazwę wartości, która istnieje bezpośrednio w węźle Nazwy.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Sprawdź strukturę rejestru, aby znaleźć odpowiednią lokalizację dla klucza. Na przykład można otworzyć klucz Oprogramowania bieżącego użytkownika i utworzyć klucz z nazwą firmy. Następnie dodaj wartości rejestru do klucza firmy.  
  
 Następujące warunki mogą powodować wyjątek:  
  
- Nazwa klucza jest null.  
  
- Użytkownik nie ma uprawnień do tworzenia kluczy rejestru.  
  
- Nazwa klucza przekracza limit 255 znaków.  
  
- Klucz jest zamknięty.  
  
- Klucz rejestru jest tylko do odczytu.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Bezpieczniej jest zapisywać dane w `Microsoft.Win32.Registry.CurrentUser` folderze użytkownika — a `Microsoft.Win32.Registry.LocalMachine`nie na komputerze lokalnym — .  
  
 Podczas tworzenia wartości rejestru należy zdecydować, co zrobić, jeśli ta wartość już istnieje. Inny proces, być może złośliwy, mógł już utworzyć wartość i mieć do niej dostęp. Po umieszczeniu danych w wartości rejestru dane są dostępne dla innego procesu. Aby temu zapobiec, należy użyć.`Overload:Microsoft.Win32.RegistryKey.GetValue` Metoda. Zwraca wartość null, jeśli klucz jeszcze nie istnieje.  
  
 Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze jako zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony listami kontroli dostępu (ACL).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania języka C#](../index.md)
- [System plików i rejestr (Przewodnik programowania w języku C#)](./index.md)
- [Odczyt, zapis i usunięcie z rejestru za pomocą c #](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
