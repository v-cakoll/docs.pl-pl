---
title: 'Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: 2d87a2bd882adb6eca144288ace72b0e7c464907
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829502"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a><span data-ttu-id="3f4c4-102">Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f4c4-102">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="3f4c4-103">W tym przykładzie pokazano, jak używać programu LINQ do porównywania dwóch list ciągów i danych wyjściowych tych wierszy, które są w names1.txt, ale nie w names2.txt.</span><span class="sxs-lookup"><span data-stu-id="3f4c4-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="3f4c4-104">Aby utworzyć pliki danych</span><span class="sxs-lookup"><span data-stu-id="3f4c4-104">To create the data files</span></span>  
  
1.  <span data-ttu-id="3f4c4-105">Skopiuj names1.txt i names2.txt do folderu rozwiązania, jak pokazano na [jak: Łączenie i porównywanie kolekcji ciągów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span><span class="sxs-lookup"><span data-stu-id="3f4c4-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to: Combine and Compare String Collections (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f4c4-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f4c4-106">Example</span></span>  
  
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
  
 <span data-ttu-id="3f4c4-107">Niektóre typy zapytań operacji w języku Visual Basic, takie jak <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, i <xref:System.Linq.Enumerable.Concat%2A>, tylko mogą być wyrażone w składni oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="3f4c4-107">Some types of query operations in Visual Basic, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3f4c4-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3f4c4-108">Compiling the Code</span></span>  
 <span data-ttu-id="3f4c4-109">Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji dla przestrzeni nazw System.Linq.</span><span class="sxs-lookup"><span data-stu-id="3f4c4-109">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f4c4-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f4c4-110">See also</span></span>

- [<span data-ttu-id="3f4c4-111">LINQ i ciągi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f4c4-111">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
