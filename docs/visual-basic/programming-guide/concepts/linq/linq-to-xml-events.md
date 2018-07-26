---
title: Zdarzenia LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: 216c2af87d2ae3a767548ccaa1efe118215cc6a0
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245289"
---
# <a name="linq-to-xml-events-visual-basic"></a>Zdarzenia LINQ to XML (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zdarzenia umożliwiają otrzymasz powiadomienie, gdy zostanie zmieniona drzewa XML.  
  
 Można dodać zdarzenia do dowolnego wystąpienia <xref:System.Xml.Linq.XObject>. Zadzwonimy zdarzenia dla zmian do tego programu obsługi zdarzeń <xref:System.Xml.Linq.XObject> i wszystkich jego obiektów podrzędnych. Na przykład możesz dodać program obsługi zdarzeń do katalogu głównego drzewa i obsługiwać wszystkie modyfikacje w drzewie z tej obsługi zdarzeń.  
  
 Przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zdarzenia, zobacz <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed>.  
  
## <a name="types-and-events"></a>Typy i zdarzenia  
 Podczas pracy ze zdarzeniami należy użyć następujących typów:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Określa typ zdarzenia, gdy zdarzenie jest wywoływane dla <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Udostępnia dane dla <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed> zdarzenia.|  
  
 Następujące zdarzenia są wywoływane, gdy modyfikowanie drzewa XML:  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Występuje zaraz przed tym <xref:System.Xml.Linq.XObject> lub przechodzi do dowolnego z jego obiektów podrzędnych do zmiany.|  
|<xref:System.Xml.Linq.XObject.Changed>|Występuje, gdy <xref:System.Xml.Linq.XObject> został zmieniony lub dowolnego z jego elementy podrzędne zostały zmienione.|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Zdarzenia są przydatne, gdy użytkownik chce przechowywać pewne informacje agregacji w drzewie XML. Na przykład można zachować Suma faktury, która jest sumą pozycje faktury. W tym przykładzie użyto zdarzeń do obsługi sumę wszystkich elementów podrzędnych w elemencie złożonych `Items`.  
  
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
  
```  
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
 [Zaawansowane LINQ to XML programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
