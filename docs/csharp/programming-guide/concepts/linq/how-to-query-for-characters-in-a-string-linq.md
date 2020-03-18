---
title: Jak wysyłać zapytania o znaki w ciągu (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: d85e488a38a6167505732103b4c540cade6ea9bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345680"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="59b6d-102">Jak wysyłać zapytania o znaki w ciągu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="59b6d-102">How to query for characters in a string (LINQ) (C#)</span></span>
<span data-ttu-id="59b6d-103">Ponieważ <xref:System.String> klasa implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejs ogólny, każdy ciąg można zbadać jako sekwencję znaków.</span><span class="sxs-lookup"><span data-stu-id="59b6d-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="59b6d-104">Jednak nie jest to powszechne zastosowanie LINQ.</span><span class="sxs-lookup"><span data-stu-id="59b6d-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="59b6d-105">W przypadku operacji dopasowywania wzorców złożonych należy użyć <xref:System.Text.RegularExpressions.Regex> klasy.</span><span class="sxs-lookup"><span data-stu-id="59b6d-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59b6d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="59b6d-106">Example</span></span>  
 <span data-ttu-id="59b6d-107">Poniższy przykład kwerendy ciąg, aby określić liczbę cyfr, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="59b6d-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="59b6d-108">Należy zauważyć, że kwerenda jest "ponownie używane" po wykonaniu po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="59b6d-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="59b6d-109">Jest to możliwe, ponieważ sama kwerenda nie przechowuje żadnych rzeczywistych wyników.</span><span class="sxs-lookup"><span data-stu-id="59b6d-109">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="59b6d-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="59b6d-110">Compiling the Code</span></span>  
 <span data-ttu-id="59b6d-111">Utwórz projekt aplikacji konsoli `using` C# z dyrektywami dla system.Linq i System.IO przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="59b6d-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b6d-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59b6d-112">See also</span></span>

- [<span data-ttu-id="59b6d-113">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="59b6d-113">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="59b6d-114">Jak połączyć zapytania LINQ z wyrażeniami regularnymi (C#)</span><span class="sxs-lookup"><span data-stu-id="59b6d-114">How to combine LINQ queries with regular expressions (C#)</span></span>](./how-to-combine-linq-queries-with-regular-expressions.md)
