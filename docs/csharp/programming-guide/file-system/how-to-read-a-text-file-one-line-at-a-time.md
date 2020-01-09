---
title: Jak odczytać plik tekstowy po jednym wierszu w przewodniku C# programowania w czasie
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: a6af48cdacd836465d776a3fd4e1d17aa0298b77
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635343"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a>Jak czytać plik tekstowy po jednym wierszu (C# Przewodnik programowania)
Ten przykład odczytuje zawartość pliku tekstowego, po jednym wierszu w czasie, do ciągu przy użyciu metody `ReadLine` klasy `StreamReader`. Każdy wiersz tekstu jest przechowywany w ciągu `line` i wyświetlany na ekranie.  
  
## <a name="example"></a>Przykład  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =   
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj kod i wklej go do metody `Main` aplikacji konsolowej.  
  
 Zastąp `"c:\test.txt"` rzeczywistą nazwą pliku.  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Plik może nie istnieć.  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik `myFile.cs` nie może być plikiem C# źródłowym.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../index.md)
- [System plików i Rejestr (C# Przewodnik programowania)](./index.md)
