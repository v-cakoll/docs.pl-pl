---
title: 'Porady: strumienia fragmenty XML z element XmlReader (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f18c922208fb52ffa775bd36e76c74f04d60f3b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a>Porady: strumienia fragmenty XML z element XmlReader (Visual Basic)
Podczas przetwarzania dużych plików XML, może nie być możliwe do załadowania całego drzewa XML do pamięci. W tym temacie przedstawiono sposób strumienia fragmenty przy użyciu <xref:System.Xml.XmlReader>.  
  
 Jedną z najbardziej skutecznych sposobów użycia <xref:System.Xml.XmlReader> odczytać <xref:System.Xml.Linq.XElement> obiektów jest napisanie własnej metody niestandardowe osi. Metoda osi takich jak zwykle zwraca kolekcję <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, jak pokazano w przykładzie w tym temacie. W metodzie niestandardowych osi, po utworzeniu fragmentu XML przez wywołanie metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody zwrócić przy użyciu kolekcji `yield return`. Zapewnia to wykonanie odroczone semantyki do metody niestandardowe osi.  
  
 Po utworzeniu drzewo XML z <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader> musi być umieszczony w elemencie. <xref:System.Xml.Linq.XNode.ReadFrom%2A> Nie może zwracać metoda dopóki odczyta tagu zamknięcia elementu.  
  
 Jeśli chcesz utworzyć drzewa częściowe, można utworzyć wystąpienia <xref:System.Xml.XmlReader>, umieść czytnik na węźle, który ma zostać przekonwertowany na <xref:System.Xml.Linq.XElement> drzewa, a następnie utwórz <xref:System.Xml.Linq.XElement> obiektu.  
  
 Temat [porady: strumień fragmenty XML z dostępem do informacji w nagłówku (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) zawiera informacje i przykład dotyczące strumienia bardziej złożonych dokumentu.  
  
 Temat [porady: wykonaj przesyłania strumieniowego przekształcenie o dużych dokumentów XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) zawiera przykład LINQ do XML do transformacji dokumentów XML wyjątkowa przy zachowaniu zużycia pamięci.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tworzy metodę niestandardowych osi. Odpytywaną przy użyciu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Metody niestandardowe osi `StreamRootChildDoc`, to metoda, która jest zaprojektowany specjalnie w celu odczytu dokumentu, który zawiera powtarzające się `Child` elementu.  
  
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
  
 W tym przykładzie dokument źródłowy jest bardzo mała. Jednak nawet wtedy, gdy było miliony `Child` elementów, w tym przykładzie nadal będzie miał zużycie pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Wdrażanie IEnumerable(Of T) w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)  
 [Analiza kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
