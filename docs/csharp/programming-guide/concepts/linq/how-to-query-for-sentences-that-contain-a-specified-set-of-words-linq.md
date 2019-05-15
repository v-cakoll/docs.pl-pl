---
title: 'Instrukcje: Zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: 11f065594ed6b6c162ac95e0a1e6c502c1ad8de5
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584289"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="c195b-102">Instrukcje: Zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c195b-102">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>
<span data-ttu-id="c195b-103">W tym przykładzie pokazano, jak można znaleźć zdań w pliku tekstowym, które zawierają dopasowania dla każdego określony zestaw wyrazów.</span><span class="sxs-lookup"><span data-stu-id="c195b-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="c195b-104">Mimo że tablicy wyszukiwane terminy ustalone w tym przykładzie, jego można również są wypełnione dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c195b-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="c195b-105">W tym przykładzie zapytanie zwraca zdania zawierające słowa "Historycznie", "dane" i "zintegrowane".</span><span class="sxs-lookup"><span data-stu-id="c195b-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="c195b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c195b-106">Example</span></span>  
  
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
  
 <span data-ttu-id="c195b-107">Zapytanie działa najpierw dzieląc go na zdania, a następnie dzieląc zdania na tablicę ciągów, zawierających każdego wyrazu.</span><span class="sxs-lookup"><span data-stu-id="c195b-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="c195b-108">Dla każdego z tych tablic <xref:System.Linq.Enumerable.Distinct%2A> metoda usuwa wszystkie zduplikowane wyrazy, a następnie wykonuje zapytanie <xref:System.Linq.Enumerable.Intersect%2A> operacji na tablicy programu word i `wordsToMatch` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c195b-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="c195b-109">Jeśli liczba wspólną jest taka sama jak liczba `wordsToMatch` tablicy, wszystkie wyrazy zostały znalezione w wyrazy i zwracany jest oryginalne zdanie.</span><span class="sxs-lookup"><span data-stu-id="c195b-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="c195b-110">W wywołaniu <xref:System.String.Split%2A>, znaków interpunkcyjnych są używane jako separatory, aby można było je usunąć z ciągu.</span><span class="sxs-lookup"><span data-stu-id="c195b-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="c195b-111">Jeśli nie została, na przykład można mieć ciąg "W przeszłości", który nie będzie odpowiadać "W przeszłości" w `wordsToMatch` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c195b-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="c195b-112">Należy użyć dodatkowych separatory, w zależności od typów w tekście źródłowym znaleziono znaki interpunkcyjne.</span><span class="sxs-lookup"><span data-stu-id="c195b-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c195b-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c195b-113">Compiling the Code</span></span>  
<span data-ttu-id="c195b-114">Tworzenie C# konsoli projekt aplikacji z `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.</span><span class="sxs-lookup"><span data-stu-id="c195b-114">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="c195b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c195b-115">See also</span></span>

- [<span data-ttu-id="c195b-116">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="c195b-116">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
