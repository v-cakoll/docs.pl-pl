---
title: 'Instrukcje: Znajdowanie atrybutu elementu nadrzędnego (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: ce8fbb828a5ea8df79f449d50f1d61702a4e3df2
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249929"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a>Instrukcje: Znajdowanie atrybutu elementu nadrzędnego (XPath-LINQ to XML) (Visual Basic)
W tym temacie pokazano, jak przejść do elementu nadrzędnego i znaleźć jego atrybut.  
  
 Wyrażenie XPath:  
  
 `../@id`  
  
## <a name="example"></a>Przykład  
 Ten przykład najpierw odnajduje element `Author`. Następnie znajduje atrybut `id` elementu nadrzędnego.  
  
 Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```vb  
Dim books As XDocument = XDocument.Load("Books.xml")  
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()  
  
' LINQ to XML query  
Dim att1 As XAttribute = author.Parent.Attribute("id")  
  
' XPath expression  
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _  
    IEnumerable).Cast(Of XAttribute)().First()  
  
If att1 Is att2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(att1)  
```  
  
 Ten przykład generuje następujące dane wyjściowe:  
  
```console  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML dla użytkowników XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
