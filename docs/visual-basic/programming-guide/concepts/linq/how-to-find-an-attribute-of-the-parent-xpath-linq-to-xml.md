---
title: 'Porady: znajdowanie atrybutu nadrzędnego (XPath-LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: af2b6fc3aaebe4ba45be405c587c549ea73b3289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="ba240-102">Porady: znajdowanie atrybutu nadrzędnego (XPath-LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba240-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ba240-103">W tym temacie przedstawiono sposób przejdź do elementu nadrzędnego i odnalezienia atrybutu o tym.</span><span class="sxs-lookup"><span data-stu-id="ba240-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="ba240-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="ba240-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="ba240-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba240-105">Example</span></span>  
 <span data-ttu-id="ba240-106">W tym przykładzie najpierw znajduje `Author` elementu.</span><span class="sxs-lookup"><span data-stu-id="ba240-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="ba240-107">Następnie wyszukuje `id` atrybutu elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ba240-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="ba240-108">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: książek (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ba240-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="ba240-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ba240-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba240-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba240-110">See Also</span></span>  
 [<span data-ttu-id="ba240-111">LINQ do XML dla wyrażenia XPath użytkowników (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba240-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
