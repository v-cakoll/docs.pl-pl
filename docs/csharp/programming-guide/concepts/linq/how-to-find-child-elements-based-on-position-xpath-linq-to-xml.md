---
title: Jak znaleźć elementy podrzędne na podstawie pozycji (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: cc0ff5639345d36ebb0423a12b66de8f1a70ade1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141120"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a><span data-ttu-id="af84b-102">Jak znaleźć elementy podrzędne na podstawie pozycji (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="af84b-102">How to find child elements based on position (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="af84b-103">Czasami chcesz znaleźć elementy na podstawie ich pozycji.</span><span class="sxs-lookup"><span data-stu-id="af84b-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="af84b-104">Możesz chcieć znaleźć drugi element lub możesz chcieć znaleźć trzeci za pośrednictwem piątego elementu.</span><span class="sxs-lookup"><span data-stu-id="af84b-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="af84b-105">Wyrażenie XPath jest następujące:</span><span class="sxs-lookup"><span data-stu-id="af84b-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="af84b-106">Istnieją dwa podejścia do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pisania tej kwerendy w sposób leniwy.</span><span class="sxs-lookup"><span data-stu-id="af84b-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="af84b-107">Można użyć <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> operatorów lub można <xref:System.Linq.Enumerable.Where%2A> użyć przeciążenia, który ma indeks.</span><span class="sxs-lookup"><span data-stu-id="af84b-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="af84b-108">Korzystając z <xref:System.Linq.Enumerable.Where%2A> przeciążenia, należy użyć wyrażenia lambda, który przyjmuje dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="af84b-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="af84b-109">W poniższym przykładzie przedstawiono obie metody wybierania na podstawie pozycji.</span><span class="sxs-lookup"><span data-stu-id="af84b-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af84b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="af84b-110">Example</span></span>  
 <span data-ttu-id="af84b-111">W tym przykładzie znajduje `Test` drugi przez czwarty element.</span><span class="sxs-lookup"><span data-stu-id="af84b-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="af84b-112">Wynik jest zbiorem elementów.</span><span class="sxs-lookup"><span data-stu-id="af84b-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="af84b-113">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Konfiguracja testu (LINQ do XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="af84b-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="af84b-114">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="af84b-114">This example produces the following output:</span></span>  
  
```output  
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
