---
title: 'Porady: nowy typ (LINQ do XML) projektu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: da45c527ef9943cabf207a0b475a8a2114d5c6d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642045"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a>Porady: nowy typ (LINQ do XML) projektu (Visual Basic)
Inne przykłady w tej sekcji wykazały zapytań, które zwracają wyniki w postaci <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> z `string`, i <xref:System.Collections.Generic.IEnumerable%601> z `int`. Te są popularne typy wyników, ale nie są odpowiednie dla każdego scenariusza. W wielu przypadkach można zapytania do zwrócenia <xref:System.Collections.Generic.IEnumerable%601> z innego typu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób tworzenia wystąpienia obiektów w `Select` klauzuli. Kod najpierw definiuje nową klasę z konstruktorem, a następnie modyfikuje `Select` instrukcji, aby wyrażenie jest nowe wystąpienie klasy nowa klasa.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Public Class NameQty  
    Public name As String  
    Public qty As Integer  
    Public Sub New(ByVal n As String, ByVal q As Integer)  
        name = n  
        qty = q  
    End Sub  
End Class  
  
Public Class Program  
    Shared Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
  
        Dim nqList As IEnumerable(Of NameQty) = _  
            From n In po...<Item> _  
            Select New NameQty( _  
                n.<ProductName>.Value, CInt(n.<Quantity>.Value))  
  
        For Each n As NameQty In nqList  
            Console.WriteLine(n.name & ":" & n.qty)  
        Next  
    End Sub  
End Class  
```  
  
 W tym przykładzie użyto `M:System.Xml.Linq.XElement.Element` metodę, która została wprowadzona w temacie [porady: pobieranie pojedynczego elementu podrzędnego (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md). Ponadto użyto rzutowania można pobrać wartości elementów, które są zwracane przez `M:System.Xml.Linq.XElement.Element` metody.  
  
 Ten przykład generuje następujące wyniki:  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Projekcje i przekształcenia (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
