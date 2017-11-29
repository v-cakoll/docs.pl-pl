---
title: "Porady: znajdowanie atrybutu nadrzędnego (XPath-LINQ do XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4da7888ab838dacbdda097f24580745692d407fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a>Porady: znajdowanie atrybutu nadrzędnego (XPath-LINQ do XML) (Visual Basic)
W tym temacie przedstawiono sposób przejdź do elementu nadrzędnego i odnalezienia atrybutu o tym.  
  
 Wyrażenie XPath jest:  
  
 `../@id`  
  
## <a name="example"></a>Przykład  
 W tym przykładzie najpierw znajduje `Author` elementu. Następnie wyszukuje `id` atrybutu elementu nadrzędnego.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: książek (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do XML dla wyrażenia XPath użytkowników (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
