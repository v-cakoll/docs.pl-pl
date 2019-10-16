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
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a><span data-ttu-id="3536f-102">Instrukcje: Tworzenie projektu nowego typu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3536f-102">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="3536f-103">W innych przykładach w tej sekcji przedstawiono zapytania, które zwracają wyniki jako <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> z `string` i <xref:System.Collections.Generic.IEnumerable%601> z `int`.</span><span class="sxs-lookup"><span data-stu-id="3536f-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="3536f-104">Są to typowe typy wyników, ale nie są one odpowiednie dla każdego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="3536f-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="3536f-105">W wielu przypadkach zapytania będą zwracać <xref:System.Collections.Generic.IEnumerable%601> innego typu.</span><span class="sxs-lookup"><span data-stu-id="3536f-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3536f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="3536f-106">Example</span></span>  
 <span data-ttu-id="3536f-107">Ten przykład pokazuje, jak utworzyć wystąpienie obiektów w klauzuli `Select`.</span><span class="sxs-lookup"><span data-stu-id="3536f-107">This example shows how to instantiate objects in the `Select` clause.</span></span> <span data-ttu-id="3536f-108">Kod najpierw definiuje nową klasę z konstruktorem, a następnie modyfikuje `Select` instrukcji tak, że wyrażenie jest nowym wystąpieniem nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="3536f-108">The code first defines a new class with a constructor, and then modifies the `Select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="3536f-109">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3536f-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="3536f-110">W tym przykładzie użyto metody `M:System.Xml.Linq.XElement.Element`, która została wprowadzona w temacie [jak: Pobieranie pojedynczego elementu podrzędnego (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3536f-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="3536f-111">Używa również rzutowania do pobrania wartości elementów, które są zwracane przez metodę `M:System.Xml.Linq.XElement.Element`.</span><span class="sxs-lookup"><span data-stu-id="3536f-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="3536f-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3536f-112">This example produces the following output:</span></span>  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="3536f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3536f-113">See also</span></span>

- [<span data-ttu-id="3536f-114">Projekcje i przekształcenia (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3536f-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
