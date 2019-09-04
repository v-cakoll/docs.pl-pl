---
title: 'Instrukcje: Znajdź bezpośrednio poprzedni element równorzędny (XPath-LINQ to XML)C#()'
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: bc0a3250cf1f56ebf9a367f6472be8f3230cee5a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253630"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a>Instrukcje: Znajdź bezpośrednio poprzedni element równorzędny (XPath-LINQ to XML)C#()
Czasami chcesz znaleźć bezpośrednio poprzedni element równorzędny do węzła. Ze względu na różnicę w semantyce predykatów pozycyjnych dla poprzedzających osi elementów równorzędnych w XPath, w przeciwieństwie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]do, jest to jedno z bardziej interesujących porównań.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytanie używa operatora, <xref:System.Linq.Enumerable.Last%2A> aby znaleźć ostatni węzeł w kolekcji zwróconej przez <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>. Z kolei wyrażenie XPath używa predykatu o wartości 1, aby znaleźć bezpośrednio poprzedzający element.  
  
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
