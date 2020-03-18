---
title: Jak znaleźć różnicę między dwiema listami (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 03fae5451ee395487e73ed7c38d465c3f891e0f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169184"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="0aa17-102">Jak znaleźć różnicę między dwiema listami (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="0aa17-102">How to find the set difference between two lists (LINQ) (C#)</span></span>
<span data-ttu-id="0aa17-103">W tym przykładzie pokazano, jak użyć LINQ do porównania dwóch list ciągów i wyjmować te wiersze, które są w names1.txt, ale nie w names2.txt.</span><span class="sxs-lookup"><span data-stu-id="0aa17-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="0aa17-104">Aby utworzyć pliki danych</span><span class="sxs-lookup"><span data-stu-id="0aa17-104">To create the data files</span></span>  
  
1. <span data-ttu-id="0aa17-105">Skopiuj names1.txt i names2.txt do folderu rozwiązania, jak pokazano w [jak połączyć i porównać kolekcje ciągów (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span><span class="sxs-lookup"><span data-stu-id="0aa17-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to combine and compare string collections (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0aa17-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="0aa17-106">Example</span></span>  
  
```csharp  
class CompareLists  
{
    static void Main()  
    {  
        // Create the IEnumerable data sources.  
        string[] names1 = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] names2 = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Create the query. Note that method syntax must be used here.  
        IEnumerable<string> differenceQuery =  
          names1.Except(names2);  
  
        // Execute the query.  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt");  
        foreach (string s in differenceQuery)  
            Console.WriteLine(s);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
     The following lines are in names1.txt but not names2.txt  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
     */  
```  
  
 <span data-ttu-id="0aa17-107">Niektóre typy operacji kwerend w języku <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Union%2A>C#, takie jak <xref:System.Linq.Enumerable.Concat%2A> <xref:System.Linq.Enumerable.Except%2A>, , , i , mogą być wyrażone tylko w składni opartej na metodach.</span><span class="sxs-lookup"><span data-stu-id="0aa17-107">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0aa17-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0aa17-108">Compiling the Code</span></span>  
 <span data-ttu-id="0aa17-109">Utwórz projekt aplikacji konsoli `using` C# z dyrektywami dla system.Linq i System.IO przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0aa17-109">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa17-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0aa17-110">See also</span></span>

- [<span data-ttu-id="0aa17-111">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="0aa17-111">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
