---
title: "Porady: znajdowanie elementów z określonym atrybutem (XPath-LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66053135dbfdf6f61ff1f09b846acd9d9cfe054f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="69fc1-102">Porady: znajdowanie elementów z określonym atrybutem (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="69fc1-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="69fc1-103">Czasami chcesz znaleźć wszystkie elementy, które mają określony atrybut.</span><span class="sxs-lookup"><span data-stu-id="69fc1-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="69fc1-104">Nie masz obawy zawartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="69fc1-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="69fc1-105">Zamiast tego chcesz wybrać na podstawie istnienia atrybutu.</span><span class="sxs-lookup"><span data-stu-id="69fc1-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="69fc1-106">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="69fc1-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="69fc1-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="69fc1-107">Example</span></span>  
 <span data-ttu-id="69fc1-108">Poniższy kod wybiera tylko elementów, które mają `Select` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="69fc1-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
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
  
 <span data-ttu-id="69fc1-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="69fc1-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="69fc1-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69fc1-110">See Also</span></span>  
 [<span data-ttu-id="69fc1-111">LINQ do XML dla użytkowników XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="69fc1-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
