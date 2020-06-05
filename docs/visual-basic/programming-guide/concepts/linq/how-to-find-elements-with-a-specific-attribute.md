---
title: 'Instrukcje: znajdowanie elementów o określonym atrybucie (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 4bb38d2c-bc7c-4196-8909-aaf41fb86b28
ms.openlocfilehash: 4b625fcccc834f860072ad92587bbfd7ed5ec4ad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364776"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="9fb13-102">Instrukcje: Znajdowanie elementów z określonym atrybutem (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fb13-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="9fb13-103">Czasami chcesz znaleźć wszystkie elementy, które mają określony atrybut.</span><span class="sxs-lookup"><span data-stu-id="9fb13-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="9fb13-104">Nie dotyczy zawartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9fb13-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="9fb13-105">Zamiast tego należy wybrać opcję na podstawie istnienia atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9fb13-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="9fb13-106">Wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="9fb13-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="9fb13-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9fb13-107">Example</span></span>  
 <span data-ttu-id="9fb13-108">Poniższy kod wybiera tylko elementy, które mają `Select` atrybut.</span><span class="sxs-lookup"><span data-stu-id="9fb13-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
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
  
 <span data-ttu-id="9fb13-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9fb13-109">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fb13-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fb13-110">See also</span></span>

- [<span data-ttu-id="9fb13-111">LINQ to XML dla użytkowników XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fb13-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
