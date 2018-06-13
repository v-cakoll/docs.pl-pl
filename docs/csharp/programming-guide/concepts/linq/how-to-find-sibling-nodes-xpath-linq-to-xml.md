---
title: 'Porady: znajdowanie węzłami tego samego poziomu (XPath-LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: a448be9d86f9f2e2f85d45f9bc1f019b3f72305c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324164"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a>Porady: znajdowanie węzłami tego samego poziomu (XPath-LINQ do XML) (C#)
Można znaleźć wszystkich elementów równorzędnych węzła, które ma określoną nazwę. Wynikowa kolekcji może zawierać węzeł kontekstu, jeśli węzeł kontekstu ma również określonej nazwy.  
  
 Wyrażenie XPath jest:  
  
 `../Book`  
  
## <a name="example"></a>Przykład  
 W tym przykładzie najpierw znajduje `Book` elementu i wszystkich elementów równorzędnych o nazwie uzna `Book`. Wynikowa kolekcja zawiera węzeł kontekstu.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: książek (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
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
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do XML dla użytkowników XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
