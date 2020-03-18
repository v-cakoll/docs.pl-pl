---
title: Jak wysyłać zapytania do zdań zawierających określony zestaw słów (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: df279f57d9965d796397cbcf7a0f3ba05bf9e5c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168859"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a>Jak wysyłać zapytania do zdań zawierających określony zestaw słów (LINQ) (C#)
W tym przykładzie pokazano, jak znaleźć zdania w pliku tekstowym, które zawierają dopasowania dla każdego z określonego zestawu słów. Mimo że tablica wyszukiwanych terminów jest zakodowana w tym przykładzie, może być również wypełniana dynamicznie w czasie wykonywania. W tym przykładzie kwerenda zwraca zdania zawierające słowa "Historycznie", "dane" i "zintegrowane".  
  
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
  
 Kwerenda działa najpierw dzieląc tekst na zdania, a następnie dzieląc zdania na tablicę ciągów, które zawierają każdy wyraz. Dla każdej z tych <xref:System.Linq.Enumerable.Distinct%2A> tablic metoda usuwa wszystkie zduplikowane wyrazy, a następnie kwerenda wykonuje operację <xref:System.Linq.Enumerable.Intersect%2A> na tablicy słów i tablicy. `wordsToMatch` Jeśli liczba przecięcia jest taka sama jak `wordsToMatch` liczba tablicy, wszystkie wyrazy zostały znalezione w słowach i oryginalne zdanie jest zwracany.  
  
 W wywołaniu <xref:System.String.Split%2A>, znaki interpunkcyjne są używane jako separatory w celu usunięcia ich z ciągu. Jeśli tego nie zrobisz, na przykład można mieć ciąg "Historycznie", który nie `wordsToMatch` pasuje "Historycznie" w tablicy. Może być konieczne użycie dodatkowych separatorów, w zależności od typów znaków interpunkcyjnych znalezionych w tekście źródłowym.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
Utwórz projekt aplikacji konsoli `using` C# z dyrektywami dla system.Linq i System.IO przestrzeni nazw.

## <a name="see-also"></a>Zobacz też

- [LINQ i ciągi (C#)](./linq-and-strings.md)
