---
title: 'Porady: strumienia fragmenty XML z dostępem do informacji w nagłówku (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: 60ec63c33d20fa38bed32d9c46c4acfe649ecd15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644475"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a>Porady: strumienia fragmenty XML z dostępem do informacji w nagłówku (Visual Basic)
Czasami trzeba arbitralnie duże pliki XML do odczytu i zapisu aplikacji, dzięki czemu zużycie pamięci aplikacji jest atrybutem wartości prognozowanych. Przy próbie wypełnić drzewo XML z dużego pliku XML, użycie pamięci będzie proporcjonalny do rozmiaru pliku — to znaczy nadmierne. W związku z tym należy w zamian użyj technika przesyłania strumieniowego.  
  
 Jedną z opcji jest napisanie swojej aplikacji za pomocą <xref:System.Xml.XmlReader>. Jednak możesz chcieć użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do badania drzewo składni XML. Jeśli jest to możliwe, można napisać metodę niestandardowych osi. Aby uzyskać więcej informacji, zobacz [porady: pisanie LINQ do metody osi XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).  
  
 Aby napisać metodę osi, zapisu małych metody, która używa <xref:System.Xml.XmlReader> odczytać węzłów, dopóki nie osiągnie jednego z węzłów, w których jesteś zainteresowany. Następnie wywołuje metodę <xref:System.Xml.Linq.XNode.ReadFrom%2A>, która odczytuje z <xref:System.Xml.XmlReader> i tworzy XML fragment. Następnie można pisać zapytania LINQ metodę niestandardowych osi.  
  
 Techniki przesyłania strumieniowego najlepiej są stosowane w sytuacji, gdy musisz przetworzyć dokumentu źródłowego tylko raz i może przetwarzać elementów w kolejności dokumentu. Niektóre standardowy kwerendy operatorów, takich jak <xref:System.Linq.Enumerable.OrderBy%2A>, iteracji ich źródłem Zbieraj wszystkie dane, sortowanie ich i ostatecznie yield pierwszego elementu w sekwencji. Należy pamiętać, że użycie operatora zapytania, który zostaje źródła przed reaguje pierwszy element, możesz nie zostaną zachowane zużycie pamięci.  
  
## <a name="example"></a>Przykład  
 Czasami problem pobiera małą ilością interesujące więcej. W następującym dokumencie XML konsumenta metodę niestandardowych osi również musi znać nazwę każdego elementu należącego do klienta.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
 Podejście, które przyjmuje w tym przykładzie jest również obejrzeć takie informacje nagłówka, Zapisz informacje nagłówka i późniejszego kompilowania małych drzewa XML, który zawiera informacje o nagłówku i szczegóły są wyliczania. Metoda osi następnie daje w wyniku tego nowego, mała drzewa XML. Zapytanie następnie ma dostęp do informacji w nagłówku, a także szczegółowe informacje.  
  
 Takie podejście charakteryzuje się zużycie pamięci. Jak każdego fragmentu XML szczegółów jest zwróciło, nie będą przechowywane żadnych odwołań do poprzedniego fragmentu, i jest dostępny dla wyrzucanie elementów bezużytecznych. Należy pamiętać, że ta metoda tworzy wiele obiektów krótko na stosie.  
  
 Poniższy przykład pokazuje, jak do wdrożenia i używa metody osi niestandardowych strumieni fragmenty XML z pliku określonego przez identyfikator URI. Tej osi niestandardowe są zapisywane w szczególności taki sposób, że oczekuje, że dokument, który ma `Customer`, `Name`, i `Item` elementów i rozmieszczenia elementów jak powyższych `Source.xml` dokumentu. Jest simplistic implementacji. Czy można przygotować bardziej niezawodne implementacji przeanalizować nieprawidłowy dokument.  
  
```vb  
Module Module1  
  
    Sub Main()  
        Dim xmlTree = <Root>  
                          <%=  
                              From el In New StreamCustomerItem("Source.xml")  
                              Let itemKey = CInt(el.<Key>.Value)  
                              Where itemKey >= 3 AndAlso itemKey <= 7  
                              Select <Item>  
                                         <Customer><%= el.Parent.<Name>.Value %></Customer>  
                                         <%= el.<Key> %>  
                                     </Item>  
                          %>  
                      </Root>  
  
        Console.WriteLine(xmlTree)  
    End Sub  
  
End Module  
  
Public Class StreamCustomerItem  
    Implements IEnumerable(Of XElement)  
  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamCustomerItemEnumerator(_uri)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamCustomerItemEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _customerName As String  
    Private _reader As Xml.XmlReader  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        Dim item As XElement  
        Dim name As XElement  
  
        ' Parse the file, save header information when encountered, and return the  
        ' current Item XElement.  
  
        ' loop through Customer elements  
        While _reader.Read()  
            If _reader.NodeType = Xml.XmlNodeType.Element Then  
                Select Case _reader.Name  
                    Case "Customer"  
                        ' move to Name element  
                        While _reader.Read()  
  
                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso  
                                _reader.Name = "Name" Then  
  
                                name = TryCast(XElement.ReadFrom(_reader), XElement)  
                                _customerName = If(name IsNot Nothing, name.Value, "")  
                                Exit While  
                            End If  
  
                        End While  
                    Case "Item"  
                        item = TryCast(XElement.ReadFrom(_reader), XElement)  
                        Dim tempRoot = <Root>  
                                           <Name><%= _customerName %></Name>  
                                           <%= item %>  
                                       </Root>  
                        _current = item  
                        Return True  
                End Select  
            End If  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane LINQ do XML programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
