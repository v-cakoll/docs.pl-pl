---
title: Jak znaleźć atrybut nadrzędnego (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: bfe7554a5c767adde5e7170c8e1ea0537155f6df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141179"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="40fd1-102">Jak znaleźć atrybut nadrzędnego (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="40fd1-102">How to find an attribute of the parent (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="40fd1-103">W tym temacie pokazano, jak przejść do elementu nadrzędnego i znaleźć jego atrybut.</span><span class="sxs-lookup"><span data-stu-id="40fd1-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>

<span data-ttu-id="40fd1-104">Wyrażenie XPath jest następujące:</span><span class="sxs-lookup"><span data-stu-id="40fd1-104">The XPath expression is:</span></span>

`../@id`

## <a name="example"></a><span data-ttu-id="40fd1-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="40fd1-105">Example</span></span>

<span data-ttu-id="40fd1-106">W tym przykładzie `Author` najpierw znajduje element.</span><span class="sxs-lookup"><span data-stu-id="40fd1-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="40fd1-107">Następnie znajduje `id` atrybut elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="40fd1-107">It then finds the `id` attribute of the parent element.</span></span>

<span data-ttu-id="40fd1-108">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Książki (LINQ do XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="40fd1-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>

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

<span data-ttu-id="40fd1-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="40fd1-109">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
```
