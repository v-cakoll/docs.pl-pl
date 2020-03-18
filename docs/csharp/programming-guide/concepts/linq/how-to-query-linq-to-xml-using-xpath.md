---
title: Jak wysyłać zapytania linq do XML przy użyciu XPath (C#)
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: 61878febd9b4880872b7bc58e4de04b37cff96f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344810"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a>Jak wysyłać zapytania linq do XML przy użyciu XPath (C#)
W tym temacie przedstawiono metody rozszerzenia, które umożliwiają wykonywanie zapytań do drzewa XML przy użyciu xpath. Aby uzyskać szczegółowe informacje na temat <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>korzystania z tych metod rozszerzenia, zobacz .  
  
 Chyba że masz bardzo konkretny powód do wykonywania zapytań przy użyciu XPath, takich jak szerokie wykorzystanie starszego kodu, przy użyciu XPath z LINQ do XML nie jest zalecane. Kwerendy XPath nie będą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wykonywać, jak również kwerendy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy małe drzewo XML i używa <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> do wybierania zestawu elementów.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  