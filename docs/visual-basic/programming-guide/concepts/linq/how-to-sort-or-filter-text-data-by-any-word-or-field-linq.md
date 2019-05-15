---
title: 'Instrukcje: Sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
ms.openlocfilehash: 5d6a8d26f28feafecfbddfb8d2b538adc22f1b90
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592461"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a><span data-ttu-id="e2d88-102">Instrukcje: Sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2d88-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="e2d88-103">Poniższy przykład pokazuje sposób sortowania wierszami strukturalnych, takie jak wartości rozdzielanych przecinkami, według dowolnego pola w wierszu.</span><span class="sxs-lookup"><span data-stu-id="e2d88-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="e2d88-104">Pole może być określana dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e2d88-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="e2d88-105">Załóżmy, że pola w scores.csv reprezentuje numer identyfikacyjny Studenta, następuje serię czterech wyniki testów.</span><span class="sxs-lookup"><span data-stu-id="e2d88-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="e2d88-106">Aby utworzyć plik zawierający dane</span><span class="sxs-lookup"><span data-stu-id="e2d88-106">To create a file that contains data</span></span>  
  
1. <span data-ttu-id="e2d88-107">Kopiowanie danych scores.csv z tematu [jak: Dołącz zawartość z niepodobnych plików (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) i zapisz go do folderu rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e2d88-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2d88-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2d88-108">Example</span></span>  
  
```vb  
Class SortLines  
  
    Shared Sub Main()  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' Change this to any value from 0 to 4  
        Dim sortField As Integer = 1  
  
        Console.WriteLine("Sorted highest to lowest by field " & sortField)  
  
        ' Demonstrates how to return query from a method.  
        ' The query is executed here.  
        For Each str As String In SortQuery(scores, sortField)  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    Shared Function SortQuery(  
        ByVal source As IEnumerable(Of String),   
        ByVal num As Integer) As IEnumerable(Of String)  
  
        Dim scoreQuery = From line In source   
                         Let fields = line.Split(New Char() {","})   
                         Order By fields(num) Descending   
                         Select line  
  
        Return scoreQuery  
    End Function  
End Class  
' Output:  
' Sorted highest to lowest by field 1  
' 116, 99, 86, 90, 94  
' 120, 99, 82, 81, 79  
' 111, 97, 92, 81, 60  
' 114, 97, 89, 85, 82  
' 121, 96, 85, 91, 60  
' 122, 94, 92, 91, 91  
' 117, 93, 92, 80, 87  
' 118, 92, 90, 83, 78  
' 113, 88, 94, 65, 91  
' 112, 75, 84, 91, 39  
' 119, 68, 79, 88, 92  
' 115, 35, 72, 91, 70  
```  
  
 <span data-ttu-id="e2d88-109">Ten przykład ilustruje też sposób zwracania zmiennej zapytania z funkcji.</span><span class="sxs-lookup"><span data-stu-id="e2d88-109">This example also demonstrates how to return a query variable from a Function.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e2d88-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e2d88-110">Compiling the Code</span></span>  
<span data-ttu-id="e2d88-111">Utwórz projekt aplikacji konsoli VB.NET, za pomocą `Imports` instrukcji dla przestrzeni nazw System.Linq.</span><span class="sxs-lookup"><span data-stu-id="e2d88-111">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e2d88-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2d88-112">See also</span></span>

- [<span data-ttu-id="e2d88-113">LINQ i ciągi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2d88-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
