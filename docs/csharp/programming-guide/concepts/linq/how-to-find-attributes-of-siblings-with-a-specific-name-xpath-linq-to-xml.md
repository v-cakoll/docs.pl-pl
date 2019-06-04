---
title: 'Instrukcje: Znajdowanie atrybutów elementów równorzędnych o określonej nazwie (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 0c62ecb7660a012af556515ba5e7de330d5ab5e7
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486789"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="4720c-102">Instrukcje: Znajdowanie atrybutów elementów równorzędnych o określonej nazwie (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4720c-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="4720c-103">W tym temacie pokazano, jak można znaleźć wszystkie atrybuty elementów równorzędnych węzła kontekstu.</span><span class="sxs-lookup"><span data-stu-id="4720c-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="4720c-104">W kolekcji, zwracane są tylko atrybuty o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="4720c-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="4720c-105">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="4720c-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="4720c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="4720c-106">Example</span></span>  
 <span data-ttu-id="4720c-107">W tym przykładzie najpierw wyszukuje `Book` elementu, a następnie znajduje wszystkich elementów równorzędnych o nazwie `Book`, a następnie znajduje wszystkie atrybuty o nazwie `id`.</span><span class="sxs-lookup"><span data-stu-id="4720c-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="4720c-108">Wynik jest Kolekcja atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4720c-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="4720c-109">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4720c-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="4720c-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="4720c-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  