---
title: 'Instrukcje: Znajdź Unię dwóch ścieżek lokalizacji (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 9fc88a8784958294ba6077893a5d54110de335a0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593744"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a>Instrukcje: Znajdź Unię dwóch ścieżek lokalizacji (XPath-LINQ to XML) (C#)
Wyrażenie XPath umożliwia znalezienie związku z wynikami dwóch ścieżek lokalizacji XPath.  
  
 Wyrażenie XPath:  
  
 `//Category|//Price`  
  
 Można osiągnąć te same wyniki przy użyciu <xref:System.Linq.Enumerable.Concat%2A> standardowego operatora zapytań.  
  
## <a name="example"></a>Przykład  
 Ten przykład umożliwia znalezienie wszystkich `Category` elementów i wszystkich `Price` elementów i połączenie ich w jedną kolekcję. Należy zauważyć, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] że zapytanie <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> wywołuje w celu uporządkowania wyników. Wyniki obliczania wyrażenia XPath również są w kolejności dokumentu.  
  
 W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Dane liczbowe (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).  
  
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
  