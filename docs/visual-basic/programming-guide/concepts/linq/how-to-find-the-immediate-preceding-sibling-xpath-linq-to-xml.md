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
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="811d3-102">Instrukcje: wyszukiwanie bezpośrednio poprzedzającego elementu równorzędnego (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="811d3-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="811d3-103">Czasami chcesz znaleźć bezpośrednio poprzedni element równorzędny do węzła.</span><span class="sxs-lookup"><span data-stu-id="811d3-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="811d3-104">Ze względu na różnicę w semantyce predykatów pozycyjnych dla poprzedzających osi elementów równorzędnych w XPath, w przeciwieństwie do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , jest to jedno z bardziej interesujących porównań.</span><span class="sxs-lookup"><span data-stu-id="811d3-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>

## <a name="example"></a><span data-ttu-id="811d3-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="811d3-105">Example</span></span>

<span data-ttu-id="811d3-106">W tym przykładzie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytanie używa <xref:System.Linq.Enumerable.Last%2A> operatora, aby znaleźć ostatni węzeł w kolekcji zwróconej przez <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> .</span><span class="sxs-lookup"><span data-stu-id="811d3-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="811d3-107">Z kolei wyrażenie XPath używa predykatu o wartości 1, aby znaleźć bezpośrednio poprzedzający element.</span><span class="sxs-lookup"><span data-stu-id="811d3-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>

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

<span data-ttu-id="811d3-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="811d3-108">This example produces the following output:</span></span>

```console
Results are identical
<Child3 />
```

## <a name="see-also"></a><span data-ttu-id="811d3-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="811d3-109">See also</span></span>

- [<span data-ttu-id="811d3-110">LINQ to XML dla użytkowników XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="811d3-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
