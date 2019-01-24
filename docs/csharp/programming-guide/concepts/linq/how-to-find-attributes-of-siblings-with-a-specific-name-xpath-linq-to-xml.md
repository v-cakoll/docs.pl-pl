---
title: 'Instrukcje: Znajdowanie atrybutów elementów równorzędnych o określonej nazwie (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 562f3a40e1670a76778a64570f980326d946a4c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584678"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a>Instrukcje: Znajdowanie atrybutów elementów równorzędnych o określonej nazwie (XPath-LINQ to XML) (C#)
W tym temacie pokazano, jak można znaleźć wszystkie atrybuty elementów równorzędnych węzła kontekstu. W kolekcji, zwracane są tylko atrybuty o określonej nazwie.  
  
 Wyrażenie XPath jest:  
  
 `../Book/@id`  
  
## <a name="example"></a>Przykład  
 W tym przykładzie najpierw wyszukuje `Book` elementu, a następnie znajduje wszystkich elementów równorzędnych o nazwie `Book`, a następnie znajduje wszystkie atrybuty o nazwie `id`. Wynik jest Kolekcja atrybutów.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
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
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML dla użytkowników metody XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
