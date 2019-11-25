---
title: Jak znaleźć Unię dwóch ścieżek lokalizacji (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 17a3310f367cb68b3b80b1a3f30af40428f6d2c7
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141209"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a>Jak znaleźć Unię dwóch ścieżek lokalizacji (XPath-LINQ to XML) (C#)
Wyrażenie XPath umożliwia znalezienie związku z wynikami dwóch ścieżek lokalizacji XPath.  
  
 Wyrażenie XPath:  
  
 `//Category|//Price`  
  
 Można osiągnąć te same wyniki przy użyciu standardowego operatora zapytań <xref:System.Linq.Enumerable.Concat%2A>.  
  
## <a name="example"></a>Przykład  
 Ten przykład znajduje wszystkie elementy `Category` i wszystkie elementy `Price` i łączy je w jedną kolekcję. Należy zauważyć, że zapytanie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wywołuje <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> w celu uporządkowania wyników. Wyniki obliczania wyrażenia XPath również są w kolejności dokumentu.  
  
 Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: dane liczbowe (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```output  
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
  