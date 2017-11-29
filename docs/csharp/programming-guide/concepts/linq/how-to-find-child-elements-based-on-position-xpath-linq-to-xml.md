---
title: "Porady: znajdowanie elementów podrzędnych na podstawie pozycji (XPath-LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: df586c74d46513122029b3f5fdb5bec4f7b6003b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a><span data-ttu-id="40a17-102">Porady: znajdowanie elementów podrzędnych na podstawie pozycji (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="40a17-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="40a17-103">Czasami chcesz znaleźć elementy na podstawie ich pozycji.</span><span class="sxs-lookup"><span data-stu-id="40a17-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="40a17-104">Możesz chcieć znaleźć drugi element lub możesz chcieć znaleźć innych za pomocą elementu piątego.</span><span class="sxs-lookup"><span data-stu-id="40a17-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="40a17-105">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="40a17-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="40a17-106">Istnieją dwa podejścia do zapisu to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania w sposób opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="40a17-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="40a17-107">Można użyć <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> operatory lub użyć <xref:System.Linq.Enumerable.Where%2A> przeciążenia, które przyjmuje indeksu.</span><span class="sxs-lookup"><span data-stu-id="40a17-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="40a17-108">Jeśli używasz <xref:System.Linq.Enumerable.Where%2A> przeciążenia, użyj wyrażenia lambda, która przyjmuje dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="40a17-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="40a17-109">W poniższym przykładzie przedstawiono obie metody wybierania, na podstawie pozycji.</span><span class="sxs-lookup"><span data-stu-id="40a17-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40a17-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="40a17-110">Example</span></span>  
 <span data-ttu-id="40a17-111">W tym przykładzie znajduje drugiego do czwartego `Test` elementu.</span><span class="sxs-lookup"><span data-stu-id="40a17-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="40a17-112">Wynik jest kolekcją elementów.</span><span class="sxs-lookup"><span data-stu-id="40a17-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="40a17-113">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: konfiguracji testu (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="40a17-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement testCfg = XElement.Load("TestConfig.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    testCfg  
    .Elements("Test")  
    .Skip(1)  
    .Take(3);  
  
// LINQ to XML query  
IEnumerable<XElement> list2 =  
    testCfg  
    .Elements("Test")  
    .Where((el, idx) => idx >= 1 && idx <= 3);  
  
// XPath expression  
IEnumerable<XElement> list3 =  
  testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]");  
  
if (list1.Count() == list2.Count() &&  
    list1.Count() == list3.Count() &&  
    list1.Intersect(list2).Count() == list1.Count() &&  
    list1.Intersect(list3).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="40a17-114">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="40a17-114">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Test TestId="0002" TestType="CMD">  
  <Name>Find succeeding characters</Name>  
  <CommandLine>Examp2.EXE</CommandLine>  
  <Input>abc</Input>  
  <Output>def</Output>  
</Test>  
<Test TestId="0003" TestType="GUI">  
  <Name>Convert multiple numbers to strings</Name>  
  <CommandLine>Examp2.EXE /Verbose</CommandLine>  
  <Input>123</Input>  
  <Output>One Two Three</Output>  
</Test>  
<Test TestId="0004" TestType="GUI">  
  <Name>Find correlated key</Name>  
  <CommandLine>Examp3.EXE</CommandLine>  
  <Input>a1</Input>  
  <Output>b1</Output>  
</Test>  
```  
  
## <a name="see-also"></a><span data-ttu-id="40a17-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40a17-115">See Also</span></span>  
 [<span data-ttu-id="40a17-116">LINQ do XML dla użytkowników XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="40a17-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
