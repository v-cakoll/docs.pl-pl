---
title: 'Instrukcje: praca ze słownikami przy użyciu LINQ to XML'
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: 14c9c35693f323292849f01af79ae81f92921611
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397677"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a>Instrukcje: korzystanie ze słowników przy użyciu LINQ to XML (Visual Basic)
Często wygodnie jest przekonwertować różne struktury danych na XML, a następnie XML z powrotem do innych struktur danych. W tym temacie przedstawiono określoną implementację ogólnego podejścia poprzez konwersję <xref:System.Collections.Generic.Dictionary%602> do formatu XML i z powrotem.  
  
## <a name="example"></a>Przykład  
 Ten przykład używa literałów XML i zapytania w wyrażeniu osadzonym. Zapytanie projektuje nowe <xref:System.Xml.Linq.XElement> obiekty, które następnie staje się nową zawartością dla `Root` <xref:System.Xml.Linq.XElement> obiektu.  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy słownik z pliku XML.  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```console  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>Zobacz też

- [Projekcje i przekształcenia (LINQ to XML) (Visual Basic)](projections-and-transformations-linq-to-xml.md)
