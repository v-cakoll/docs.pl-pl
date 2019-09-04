---
title: 'Instrukcje: Znajdź węzły równorzędne (XPath-LINQ to XML)C#()'
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: 6c7509ea0667bb84d62ee804f4d232d74fa7f6e0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253612"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a>Instrukcje: Znajdź węzły równorzędne (XPath-LINQ to XML)C#()
Możesz chcieć znaleźć wszystkie elementy równorzędne węzła o określonej nazwie. Utworzona kolekcja może zawierać węzeł kontekstu, jeśli węzeł kontekstu ma również określoną nazwę.  
  
 Wyrażenie XPath:  
  
 `../Book`  
  
## <a name="example"></a>Przykład  
 Ten przykład najpierw odnajduje `Book` element, a następnie znajduje wszystkie elementy równorzędne `Book`o nazwie. Kolekcja wyników zawiera węzeł kontekstu.  
  
 W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Elements("Book")  
    .Skip(1)  
    .First();  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    book  
    .Parent  
    .Elements("Book");  
  
// XPath expression  
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");  
  
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
<Book id="bk101">  
  <Author>Garghentini, Davide</Author>  
  <Title>XML Developer's Guide</Title>  
  <Genre>Computer</Genre>  
  <Price>44.95</Price>  
  <PublishDate>2000-10-01</PublishDate>  
  <Description>An in-depth look at creating applications   
      with XML.</Description>  
</Book>  
<Book id="bk102">  
  <Author>Garcia, Debra</Author>  
  <Title>Midnight Rain</Title>  
  <Genre>Fantasy</Genre>  
  <Price>5.95</Price>  
  <PublishDate>2000-12-16</PublishDate>  
  <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
</Book>  
```  
