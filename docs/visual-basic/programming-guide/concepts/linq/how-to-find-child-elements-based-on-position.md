---
title: 'Porady: znajdowanie elementów podrzędnych na podstawie pozycji (XPath-LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
ms.openlocfilehash: 9f18da12786b4c44dc21e54c8d5020f49ef9ecb6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="7d795-102">Porady: znajdowanie elementów podrzędnych na podstawie pozycji (XPath-LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d795-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="7d795-103">Czasami chcesz znaleźć elementy na podstawie ich pozycji.</span><span class="sxs-lookup"><span data-stu-id="7d795-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="7d795-104">Możesz chcieć znaleźć drugi element lub możesz chcieć znaleźć innych za pomocą elementu piątego.</span><span class="sxs-lookup"><span data-stu-id="7d795-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="7d795-105">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="7d795-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="7d795-106">Istnieją dwa podejścia do zapisu to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania w sposób opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="7d795-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="7d795-107">Można użyć <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> operatory lub użyć <xref:System.Linq.Enumerable.Where%2A> przeciążenia, które przyjmuje indeksu.</span><span class="sxs-lookup"><span data-stu-id="7d795-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="7d795-108">Jeśli używasz <xref:System.Linq.Enumerable.Where%2A> przeciążenia, użyj wyrażenia lambda, która przyjmuje dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="7d795-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="7d795-109">W poniższym przykładzie przedstawiono obie metody wybierania, na podstawie pozycji.</span><span class="sxs-lookup"><span data-stu-id="7d795-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d795-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d795-110">Example</span></span>  
 <span data-ttu-id="7d795-111">W tym przykładzie znajduje drugiego do czwartego `Test` elementu.</span><span class="sxs-lookup"><span data-stu-id="7d795-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="7d795-112">Wynik jest kolekcją elementów.</span><span class="sxs-lookup"><span data-stu-id="7d795-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="7d795-113">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: konfiguracji testu (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7d795-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```vb  
Dim testCfg As XElement = XElement.Load("TestConfig.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test").Skip(1).Take(3)  
  
'LINQ to XML query  
Dim list2 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test"). _  
    Where(Function(ByVal el, ByVal idx) idx >= 1 And idx <= 3)  
  
' XPath expression  
Dim list3 As IEnumerable(Of XElement) = _  
    testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]")  
  
If list1.Count() = list2.Count() And _  
       list1.Count() = list3.Count() And _  
       list1.Intersect(list2).Count() = list1.Count() And _  
       list1.Intersect(list3).Count() = list1.Count() Then  
  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="7d795-114">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7d795-114">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d795-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d795-115">See Also</span></span>  
 [<span data-ttu-id="7d795-116">LINQ do XML dla wyrażenia XPath użytkowników (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d795-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
