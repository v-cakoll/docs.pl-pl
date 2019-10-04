---
title: 'Instrukcje: strumieniowe fragmenty XML z elementu XmlReader (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: 3edb9cbbe9b649a5b4d232a3937e6f322b4a6b7d
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835145"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a>Instrukcje: strumieniowe fragmenty XML z elementu XmlReader (Visual Basic)
W przypadku konieczności przetworzenia dużych plików XML może nie być możliwe załadowanie całego drzewa XML do pamięci. W tym temacie przedstawiono sposób przesyłania fragmentów przy użyciu <xref:System.Xml.XmlReader>.  
  
 Jednym z najbardziej skutecznych sposobów używania <xref:System.Xml.XmlReader> do odczytu obiektów <xref:System.Xml.Linq.XElement> jest zapisanie własnej metody osi niestandardowej. Metoda osi zwykle zwraca kolekcję, taką jak <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, jak pokazano w przykładzie w tym temacie. W metodzie osi niestandardowej po utworzeniu fragmentu kodu XML przez wywołanie metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> Zwróć kolekcję przy użyciu `yield return`. Zapewnia to odroczoną semantykę wykonania do niestandardowej metody osi.  
  
 Podczas tworzenia drzewa XML na podstawie obiektu <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReader> musi być umieszczony w elemencie. Metoda <xref:System.Xml.Linq.XNode.ReadFrom%2A> nie zwraca do momentu odczytania tagu zamknięcia elementu.  
  
 Jeśli chcesz utworzyć drzewo częściowe, możliwe jest utworzenie wystąpienia <xref:System.Xml.XmlReader>, umieszczenie czytnika w węźle, który ma zostać przekonwertowany na drzewo <xref:System.Xml.Linq.XElement>, a następnie utworzenie obiektu <xref:System.Xml.Linq.XElement>.  
  
 Temat [instrukcje: Stream fragmenty XML z dostępem do informacji nagłówka (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) zawierają informacje i przykład na potrzeby przesyłania strumieniowego bardziej złożonego dokumentu.  
  
 Temat [instrukcje: wykonywanie transformacji strumieniowej dużych dokumentów XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) zawiera przykład użycia LINQ to XML do przekształcania bardzo dużych dokumentów XML przy zachowaniu małej ilości pamięci.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest tworzona Metoda osi niestandardowej. Zapytanie można wykonać przy użyciu kwerendy [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Metoda osi niestandardowej, `StreamRootChildDoc`, to metoda, która jest przeznaczona specjalnie do odczytywania dokumentu, który ma powtarzający się element `Child`.  
  
```vb  
Module Module1  
    Sub Main()  
        Dim markup = "<Root>" &  
                     "  <Child Key=""01"">" &  
                     "    <GrandChild>aaa</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""02"">" &  
                     "    <GrandChild>bbb</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""03"">" &  
                     "    <GrandChild>ccc</GrandChild>" &  
                     "  </Child>" &  
                     "</Root>"  
  
        Dim grandChildData =  
             From el In New StreamRootChildDoc(New IO.StringReader(markup))  
             Where CInt(el.@Key) > 1  
             Select el.<GrandChild>.Value  
  
        For Each s In grandChildData  
            Console.WriteLine(s)  
        Next  
    End Sub  
End Module  
  
Public Class StreamRootChildDoc  
    Implements IEnumerable(Of XElement)  
  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamChildEnumerator(_stringReader)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamChildEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _reader As Xml.XmlReader  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
        _reader = Xml.XmlReader.Create(_stringReader)  
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
        While _reader.Read()  
            Select Case _reader.NodeType  
                Case Xml.XmlNodeType.Element  
                    Dim el = TryCast(XElement.ReadFrom(_reader), XElement)  
                    If el IsNot Nothing Then  
                        _current = el  
                        Return True  
                    End If  
            End Select  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_stringReader)  
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
  
 Ten przykład generuje następujące wyniki:  
  
```console  
bbb  
ccc  
```  
  
 W tym przykładzie dokument źródłowy jest bardzo mały. Jednak nawet w przypadku milionów elementów `Child` ten przykład nadal ma niewielki rozmiar pamięci.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: implementowanie interfejsu IEnumerable (Of T) w Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)
- [Analizowanie kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
