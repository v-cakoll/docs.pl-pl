---
title: Jak znaleźć atrybuty rodzeństwa o określonej nazwie (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 331e1a7f432f4d06b697180b1594106ec6842c9a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169262"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="41570-102">Jak znaleźć atrybuty rodzeństwa o określonej nazwie (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="41570-102">How to find attributes of siblings with a specific name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="41570-103">W tym temacie pokazano, jak znaleźć wszystkie atrybuty elementu równorzędnego węzła kontekstu.</span><span class="sxs-lookup"><span data-stu-id="41570-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="41570-104">Tylko atrybuty o określonej nazwie są zwracane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="41570-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="41570-105">Wyrażenie XPath jest następujące:</span><span class="sxs-lookup"><span data-stu-id="41570-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="41570-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="41570-106">Example</span></span>  
 <span data-ttu-id="41570-107">W tym przykładzie `Book` najpierw znajduje element, a `Book`następnie znajduje wszystkie elementy `id`równorzędne o nazwie , a następnie znajduje wszystkie atrybuty o nazwie .</span><span class="sxs-lookup"><span data-stu-id="41570-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="41570-108">Wynik jest kolekcją atrybutów.</span><span class="sxs-lookup"><span data-stu-id="41570-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="41570-109">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Książki (LINQ do XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="41570-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="41570-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="41570-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
id="bk101"  
id="bk102"  
```  
  