---
title: 'Porady: obliczanie wartości pośredniego (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
ms.openlocfilehash: e3aa54c365e90a11ac8c31e0bf7d901c5a4a6b96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642485"
---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a><span data-ttu-id="b594e-102">Porady: obliczanie wartości pośredniego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b594e-102">How to: Calculate Intermediate Values (Visual Basic)</span></span>
<span data-ttu-id="b594e-103">Ten przykład przedstawia sposób obliczania wartości pośrednich, które mogą być używane w sortowanie, filtrowanie i wybierając.</span><span class="sxs-lookup"><span data-stu-id="b594e-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b594e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b594e-104">Example</span></span>  
 <span data-ttu-id="b594e-105">W poniższym przykładzie użyto `Let` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b594e-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="b594e-106">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: dane liczbowe (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b594e-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim extensions As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
    Where extension > 25 _  
    Order By extension _  
    Select extension  
For Each ex As Decimal In extensions  
    Console.WriteLine(ex)  
Next  
```  
  
 <span data-ttu-id="b594e-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b594e-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="b594e-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="b594e-108">Example</span></span>  
 <span data-ttu-id="b594e-109">W poniższym przykładzie pokazano tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b594e-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="b594e-110">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="b594e-110">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="b594e-111">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: dane liczbowe w Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b594e-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns="http://www.adatum.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim extensions As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
            Where extension > 25 _  
            Order By extension _  
            Select extension  
        For Each ex As Decimal In extensions  
            Console.WriteLine(ex)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="b594e-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b594e-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="b594e-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b594e-113">See Also</span></span>  
 [<span data-ttu-id="b594e-114">Podstawowe zapytania (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b594e-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
