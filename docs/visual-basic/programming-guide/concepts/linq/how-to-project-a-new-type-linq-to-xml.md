---
title: 'Instrukcje: Tworzenie projektu nowego typu (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: 64b563c57406caae7869905c417db9e6439e6157
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318370"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a>Instrukcje: Tworzenie projektu nowego typu (LINQ to XML) (Visual Basic)
W innych przykładach w tej sekcji przedstawiono zapytania, które zwracają wyniki jako <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> z `string` i <xref:System.Collections.Generic.IEnumerable%601> z `int`. Są to typowe typy wyników, ale nie są one odpowiednie dla każdego scenariusza. W wielu przypadkach zapytania będą zwracać <xref:System.Collections.Generic.IEnumerable%601> innego typu.  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak utworzyć wystąpienie obiektów w klauzuli `Select`. Kod najpierw definiuje nową klasę z konstruktorem, a następnie modyfikuje `Select` instrukcji tak, że wyrażenie jest nowym wystąpieniem nowej klasy.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
  
 W tym przykładzie użyto metody `M:System.Xml.Linq.XElement.Element`, która została wprowadzona w temacie [jak: Pobieranie pojedynczego elementu podrzędnego (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md). Używa również rzutowania do pobrania wartości elementów, które są zwracane przez metodę `M:System.Xml.Linq.XElement.Element`.  
  
 Ten przykład generuje następujące wyniki:  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Zobacz także

- [Projekcje i przekształcenia (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
