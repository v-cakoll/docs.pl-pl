---
title: 'Instrukcje: projektowanie nowego typu (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: 48fb82e870a4fc4fa16cfb48a127f364e6d81f13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396509"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a>Instrukcje: Tworzenie projektu nowego typu (LINQ to XML) (Visual Basic)
W innych przykładach w tej sekcji przedstawiono zapytania, które zwracają wyniki w zakresie od, do <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> `string` i <xref:System.Collections.Generic.IEnumerable%601> `int` . Są to typowe typy wyników, ale nie są one odpowiednie dla każdego scenariusza. W wielu przypadkach zapytania będą zwracały <xref:System.Collections.Generic.IEnumerable%601> Inne typy.  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak utworzyć wystąpienie obiektów w `Select` klauzuli. Kod najpierw definiuje nową klasę z konstruktorem, a następnie modyfikuje `Select` instrukcję tak, aby wyrażenie było nowym wystąpieniem nowej klasy.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
  
 W tym przykładzie użyto `M:System.Xml.Linq.XElement.Element` metody, która została wprowadzona w temacie [How to: Pobieranie pojedynczego elementu podrzędnego (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-child-element-linq-to-xml.md). Używa również rzutowania do pobrania wartości elementów, które są zwracane przez `M:System.Xml.Linq.XElement.Element` metodę.  
  
 Ten przykład generuje następujące wyniki:  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Zobacz też

- [Projekcje i przekształcenia (LINQ to XML) (Visual Basic)](projections-and-transformations-linq-to-xml.md)
