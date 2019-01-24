---
title: 'Instrukcje: Znajdowanie Unii dwóch ścieżek lokalizacji (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 837a94f716c87a1671b5577f8a21a520d4314ec1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526768"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a>Instrukcje: Znajdowanie Unii dwóch ścieżek lokalizacji (XPath-LINQ to XML) (C#)
Wyrażenie XPath umożliwia znajdowanie Unii wyniki z dwóch ścieżek lokalizacji XPath.  
  
 Wyrażenie XPath jest:  
  
 `//Category|//Price`  
  
 Te same wyniki można osiągnąć za pomocą <xref:System.Linq.Enumerable.Concat%2A> standardowego operatora zapytania.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyszukuje wszystkie `Category` elementy i wszystkie `Price` elementy i łączy je w jedną kolekcję. Należy pamiętać, że [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania wywołania <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> aby uporządkować wyniki. Wynikiem obliczenia wyrażenia XPath są również w kolejności dokumentu.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Dane liczbowe (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML dla użytkowników metody XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
