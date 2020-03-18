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
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a>Jak znaleźć elementy podrzędne na podstawie pozycji (XPath-LINQ do XML) (C#)
Czasami chcesz znaleźć elementy na podstawie ich pozycji. Możesz chcieć znaleźć drugi element lub możesz chcieć znaleźć trzeci za pośrednictwem piątego elementu.  
  
 Wyrażenie XPath jest następujące:  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 Istnieją dwa podejścia do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pisania tej kwerendy w sposób leniwy. Można użyć <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> operatorów lub można <xref:System.Linq.Enumerable.Where%2A> użyć przeciążenia, który ma indeks. Korzystając z <xref:System.Linq.Enumerable.Where%2A> przeciążenia, należy użyć wyrażenia lambda, który przyjmuje dwa argumenty. W poniższym przykładzie przedstawiono obie metody wybierania na podstawie pozycji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie znajduje `Test` drugi przez czwarty element. Wynik jest zbiorem elementów.  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Konfiguracja testu (LINQ do XML)](./sample-xml-file-test-configuration-linq-to-xml.md).  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
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
