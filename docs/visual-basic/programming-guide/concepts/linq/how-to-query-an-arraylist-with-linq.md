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
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>Instrukcje: Zapytanie w ArrayList za pomocą LINQ (Visual Basic)
Gdy za pomocą LINQ do kwerendy nieogólnego <xref:System.Collections.IEnumerable> kolekcji, takie jak <xref:System.Collections.ArrayList>, należy jawnie zadeklarować rodzaj zmiennej zakresu w celu odzwierciedlenia określonego typu obiektów w kolekcji. Na przykład, jeśli masz <xref:System.Collections.ArrayList> z `Student` obiektów, Twoje [klauzuli From](../../../../visual-basic/language-reference/queries/from-clause.md) powinien wyglądać następująco:  
  
```  
Dim query = From student As Student In arrList   
...  
```  
  
 Przez określenie typu zmiennej zakresu, są rzutowanie każdego elementu w <xref:System.Collections.ArrayList> do `Student`.  
  
 Użycie zmiennej zakresu jawnie wpisanych w wyrażeniu zapytania jest równoważne z wywoływaniem <xref:System.Linq.Enumerable.Cast%2A> metody. <xref:System.Linq.Enumerable.Cast%2A> zgłasza wyjątek, jeśli nie można wykonać określone rzutowanie. <xref:System.Linq.Enumerable.Cast%2A> i <xref:System.Linq.Enumerable.OfType%2A> są dwie metody standardowej kwerendy operatora, które działają w nieogólnej <xref:System.Collections.IEnumerable> typów. W języku Visual Basic należy jawnie wywołać <xref:System.Linq.Enumerable.Cast%2A> metody w źródle danych, aby upewnić się, typu zmiennej zakresu określonego. Aby uzyskać więcej informacji, zobacz [relacje typu w operacjach zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia proste zapytanie <xref:System.Collections.ArrayList>. Należy pamiętać, że w tym przykładzie używa inicjatorów obiektów, gdy kod wywołuje <xref:System.Collections.ArrayList.Add%2A> metody, ale nie jest wymagane.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
