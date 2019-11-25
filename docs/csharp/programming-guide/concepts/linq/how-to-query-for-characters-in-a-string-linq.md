---
title: 'Instrukcje: zapytanie o znaki w ciągu (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: bc72c4370ff408a60f48aa020a16dae7f48f702a
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140960"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="f8e9b-102">Instrukcje: zapytanie o znaki w ciągu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f8e9b-102">How to: Query for Characters in a String (LINQ) (C#)</span></span>
<span data-ttu-id="f8e9b-103">Ponieważ Klasa <xref:System.String> implementuje ogólny interfejs <xref:System.Collections.Generic.IEnumerable%601>, każdy ciąg może być badany jako sekwencja znaków.</span><span class="sxs-lookup"><span data-stu-id="f8e9b-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="f8e9b-104">Nie jest to jednak powszechne użycie LINQ.</span><span class="sxs-lookup"><span data-stu-id="f8e9b-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="f8e9b-105">W przypadku złożonych operacji dopasowania do wzorca Użyj klasy <xref:System.Text.RegularExpressions.Regex>.</span><span class="sxs-lookup"><span data-stu-id="f8e9b-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8e9b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8e9b-106">Example</span></span>  
 <span data-ttu-id="f8e9b-107">Poniższy przykład wysyła zapytanie do ciągu, aby określić liczbę cyfr, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="f8e9b-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="f8e9b-108">Należy pamiętać, że zapytanie jest "ponownie używane" po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="f8e9b-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="f8e9b-109">Jest to możliwe, ponieważ samo zapytanie nie przechowuje żadnych rzeczywistych wyników.</span><span class="sxs-lookup"><span data-stu-id="f8e9b-109">This is possible because the query itself does not store any actual results.</span></span>  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8e9b-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f8e9b-110">Compiling the Code</span></span>  
 <span data-ttu-id="f8e9b-111">Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. Linq i system.IO.</span><span class="sxs-lookup"><span data-stu-id="f8e9b-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8e9b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8e9b-112">See also</span></span>

- [<span data-ttu-id="f8e9b-113">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="f8e9b-113">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="f8e9b-114">Jak połączyć zapytania LINQ z wyrażeniami regularnymiC#()</span><span class="sxs-lookup"><span data-stu-id="f8e9b-114">How to combine LINQ queries with regular expressions (C#)</span></span>](./how-to-combine-linq-queries-with-regular-expressions.md)
