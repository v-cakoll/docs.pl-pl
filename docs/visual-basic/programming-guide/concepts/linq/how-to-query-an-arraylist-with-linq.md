---
title: "Porady: zapytanie w ArrayList za pomocą LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6740d8a7c6d4a31ccd3730249695c24c6417785d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a><span data-ttu-id="38bfd-102">Porady: zapytanie w ArrayList za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38bfd-102">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>
<span data-ttu-id="38bfd-103">W przypadku używania LINQ do zapytania nieogólnego <xref:System.Collections.IEnumerable> kolekcji, takie jak <xref:System.Collections.ArrayList>, musisz jawnie zadeklarować typu zmienną zakresu w celu odzwierciedlenia określonego typu obiektu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="38bfd-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="38bfd-104">Na przykład, jeśli masz <xref:System.Collections.ArrayList> z `Student` obiektów, z [klauzuli From](../../../../visual-basic/language-reference/queries/from-clause.md) powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="38bfd-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md) should look like this:</span></span>  
  
```  
Dim query = From student As Student In arrList   
...  
```  
  
 <span data-ttu-id="38bfd-105">Określenie typu zmiennej zakresu, są rzutowanie każdego elementu w <xref:System.Collections.ArrayList> do `Student`.</span><span class="sxs-lookup"><span data-stu-id="38bfd-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="38bfd-106">Użycie zmiennej zakresu jawnie typu w wyrażeniu zapytania jest odpowiednikiem wywołania <xref:System.Linq.Enumerable.Cast%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="38bfd-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="38bfd-107"><xref:System.Linq.Enumerable.Cast%2A>zgłasza wyjątek, jeśli nie można wykonać określone rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="38bfd-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="38bfd-108"><xref:System.Linq.Enumerable.Cast%2A>i <xref:System.Linq.Enumerable.OfType%2A> są dwie metody standardowe — Operator zapytań, które pracują na inny niż ogólny <xref:System.Collections.IEnumerable> typów.</span><span class="sxs-lookup"><span data-stu-id="38bfd-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="38bfd-109">W języku Visual Basic, należy jawnie wywołać <xref:System.Linq.Enumerable.Cast%2A> metody w źródle danych, aby upewnić się, typ zmiennej określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="38bfd-109">In Visual Basic, you must explicitly call the <xref:System.Linq.Enumerable.Cast%2A> method on the data source to ensure a specific range variable type.</span></span> <span data-ttu-id="38bfd-110">Aby uzyskać więcej informacji, zobacz[relacje typu w operacjach zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="38bfd-110">For more information, see[Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38bfd-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="38bfd-111">Example</span></span>  
 <span data-ttu-id="38bfd-112">W poniższym przykładzie przedstawiono prostego zapytania za pośrednictwem <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="38bfd-112">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="38bfd-113">Należy pamiętać, że w tym przykładzie użyto inicjatory obiektów, gdy kod wywołuje <xref:System.Collections.ArrayList.Add%2A> metody, ale nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="38bfd-113">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38bfd-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38bfd-114">See Also</span></span>  
 [<span data-ttu-id="38bfd-115">LINQ do obiektów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38bfd-115">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
