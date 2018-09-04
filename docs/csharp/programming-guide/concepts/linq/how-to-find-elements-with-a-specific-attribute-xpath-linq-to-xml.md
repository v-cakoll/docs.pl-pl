---
title: 'Porady: znajdowanie elementów o określonym atrybucie (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: da7633b34ddd61577bfc62f4f76d8f8929be1cc4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500283"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="450b2-102">Porady: znajdowanie elementów o określonym atrybucie (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="450b2-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="450b2-103">Czasami chcesz znaleźć wszystkie elementy, które mają określony atrybut.</span><span class="sxs-lookup"><span data-stu-id="450b2-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="450b2-104">Nie masz zajmującym się ochroną zawartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="450b2-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="450b2-105">Zamiast tego chcesz wybrać na podstawie istnienia atrybutu.</span><span class="sxs-lookup"><span data-stu-id="450b2-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="450b2-106">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="450b2-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="450b2-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="450b2-107">Example</span></span>  
 <span data-ttu-id="450b2-108">Poniższy kod wybiera tylko elementy, które mają `Select` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="450b2-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(  
@"<Root>  
    <Child1>1</Child1>  
    <Child2 Select='true'>2</Child2>  
    <Child3>3</Child3>  
    <Child4 Select='true'>4</Child4>  
    <Child5>5</Child5>  
</Root>");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    from el in doc.Elements()  
    where el.Attribute("Select") != null  
    select el;  
  
// XPath expression  
IEnumerable<XElement> list2 =  
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="450b2-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="450b2-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="450b2-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="450b2-110">See Also</span></span>

- [<span data-ttu-id="450b2-111">LINQ to XML dla użytkowników metody XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="450b2-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
