---
title: 'Instrukcje: Zapytanie w ArrayList za pomocą LINQ (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: 5e1a7e84c8f8789edb3f0c867986d5a5e27674c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669032"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a><span data-ttu-id="5fa5a-102">Instrukcje: Zapytanie w ArrayList za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fa5a-102">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>
<span data-ttu-id="5fa5a-103">Gdy za pomocą LINQ do kwerendy nieogólnego <xref:System.Collections.IEnumerable> kolekcji, takie jak <xref:System.Collections.ArrayList>, należy jawnie zadeklarować rodzaj zmiennej zakresu w celu odzwierciedlenia określonego typu obiektów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5fa5a-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="5fa5a-104">Na przykład, jeśli masz <xref:System.Collections.ArrayList> z `Student` obiektów, Twoje [klauzuli From](../../../../visual-basic/language-reference/queries/from-clause.md) powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="5fa5a-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md) should look like this:</span></span>  
  
```  
Dim query = From student As Student In arrList   
...  
```  
  
 <span data-ttu-id="5fa5a-105">Przez określenie typu zmiennej zakresu, są rzutowanie każdego elementu w <xref:System.Collections.ArrayList> do `Student`.</span><span class="sxs-lookup"><span data-stu-id="5fa5a-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="5fa5a-106">Użycie zmiennej zakresu jawnie wpisanych w wyrażeniu zapytania jest równoważne z wywoływaniem <xref:System.Linq.Enumerable.Cast%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5fa5a-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="5fa5a-107"><xref:System.Linq.Enumerable.Cast%2A> zgłasza wyjątek, jeśli nie można wykonać określone rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="5fa5a-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="5fa5a-108"><xref:System.Linq.Enumerable.Cast%2A> i <xref:System.Linq.Enumerable.OfType%2A> są dwie metody standardowej kwerendy operatora, które działają w nieogólnej <xref:System.Collections.IEnumerable> typów.</span><span class="sxs-lookup"><span data-stu-id="5fa5a-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="5fa5a-109">W języku Visual Basic należy jawnie wywołać <xref:System.Linq.Enumerable.Cast%2A> metody w źródle danych, aby upewnić się, typu zmiennej zakresu określonego.</span><span class="sxs-lookup"><span data-stu-id="5fa5a-109">In Visual Basic, you must explicitly call the <xref:System.Linq.Enumerable.Cast%2A> method on the data source to ensure a specific range variable type.</span></span> <span data-ttu-id="5fa5a-110">Aby uzyskać więcej informacji, zobacz [relacje typu w operacjach zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="5fa5a-110">For more information, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fa5a-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fa5a-111">Example</span></span>  
 <span data-ttu-id="5fa5a-112">Poniższy przykład przedstawia proste zapytanie <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="5fa5a-112">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="5fa5a-113">Należy pamiętać, że w tym przykładzie używa inicjatorów obiektów, gdy kod wywołuje <xref:System.Collections.ArrayList.Add%2A> metody, ale nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="5fa5a-113">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
```vb  
Imports System.Collections  
Imports System.Linq  
  
Module Module1  
  
    Public Class Student  
        Public Property FirstName As String  
        Public Property LastName As String  
        Public Property Scores As Integer()  
    End Class  
  
    Sub Main()  
  
        Dim student1 As New Student With {.FirstName = "Svetlana",   
                                     .LastName = "Omelchenko",   
                                     .Scores = New Integer() {98, 92, 81, 60}}  
        Dim student2 As New Student With {.FirstName = "Claire",   
                                    .LastName = "O'Donnell",   
                                    .Scores = New Integer() {75, 84, 91, 39}}  
        Dim student3 As New Student With {.FirstName = "Cesar",   
                                    .LastName = "Garcia",   
                                    .Scores = New Integer() {97, 89, 85, 82}}  
        Dim student4 As New Student With {.FirstName = "Sven",   
                                    .LastName = "Mortensen",   
                                    .Scores = New Integer() {88, 94, 65, 91}}  
  
        Dim arrList As New ArrayList()  
        arrList.Add(student1)  
        arrList.Add(student2)  
        arrList.Add(student3)  
        arrList.Add(student4)  
  
        ' Use an explicit type for non-generic collections  
        Dim query = From student As Student In arrList   
                    Where student.Scores(0) > 95   
                    Select student  
  
        For Each student As Student In query  
            Console.WriteLine(student.LastName & ": " & student.Scores(0))  
        Next  
        ' Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Module  
' Output:  
'   Omelchenko: 98  
'   Garcia: 97  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fa5a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fa5a-114">See also</span></span>
- [<span data-ttu-id="5fa5a-115">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fa5a-115">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
