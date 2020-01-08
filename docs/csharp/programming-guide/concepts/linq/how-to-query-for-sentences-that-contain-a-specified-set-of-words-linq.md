---
title: Jak wykonać zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: efb0eb60a9695c19e16b507d29ef6994e904cff9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347694"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a>Jak wykonać zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)
Ten przykład pokazuje, jak znaleźć zdania w pliku tekstowym zawierającym dopasowania dla każdego z określonych wyrazów. Mimo że tablica terminów wyszukiwania jest zakodowana w tym przykładzie, można ją również wypełnić dynamicznie w czasie wykonywania. W tym przykładzie zapytanie zwraca zdania zawierające słowa "historyczne", "dane" i "zintegrowane".  
  
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
  
 Zapytanie działa przez pierwsze dzielenie tekstu na zdania, a następnie dzielenie zdań na tablicę ciągów, które zawierają każdy wyraz. Dla każdej z tych tablic Metoda <xref:System.Linq.Enumerable.Distinct%2A> usuwa wszystkie zduplikowane wyrazy, a następnie wykonuje operację <xref:System.Linq.Enumerable.Intersect%2A> na tablicy słów i tablicy `wordsToMatch`. Jeśli liczba przecięć jest taka sama jak liczba tablicy `wordsToMatch`, wszystkie wyrazy zostały znalezione w wyrazach, a zdanie oryginalne zostanie zwrócone.  
  
 W wywołaniu do <xref:System.String.Split%2A>znaki interpunkcyjne są używane jako separatory w celu usunięcia ich z ciągu. Jeśli tego nie zrobiono, na przykład możesz mieć ciąg "historyczny", który nie pasuje do "historycznie" w tablicy `wordsToMatch`. Może być konieczne użycie dodatkowych separatorów, w zależności od typów znaków interpunkcyjnych znalezionych w tekście źródłowym.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. Linq i system.IO.

## <a name="see-also"></a>Zobacz także

- [LINQ i ciągi (C#)](./linq-and-strings.md)
