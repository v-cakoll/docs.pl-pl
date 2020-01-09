---
title: 'Instrukcje: strumieniowe fragmenty XML z elementu XmlReader'
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: 42d3edb390035d20f506388974000aa204312109
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636799"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="081fc-102">Instrukcje: strumieniowe fragmenty XML z elementu XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="081fc-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="081fc-103">W przypadku konieczności przetworzenia dużych plików XML może nie być możliwe załadowanie całego drzewa XML do pamięci.</span><span class="sxs-lookup"><span data-stu-id="081fc-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="081fc-104">W tym temacie pokazano, jak przesyłać fragmenty strumieni przy użyciu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="081fc-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="081fc-105">Jednym z najbardziej skutecznych sposobów używania <xref:System.Xml.XmlReader> do odczytu obiektów <xref:System.Xml.Linq.XElement> jest pisanie własnej niestandardowej metody osi.</span><span class="sxs-lookup"><span data-stu-id="081fc-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="081fc-106">Metoda osi zwykle zwraca kolekcję, taką jak <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, jak pokazano w przykładzie w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="081fc-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="081fc-107">W metodzie osi niestandardowej po utworzeniu fragmentu kodu XML przez wywołanie metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> Zwróć kolekcję przy użyciu `yield return`.</span><span class="sxs-lookup"><span data-stu-id="081fc-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="081fc-108">Zapewnia to odroczoną semantykę wykonania do niestandardowej metody osi.</span><span class="sxs-lookup"><span data-stu-id="081fc-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="081fc-109">Podczas tworzenia drzewa XML na podstawie obiektu <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReader> musi być umieszczony w elemencie.</span><span class="sxs-lookup"><span data-stu-id="081fc-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="081fc-110">Metoda <xref:System.Xml.Linq.XNode.ReadFrom%2A> nie zwraca do momentu odczytania tagu zamknięcia elementu.</span><span class="sxs-lookup"><span data-stu-id="081fc-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="081fc-111">Jeśli chcesz utworzyć częściowe drzewo, Utwórz wystąpienie <xref:System.Xml.XmlReader>, umieść czytnik w węźle, który ma zostać przekonwertowany na drzewo <xref:System.Xml.Linq.XElement>, a następnie Utwórz obiekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="081fc-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="081fc-112">Temat [instrukcje: Stream fragmenty XML z dostępem do informacji nagłówka (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) zawierają informacje i przykład na potrzeby przesyłania strumieniowego bardziej złożonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="081fc-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="081fc-113">Temat [instrukcje: wykonywanie transformacji strumieniowej dużych dokumentów XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) zawiera przykład użycia LINQ to XML do przekształcania bardzo dużych dokumentów XML przy zachowaniu małej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="081fc-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="081fc-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="081fc-114">Example</span></span>  
 <span data-ttu-id="081fc-115">W tym przykładzie jest tworzona Metoda osi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="081fc-115">This example creates a custom axis method.</span></span> <span data-ttu-id="081fc-116">Zapytanie można wykonać za pomocą zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="081fc-116">You can query it by using a LINQ query.</span></span> <span data-ttu-id="081fc-117">Metoda osi niestandardowej, `StreamRootChildDoc`, to metoda, która jest przeznaczona specjalnie do odczytywania dokumentu, który ma powtarzający się element `Child`.</span><span class="sxs-lookup"><span data-stu-id="081fc-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="081fc-118">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="081fc-118">This example produces the following output:</span></span>  
  
```console  
bbb  
ccc  
```  
  
 <span data-ttu-id="081fc-119">W tym przykładzie dokument źródłowy jest bardzo mały.</span><span class="sxs-lookup"><span data-stu-id="081fc-119">In this example, the source document is very small.</span></span> <span data-ttu-id="081fc-120">Jednak nawet jeśli wystąpiły miliony elementów `Child`, ten przykład nadal ma niewielki wpływ na pamięć.</span><span class="sxs-lookup"><span data-stu-id="081fc-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="081fc-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="081fc-121">See also</span></span>

- [<span data-ttu-id="081fc-122">Przewodnik: implementowanie interfejsu IEnumerable (Of T) w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="081fc-122">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)
- [<span data-ttu-id="081fc-123">Analizowanie kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="081fc-123">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
