---
title: 'Porady: odczyt pliku tekstowego po jednym wierszu (Visual C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5e43251f29030b8f912b10ee7adb5a6492f2afad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a>Porady: odczyt pliku tekstowego po jednym wierszu (Visual C#)
Ten przykład odczytuje zawartość pliku tekstowego, jeden wiersz w czasie, w ciągu przy użyciu `ReadLine` metody `StreamReader` klasy. Każdy wiersz tekstu jest przechowywany w ciągu `line` i wyświetlane na ekranie.  
  
## <a name="example"></a>Przykład  
  
```  
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =   
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine (line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj kod i wklej ją do `Main` metoda aplikacji konsoli.  
  
 Zastąp `"c:\test.txt"` z rzeczywistą nazwę pliku.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Plik nie istnieje.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik `myFile.cs` nie może być pliku źródłowego C#.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO?displayProperty=nameWithType>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [System plików i rejestr (C# przewodnik programowania w języku)](../../../csharp/programming-guide/file-system/index.md)
