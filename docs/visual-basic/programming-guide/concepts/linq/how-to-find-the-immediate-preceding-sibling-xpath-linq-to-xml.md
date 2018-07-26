---
title: 'Porady: znajdowanie bezpośrednio poprzednich elementów równorzędnych (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: 47ba557343d0f691c2ee0f2c56102df313ecfb30
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39220925"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a>Porady: znajdowanie bezpośrednio poprzednich elementów równorzędnych (XPath-LINQ to XML) (Visual Basic)
Czasami trzeba znajdowanie bezpośrednio poprzednich elementów równorzędnych węzła. Ze względu na różnice w semantyce pozycyjne predykatów dla osi poprzedni element równorzędny w wyrażenie XPath, w przeciwieństwie do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], jest to jedna z bardziej interesujące porównania.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytanie używa <xref:System.Linq.Enumerable.Last%2A> operatora, aby znaleźć ostatniego węzła w kolekcji zwróconej przez <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>. Z drugiej strony wyrażenie XPath używa predykatu o wartości 1, można znaleźć bezpośrednio poprzedzający element.  
  
```vb  
Dim root As XElement = _   
    <Root>  
        <Child1/>  
        <Child2/>  
        <Child3/>  
        <Child4/>  
    </Root>  
Dim child4 As XElement = root.Element("Child4")  
  
' LINQ to XML query  
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()  
  
' XPath expression  
Dim el2 As XElement = _  
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _  
    IEnumerable).Cast(Of XElement)().First()  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to XML dla użytkowników metody XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
