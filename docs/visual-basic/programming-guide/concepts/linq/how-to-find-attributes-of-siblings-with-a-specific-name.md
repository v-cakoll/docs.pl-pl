---
title: 'Instrukcje: Znajdowanie atrybutów elementów równorzędnych o określonej nazwie (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
ms.openlocfilehash: ce97cbc4b8b1105e8431016a9c296c158cf0091c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596192"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="ac3c8-102">Instrukcje: Znajdowanie atrybutów elementów równorzędnych o określonej nazwie (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac3c8-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ac3c8-103">W tym temacie pokazano, jak można znaleźć wszystkie atrybuty elementów równorzędnych węzła kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ac3c8-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="ac3c8-104">W kolekcji, zwracane są tylko atrybuty o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="ac3c8-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="ac3c8-105">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="ac3c8-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="ac3c8-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac3c8-106">Example</span></span>  
 <span data-ttu-id="ac3c8-107">W tym przykładzie najpierw wyszukuje `Book` elementu, a następnie znajduje wszystkich elementów równorzędnych o nazwie `Book`, a następnie znajduje wszystkie atrybuty o nazwie `id`.</span><span class="sxs-lookup"><span data-stu-id="ac3c8-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="ac3c8-108">Wynik jest Kolekcja atrybutów.</span><span class="sxs-lookup"><span data-stu-id="ac3c8-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="ac3c8-109">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ac3c8-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="ac3c8-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ac3c8-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac3c8-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac3c8-111">See also</span></span>
- [<span data-ttu-id="ac3c8-112">LINQ to XML dla użytkowników metody XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac3c8-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
