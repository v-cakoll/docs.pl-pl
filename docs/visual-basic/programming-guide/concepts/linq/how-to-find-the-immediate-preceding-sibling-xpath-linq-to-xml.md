---
title: 'Porady: znajdowanie natychmiastowego poprzedniego elementu równorzędnego (XPath-LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: 47ba557343d0f691c2ee0f2c56102df313ecfb30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641118"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="259e5-102">Porady: znajdowanie natychmiastowego poprzedniego elementu równorzędnego (XPath-LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="259e5-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="259e5-103">Czasami chcesz znaleźć natychmiastowego poprzedniego elementu równorzędnego do węzła.</span><span class="sxs-lookup"><span data-stu-id="259e5-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="259e5-104">Z powodu różnic w semantykę pozycyjnych predykatów dla powyższej osi element równorzędny XPath w przeciwieństwie do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], jest to jedna z bardziej interesującego porównania.</span><span class="sxs-lookup"><span data-stu-id="259e5-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="259e5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="259e5-105">Example</span></span>  
 <span data-ttu-id="259e5-106">W tym przykładzie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytanie używa <xref:System.Linq.Enumerable.Last%2A> operator można znaleźć w kolekcji zwróconej przez ostatni węzeł <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="259e5-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="259e5-107">Z kolei wyrażenie XPath użycie predykatu o wartości 1 w celu znalezienia natychmiast poprzedni element.</span><span class="sxs-lookup"><span data-stu-id="259e5-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
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
  
 <span data-ttu-id="259e5-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="259e5-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="259e5-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="259e5-109">See Also</span></span>  
 [<span data-ttu-id="259e5-110">LINQ do XML dla wyrażenia XPath użytkowników (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="259e5-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
