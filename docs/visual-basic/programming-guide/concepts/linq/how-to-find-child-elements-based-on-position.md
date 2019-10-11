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
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a>Instrukcje: Znajdowanie elementów podrzędnych na podstawie pozycji (XPath-LINQ to XML) (Visual Basic)
Czasami chcesz znaleźć elementy na podstawie ich położenia. Może być konieczne znalezienie drugiego elementu lub znalezienie trzeciej przez piąty element.  
  
 Wyrażenie XPath:  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 Istnieją dwa podejścia do pisania tego zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w sposób opóźniony. Można użyć operatorów <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> lub użyć przeciążenia <xref:System.Linq.Enumerable.Where%2A>, które przyjmuje indeks. W przypadku używania przeciążenia <xref:System.Linq.Enumerable.Where%2A> należy użyć wyrażenia lambda, które przyjmuje dwa argumenty. W poniższym przykładzie przedstawiono obie metody wyboru na podstawie pozycji.  
  
## <a name="example"></a>Przykład  
 Ten przykład wyszukuje sekundę za pomocą czwartego elementu `Test`. Wynik jest kolekcją elementów.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Konfiguracja testu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).  
  
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
  
 Ten przykład generuje następujące dane wyjściowe:  
  
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
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML dla użytkowników XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
