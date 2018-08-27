---
title: 'Porady: znajdowanie bezpośrednio poprzednich elementów równorzędnych (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 82c0ee6e7340ada18fb2077c0b8b04fb6a41671a
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935196"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a>Porady: znajdowanie bezpośrednio poprzednich elementów równorzędnych (XPath-LINQ to XML) (C#)
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
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to XML dla użytkowników metody XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
