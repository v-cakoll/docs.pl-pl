---
title: "Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: befc93a21388a87fdfd2416349b1310e82378f18
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a>Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)
W tym przykładzie pokazano, jak można znaleźć w pliku tekstowym, która zawiera dopasowań dla każdego określony zestaw wyrazów zdań. Tablica terminy wyszukiwania ma ustalony w tym przykładzie, ale jego można również można wypełnić dynamicznie w czasie wykonywania. W tym przykładzie zapytanie zwraca zdania zawierające słowa "Historycznie", "dane" i "zintegrowane".  
  
## <a name="example"></a>Przykład  
  
```csharp  
class FindSentences  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects " +  
        @"have not been well integrated. Programmers work in C# or Visual Basic " +  
        @"and also in SQL or XQuery. On the one side are concepts such as classes, " +  
        @"objects, fields, inheritance, and .NET Framework APIs. On the other side " +  
        @"are tables, columns, rows, nodes, and separate languages for dealing with " +  
        @"them. Data types often require translation between the two worlds; there are " +  
        @"different standard functions. Because the object world has no notion of query, a " +  
        @"query can only be represented as a string without compile-time type checking or " +  
        @"IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " +  
        @"objects in memory is often tedious and error-prone.";  
  
        // Split the text block into an array of sentences.  
        string[] sentences = text.Split(new char[] { '.', '?', '!' });  
  
        // Define the search terms. This list could also be dynamically populated at runtime.  
        string[] wordsToMatch = { "Historically", "data", "integrated" };  
  
        // Find sentences that contain all the terms in the wordsToMatch array.  
        // Note that the number of terms to match is not specified at compile time.  
        var sentenceQuery = from sentence in sentences  
                            let w = sentence.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' },  
                                                    StringSplitOptions.RemoveEmptyEntries)  
                            where w.Distinct().Intersect(wordsToMatch).Count() == wordsToMatch.Count()  
                            select sentence;  
  
        // Execute the query. Note that you can explicitly type  
        // the iteration variable here even though sentenceQuery  
        // was implicitly typed.   
        foreach (string str in sentenceQuery)  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
Historically, the world of data and the world of objects have not been well integrated  
*/  
```  
  
 Zapytanie działa najpierw podziału tekstu do zdań, a następnie Podziel zdania na tablicę ciągów zawierających każdego wyrazu. Dla każdego z tych tablic <xref:System.Linq.Enumerable.Distinct%2A> metoda usuwa wszystkie zduplikowane słowa, a następnie wykonuje zapytanie <xref:System.Linq.Enumerable.Intersect%2A> operacji na tablicy programu word i `wordsToMatch` tablicy. Jeśli liczba przecięcie jest taka sama jak liczba `wordsToMatch` tablicy, nie znaleziono wszystkich wyrazów w wyrazy i zdanie oryginalna jest zwracana.  
  
 W wywołaniu <xref:System.String.Split%2A>, aby można było je usunąć z ciągu służą jako separatorów znaków interpunkcyjnych. Jeśli nie zrobisz, na przykład można używać ciągu "W przeszłości", który będzie niezgodny "W przeszłości" w `wordsToMatch` tablicy. Użytkownik może być konieczne użycie dodatkowych separatorów, w zależności od typów znaków interpunkcyjnych, zazwyczaj w tekstach źródła.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ i ciągi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
