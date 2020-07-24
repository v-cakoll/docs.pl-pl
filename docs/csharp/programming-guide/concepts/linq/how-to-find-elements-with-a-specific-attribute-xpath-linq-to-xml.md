---
title: Jak znaleźć elementy z określonym atrybutem (XPath-LINQ to XML) (C#)
description: Ten przykład w języku C# porównuje wyrażenie XPath LINQ to XML, aby znaleźć elementy, które mają określony atrybut.
ms.date: 07/20/2015
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: eb0b5c27fb3993b487c5e8d70c6562c1d0562860
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105268"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a>Jak znaleźć elementy z określonym atrybutem (XPath-LINQ to XML) (C#)
Czasami chcesz znaleźć wszystkie elementy, które mają określony atrybut. Nie dotyczy zawartości atrybutu. Zamiast tego należy wybrać opcję na podstawie istnienia atrybutu.  
  
 Wyrażenie XPath:  
  
 `./*[@Select]`  
  
## <a name="example"></a>Przykład  
 Poniższy kod wybiera tylko elementy, które mają `Select` atrybut.  
  
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
  
```output  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  