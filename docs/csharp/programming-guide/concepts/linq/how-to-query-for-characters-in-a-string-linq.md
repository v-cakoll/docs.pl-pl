---
title: 'Instrukcje: Zapytanie o znaki w ciągu (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: 0c577fc2dc2ae07574580f819a6fb51336107dfb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665633"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="2442b-102">Instrukcje: Zapytanie o znaki w ciągu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2442b-102">How to: Query for Characters in a String (LINQ) (C#)</span></span>
<span data-ttu-id="2442b-103">Ponieważ <xref:System.String> klasa implementuje ogólnego <xref:System.Collections.Generic.IEnumerable%601> interfejsu, dowolny ciąg może być odpytywany za pomocą sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="2442b-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="2442b-104">Jednak to nie jest typowym zastosowaniem LINQ.</span><span class="sxs-lookup"><span data-stu-id="2442b-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="2442b-105">Złożone celu dopasowania do wzorca operacji, należy użyć <xref:System.Text.RegularExpressions.Regex> klasy.</span><span class="sxs-lookup"><span data-stu-id="2442b-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2442b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="2442b-106">Example</span></span>  
 <span data-ttu-id="2442b-107">Poniższy przykład wykonuje kwerendę ciągu, aby określić liczbę cyfr, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="2442b-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="2442b-108">Należy pamiętać, że zapytanie jest "ponownie" po wykonaniu po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="2442b-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="2442b-109">Jest to możliwe, ponieważ samo zapytanie nie zapisuje żadnych rzeczywistych wyników.</span><span class="sxs-lookup"><span data-stu-id="2442b-109">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="2442b-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2442b-110">Compiling the Code</span></span>  
 <span data-ttu-id="2442b-111">Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego, za pomocą odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.</span><span class="sxs-lookup"><span data-stu-id="2442b-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2442b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2442b-112">See also</span></span>

- [<span data-ttu-id="2442b-113">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="2442b-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="2442b-114">Instrukcje: Łączenie zapytań LINQ z wyrażeniami regularnymi (C#)</span><span class="sxs-lookup"><span data-stu-id="2442b-114">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
