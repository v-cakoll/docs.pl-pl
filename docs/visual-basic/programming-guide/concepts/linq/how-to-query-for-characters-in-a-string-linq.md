---
title: 'Instrukcje: Zapytanie o znaki w ciągu (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: 3a4f3bbca313747e0b16170719b9028e5dc9174f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559752"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="b266e-102">Instrukcje: Zapytanie o znaki w ciągu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b266e-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="b266e-103">Ponieważ <xref:System.String> klasa implementuje ogólnego <xref:System.Collections.Generic.IEnumerable%601> interfejsu, dowolny ciąg może być odpytywany za pomocą sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="b266e-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="b266e-104">Jednak to nie jest typowym zastosowaniem LINQ.</span><span class="sxs-lookup"><span data-stu-id="b266e-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="b266e-105">Złożone celu dopasowania do wzorca operacji, należy użyć <xref:System.Text.RegularExpressions.Regex> klasy.</span><span class="sxs-lookup"><span data-stu-id="b266e-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b266e-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b266e-106">Example</span></span>  
 <span data-ttu-id="b266e-107">Poniższy przykład wykonuje kwerendę ciągu, aby określić liczbę cyfr, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="b266e-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="b266e-108">Należy pamiętać, że zapytanie jest "ponownie" po wykonaniu po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="b266e-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="b266e-109">Jest to możliwe, ponieważ samo zapytanie nie zapisuje żadnych rzeczywistych wyników.</span><span class="sxs-lookup"><span data-stu-id="b266e-109">This is possible because the query itself does not store any actual results.</span></span>  
  
```vb  
Class QueryAString  
  
    Shared Sub Main()  
  
        ' A string is an IEnumerable data source.  
        Dim aString As String = "ABCDE99F-J74-12-89A"  
  
        ' Select only those characters that are numbers  
        Dim stringQuery = From ch In aString   
                          Where Char.IsDigit(ch)   
                          Select ch  
        ' Execute the query  
        For Each c As Char In stringQuery  
            Console.Write(c & " ")  
        Next  
  
        ' Call the Count method on the existing query.  
        Dim count As Integer = stringQuery.Count()  
        Console.WriteLine(System.Environment.NewLine & "Count = " & count)  
  
        ' Select all characters before the first '-'  
        Dim stringQuery2 = aString.TakeWhile(Function(c) c <> "-")  
  
        ' Execute the second query  
        For Each ch In stringQuery2  
            Console.Write(ch)  
        Next  
  
        Console.WriteLine(System.Environment.NewLine & "Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 9 9 7 4 1 2 8 9   
' Count = 8  
' ABCDE99F  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b266e-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b266e-110">Compiling the Code</span></span>  
 <span data-ttu-id="b266e-111">Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji dla przestrzeni nazw System.Linq.</span><span class="sxs-lookup"><span data-stu-id="b266e-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b266e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b266e-112">See also</span></span>
- [<span data-ttu-id="b266e-113">LINQ i ciągi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b266e-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="b266e-114">Instrukcje: Łączenie zapytań LINQ z wyrażeniami regularnymi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b266e-114">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
