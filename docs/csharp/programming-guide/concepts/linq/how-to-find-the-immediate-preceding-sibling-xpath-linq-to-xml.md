---
title: "Porady: znajdowanie natychmiastowego poprzedniego elementu równorzędnego (XPath-LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 88a27b15fb46651d5a4c3a8e2ac8a357b600dec2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="b9e98-102">Porady: znajdowanie natychmiastowego poprzedniego elementu równorzędnego (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b9e98-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="b9e98-103">Czasami chcesz znaleźć natychmiastowego poprzedniego elementu równorzędnego do węzła.</span><span class="sxs-lookup"><span data-stu-id="b9e98-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="b9e98-104">Z powodu różnic w semantykę pozycyjnych predykatów dla powyższej osi element równorzędny XPath w przeciwieństwie do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], jest to jedna z bardziej interesującego porównania.</span><span class="sxs-lookup"><span data-stu-id="b9e98-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9e98-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9e98-105">Example</span></span>  
 <span data-ttu-id="b9e98-106">W tym przykładzie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytanie używa <xref:System.Linq.Enumerable.Last%2A> operator można znaleźć w kolekcji zwróconej przez ostatni węzeł <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="b9e98-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="b9e98-107">Z kolei wyrażenie XPath użycie predykatu o wartości 1 w celu znalezienia natychmiast poprzedni element.</span><span class="sxs-lookup"><span data-stu-id="b9e98-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
    @"<Root>  
    <Child1/>  
    <Child2/>  
    <Child3/>  
    <Child4/>  
</Root>");  
XElement child4 = root.Element("Child4");  
  
// LINQ to XML query  
XElement el1 =  
    child4  
    .ElementsBeforeSelf()  
    .Last();  
  
// XPath expression  
XElement el2 =  
    ((IEnumerable)child4  
                 .XPathEvaluate("preceding-sibling::*[1]"))  
                 .Cast<XElement>()  
                 .First();  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="b9e98-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b9e98-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9e98-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9e98-109">See Also</span></span>  
 [<span data-ttu-id="b9e98-110">LINQ do XML dla użytkowników XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="b9e98-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
