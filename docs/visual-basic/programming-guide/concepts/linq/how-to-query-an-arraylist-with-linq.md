---
title: 'Instrukcje: wykonywanie zapytań do ArrayList za pomocą LINQ (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: c9cc86c6f74c8edc628050c911474bf515784180
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320309"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>Instrukcje: wykonywanie zapytań do ArrayList za pomocą LINQ (Visual Basic)
Używając LINQ do wykonywania zapytań dotyczących nieogólnych kolekcji <xref:System.Collections.IEnumerable>, takich jak <xref:System.Collections.ArrayList>, należy jawnie zadeklarować typ zmiennej zakresu w celu odzwierciedlenia określonego typu obiektów w kolekcji. Jeśli na przykład masz <xref:System.Collections.ArrayList> obiektów `Student`, [klauzula FROM](../../../../visual-basic/language-reference/queries/from-clause.md) powinna wyglądać następująco:  
  
```vb  
Dim query = From student As Student In arrList   
'...  
```  
  
 Określając typ zmiennej zakresu, rzutuje każdy element w <xref:System.Collections.ArrayList> do `Student`.  
  
 Użycie jawnie wpisanej zmiennej zakresu w wyrażeniu zapytania jest równoznaczne z wywołaniem metody <xref:System.Linq.Enumerable.Cast%2A>. <xref:System.Linq.Enumerable.Cast%2A> zgłasza wyjątek, jeśli nie można wykonać określonego rzutowania. <xref:System.Linq.Enumerable.Cast%2A> i <xref:System.Linq.Enumerable.OfType%2A> to dwie metody standardowego operatora zapytań, które działają na nieogólnych typach <xref:System.Collections.IEnumerable>. W Visual Basic należy jawnie wywołać metodę <xref:System.Linq.Enumerable.Cast%2A> w źródle danych, aby upewnić się, że określony typ zmiennej zakresu. Aby uzyskać więcej informacji, zobacz [relacje typu w operacjach zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano proste zapytanie dla <xref:System.Collections.ArrayList>. Należy zauważyć, że w tym przykładzie są używane Inicjatory obiektów, gdy kod wywołuje metodę <xref:System.Collections.ArrayList.Add%2A>, ale nie jest to wymagane.  
  
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
