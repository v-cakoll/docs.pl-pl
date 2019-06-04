---
title: 'Instrukcje: Znajdowanie elementów podrzędnych na podstawie położenia (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: b889c727fb59853cabc6f238c574764700dbbf3e
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485622"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a><span data-ttu-id="f7707-102">Instrukcje: Znajdowanie elementów podrzędnych na podstawie położenia (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f7707-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="f7707-103">Czasami trzeba znajdowanie elementów na podstawie ich pozycji.</span><span class="sxs-lookup"><span data-stu-id="f7707-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="f7707-104">Możesz chcieć znaleźć drugiego elementu, lub możesz chcieć znaleźć trzeci za pośrednictwem piąty element.</span><span class="sxs-lookup"><span data-stu-id="f7707-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="f7707-105">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="f7707-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="f7707-106">Istnieją dwa podejścia do pisania to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania w taki sposób, z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="f7707-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="f7707-107">Możesz użyć <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> operatorów, lub użyć <xref:System.Linq.Enumerable.Where%2A> przeciążenia przyjmującego indeksu.</span><span class="sxs-lookup"><span data-stu-id="f7707-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="f7707-108">Kiedy używasz <xref:System.Linq.Enumerable.Where%2A> przeciążenie, można użyć Wyrażenie lambda, która przyjmuje dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="f7707-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="f7707-109">Poniższy kod przedstawia obie metody wybierania, na podstawie położenia.</span><span class="sxs-lookup"><span data-stu-id="f7707-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7707-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7707-110">Example</span></span>  
 <span data-ttu-id="f7707-111">W tym przykładzie wyszukuje drugiego do czwartego `Test` elementu.</span><span class="sxs-lookup"><span data-stu-id="f7707-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="f7707-112">Wynik jest kolekcją elementów.</span><span class="sxs-lookup"><span data-stu-id="f7707-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="f7707-113">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Konfiguracja testowa (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f7707-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="f7707-114">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f7707-114">This example produces the following output:</span></span>  
  
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
