---
title: "Porady: znajdowanie złożenie dwóch ścieżek lokalizacji (XPath-LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 48c5182a32a78dd7f32f73b8180f90c0787e197a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="27ebe-102">Porady: znajdowanie złożenie dwóch ścieżek lokalizacji (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="27ebe-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="27ebe-103">Wyrażenie XPath umożliwia znaleźć złożenie wyników dwie ścieżki do lokalizacji XPath.</span><span class="sxs-lookup"><span data-stu-id="27ebe-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="27ebe-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="27ebe-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="27ebe-105">Takie same wyniki można osiągnąć za pomocą <xref:System.Linq.Enumerable.Concat%2A> — operator zapytań standardowa.</span><span class="sxs-lookup"><span data-stu-id="27ebe-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27ebe-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="27ebe-106">Example</span></span>  
 <span data-ttu-id="27ebe-107">W tym przykładzie znajduje wszystkie `Category` elementów i wszystkie `Price` elementów i łączy je do jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="27ebe-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="27ebe-108">Należy pamiętać, że [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania wywołania <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> do kolejność wyników.</span><span class="sxs-lookup"><span data-stu-id="27ebe-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="27ebe-109">Wyniki oceny wyrażenia XPath są również w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="27ebe-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="27ebe-110">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: dane liczbowe (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="27ebe-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="27ebe-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="27ebe-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="27ebe-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27ebe-112">See Also</span></span>  
 [<span data-ttu-id="27ebe-113">LINQ do XML dla użytkowników XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="27ebe-113">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
