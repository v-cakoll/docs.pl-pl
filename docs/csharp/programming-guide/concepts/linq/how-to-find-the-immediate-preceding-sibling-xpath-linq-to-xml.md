---
title: 'Instrukcje: Znajdowanie bezpośrednio poprzednich elementów równorzędnych (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 7d1d49f262b13f769ab1d28de8b75d214d8abe64
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486716"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a>Instrukcje: Znajdowanie bezpośrednio poprzednich elementów równorzędnych (XPath-LINQ to XML) (C#)
Czasami trzeba znajdowanie bezpośrednio poprzednich elementów równorzędnych węzła. Ze względu na różnice w semantyce pozycyjne predykatów dla osi poprzedni element równorzędny w wyrażenie XPath, w przeciwieństwie do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], jest to jedna z bardziej interesujące porównania.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytanie używa <xref:System.Linq.Enumerable.Last%2A> operatora, aby znaleźć ostatniego węzła w kolekcji zwróconej przez <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>. Z drugiej strony wyrażenie XPath używa predykatu o wartości 1, można znaleźć bezpośrednio poprzedzający element.  
  
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
  
```  
Results are identical  
<Child3 />  
```  
