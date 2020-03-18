---
title: Jak znaleźć połączenie dwóch ścieżek lokalizacji (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 17a3310f367cb68b3b80b1a3f30af40428f6d2c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141209"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a>Jak znaleźć połączenie dwóch ścieżek lokalizacji (XPath-LINQ do XML) (C#)
XPath umożliwia znalezienie unii wyników dwóch ścieżek lokalizacji XPath.  
  
 Wyrażenie XPath jest następujące:  
  
 `//Category|//Price`  
  
 Można osiągnąć te same wyniki <xref:System.Linq.Enumerable.Concat%2A> przy użyciu standardowego operatora kwerendy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `Category` znajduje wszystkie elementy `Price` i wszystkie elementy i łączy je w jednej kolekcji. Należy zauważyć, że kwerenda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wywołuje, <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> aby zamówić wyniki. Wyniki oceny wyrażenia XPath są również w kolejności dokumentu.  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Dane numeryczne (LINQ do XML)](./sample-xml-file-numerical-data-linq-to-xml.md).  
  
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
  