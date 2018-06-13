---
title: 'Porady: znajdowanie atrybutu nadrzędnego (XPath-LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 6f796bfb8f8b0051af4e31f6e82a503dbfbbc334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318802"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>Porady: znajdowanie atrybutu nadrzędnego (XPath-LINQ do XML) (C#)
W tym temacie przedstawiono sposób przejdź do elementu nadrzędnego i odnalezienia atrybutu o tym.  
  
 Wyrażenie XPath jest:  
  
 `../@id`  
  
## <a name="example"></a>Przykład  
 W tym przykładzie najpierw znajduje `Author` elementu. Następnie wyszukuje `id` atrybutu elementu nadrzędnego.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: książek (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement author =   
    books  
    .Root  
    .Element("Book")  
    .Element("Author");  
  
// LINQ to XML query  
XAttribute att1 =  
    author  
    .Parent  
    .Attribute("id");  
  
// XPath expression  
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();  
  
if (att1 == att2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(att1);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do XML dla użytkowników XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
