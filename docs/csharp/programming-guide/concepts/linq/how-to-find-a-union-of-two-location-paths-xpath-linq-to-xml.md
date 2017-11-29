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
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a>Porady: znajdowanie złożenie dwóch ścieżek lokalizacji (XPath-LINQ do XML) (C#)
Wyrażenie XPath umożliwia znaleźć złożenie wyników dwie ścieżki do lokalizacji XPath.  
  
 Wyrażenie XPath jest:  
  
 `//Category|//Price`  
  
 Takie same wyniki można osiągnąć za pomocą <xref:System.Linq.Enumerable.Concat%2A> — operator zapytań standardowa.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie znajduje wszystkie `Category` elementów i wszystkie `Price` elementów i łączy je do jednej kolekcji. Należy pamiętać, że [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania wywołania <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> do kolejność wyników. Wyniki oceny wyrażenia XPath są również w kolejności dokumentu.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: dane liczbowe (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do XML dla użytkowników XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
