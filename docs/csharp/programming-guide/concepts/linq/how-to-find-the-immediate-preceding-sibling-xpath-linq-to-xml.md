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
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a>Jak znaleźć bezpośrednie poprzednie elementy równorzędne (XPath-LINQ do XML) (C#)
Czasami chcesz znaleźć bezpośrednie poprzedzających rodzeństwo do węzła. Ze względu na różnicę w semantyce predykatów pozycyjnych dla poprzednich osi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]równorzędnych w XPath, w przeciwieństwie do , jest to jedno z ciekawszych porównań.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kwerenda <xref:System.Linq.Enumerable.Last%2A> używa operatora, aby znaleźć ostatni węzeł <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>w kolekcji zwrócone przez . Natomiast wyrażenie XPath używa predykatu o wartości 1, aby znaleźć bezpośrednio poprzedzający element.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```output  
Results are identical  
<Child3 />  
```  
