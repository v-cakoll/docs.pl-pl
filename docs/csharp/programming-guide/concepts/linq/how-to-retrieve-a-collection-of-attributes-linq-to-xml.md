---
title: Jak pobrać kolekcję atrybutów (LINQ to XML) (C#)
description: Metoda Attributes w języku C# Pobiera atrybuty elementu. Ten LINQ to XML przykład wykonuje iterację w kolekcji atrybutów elementu.
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 5994086db6133530e63eb1328a7b524d30a0797d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103383"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a>Jak pobrać kolekcję atrybutów (LINQ to XML) (C#)
W tym temacie przedstawiono <xref:System.Xml.Linq.XElement.Attributes%2A> metodę. Ta metoda pobiera atrybuty elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wykonać iterację kolekcji atrybutów elementu.  
  
```csharp  
XElement val = new XElement("Value",  
    new XAttribute("ID", "1243"),  
    new XAttribute("Type", "int"),  
    new XAttribute("ConvertableTo", "double"),  
    "100");  
IEnumerable<XAttribute> listOfAttributes =  
    from att in val.Attributes()  
    select att;  
foreach (XAttribute a in listOfAttributes)  
    Console.WriteLine(a);  
```  
  
 Ten kod spowoduje wygenerowanie następujących danych wyjściowych:  
  
```output  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>Zobacz też

- [Osie LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
