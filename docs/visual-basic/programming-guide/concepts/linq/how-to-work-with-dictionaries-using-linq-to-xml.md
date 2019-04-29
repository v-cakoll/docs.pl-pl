---
title: 'Instrukcje: Praca ze słownikami przy użyciu LINQ to XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: def00fcd356472825ebc4b9f5c306cf3547991e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614148"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a>Instrukcje: Praca ze słownikami przy użyciu LINQ to XML (Visual Basic)
Często jest to wygodne przekonwertować różne typy struktur danych XML i XML do innych struktur danych. W tym temacie przedstawiono określoną implementację tego podejścia ogólne, konwertując <xref:System.Collections.Generic.Dictionary%602> XML i na odwrót.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa literały XML i zapytanie w wyrażeniu osadzonych. Nowe projekty zapytania <xref:System.Xml.Linq.XElement> obiekty, które następnie stają się nowej zawartości dla `Root` <xref:System.Xml.Linq.XElement> obiektu.  
  
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
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>Zobacz także

- [Projekcje i przekształcenia (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
