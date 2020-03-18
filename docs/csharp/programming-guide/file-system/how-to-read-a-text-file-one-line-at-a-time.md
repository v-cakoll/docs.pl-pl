---
title: Jak czytać plik tekstowy po jednym wierszu naraz - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: e4a9ba2da2548991f442c2f5ab09d39243137875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167520"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a>Jak czytać plik tekstowy po jednym wierszu naraz (Przewodnik programowania C#)
W tym przykładzie odczytuje zawartość pliku tekstowego, jeden wiersz na `ReadLine` raz, `StreamReader` do ciągu przy użyciu metody klasy. Każdy wiersz tekstu jest `line` zapisywany w ciągu i wyświetlany na ekranie.  
  
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
 Skopiuj kod i `Main` wklej go do metody aplikacji konsoli.  
  
 Zamień `"c:\test.txt"` na rzeczywistą nazwę pliku.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Plik może nie istnieć.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik `myFile.cs` może nie być plikiem źródłowym Języka C#.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania języka C#](../index.md)
- [System plików i rejestr (Przewodnik programowania w języku C#)](./index.md)
