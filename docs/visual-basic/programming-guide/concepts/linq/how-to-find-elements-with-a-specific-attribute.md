---
title: 'Instrukcje: Znajdowanie elementów o określonym atrybucie (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 4bb38d2c-bc7c-4196-8909-aaf41fb86b28
ms.openlocfilehash: 0efc0d6cebce760d90213d5149ca729a7b04663e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654428"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="278ff-102">Instrukcje: Znajdowanie elementów o określonym atrybucie (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="278ff-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="278ff-103">Czasami chcesz znaleźć wszystkie elementy, które mają określony atrybut.</span><span class="sxs-lookup"><span data-stu-id="278ff-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="278ff-104">Nie masz zajmującym się ochroną zawartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="278ff-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="278ff-105">Zamiast tego chcesz wybrać na podstawie istnienia atrybutu.</span><span class="sxs-lookup"><span data-stu-id="278ff-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="278ff-106">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="278ff-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="278ff-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="278ff-107">Example</span></span>  
 <span data-ttu-id="278ff-108">Poniższy kod wybiera tylko elementy, które mają `Select` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="278ff-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
```vb  
Dim doc As XElement = _   
    <Root>  
        <Child1>1</Child1>  
        <Child2 Select='true'>2</Child2>  
        <Child3>3</Child3>  
        <Child4 Select='true'>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    From el In doc.Elements() _  
    Where el.@Select <> Nothing _  
    Select el  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = DirectCast(doc.XPathEvaluate _  
    ("./*[@Select]"), IEnumerable).Cast(Of XElement)()  
  
If list1.Count() = list2.Count() And _  
    list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="278ff-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="278ff-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="278ff-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="278ff-110">See also</span></span>
- [<span data-ttu-id="278ff-111">LINQ to XML dla użytkowników metody XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="278ff-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
