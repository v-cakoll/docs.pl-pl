---
title: Jak zbadać LINQ to XML przy użyciu XPath (C#)
description: Można użyć metod rozszerzających w języku C# do wykonywania zapytań w drzewie XML przy użyciu XPath. Ogólnie rzecz biorąc nie zalecamy używania XPath z LINQ to XML.
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: fff45a93380b5af85aa640fc690783cc95e6298b
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104339"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="7e540-104">Jak zbadać LINQ to XML przy użyciu XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="7e540-104">How to query LINQ to XML using XPath (C#)</span></span>
<span data-ttu-id="7e540-105">W tym temacie przedstawiono metody rozszerzające, które umożliwiają badanie drzewa XML przy użyciu XPath.</span><span class="sxs-lookup"><span data-stu-id="7e540-105">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="7e540-106">Aby uzyskać szczegółowe informacje na temat korzystania z tych metod rozszerzających, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7e540-106">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="7e540-107">Chyba że masz bardzo konkretny powód wykonywania zapytań przy użyciu XPath, na przykład w przypadku korzystania z starszego kodu, używanie XPath z LINQ to XML nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="7e540-107">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="7e540-108">Zapytania XPath nie będą wykonywane, a także [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="7e540-108">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e540-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e540-109">Example</span></span>  
 <span data-ttu-id="7e540-110">Poniższy przykład tworzy małe drzewo XML i używa <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> do wybierania zestawu elementów.</span><span class="sxs-lookup"><span data-stu-id="7e540-110">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="7e540-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7e540-111">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  