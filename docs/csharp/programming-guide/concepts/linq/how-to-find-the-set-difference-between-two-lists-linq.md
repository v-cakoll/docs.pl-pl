---
title: 'Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: c8f01cb53665d01d4c7861bab758ecc9e0dcc3c8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585710"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a>Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (C#)
W tym przykładzie pokazano, jak używać programu LINQ do porównywania dwóch list ciągów i danych wyjściowych tych wierszy, które są w names1.txt, ale nie w names2.txt.  
  
### <a name="to-create-the-data-files"></a>Aby utworzyć pliki danych  
  
1. Skopiuj names1.txt i names2.txt do folderu rozwiązania, jak pokazano na [jak: Łączenie i porównywanie kolekcji ciągów (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).  
  
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
  
 Niektóre typy zapytań operacji w języku C#, takie jak <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, i <xref:System.Linq.Enumerable.Concat%2A>, tylko mogą być wyrażone w składni oparte na metodzie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie C# konsoli projekt aplikacji z `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ i ciągi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
