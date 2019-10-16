---
title: 'Instrukcje: wyszukiwanie bezpośrednio poprzedzającego elementu równorzędnego (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: bc54239d2ddaafcc46413ed13c274449daaba0c7
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320600"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a>Instrukcje: wyszukiwanie bezpośrednio poprzedzającego elementu równorzędnego (XPath-LINQ to XML) (Visual Basic)
Czasami chcesz znaleźć bezpośrednio poprzedni element równorzędny do węzła. Ze względu na różnicę w semantyce predykatów pozycyjnych dla poprzedzających osi elementów równorzędnych w XPath, w przeciwieństwie do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], jest to jedno z bardziej interesujących porównań.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zapytanie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] używa operatora <xref:System.Linq.Enumerable.Last%2A> w celu znalezienia ostatniego węzła w kolekcji zwróconej przez <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>. Z kolei wyrażenie XPath używa predykatu o wartości 1, aby znaleźć bezpośrednio poprzedzający element.  
  
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
  
```console
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML dla użytkowników XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
