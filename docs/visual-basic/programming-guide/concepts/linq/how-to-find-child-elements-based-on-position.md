---
title: 'Porady: znajdowanie elementów podrzędnych na podstawie położenia (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
ms.openlocfilehash: 9f18da12786b4c44dc21e54c8d5020f49ef9ecb6
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42751947"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a>Porady: znajdowanie elementów podrzędnych na podstawie położenia (XPath-LINQ to XML) (Visual Basic)
Czasami trzeba znajdowanie elementów na podstawie ich pozycji. Możesz chcieć znaleźć drugiego elementu, lub możesz chcieć znaleźć trzeci za pośrednictwem piąty element.  
  
 Wyrażenie XPath jest:  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 Istnieją dwa podejścia do pisania to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania w taki sposób, z opóźnieniem. Możesz użyć <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> operatorów, lub użyć <xref:System.Linq.Enumerable.Where%2A> przeciążenia przyjmującego indeksu. Kiedy używasz <xref:System.Linq.Enumerable.Where%2A> przeciążenie, można użyć Wyrażenie lambda, która przyjmuje dwa argumenty. Poniższy kod przedstawia obie metody wybierania, na podstawie położenia.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyszukuje drugiego do czwartego `Test` elementu. Wynik jest kolekcją elementów.  
  
 W tym przykładzie użyto następujący dokument XML: [przykładowy plik XML: Konfiguracja testu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to XML dla użytkowników metody XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
