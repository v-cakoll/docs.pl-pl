---
title: "Porady: liczenie wystąpień słowa w ciągu (LINQ) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 56cfe11a0c559e64b11aad02ead3699c71cae2a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a>Porady: liczenie wystąpień słowa w ciągu (LINQ) (C#)
Ten przykład przedstawia sposób użycia zliczania wystąpień określonego słowa w ciągu zapytania LINQ. Należy pamiętać, że przeprowadzić licznik <xref:System.String.Split%2A> — metoda jest wywoływana w celu utworzenia tablicy słów. Brak koszt wydajności <xref:System.String.Split%2A> metody. Jeśli działanie tylko na ciąg Zliczanie wyrazów, należy rozważyć użycie <xref:System.Text.RegularExpressions.Regex.Matches%2A> lub <xref:System.String.IndexOf%2A> metody zamiast tego. Jednak jeśli wydajność nie ma problem krytyczny lub już został rozdzielony zdanie w celu wykonywania innych typów kwerend nad nim, następnie warto na potrzeby zliczania słów ani fraz również LINQ.  
  
## <a name="example"></a>Przykład  
  
```csharp  
class CountWords  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects" +  
          @" have not been well integrated. Programmers work in C# or Visual Basic" +  
          @" and also in SQL or XQuery. On the one side are concepts such as classes," +  
          @" objects, fields, inheritance, and .NET Framework APIs. On the other side" +  
          @" are tables, columns, rows, nodes, and separate languages for dealing with" +  
          @" them. Data types often require translation between the two worlds; there are" +  
          @" different standard functions. Because the object world has no notion of query, a" +  
          @" query can only be represented as a string without compile-time type checking or" +  
          @" IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" +  
          @" objects in memory is often tedious and error-prone.";  
  
        string searchTerm = "data";  
  
        //Convert the string into an array of words  
        string[] source = text.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' }, StringSplitOptions.RemoveEmptyEntries);  
  
        // Create the query.  Use ToLowerInvariant to match "data" and "Data"   
        var matchQuery = from word in source  
                         where word.ToLowerInvariant() == searchTerm.ToLowerInvariant()  
                         select word;  
  
        // Count the matches, which executes the query.  
        int wordCount = matchQuery.Count();  
        Console.WriteLine("{0} occurrences(s) of the search term \"{1}\" were found.", wordCount, searchTerm);  
  
        // Keep console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
   3 occurrences(s) of the search term "data" were found.  
*/  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ i ciągi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
