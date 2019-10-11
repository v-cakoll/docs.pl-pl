---
title: 'Instrukcje: Znajdowanie elementów podrzędnych na podstawie pozycji (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
ms.openlocfilehash: 11a9fdd7ed8565c38b0527d266af75b8fb611a20
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249693"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="24a48-102">Instrukcje: Znajdowanie elementów podrzędnych na podstawie pozycji (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24a48-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="24a48-103">Czasami chcesz znaleźć elementy na podstawie ich położenia.</span><span class="sxs-lookup"><span data-stu-id="24a48-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="24a48-104">Może być konieczne znalezienie drugiego elementu lub znalezienie trzeciej przez piąty element.</span><span class="sxs-lookup"><span data-stu-id="24a48-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="24a48-105">Wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="24a48-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="24a48-106">Istnieją dwa podejścia do pisania tego zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w sposób opóźniony.</span><span class="sxs-lookup"><span data-stu-id="24a48-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="24a48-107">Można użyć operatorów <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> lub użyć przeciążenia <xref:System.Linq.Enumerable.Where%2A>, które przyjmuje indeks.</span><span class="sxs-lookup"><span data-stu-id="24a48-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="24a48-108">W przypadku używania przeciążenia <xref:System.Linq.Enumerable.Where%2A> należy użyć wyrażenia lambda, które przyjmuje dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="24a48-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="24a48-109">W poniższym przykładzie przedstawiono obie metody wyboru na podstawie pozycji.</span><span class="sxs-lookup"><span data-stu-id="24a48-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24a48-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="24a48-110">Example</span></span>  
 <span data-ttu-id="24a48-111">Ten przykład wyszukuje sekundę za pomocą czwartego elementu `Test`.</span><span class="sxs-lookup"><span data-stu-id="24a48-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="24a48-112">Wynik jest kolekcją elementów.</span><span class="sxs-lookup"><span data-stu-id="24a48-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="24a48-113">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Konfiguracja testu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="24a48-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="24a48-114">Ten przykład generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="24a48-114">This example produces the following output:</span></span>  
  
```console  
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
  
## <a name="see-also"></a><span data-ttu-id="24a48-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24a48-115">See also</span></span>

- [<span data-ttu-id="24a48-116">LINQ to XML dla użytkowników XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24a48-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
