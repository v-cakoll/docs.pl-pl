---
title: 'Porady: znajdowanie atrybutów elementów równorzędnych o określonej nazwie (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 60b6529f310ccbb02160ff96e1db7870bcc71058
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43739971"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="1cba8-102">Porady: znajdowanie atrybutów elementów równorzędnych o określonej nazwie (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1cba8-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="1cba8-103">W tym temacie pokazano, jak można znaleźć wszystkie atrybuty elementów równorzędnych węzła kontekstu.</span><span class="sxs-lookup"><span data-stu-id="1cba8-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="1cba8-104">W kolekcji, zwracane są tylko atrybuty o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="1cba8-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="1cba8-105">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="1cba8-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="1cba8-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1cba8-106">Example</span></span>  
 <span data-ttu-id="1cba8-107">W tym przykładzie najpierw wyszukuje `Book` elementu, a następnie znajduje wszystkich elementów równorzędnych o nazwie `Book`, a następnie znajduje wszystkie atrybuty o nazwie `id`.</span><span class="sxs-lookup"><span data-stu-id="1cba8-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="1cba8-108">Wynik jest Kolekcja atrybutów.</span><span class="sxs-lookup"><span data-stu-id="1cba8-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="1cba8-109">W tym przykładzie użyto następujący dokument XML: [przykładowy plik XML: książki (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1cba8-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="1cba8-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1cba8-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="1cba8-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1cba8-111">See Also</span></span>

- [<span data-ttu-id="1cba8-112">LINQ to XML dla użytkowników metody XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="1cba8-112">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
