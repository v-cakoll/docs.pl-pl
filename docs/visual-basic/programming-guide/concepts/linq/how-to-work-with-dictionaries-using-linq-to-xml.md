---
title: 'Porady: Praca z słowniki za pomocą LINQ do XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: b6e41f61358563472f49b22df389df00e721503e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644826"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a>Porady: Praca z słowniki za pomocą LINQ do XML (Visual Basic)
Często jest to wygodny do przekonwertowania odmian struktur danych XML i XML inne struktury danych. W tym temacie przedstawiono konkretnej implementacji tego podejścia ogólne konwertując <xref:System.Collections.Generic.Dictionary%602> XML i na odwrót.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używane literały XML i zapytanie w wyrażenia osadzonego. Nowe projekty zapytania <xref:System.Xml.Linq.XElement> obiekty, które następnie stają się nowa zawartość `Root` <xref:System.Xml.Linq.XElement> obiektu.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Projekcje i przekształcenia (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
