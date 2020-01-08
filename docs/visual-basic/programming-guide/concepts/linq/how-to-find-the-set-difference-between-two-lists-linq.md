---
title: 'Porady: znajdowanie różnicy pomiędzy dwoma listami (LINQ)'
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: 42c5b5ee8a6af1323cb5eee12694fb94063eb877
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347511"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a>Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (Visual Basic)
Ten przykład pokazuje, jak używać LINQ do porównywania dwóch list ciągów i wyprowadzania tych wierszy w names1. txt, ale nie w names2. txt.  
  
### <a name="to-create-the-data-files"></a>Aby utworzyć pliki danych  
  
1. Skopiuj names1. txt i names2. txt do folderu rozwiązania, jak pokazano poniżej [: łączenie i porównywanie kolekcji ciągów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).  
  
## <a name="example"></a>Przykład  
  
```vb  
Class CompareLists  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data sources.  
        Dim names1 As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim names2 As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Create the query. Note that method syntax must be used here.  
        Dim differenceQuery = names1.Except(names2)  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt")  
  
        ' Execute the query.  
        For Each name As String In differenceQuery  
            Console.WriteLine(name)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' The following lines are in names1.txt but not names2.txt  
' Potra, Cristina  
' Noriega, Fabricio  
' Aw, Kam Foo  
' Toyoshima, Tim  
' Guy, Wey Yuan  
' Garcia, Debra  
```  
  
 Niektóre typy operacji zapytania w Visual Basic, takie jak <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>i <xref:System.Linq.Enumerable.Concat%2A>, mogą być wyrażone wyłącznie w składni opartej na metodzie.  
  
## <a name="compile-the-code"></a>Skompilować kod  
Utwórz projekt aplikacji konsolowej Visual Basic przy użyciu instrukcji `Imports` dla przestrzeni nazw System. LINQ.
  
## <a name="see-also"></a>Zobacz także

- [LINQ i ciągi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
