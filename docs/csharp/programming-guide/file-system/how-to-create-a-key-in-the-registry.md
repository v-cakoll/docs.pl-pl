---
title: 'Instrukcje: Tworzenie klucza w rejestrze (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: e67a80fa8f9a088f0eefe2dd2eeaa983e0a5a2c3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590042"
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a>Instrukcje: Tworzenie klucza w rejestrze (Visual C#)
Ten przykład dodaje parę wartości "name" i "Isabella" do rejestru bieżącego użytkownika w kluczu "names" (nazwy).  
  
## <a name="example"></a>Przykład  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Skopiuj kod i wklej go do `Main` metody aplikacji konsolowej.  
  
- Zastąp `Names` parametr nazwą klucza, który istnieje bezpośrednio w węźle HKEY_CURRENT_USER rejestru.  
  
- Zastąp `Name` parametr nazwą wartości, która istnieje bezpośrednio pod węzłem nazwy.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Sprawdź strukturę rejestru, aby znaleźć odpowiednią lokalizację klucza. Na przykład możesz chcieć otworzyć klucz oprogramowania bieżącego użytkownika i utworzyć klucz z nazwą swojej firmy. Następnie Dodaj wartości rejestru do klucza firmy.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa klucza ma wartość null.  
  
- Użytkownik nie ma uprawnień do tworzenia kluczy rejestru.  
  
- Nazwa klucza przekracza limit 255 znaków.  
  
- Klucz jest zamknięty.  
  
- Klucz rejestru jest tylko do odczytu.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Bardziej bezpieczne jest zapisanie danych do folderu użytkownika — `Microsoft.Win32.Registry.CurrentUser` a nie na komputerze lokalnym —. `Microsoft.Win32.Registry.LocalMachine`  
  
 Podczas tworzenia wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje. Inny proces, prawdopodobnie złośliwy, mógł już utworzyć wartość i uzyskać do niej dostęp. Po umieszczeniu danych w wartości rejestru, dane są dostępne dla drugiego procesu. Aby temu zapobiec, użyj.`Overload:Microsoft.Win32.RegistryKey.GetValue` Method. Zwraca wartość null, jeśli klucz jeszcze nie istnieje.  
  
 Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy kontroli dostępu (ACL).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../index.md)
- [System plików i Rejestr (C# Przewodnik programowania)](./index.md)
- [Odczytuj, zapisuj i usuwaj z rejestru za pomocąC#](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
