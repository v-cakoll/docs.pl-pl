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
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>Instrukcje: Znajdowanie atrybutu elementu nadrzędnego (XPath-LINQ to XML) (C#)

W tym temacie przedstawiono sposób przejdź do elementu nadrzędnego i znajdowanie atrybutu elementu go.

Wyrażenie XPath jest:

`../@id`

## <a name="example"></a>Przykład

W tym przykładzie najpierw wyszukuje `Author` elementu. Następnie wyszukuje `id` atrybutu elementu nadrzędnego.

W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).

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

Ten przykład generuje następujące wyniki:

```
Results are identical
id="bk101"
```
