---
title: 'Instrukcje: Projektowanie nowego typu (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: 5d0679c3c6f1fa26408905799f5b7a5d0cef6266
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592101"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a><span data-ttu-id="3a753-102">Instrukcje: Projektowanie nowego typu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a753-102">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="3a753-103">Inne przykłady w tej sekcji wykazały zapytań, które zwracają wyniki w postaci <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> z `string`, i <xref:System.Collections.Generic.IEnumerable%601> z `int`.</span><span class="sxs-lookup"><span data-stu-id="3a753-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="3a753-104">Są to typowe typy wyników, ale nie są odpowiednie dla każdego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="3a753-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="3a753-105">W wielu przypadkach można zapytania do zwrócenia <xref:System.Collections.Generic.IEnumerable%601> z innego typu.</span><span class="sxs-lookup"><span data-stu-id="3a753-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a753-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a753-106">Example</span></span>  
 <span data-ttu-id="3a753-107">W tym przykładzie przedstawiono sposób tworzenia wystąpień obiektów w `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3a753-107">This example shows how to instantiate objects in the `Select` clause.</span></span> <span data-ttu-id="3a753-108">Ten kod najpierw definiuje nową klasę za pomocą konstruktora, a następnie modyfikuje `Select` instrukcji, aby wyrażenie jest nowe wystąpienie klasy nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="3a753-108">The code first defines a new class with a constructor, and then modifies the `Select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="3a753-109">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3a753-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="3a753-110">W tym przykładzie użyto `M:System.Xml.Linq.XElement.Element` metody, która została wprowadzona w temacie [jak: Pobierz jeden typ elementów podrzędnych (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3a753-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="3a753-111">Korzysta również rzutowania można pobrać wartości elementów, które są zwracane przez `M:System.Xml.Linq.XElement.Element` metody.</span><span class="sxs-lookup"><span data-stu-id="3a753-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="3a753-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3a753-112">This example produces the following output:</span></span>  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a753-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a753-113">See also</span></span>
- [<span data-ttu-id="3a753-114">Projekcje i przekształcenia (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a753-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
