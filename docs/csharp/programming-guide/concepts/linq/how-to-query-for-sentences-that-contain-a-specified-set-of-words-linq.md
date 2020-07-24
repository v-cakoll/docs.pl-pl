---
title: Jak wykonać zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)
description: Dowiedz się, jak używać LINQ w języku C#, aby znaleźć zdania w pliku tekstowym zawierającym dopasowania dla każdego zestawu słów, które mogą być wypełnione w czasie wykonywania.
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: c334c7948f19fb857709ff04a83e1dae56fc69da
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104526"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="71244-103">Jak wykonać zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="71244-103">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>
<span data-ttu-id="71244-104">Ten przykład pokazuje, jak znaleźć zdania w pliku tekstowym zawierającym dopasowania dla każdego z określonych wyrazów.</span><span class="sxs-lookup"><span data-stu-id="71244-104">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="71244-105">Mimo że tablica terminów wyszukiwania jest zakodowana w tym przykładzie, można ją również wypełnić dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="71244-105">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="71244-106">W tym przykładzie zapytanie zwraca zdania zawierające słowa "historyczne", "dane" i "zintegrowane".</span><span class="sxs-lookup"><span data-stu-id="71244-106">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="71244-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="71244-107">Example</span></span>  
  
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
  
 <span data-ttu-id="71244-108">Zapytanie działa przez pierwsze dzielenie tekstu na zdania, a następnie dzielenie zdań na tablicę ciągów, które zawierają każdy wyraz.</span><span class="sxs-lookup"><span data-stu-id="71244-108">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="71244-109">Dla każdej z tych tablic <xref:System.Linq.Enumerable.Distinct%2A> Metoda powoduje usunięcie wszystkich zduplikowanych wyrazów, a następnie zapytanie wykonuje <xref:System.Linq.Enumerable.Intersect%2A> operację na tablicy słów i `wordsToMatch` tablicy.</span><span class="sxs-lookup"><span data-stu-id="71244-109">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="71244-110">Jeśli liczba przedziałów jest taka sama jak liczba `wordsToMatch` tablicy, wszystkie wyrazy zostały znalezione w wyrazach, a zdanie oryginalne zostanie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="71244-110">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="71244-111">W wywołaniu do <xref:System.String.Split%2A> , znaki interpunkcyjne są używane jako separatory w celu usunięcia ich z ciągu.</span><span class="sxs-lookup"><span data-stu-id="71244-111">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="71244-112">Jeśli tego nie zrobiono, na przykład możesz mieć ciąg "historyczny", który nie pasuje do "historycznie" w `wordsToMatch` tablicy.</span><span class="sxs-lookup"><span data-stu-id="71244-112">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="71244-113">Może być konieczne użycie dodatkowych separatorów, w zależności od typów znaków interpunkcyjnych znalezionych w tekście źródłowym.</span><span class="sxs-lookup"><span data-stu-id="71244-113">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="71244-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="71244-114">Compiling the Code</span></span>  
<span data-ttu-id="71244-115">Utwórz projekt aplikacji konsolowej w języku C# z `using` dyrektywami dotyczącymi przestrzeni nazw System. LINQ i system.IO.</span><span class="sxs-lookup"><span data-stu-id="71244-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="71244-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71244-116">See also</span></span>

- [<span data-ttu-id="71244-117">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="71244-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
