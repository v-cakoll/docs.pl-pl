---
title: 'Instrukcje: znajdowanie bezpośrednio poprzednich elementów równorzędnych (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: 8b0071b2f39b8debdd52083718fe928c1f9fb6f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364529"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a>Instrukcje: wyszukiwanie bezpośrednio poprzedzającego elementu równorzędnego (XPath-LINQ to XML) (Visual Basic)

Czasami chcesz znaleźć bezpośrednio poprzedni element równorzędny do węzła. Ze względu na różnicę w semantyce predykatów pozycyjnych dla poprzedzających osi elementów równorzędnych w XPath, w przeciwieństwie do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , jest to jedno z bardziej interesujących porównań.

## <a name="example"></a>Przykład

W tym przykładzie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytanie używa <xref:System.Linq.Enumerable.Last%2A> operatora, aby znaleźć ostatni węzeł w kolekcji zwróconej przez <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> . Z kolei wyrażenie XPath używa predykatu o wartości 1, aby znaleźć bezpośrednio poprzedzający element.

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

## <a name="see-also"></a>Zobacz też

- [LINQ to XML dla użytkowników XPath (Visual Basic)](linq-to-xml-for-xpath-users.md)
