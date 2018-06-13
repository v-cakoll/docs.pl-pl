---
title: 'Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: 736078ccf97ba3e61748932c3e48fb436b2c5564
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319887"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="226ba-102">Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="226ba-102">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>
<span data-ttu-id="226ba-103">W tym przykładzie pokazano, jak można znaleźć w pliku tekstowym, która zawiera dopasowań dla każdego określony zestaw wyrazów zdań.</span><span class="sxs-lookup"><span data-stu-id="226ba-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="226ba-104">Tablica terminy wyszukiwania ma ustalony w tym przykładzie, ale jego można również można wypełnić dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="226ba-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="226ba-105">W tym przykładzie zapytanie zwraca zdania zawierające słowa "Historycznie", "dane" i "zintegrowane".</span><span class="sxs-lookup"><span data-stu-id="226ba-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="226ba-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="226ba-106">Example</span></span>  
  
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
  
 <span data-ttu-id="226ba-107">Zapytanie działa najpierw podziału tekstu do zdań, a następnie Podziel zdania na tablicę ciągów zawierających każdego wyrazu.</span><span class="sxs-lookup"><span data-stu-id="226ba-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="226ba-108">Dla każdego z tych tablic <xref:System.Linq.Enumerable.Distinct%2A> metoda usuwa wszystkie zduplikowane słowa, a następnie wykonuje zapytanie <xref:System.Linq.Enumerable.Intersect%2A> operacji na tablicy programu word i `wordsToMatch` tablicy.</span><span class="sxs-lookup"><span data-stu-id="226ba-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="226ba-109">Jeśli liczba przecięcie jest taka sama jak liczba `wordsToMatch` tablicy, nie znaleziono wszystkich wyrazów w wyrazy i zdanie oryginalna jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="226ba-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="226ba-110">W wywołaniu <xref:System.String.Split%2A>, aby można było je usunąć z ciągu służą jako separatorów znaków interpunkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="226ba-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="226ba-111">Jeśli nie zrobisz, na przykład można używać ciągu "W przeszłości", który będzie niezgodny "W przeszłości" w `wordsToMatch` tablicy.</span><span class="sxs-lookup"><span data-stu-id="226ba-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="226ba-112">Użytkownik może być konieczne użycie dodatkowych separatorów, w zależności od typów znaków interpunkcyjnych, zazwyczaj w tekstach źródła.</span><span class="sxs-lookup"><span data-stu-id="226ba-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="226ba-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="226ba-113">Compiling the Code</span></span>  
 <span data-ttu-id="226ba-114">Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.</span><span class="sxs-lookup"><span data-stu-id="226ba-114">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226ba-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="226ba-115">See Also</span></span>  
 [<span data-ttu-id="226ba-116">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="226ba-116">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
