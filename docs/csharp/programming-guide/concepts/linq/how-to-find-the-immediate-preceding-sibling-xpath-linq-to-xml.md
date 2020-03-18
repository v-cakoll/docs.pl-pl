---
title: Jak znaleźć bezpośrednie poprzednie elementy równorzędne (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 1e5aece41021642d43b7f6f7b78bb105156ee4ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141003"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="f2044-102">Jak znaleźć bezpośrednie poprzednie elementy równorzędne (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f2044-102">How to find the immediate preceding sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="f2044-103">Czasami chcesz znaleźć bezpośrednie poprzedzających rodzeństwo do węzła.</span><span class="sxs-lookup"><span data-stu-id="f2044-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="f2044-104">Ze względu na różnicę w semantyce predykatów pozycyjnych dla poprzednich osi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]równorzędnych w XPath, w przeciwieństwie do , jest to jedno z ciekawszych porównań.</span><span class="sxs-lookup"><span data-stu-id="f2044-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2044-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2044-105">Example</span></span>  
 <span data-ttu-id="f2044-106">W tym przykładzie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kwerenda <xref:System.Linq.Enumerable.Last%2A> używa operatora, aby znaleźć ostatni węzeł <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>w kolekcji zwrócone przez .</span><span class="sxs-lookup"><span data-stu-id="f2044-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="f2044-107">Natomiast wyrażenie XPath używa predykatu o wartości 1, aby znaleźć bezpośrednio poprzedzający element.</span><span class="sxs-lookup"><span data-stu-id="f2044-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
    @"<Root>  
    <Child1/>  
    <Child2/>  
    <Child3/>  
    <Child4/>  
</Root>");  
XElement child4 = root.Element("Child4");  
  
// LINQ to XML query  
XElement el1 =  
    child4  
    .ElementsBeforeSelf()  
    .Last();  
  
// XPath expression  
XElement el2 =  
    ((IEnumerable)child4  
                 .XPathEvaluate("preceding-sibling::*[1]"))  
                 .Cast<XElement>()  
                 .First();  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="f2044-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f2044-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Child3 />  
```  
