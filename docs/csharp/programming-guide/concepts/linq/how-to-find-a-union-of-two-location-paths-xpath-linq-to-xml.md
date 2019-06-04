---
title: 'Instrukcje: Znajdowanie Unii dwóch ścieżek lokalizacji (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: e00c606460159d05f1d3fcaddb1ac5f7b2ec86fa
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485608"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="afed4-102">Instrukcje: Znajdowanie Unii dwóch ścieżek lokalizacji (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="afed4-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="afed4-103">Wyrażenie XPath umożliwia znajdowanie Unii wyniki z dwóch ścieżek lokalizacji XPath.</span><span class="sxs-lookup"><span data-stu-id="afed4-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="afed4-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="afed4-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="afed4-105">Te same wyniki można osiągnąć za pomocą <xref:System.Linq.Enumerable.Concat%2A> standardowego operatora zapytania.</span><span class="sxs-lookup"><span data-stu-id="afed4-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afed4-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="afed4-106">Example</span></span>  
 <span data-ttu-id="afed4-107">W tym przykładzie wyszukuje wszystkie `Category` elementy i wszystkie `Price` elementy i łączy je w jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="afed4-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="afed4-108">Należy pamiętać, że [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania wywołania <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> aby uporządkować wyniki.</span><span class="sxs-lookup"><span data-stu-id="afed4-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="afed4-109">Wynikiem obliczenia wyrażenia XPath są również w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="afed4-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="afed4-110">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Dane liczbowe (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="afed4-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="afed4-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="afed4-111">This example produces the following output:</span></span>  
  
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
  