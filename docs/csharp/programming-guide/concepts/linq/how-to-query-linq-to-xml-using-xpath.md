---
title: 'Porady: tworzenie zapytań dotyczących LINQ to XML przy użyciu XPath (C#)'
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: 3d4a75e4688725f2444d3bbc4d55bec828485a5d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511194"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="f7a05-102">Porady: tworzenie zapytań dotyczących LINQ to XML przy użyciu XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="f7a05-102">How to: Query LINQ to XML Using XPath (C#)</span></span>
<span data-ttu-id="f7a05-103">W tym temacie przedstawiono metody rozszerzenia, które pozwalają na wykonywanie zapytań drzewa XML przy użyciu wyrażenie XPath.</span><span class="sxs-lookup"><span data-stu-id="f7a05-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="f7a05-104">Aby uzyskać szczegółowe informacje o używaniu tych metod rozszerzenia, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7a05-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f7a05-105">Jeśli nie masz bardzo powód do wykonywania zapytań przy użyciu XPath, takie jak zwiększone użycie starszego kodu, za pomocą LINQ to XML przy użyciu XPath nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="f7a05-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="f7a05-106">Zapytania XPath nie będzie wykonywać także [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="f7a05-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7a05-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7a05-107">Example</span></span>  
 <span data-ttu-id="f7a05-108">Poniższy przykład tworzy mały drzewa XML i używa <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> wybrać zestaw elementów.</span><span class="sxs-lookup"><span data-stu-id="f7a05-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="f7a05-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f7a05-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7a05-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7a05-110">See Also</span></span>

- [<span data-ttu-id="f7a05-111">Zaawansowane techniki zapytań (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f7a05-111">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
