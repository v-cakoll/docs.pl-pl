---
title: 'Porady: liczenie wystąpień wyrazu w ciągu (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
ms.openlocfilehash: 48eda99970744a659a803f52bb3a3c499390f5c8
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44352966"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a>Porady: liczenie wystąpień wyrazu w ciągu (LINQ) (C#)
W tym przykładzie pokazano, jak korzystać z zapytania LINQ można zliczać wystąpienia określonego wyrazu w ciągu. Należy pamiętać, że przeprowadzenie liczba <xref:System.String.Split%2A> metoda jest wywoływana, aby utworzyć tablicę słów. Występuje spadek wydajności, aby <xref:System.String.Split%2A> metody. W przypadku operacji tylko na ciąg do zliczania wyrazów, należy rozważyć użycie <xref:System.Text.RegularExpressions.Regex.Matches%2A> lub <xref:System.String.IndexOf%2A> metody zamiast tego. Jednak jeśli wydajność nie jest to problem krytyczny lub ma już Podziel zdania w celu wykonywania innych typów kwerend nad nim, następnie dobrym pomysłem liczba słów lub fraz, a także przy użyciu LINQ.  
  
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
 Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego, za pomocą odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ i ciągi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
