---
title: 'Instrukcje: Znajdowanie atrybutu elementu nadrzędnego (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: f30c810483d8253132b9fe3e0959d04a8b4d26a0
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690064"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="a2f97-102">Instrukcje: Znajdowanie atrybutu elementu nadrzędnego (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a2f97-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="a2f97-103">W tym temacie przedstawiono sposób przejdź do elementu nadrzędnego i znajdowanie atrybutu elementu go.</span><span class="sxs-lookup"><span data-stu-id="a2f97-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>

<span data-ttu-id="a2f97-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="a2f97-104">The XPath expression is:</span></span>

`../@id`

## <a name="example"></a><span data-ttu-id="a2f97-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2f97-105">Example</span></span>

<span data-ttu-id="a2f97-106">W tym przykładzie najpierw wyszukuje `Author` elementu.</span><span class="sxs-lookup"><span data-stu-id="a2f97-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="a2f97-107">Następnie wyszukuje `id` atrybutu elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a2f97-107">It then finds the `id` attribute of the parent element.</span></span>

<span data-ttu-id="a2f97-108">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a2f97-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>

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

<span data-ttu-id="a2f97-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="a2f97-109">This example produces the following output:</span></span>

```
Results are identical
id="bk101"
```
