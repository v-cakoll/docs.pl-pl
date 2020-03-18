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
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a>Jak znaleźć różnicę między dwiema listami (LINQ) (C#)
W tym przykładzie pokazano, jak użyć LINQ do porównania dwóch list ciągów i wyjmować te wiersze, które są w names1.txt, ale nie w names2.txt.  
  
### <a name="to-create-the-data-files"></a>Aby utworzyć pliki danych  
  
1. Skopiuj names1.txt i names2.txt do folderu rozwiązania, jak pokazano w [jak połączyć i porównać kolekcje ciągów (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).  
  
## <a name="example"></a>Przykład  
  
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
  
 Niektóre typy operacji kwerend w języku <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Union%2A>C#, takie jak <xref:System.Linq.Enumerable.Concat%2A> <xref:System.Linq.Enumerable.Except%2A>, , , i , mogą być wyrażone tylko w składni opartej na metodach.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Utwórz projekt aplikacji konsoli `using` C# z dyrektywami dla system.Linq i System.IO przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ i ciągi (C#)](./linq-and-strings.md)
