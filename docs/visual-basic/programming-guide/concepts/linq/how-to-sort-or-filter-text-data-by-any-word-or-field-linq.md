---
title: 'Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
ms.openlocfilehash: 0e27a72fcb5789ac9a067091aeb150d33f646708
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a><span data-ttu-id="a9ca9-102">Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9ca9-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="a9ca9-103">Poniższy przykład przedstawia sposób sortowania wierszy tekstu strukturalnych, takich jak wartości rozdzielanych przecinkami, przez którekolwiek z pól w wierszu.</span><span class="sxs-lookup"><span data-stu-id="a9ca9-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="a9ca9-104">Pole może być określana dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a9ca9-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="a9ca9-105">Załóżmy, że pola scores.csv reprezentują numer identyfikacyjny Studenta, następuje szereg cztery wyniki testów.</span><span class="sxs-lookup"><span data-stu-id="a9ca9-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="a9ca9-106">Aby utworzyć plik, który zawiera dane</span><span class="sxs-lookup"><span data-stu-id="a9ca9-106">To create a file that contains data</span></span>  
  
1.  <span data-ttu-id="a9ca9-107">Kopiowanie danych scores.csv z tematu [porady: Dołącz zawartości z niepodobnych plików (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) i zapisać ją w folderze rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a9ca9-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9ca9-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9ca9-108">Example</span></span>  
  
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
  
 <span data-ttu-id="a9ca9-109">Przykładzie przedstawiono również sposób zwracania zmiennej zapytania z funkcji.</span><span class="sxs-lookup"><span data-stu-id="a9ca9-109">This example also demonstrates how to return a query variable from a Function.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a9ca9-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a9ca9-110">Compiling the Code</span></span>  
 <span data-ttu-id="a9ca9-111">Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji System.Linq przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a9ca9-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ca9-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9ca9-112">See Also</span></span>  
 [<span data-ttu-id="a9ca9-113">LINQ i ciągi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9ca9-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
