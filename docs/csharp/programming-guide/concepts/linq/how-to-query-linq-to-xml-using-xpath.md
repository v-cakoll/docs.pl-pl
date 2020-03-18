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
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="0c9fb-102">Jak wysyłać zapytania linq do XML przy użyciu XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="0c9fb-102">How to query LINQ to XML using XPath (C#)</span></span>
<span data-ttu-id="0c9fb-103">W tym temacie przedstawiono metody rozszerzenia, które umożliwiają wykonywanie zapytań do drzewa XML przy użyciu xpath.</span><span class="sxs-lookup"><span data-stu-id="0c9fb-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="0c9fb-104">Aby uzyskać szczegółowe informacje na temat <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>korzystania z tych metod rozszerzenia, zobacz .</span><span class="sxs-lookup"><span data-stu-id="0c9fb-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="0c9fb-105">Chyba że masz bardzo konkretny powód do wykonywania zapytań przy użyciu XPath, takich jak szerokie wykorzystanie starszego kodu, przy użyciu XPath z LINQ do XML nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="0c9fb-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="0c9fb-106">Kwerendy XPath nie będą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wykonywać, jak również kwerendy.</span><span class="sxs-lookup"><span data-stu-id="0c9fb-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c9fb-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c9fb-107">Example</span></span>  
 <span data-ttu-id="0c9fb-108">Poniższy przykład tworzy małe drzewo XML i używa <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> do wybierania zestawu elementów.</span><span class="sxs-lookup"><span data-stu-id="0c9fb-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="0c9fb-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="0c9fb-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  