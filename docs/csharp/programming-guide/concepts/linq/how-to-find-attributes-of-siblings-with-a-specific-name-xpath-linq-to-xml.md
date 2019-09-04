---
title: 'Instrukcje: Znajdź atrybuty elementów równorzędnych o określonej nazwie (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 0d7842f190f7ce7869668929b69c2336d33c6183
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253736"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a>Instrukcje: Znajdź atrybuty elementów równorzędnych o określonej nazwie (XPath-LINQ to XML) (C#)
W tym temacie pokazano, jak znaleźć wszystkie atrybuty elementów równorzędnych węzła kontekstu. W kolekcji są zwracane tylko atrybuty o określonej nazwie.  
  
 Wyrażenie XPath:  
  
 `../Book/@id`  
  
## <a name="example"></a>Przykład  
 Ten przykład najpierw odnajduje `Book` element, a następnie znajduje wszystkie elementy równorzędne `Book`o nazwie, a następnie znajduje wszystkie `id`atrybuty o nazwie. Wynik jest kolekcją atrybutów.  
  
 W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).  
  
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
  