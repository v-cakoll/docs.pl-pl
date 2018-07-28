---
title: 'Porady: Stream fragmentów kodu XML z elementu XmlReader (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: 38a81e83421dffc997a2cbfd6d0996da5ece18d1
ms.sourcegitcommit: 869b5832b667915ac4a5dd8c86b1109ed26b6c08
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/28/2018
ms.locfileid: "39332704"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="746fc-102">Porady: Stream fragmentów kodu XML z elementu XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="746fc-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="746fc-103">W przypadku przetwarzania dużych plików XML, może nie być możliwe do załadowania całego drzewa XML do pamięci.</span><span class="sxs-lookup"><span data-stu-id="746fc-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="746fc-104">W tym temacie pokazano, jak przesyłać strumieniowo fragmentów przy użyciu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="746fc-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="746fc-105">Jedną z najbardziej skutecznych sposobów użycia <xref:System.Xml.XmlReader> odczytać <xref:System.Xml.Linq.XElement> obiektów jest napisanie własnej metody osi niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="746fc-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="746fc-106">Metody osi takich jak zwykle zwraca kolekcję <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, jak pokazano w przykładzie w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="746fc-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="746fc-107">W metodzie niestandardowej osi po utworzeniu XML fragment, wywołując <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody zwracają kolekcję przy użyciu `yield return`.</span><span class="sxs-lookup"><span data-stu-id="746fc-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="746fc-108">Dzięki temu semantyki wykonanie odroczone do metody osi niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="746fc-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="746fc-109">Podczas tworzenia drzewa XML z <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader> musi być umieszczony w elemencie.</span><span class="sxs-lookup"><span data-stu-id="746fc-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="746fc-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A> Metoda nie zwraca, dopóki odczyta Zamknij tagu elementu.</span><span class="sxs-lookup"><span data-stu-id="746fc-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="746fc-111">Jeśli chcesz utworzyć drzewo częściowe, można utworzyć wystąpienie <xref:System.Xml.XmlReader>, umieść czytelnika na węźle, który chcesz przekonwertować <xref:System.Xml.Linq.XElement> drzewa, a następnie utwórz <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="746fc-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="746fc-112">Temat [jak: Stream XML fragmentów z dostępem do informacji w nagłówku (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) zawiera informacje i obejrzeć przykład do przesyłania strumieniowego bardziej złożonych dokumentów.</span><span class="sxs-lookup"><span data-stu-id="746fc-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="746fc-113">Temat [jak: wykonywać przesyłania strumieniowego Przekształcanie z dużymi dokumentami XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) zawiera przykład korzystania z LINQ to XML do transformowania bardzo dużych dokumentów XML przy zachowaniu zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="746fc-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="746fc-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="746fc-114">Example</span></span>  
 <span data-ttu-id="746fc-115">W tym przykładzie tworzy metodę niestandardowe osi.</span><span class="sxs-lookup"><span data-stu-id="746fc-115">This example creates a custom axis method.</span></span> <span data-ttu-id="746fc-116">Można tworzyć zapytania przy użyciu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="746fc-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="746fc-117">Metoda niestandardowe osi `StreamRootChildDoc`, to metoda, która jest przeznaczona specjalnie do odczytu dokumentu, który zawiera powtarzające się `Child` elementu.</span><span class="sxs-lookup"><span data-stu-id="746fc-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="746fc-118">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="746fc-118">This example produces the following output:</span></span>  
  
```  
bbb  
ccc  
```  
  
 <span data-ttu-id="746fc-119">W tym przykładzie dokument źródłowy jest bardzo mały.</span><span class="sxs-lookup"><span data-stu-id="746fc-119">In this example, the source document is very small.</span></span> <span data-ttu-id="746fc-120">Jednak nawet wtedy, gdy było milionów `Child` elementów, w tym przykładzie nadal będzie miał zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="746fc-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="746fc-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="746fc-121">See Also</span></span>  
 [<span data-ttu-id="746fc-122">Wskazówki: Wdrażanie IEnumerable(Of T) w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="746fc-122">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)  
 [<span data-ttu-id="746fc-123">Analizowanie kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="746fc-123">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
