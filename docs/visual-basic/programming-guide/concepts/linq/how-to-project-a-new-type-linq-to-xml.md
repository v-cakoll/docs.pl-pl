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
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a><span data-ttu-id="5e31e-102">Instrukcje: Tworzenie projektu nowego typu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e31e-102">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="5e31e-103">W innych przykładach w tej sekcji przedstawiono zapytania, które zwracają wyniki w zakresie od, do <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> `string` i <xref:System.Collections.Generic.IEnumerable%601> `int` .</span><span class="sxs-lookup"><span data-stu-id="5e31e-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="5e31e-104">Są to typowe typy wyników, ale nie są one odpowiednie dla każdego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="5e31e-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="5e31e-105">W wielu przypadkach zapytania będą zwracały <xref:System.Collections.Generic.IEnumerable%601> Inne typy.</span><span class="sxs-lookup"><span data-stu-id="5e31e-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e31e-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e31e-106">Example</span></span>  
 <span data-ttu-id="5e31e-107">Ten przykład pokazuje, jak utworzyć wystąpienie obiektów w `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="5e31e-107">This example shows how to instantiate objects in the `Select` clause.</span></span> <span data-ttu-id="5e31e-108">Kod najpierw definiuje nową klasę z konstruktorem, a następnie modyfikuje `Select` instrukcję tak, aby wyrażenie było nowym wystąpieniem nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="5e31e-108">The code first defines a new class with a constructor, and then modifies the `Select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="5e31e-109">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5e31e-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="5e31e-110">W tym przykładzie użyto `M:System.Xml.Linq.XElement.Element` metody, która została wprowadzona w temacie [How to: Pobieranie pojedynczego elementu podrzędnego (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5e31e-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="5e31e-111">Używa również rzutowania do pobrania wartości elementów, które są zwracane przez `M:System.Xml.Linq.XElement.Element` metodę.</span><span class="sxs-lookup"><span data-stu-id="5e31e-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="5e31e-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="5e31e-112">This example produces the following output:</span></span>  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e31e-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e31e-113">See also</span></span>

- [<span data-ttu-id="5e31e-114">Projekcje i przekształcenia (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e31e-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
