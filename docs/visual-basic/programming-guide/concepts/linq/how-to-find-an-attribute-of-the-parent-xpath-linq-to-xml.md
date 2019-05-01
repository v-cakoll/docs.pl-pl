---
title: 'Instrukcje: Znajdowanie atrybutu elementu nadrzędnego (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: ded20c173063492d260aee5ba55f3c4c585bd961
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021651"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a>Instrukcje: Znajdowanie atrybutu elementu nadrzędnego (XPath-LINQ to XML) (Visual Basic)
W tym temacie przedstawiono sposób przejdź do elementu nadrzędnego i znajdowanie atrybutu elementu go.  
  
 Wyrażenie XPath jest:  
  
 `../@id`  
  
## <a name="example"></a>Przykład  
 W tym przykładzie najpierw wyszukuje `Author` elementu. Następnie wyszukuje `id` atrybutu elementu nadrzędnego.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML dla użytkowników metody XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
