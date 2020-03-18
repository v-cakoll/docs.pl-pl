---
title: Jak znaleźć atrybuty rodzeństwa o określonej nazwie (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 331e1a7f432f4d06b697180b1594106ec6842c9a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169262"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a>Jak znaleźć atrybuty rodzeństwa o określonej nazwie (XPath-LINQ do XML) (C#)
W tym temacie pokazano, jak znaleźć wszystkie atrybuty elementu równorzędnego węzła kontekstu. Tylko atrybuty o określonej nazwie są zwracane w kolekcji.  
  
 Wyrażenie XPath jest następujące:  
  
 `../Book/@id`  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `Book` najpierw znajduje element, a `Book`następnie znajduje wszystkie elementy `id`równorzędne o nazwie , a następnie znajduje wszystkie atrybuty o nazwie . Wynik jest kolekcją atrybutów.  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Książki (LINQ do XML)](./sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =
    books  
    .Root  
    .Element("Book");  
  
// LINQ to XML query  
IEnumerable<XAttribute> list1 =  
    from el in book.Parent.Elements("Book")  
    select el.Attribute("id");  
  
// XPath expression  
IEnumerable<XAttribute> list2 =  
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XAttribute el in list1)  
    Console.WriteLine(el);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
Results are identical  
id="bk101"  
id="bk102"  
```  
  