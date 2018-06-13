---
title: 'Porady: znajdowanie atrybuty elementów równorzędnych o określonej nazwie (XPath-LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 0e87208e033c4960843a82c9abd2b4ebd4f74d3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315870"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="aa62d-102">Porady: znajdowanie atrybuty elementów równorzędnych o określonej nazwie (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="aa62d-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="aa62d-103">W tym temacie pokazano, jak znaleźć wszystkie atrybuty elementów równorzędnych węzła kontekstu.</span><span class="sxs-lookup"><span data-stu-id="aa62d-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="aa62d-104">Zwracane są tylko atrybuty o określonej nazwie w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="aa62d-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="aa62d-105">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="aa62d-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="aa62d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa62d-106">Example</span></span>  
 <span data-ttu-id="aa62d-107">W tym przykładzie najpierw znajduje `Book` elementu i wszystkich elementów równorzędnych o nazwie uzna `Book`, a następnie znalezienie wszystkie atrybuty o nazwie `id`.</span><span class="sxs-lookup"><span data-stu-id="aa62d-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="aa62d-108">Wynik jest Kolekcja atrybutów.</span><span class="sxs-lookup"><span data-stu-id="aa62d-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="aa62d-109">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: książek (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="aa62d-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Element("Book");  
  
// LINQ to XML query  
IEnumerable<XAttribute> list1 =  
    from el in book.Parent.Elements("Book")  
    select el.Attribute("id");  
  
// XPath expression  
IEnumerable<XAttribute> list2 =  
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XAttribute el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="aa62d-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="aa62d-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa62d-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa62d-111">See Also</span></span>  
 [<span data-ttu-id="aa62d-112">LINQ do XML dla użytkowników XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="aa62d-112">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
