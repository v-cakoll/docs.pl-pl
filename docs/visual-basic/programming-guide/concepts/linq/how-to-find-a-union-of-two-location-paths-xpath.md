---
title: 'Porady: znajdowanie Unii dwóch ścieżek lokalizacji (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 3f67ac24d12e7d2fcbd74e2f27a75d982c1cf00b
ms.sourcegitcommit: a474397fd4de822f0d878d86d907e49763872b0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2018
ms.locfileid: "42751942"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="344a1-102">Porady: znajdowanie Unii dwóch ścieżek lokalizacji (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="344a1-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="344a1-103">Wyrażenie XPath umożliwia znajdowanie Unii wyniki z dwóch ścieżek lokalizacji XPath.</span><span class="sxs-lookup"><span data-stu-id="344a1-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="344a1-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="344a1-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="344a1-105">Te same wyniki można osiągnąć za pomocą <xref:System.Linq.Enumerable.Concat%2A> standardowego operatora zapytania.</span><span class="sxs-lookup"><span data-stu-id="344a1-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="344a1-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="344a1-106">Example</span></span>  
 <span data-ttu-id="344a1-107">W tym przykładzie wyszukuje wszystkie `Category` elementy i wszystkie `Price` elementy i łączy je w jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="344a1-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="344a1-108">Należy pamiętać, że [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania wywołania <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> aby uporządkować wyniki.</span><span class="sxs-lookup"><span data-stu-id="344a1-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="344a1-109">Wynikiem obliczenia wyrażenia XPath są również w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="344a1-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="344a1-110">W tym przykładzie użyto następujący dokument XML: [przykładowy plik XML: dane liczbowe (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="344a1-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="344a1-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="344a1-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="344a1-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="344a1-112">See Also</span></span>  
 [<span data-ttu-id="344a1-113">LINQ to XML dla użytkowników metody XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="344a1-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
