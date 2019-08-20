---
title: 'Instrukcje: Znajdź węzły równorzędne (XPath-LINQ to XML)C#()'
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: c64806c4505b507a9058a03d5cb882412f6868da
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593404"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a><span data-ttu-id="4fde9-102">Instrukcje: Znajdź węzły równorzędne (XPath-LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="4fde9-102">How to: Find Sibling Nodes (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="4fde9-103">Możesz chcieć znaleźć wszystkie elementy równorzędne węzła o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="4fde9-103">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="4fde9-104">Utworzona kolekcja może zawierać węzeł kontekstu, jeśli węzeł kontekstu ma również określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="4fde9-104">The resulting collection might include the context node if the context node also has the specific name.</span></span>  
  
 <span data-ttu-id="4fde9-105">Wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="4fde9-105">The XPath expression is:</span></span>  
  
 `../Book`  
  
## <a name="example"></a><span data-ttu-id="4fde9-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="4fde9-106">Example</span></span>  
 <span data-ttu-id="4fde9-107">Ten przykład najpierw odnajduje `Book` element, a następnie znajduje wszystkie elementy równorzędne `Book`o nazwie.</span><span class="sxs-lookup"><span data-stu-id="4fde9-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="4fde9-108">Kolekcja wyników zawiera węzeł kontekstu.</span><span class="sxs-lookup"><span data-stu-id="4fde9-108">The resulting collection includes the context node.</span></span>  
  
 <span data-ttu-id="4fde9-109">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4fde9-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Elements("Book")  
    .Skip(1)  
    .First();  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    book  
    .Parent  
    .Elements("Book");  
  
// XPath expression  
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="4fde9-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="4fde9-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Book id="bk101">  
  <Author>Garghentini, Davide</Author>  
  <Title>XML Developer's Guide</Title>  
  <Genre>Computer</Genre>  
  <Price>44.95</Price>  
  <PublishDate>2000-10-01</PublishDate>  
  <Description>An in-depth look at creating applications   
      with XML.</Description>  
</Book>  
<Book id="bk102">  
  <Author>Garcia, Debra</Author>  
  <Title>Midnight Rain</Title>  
  <Genre>Fantasy</Genre>  
  <Price>5.95</Price>  
  <PublishDate>2000-12-16</PublishDate>  
  <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
</Book>  
```  
