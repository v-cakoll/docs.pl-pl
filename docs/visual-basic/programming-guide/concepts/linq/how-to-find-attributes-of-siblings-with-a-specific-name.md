---
title: "Porady: znajdowanie atrybuty elementów równorzędnych o określonej nazwie (XPath-LINQ do XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 751d9559ae3b0bfe62fc866baf52fbef7babb7e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="8385f-102">Porady: znajdowanie atrybuty elementów równorzędnych o określonej nazwie (XPath-LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8385f-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="8385f-103">W tym temacie pokazano, jak znaleźć wszystkie atrybuty elementów równorzędnych węzła kontekstu.</span><span class="sxs-lookup"><span data-stu-id="8385f-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="8385f-104">Zwracane są tylko atrybuty o określonej nazwie w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8385f-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="8385f-105">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="8385f-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="8385f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="8385f-106">Example</span></span>  
 <span data-ttu-id="8385f-107">W tym przykładzie najpierw znajduje `Book` elementu i wszystkich elementów równorzędnych o nazwie uzna `Book`, a następnie znalezienie wszystkie atrybuty o nazwie `id`.</span><span class="sxs-lookup"><span data-stu-id="8385f-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="8385f-108">Wynik jest Kolekcja atrybutów.</span><span class="sxs-lookup"><span data-stu-id="8385f-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="8385f-109">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: książek (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8385f-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="8385f-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="8385f-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="8385f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8385f-111">See Also</span></span>  
 [<span data-ttu-id="8385f-112">LINQ do XML dla wyrażenia XPath użytkowników (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8385f-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
