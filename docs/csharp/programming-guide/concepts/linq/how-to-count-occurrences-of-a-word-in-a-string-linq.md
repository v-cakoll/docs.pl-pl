---
title: 'Instrukcje: Liczenie wystąpień wyrazu w ciągu (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
ms.openlocfilehash: 12118c6322df0cfb93cb3d4a4dbbc02d68a0c776
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593917"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a><span data-ttu-id="f148f-102">Instrukcje: Liczenie wystąpień wyrazu w ciągu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f148f-102">How to: Count Occurrences of a Word in a String (LINQ) (C#)</span></span>
<span data-ttu-id="f148f-103">Ten przykład pokazuje, jak używać zapytania LINQ do zliczania wystąpień określonego wyrazu w ciągu.</span><span class="sxs-lookup"><span data-stu-id="f148f-103">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="f148f-104">Należy pamiętać, że aby wykonać licznik, najpierw <xref:System.String.Split%2A> wywoływana jest metoda, aby utworzyć tablicę wyrazów.</span><span class="sxs-lookup"><span data-stu-id="f148f-104">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="f148f-105"><xref:System.String.Split%2A> Metoda jest kosztem wydajności.</span><span class="sxs-lookup"><span data-stu-id="f148f-105">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="f148f-106">Jeśli jedyną operacją na ciągu jest Liczenie wyrazów, należy rozważyć użycie <xref:System.Text.RegularExpressions.Regex.Matches%2A> metod lub. <xref:System.String.IndexOf%2A></span><span class="sxs-lookup"><span data-stu-id="f148f-106">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="f148f-107">Jeśli jednak wydajność nie jest problemem krytycznym lub zostało już podzielone zdanie w celu wykonywania innych typów zapytań na nim, warto użyć LINQ do zliczania wyrazów lub fraz.</span><span class="sxs-lookup"><span data-stu-id="f148f-107">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f148f-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="f148f-108">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="f148f-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f148f-109">Compiling the Code</span></span>  
 <span data-ttu-id="f148f-110">Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. LINQ i system.IO.</span><span class="sxs-lookup"><span data-stu-id="f148f-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f148f-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f148f-111">See also</span></span>

- [<span data-ttu-id="f148f-112">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="f148f-112">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
