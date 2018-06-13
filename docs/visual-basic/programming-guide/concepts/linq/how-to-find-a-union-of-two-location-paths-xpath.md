---
title: 'Porady: znajdowanie złożenie dwóch ścieżek lokalizacji (XPath-LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 3f67ac24d12e7d2fcbd74e2f27a75d982c1cf00b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642643"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="1b956-102">Porady: znajdowanie złożenie dwóch ścieżek lokalizacji (XPath-LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b956-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="1b956-103">Wyrażenie XPath umożliwia znaleźć złożenie wyników dwie ścieżki do lokalizacji XPath.</span><span class="sxs-lookup"><span data-stu-id="1b956-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="1b956-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="1b956-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="1b956-105">Takie same wyniki można osiągnąć za pomocą <xref:System.Linq.Enumerable.Concat%2A> — operator zapytań standardowa.</span><span class="sxs-lookup"><span data-stu-id="1b956-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b956-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b956-106">Example</span></span>  
 <span data-ttu-id="1b956-107">W tym przykładzie znajduje wszystkie `Category` elementów i wszystkie `Price` elementów i łączy je do jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1b956-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="1b956-108">Należy pamiętać, że [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania wywołania <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> do kolejność wyników.</span><span class="sxs-lookup"><span data-stu-id="1b956-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="1b956-109">Wyniki oceny wyrażenia XPath są również w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1b956-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="1b956-110">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: dane liczbowe (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1b956-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="1b956-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1b956-111">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b956-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b956-112">See Also</span></span>  
 [<span data-ttu-id="1b956-113">LINQ do XML dla wyrażenia XPath użytkowników (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b956-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
