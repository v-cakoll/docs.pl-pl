---
title: 'Instrukcje: Znajdowanie atrybutów elementów równorzędnych o określonej nazwie (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
ms.openlocfilehash: ea4492dbbe9dc8e32c675e1a938cda0d10321b7a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343676"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a>Instrukcje: Znajdowanie atrybutów elementów równorzędnych o określonej nazwie (XPath-LINQ to XML) (Visual Basic)
W tym temacie pokazano, jak znaleźć wszystkie atrybuty elementów równorzędnych węzła kontekstu. W kolekcji są zwracane tylko atrybuty o określonej nazwie.  
  
 Wyrażenie XPath:  
  
 `../Book/@id`  
  
## <a name="example"></a>Przykład  
 Ten przykład najpierw odnajduje `Book` element, a następnie znajduje wszystkie elementy równorzędne o nazwie `Book`, a następnie odnajdzie wszystkie atrybuty o nazwie `id`. Wynik jest kolekcją atrybutów.  
  
 Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```vb  
Dim books as XDocument = XDocument.Load("Books.xml")  
Dim book As XElement = books.Root.<Book>(0)  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XAttribute) = _  
    From el In book.Parent.<Book> _  
    Select el.Attribute("id")  
  
' XPath expression  
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _  
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()  
  
If list1.Count() = list2.Count() And _  
        (list1.Intersect(list2)).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XAttribute In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```console  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML dla użytkowników XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
