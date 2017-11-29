---
title: "Porady: sortowanie elementów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c09279-6c8a-482e-8e71-b1453a815052
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f8664a011538269de06ed30dd7367e8f85c510df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-elements-visual-basic"></a><span data-ttu-id="a8c45-102">Porady: sortowanie elementów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8c45-102">How to: Sort Elements (Visual Basic)</span></span>
<span data-ttu-id="a8c45-103">Ten przykład przedstawia, jak napisać zapytanie sortujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="a8c45-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8c45-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8c45-104">Example</span></span>  
 <span data-ttu-id="a8c45-105">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: dane liczbowe (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a8c45-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="a8c45-106">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a8c45-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="a8c45-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8c45-107">Example</span></span>  
 <span data-ttu-id="a8c45-108">W poniższym przykładzie pokazano tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a8c45-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="a8c45-109">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="a8c45-109">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="a8c45-110">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: dane liczbowe w Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="a8c45-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="a8c45-111">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a8c45-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8c45-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8c45-112">See Also</span></span>  
 [<span data-ttu-id="a8c45-113">Sortowanie danych</span><span class="sxs-lookup"><span data-stu-id="a8c45-113">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
 [<span data-ttu-id="a8c45-114">Podstawowe zapytania (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8c45-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
