---
title: 'Instrukcje: Znajdowanie bezpośrednio poprzednich elementów równorzędnych (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: 81113c30cae0eb29fe0cf4b783fb031156353130
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572477"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="b38ec-102">Instrukcje: Znajdowanie bezpośrednio poprzednich elementów równorzędnych (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b38ec-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b38ec-103">Czasami trzeba znajdowanie bezpośrednio poprzednich elementów równorzędnych węzła.</span><span class="sxs-lookup"><span data-stu-id="b38ec-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="b38ec-104">Ze względu na różnice w semantyce pozycyjne predykatów dla osi poprzedni element równorzędny w wyrażenie XPath, w przeciwieństwie do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], jest to jedna z bardziej interesujące porównania.</span><span class="sxs-lookup"><span data-stu-id="b38ec-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b38ec-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b38ec-105">Example</span></span>  
 <span data-ttu-id="b38ec-106">W tym przykładzie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytanie używa <xref:System.Linq.Enumerable.Last%2A> operatora, aby znaleźć ostatniego węzła w kolekcji zwróconej przez <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="b38ec-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="b38ec-107">Z drugiej strony wyrażenie XPath używa predykatu o wartości 1, można znaleźć bezpośrednio poprzedzający element.</span><span class="sxs-lookup"><span data-stu-id="b38ec-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
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
  
 <span data-ttu-id="b38ec-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b38ec-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="b38ec-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b38ec-109">See also</span></span>
- [<span data-ttu-id="b38ec-110">LINQ to XML dla użytkowników metody XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b38ec-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
