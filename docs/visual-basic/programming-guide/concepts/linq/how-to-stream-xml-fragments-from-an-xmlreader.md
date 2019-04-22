---
title: 'Instrukcje: Stream fragmentów kodu XML z elementu XmlReader (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: 8c5aa1afff983f3763bbf7c74268eba622df7751
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833597"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a>Instrukcje: Stream fragmentów kodu XML z elementu XmlReader (Visual Basic)
W przypadku przetwarzania dużych plików XML, może nie być możliwe do załadowania całego drzewa XML do pamięci. W tym temacie pokazano, jak przesyłać strumieniowo fragmentów przy użyciu <xref:System.Xml.XmlReader>.  
  
 Jedną z najbardziej skutecznych sposobów użycia <xref:System.Xml.XmlReader> odczytać <xref:System.Xml.Linq.XElement> obiektów jest napisanie własnej metody osi niestandardowych. Metody osi takich jak zwykle zwraca kolekcję <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, jak pokazano w przykładzie w tym temacie. W metodzie niestandardowej osi po utworzeniu XML fragment, wywołując <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody zwracają kolekcję przy użyciu `yield return`. Dzięki temu semantyki wykonanie odroczone do metody osi niestandardowych.  
  
 Podczas tworzenia drzewa XML z <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader> musi być umieszczony w elemencie. <xref:System.Xml.Linq.XNode.ReadFrom%2A> Metoda nie zwraca, dopóki odczyta Zamknij tagu elementu.  
  
 Jeśli chcesz utworzyć drzewo częściowe, można utworzyć wystąpienie <xref:System.Xml.XmlReader>, umieść czytelnika na węźle, który chcesz przekonwertować <xref:System.Xml.Linq.XElement> drzewa, a następnie utwórz <xref:System.Xml.Linq.XElement> obiektu.  
  
 Temat [jak: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) zawiera informacje i obejrzeć przykład do przesyłania strumieniowego bardziej złożonych dokumentów.  
  
 Temat [jak: Wykonaj przesyłania strumieniowego Przekształcanie z dużymi dokumentami XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) zawiera przykład korzystania z LINQ to XML do transformowania bardzo dużych dokumentów XML przy zachowaniu zużycie pamięci.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tworzy metodę niestandardowe osi. Można tworzyć zapytania przy użyciu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Metoda niestandardowe osi `StreamRootChildDoc`, to metoda, która jest przeznaczona specjalnie do odczytu dokumentu, który zawiera powtarzające się `Child` elementu.  
  
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
  
```  
bbb  
ccc  
```  
  
 W tym przykładzie dokument źródłowy jest bardzo mały. Jednak nawet wtedy, gdy było milionów `Child` elementów, w tym przykładzie nadal będzie miał zużycie pamięci.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: Implementowanie IEnumerable(Of T) w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)
- [Analizowanie kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
