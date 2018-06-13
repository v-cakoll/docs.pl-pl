---
title: 'Porady: tworzenie klucza w rejestrze (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: a1643310740a472ad0a1df978fa41f674f3dbcb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331470"
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a>Porady: tworzenie klucza w rejestrze (Visual C#)
W tym przykładzie dodaje pary wartości, "Name" i "Isabella", do bieżącego użytkownika, kluczu rejestru "Nazwy".  
  
## <a name="example"></a>Przykład  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Skopiuj kod i wklej ją do `Main` metoda aplikacji konsoli.  
  
-   Zastąp `Names` parametr o nazwie klucza, czy istnieje bezpośrednio w węźle HKEY_CURRENT_USER rejestru.  
  
-   Zastąp `Name` parametr o nazwie wartość, która istnieje bezpośrednio w węźle nazwy.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Sprawdź, czy struktura rejestru można znaleźć odpowiedniej lokalizacji dla klucza. Na przykład można otworzyć klucza oprogramowania bieżącego użytkownika i Utwórz klucz o nazwie firmy. Następnie dodaj odpowiednie wartości rejestru do klucza w firmie.  
  
 Poniższe warunki może spowodować wyjątek:  
  
-   Nazwa klucza jest pusta.  
  
-   Użytkownik nie ma uprawnień do tworzenia kluczy rejestru.  
  
-   Nazwa klucza przekracza limit 255 znaków.  
  
-   Klucz jest zamknięty.  
  
-   Klucz rejestru jest tylko do odczytu.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Jest bardziej bezpieczne można zapisać danych do folderu użytkownika — `Microsoft.Win32.Registry.CurrentUser` , a nie na komputerze lokalnym — `Microsoft.Win32.Registry.LocalMachine`.  
  
 Po utworzeniu wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje. Inny proces, możliwe, że złośliwe jeden mogły już zostać utworzone wartość i jest do niego dostęp. Po umieszczeniu danych w wartości rejestru, dane są dostępne do innego procesu. Aby tego uniknąć, należy użyć.`Overload:Microsoft.Win32.RegistryKey.GetValue` Metoda. Zwraca wartość null, jeśli klucz jeszcze nie istnieje.  
  
 Nie jest bezpieczny do przechowywania kluczy tajnych, takie jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy kontroli dostępu (ACL).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO?displayProperty=nameWithType>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [System plików i rejestr (C# przewodnik programowania w języku)](../../../csharp/programming-guide/file-system/index.md)  
 [Odczytu, zapisu i usuwania z rejestru w języku C#](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
