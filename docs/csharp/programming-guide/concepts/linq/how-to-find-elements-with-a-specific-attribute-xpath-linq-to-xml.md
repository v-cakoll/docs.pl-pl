---
title: 'Instrukcje: Znajdowanie elementów o określonym atrybucie (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: fc1bc285a066dcb1843dcb626b1b3b354f28da74
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486808"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a>Instrukcje: Znajdowanie elementów o określonym atrybucie (XPath-LINQ to XML) (C#)
Czasami chcesz znaleźć wszystkie elementy, które mają określony atrybut. Nie masz zajmującym się ochroną zawartości atrybutu. Zamiast tego chcesz wybrać na podstawie istnienia atrybutu.  
  
 Wyrażenie XPath jest:  
  
 `./*[@Select]`  
  
## <a name="example"></a>Przykład  
 Poniższy kod wybiera tylko elementy, które mają `Select` atrybutu.  
  
```csharp  
XElement doc = XElement.Parse(  
@"<Root>  
    <Child1>1</Child1>  
    <Child2 Select='true'>2</Child2>  
    <Child3>3</Child3>  
    <Child4 Select='true'>4</Child4>  
    <Child5>5</Child5>  
</Root>");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    from el in doc.Elements()  
    where el.Attribute("Select") != null  
    select el;  
  
// XPath expression  
IEnumerable<XElement> list2 =  
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  