---
title: 'Instrukcje: Stream XML fragmentów z dostępem do informacji w nagłówku (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: c11a64eb28e8952636ab877479852bd883fc7eba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829476"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a>Instrukcje: Stream XML fragmentów z dostępem do informacji w nagłówku (Visual Basic)
Czasami trzeba przeczytać arbitralnie dużych plików XML i zapisu aplikacji, tak aby zużycie pamięci aplikacji jest przewidywalne. Jeśli użytkownik podejmie próbę wypełnianie drzewa XML przy użyciu dużego pliku XML, wykorzystanie pamięci będzie proporcjonalny do rozmiaru pliku — oznacza to, że nadmierne. W związku z tym należy zamiast tego użyj technika przesyłania strumieniowego.  
  
 Jedną z opcji jest do zapisu w swojej aplikacji za pomocą <xref:System.Xml.XmlReader>. Jednakże, możesz chcieć użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kwerendy drzewa XML. Jeśli jest to możliwe, można napisać metodę niestandardowe osi. Aby uzyskać więcej informacji, zobacz [jak: Zapis LINQ do metody osi XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).  
  
 Aby napisać własne metody osi, zapisu małych metody, która używa <xref:System.Xml.XmlReader> odczytać węzły, aż do napotkania jednego z węzłów, w których interesuje Cię. Następnie wywołuje metodę <xref:System.Xml.Linq.XNode.ReadFrom%2A>, która odczytuje z <xref:System.Xml.XmlReader> i tworzy XML fragment. Następnie można pisać zapytania LINQ metodę niestandardowe osi.  
  
 Techniki przesyłania strumieniowego najlepiej są stosowane w sytuacji, gdy trzeba przetworzyć tylko jeden raz w dokumencie źródłowym i pozwala na przetwarzanie elementów w kolejności dokumentu. Niektóre standardowe zapytanie operatorów, takich jak <xref:System.Linq.Enumerable.OrderBy%2A>iteracji ich źródła, zbieraj wszystkie dane, ją posortować i na koniec uzyskanie pierwszego elementu w sekwencji. Należy pamiętać, że użycie operatora zapytania, który materializuje źródła przed reaguje na pierwszy element, możesz nie zostaną zachowane zużycie pamięci.  
  
## <a name="example"></a>Przykład  
 Czasami problem pobiera nieco więcej interesujące. W następującym dokumencie XML konsumenta metodę niestandardowe osi ma również znać nazwę klienta, który należy do każdego elementu.  
  
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
  
 Metody, która przyjmuje w tym przykładzie jest również obejrzeć te informacje nagłówka, Zapisz informacje nagłówka, a następnie skompilować małych drzewa XML, który zawiera zarówno informacje nagłówka, jak i szczegółów, które wyliczają to. Metody osi następnie daje to nowe, małe drzewa XML. Zapytanie uzyska dostęp do informacji nagłówka, a także szczegółowe informacje.  
  
 Takie podejście ma zużycie pamięci. Zgodnie z każdego fragmentu XML szczegółów jest uzyskane, pozostają żadnych odwołań do poprzedniego fragmentu i jest dostępny dla wyrzucania elementów bezużytecznych. Należy pamiętać, że ta technika tworzy wiele krótki czas życia obiektów na stosie.  
  
 Poniższy przykład pokazuje, jak implementować oraz użyć metody osi niestandardowej, która przesyła strumieniowo fragmentów kodu XML z pliku określonego przez identyfikator URI. Ta oś niestandardowe specjalnie są zapisywane, w której oczekuje, że dokument, który ma `Customer`, `Name`, i `Item` elementów i rozmieszczenia elementów tak jak w powyższym `Source.xml` dokumentu. Jest uproszczony implementacji. Bardziej niezawodne wdrożenia będzie przygotowana do analizowania nieprawidłowy dokument.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowane LINQ to XML programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
