---
title: 'Instrukcje: Sortuj elementy (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c2c09279-6c8a-482e-8e71-b1453a815052
ms.openlocfilehash: f92d8ca36d1b322bb8d1538fd199e7256c982b85
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710483"
---
# <a name="how-to-sort-elements-visual-basic"></a><span data-ttu-id="22faa-102">Instrukcje: Sortuj elementy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22faa-102">How to: Sort Elements (Visual Basic)</span></span>
<span data-ttu-id="22faa-103">Ten przykład pokazuje, jak napisać zapytanie, które sortuje jego wyniki.</span><span class="sxs-lookup"><span data-stu-id="22faa-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22faa-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="22faa-104">Example</span></span>  
 <span data-ttu-id="22faa-105">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Dane liczbowe (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="22faa-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim prices As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let price = Convert.ToDecimal(el.<Price>.Value) _  
    Order By (price) _  
    Select price  
For Each el As Decimal In prices  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="22faa-106">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="22faa-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="22faa-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="22faa-107">Example</span></span>  
 <span data-ttu-id="22faa-108">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="22faa-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="22faa-109">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="22faa-109">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="22faa-110">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Dane liczbowe w przestrzeni nazw](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="22faa-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim prices As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let price = Convert.ToDecimal(el.<Price>.Value) _  
            Order By (price) _  
            Select price  
        For Each el As Decimal In prices  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="22faa-111">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="22faa-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="22faa-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22faa-112">See also</span></span>

- [<span data-ttu-id="22faa-113">Sortowanie danych</span><span class="sxs-lookup"><span data-stu-id="22faa-113">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="22faa-114">Zapytania podstawowe (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22faa-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
