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
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="47c56-102">Instrukcje: Znajdowanie atrybutu elementu nadrzędnego (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47c56-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="47c56-103">W tym temacie pokazano, jak przejść do elementu nadrzędnego i znaleźć jego atrybut.</span><span class="sxs-lookup"><span data-stu-id="47c56-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="47c56-104">Wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="47c56-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="47c56-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="47c56-105">Example</span></span>  
 <span data-ttu-id="47c56-106">Ten przykład najpierw odnajduje element `Author`.</span><span class="sxs-lookup"><span data-stu-id="47c56-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="47c56-107">Następnie znajduje atrybut `id` elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="47c56-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="47c56-108">Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="47c56-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="47c56-109">Ten przykład generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="47c56-109">This example produces the following output:</span></span>  
  
```console  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="47c56-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47c56-110">See also</span></span>

- [<span data-ttu-id="47c56-111">LINQ to XML dla użytkowników XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47c56-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
