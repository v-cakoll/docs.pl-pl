---
title: Zdarzenia LINQ to XML
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: d00f6f1b2a14ac73c1bcd4a1f74b9714ca304da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368819"
---
# <a name="linq-to-xml-events-visual-basic"></a>Zdarzenia LINQ to XML (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zdarzenia umożliwiają otrzymywanie powiadomień, gdy drzewo XML zostanie zmienione.  
  
 Zdarzenia można dodać do wystąpienia dowolnego <xref:System.Xml.Linq.XObject> . Procedura obsługi zdarzeń będzie następnie otrzymywać zdarzenia dotyczące modyfikacji tego <xref:System.Xml.Linq.XObject> elementu i jego elementów podrzędnych. Na przykład można dodać program obsługi zdarzeń do elementu głównego drzewa i obsłużyć wszystkie modyfikacje drzewa z tego programu obsługi zdarzeń.  
  
 Przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zdarzeń można znaleźć w tematach <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed> .  
  
## <a name="types-and-events"></a>Typy i zdarzenia  
 Następujące typy są używane podczas pracy ze zdarzeniami:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Określa typ zdarzenia, gdy zdarzenie jest zgłaszane dla elementu <xref:System.Xml.Linq.XObject> .|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Dostarcza dane dla <xref:System.Xml.Linq.XObject.Changing> zdarzeń i <xref:System.Xml.Linq.XObject.Changed> .|  
  
 Podczas modyfikowania drzewa XML są zgłaszane następujące zdarzenia:  
  
|Wydarzenie|Opis|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Występuje tuż przed tym <xref:System.Xml.Linq.XObject> lub dowolnym z jego obiektów podrzędnych zostanie zmieniony.|  
|<xref:System.Xml.Linq.XObject.Changed>|Występuje po <xref:System.Xml.Linq.XObject> zmianie lub dowolnych jego elementów podrzędnych.|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Zdarzenia są przydatne, gdy chcesz zachować pewne zagregowane informacje w drzewie XML. Na przykład możesz chcieć zachować sumę faktury, która jest sumą wierszy faktury. Ten przykład używa zdarzeń, aby zachować sumę wszystkich elementów podrzędnych w ramach elementu złożonego `Items` .  
  
### <a name="code"></a>Kod  
  
```vb  
Module Module1  
    Dim WithEvents items As XElement = Nothing  
    Dim total As XElement = Nothing  
    Dim root As XElement = _  
            <Root>  
                <Total>0</Total>  
                <Items></Items>  
            </Root>  
  
    Private Sub XObjectChanged( _  
            ByVal sender As Object, _  
            ByVal cea As XObjectChangeEventArgs) _  
            Handles items.Changed  
        Select Case cea.ObjectChange  
            Case XObjectChange.Add  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
            Case XObjectChange.Remove  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
        End Select  
        Console.WriteLine("Changed {0} {1}", _  
                            sender.GetType().ToString(), _  
                            cea.ObjectChange.ToString())  
    End Sub  
  
    Sub Main()  
        total = root.<Total>(0)  
        items = root.<Items>(0)  
        items.SetElementValue("Item1", 25)  
        items.SetElementValue("Item2", 50)  
        items.SetElementValue("Item2", 75)  
        items.SetElementValue("Item3", 133)  
        items.SetElementValue("Item1", Nothing)  
        items.SetElementValue("Item4", 100)  
        Console.WriteLine("Total:{0}", CInt(total))  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Komentarze  
 Ten kod generuje następujące dane wyjściowe:  
  
```console  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Zaawansowane programowanie LINQ to XML (Visual Basic)](advanced-linq-to-xml-programming.md)
