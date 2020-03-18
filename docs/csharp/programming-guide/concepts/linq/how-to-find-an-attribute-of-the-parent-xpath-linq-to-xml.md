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
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>Jak znaleźć atrybut nadrzędnego (XPath-LINQ do XML) (C#)

W tym temacie pokazano, jak przejść do elementu nadrzędnego i znaleźć jego atrybut.

Wyrażenie XPath jest następujące:

`../@id`

## <a name="example"></a>Przykład

W tym przykładzie `Author` najpierw znajduje element. Następnie znajduje `id` atrybut elementu nadrzędnego.

W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Książki (LINQ do XML)](./sample-xml-file-books-linq-to-xml.md).

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

```output
Results are identical
id="bk101"
```
