---
title: 'Instrukcje: wykonywanie przekształceń strumieniowych dużych dokumentów XML'
ms.date: 07/20/2015
ms.assetid: 3d954cc9-4b3c-4b47-8132-ff7541cff53b
ms.openlocfilehash: f648371581ed2854c107ebed920068e2abec4239
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397989"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-visual-basic"></a><span data-ttu-id="04b86-102">Instrukcje: wykonywanie transformacji strumieniowej dużych dokumentów XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04b86-102">How to: Perform Streaming Transform of Large XML Documents (Visual Basic)</span></span>
<span data-ttu-id="04b86-103">Czasami konieczne jest przekształcenie dużych plików XML i zapisanie aplikacji w celu przewidzenia rozmiaru pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="04b86-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="04b86-104">Jeśli spróbujesz wypełnić drzewo XML bardzo dużym plikiem XML, użycie pamięci będzie proporcjonalne do rozmiaru pliku (to jest zbyt duże).</span><span class="sxs-lookup"><span data-stu-id="04b86-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="04b86-105">W związku z tym należy zamiast tego użyć techniki przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="04b86-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="04b86-106">Techniki przesyłania strumieniowego najlepiej zastosować w sytuacjach, gdy trzeba przetwarzać dokument źródłowy tylko raz i można przetwarzać elementy w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="04b86-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="04b86-107">Niektóre standardowe operatory zapytań, takie jak <xref:System.Linq.Enumerable.OrderBy%2A> , iteruje źródło, zbierają wszystkie dane, sortują je, a następnie zwracają pierwszy element w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="04b86-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="04b86-108">Należy pamiętać, że jeśli używasz operatora zapytania, który materializuje jego źródło przed uzyskaniem pierwszego elementu, nie będzie zachowana mała ilość pamięci dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="04b86-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="04b86-109">Nawet jeśli używasz techniki opisanej w artykule [How to: Stream fragmenty XML z dostępem do informacji nagłówka (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md), jeśli próbujesz połączyć drzewo XML zawierające przekształcony dokument, użycie pamięci będzie zbyt duże.</span><span class="sxs-lookup"><span data-stu-id="04b86-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="04b86-110">Istnieją dwa główne podejścia.</span><span class="sxs-lookup"><span data-stu-id="04b86-110">There are two main approaches.</span></span> <span data-ttu-id="04b86-111">Jednym z metod jest użycie odroczonych charakterystyk przetwarzania <xref:System.Xml.Linq.XStreamingElement> .</span><span class="sxs-lookup"><span data-stu-id="04b86-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="04b86-112">Innym rozwiązaniem jest utworzenie <xref:System.Xml.XmlWriter> i użycie funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do zapisu elementów do <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="04b86-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="04b86-113">W tym temacie przedstawiono oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="04b86-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04b86-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="04b86-114">Example</span></span>  
 <span data-ttu-id="04b86-115">Poniższy przykład kompiluje w przykładzie w [instrukcje: Stream fragmenty XML z dostępem do informacji nagłówka (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="04b86-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="04b86-116">W tym przykładzie zastosowano opóźnione funkcje wykonywania <xref:System.Xml.Linq.XStreamingElement> w celu przesyłania strumieniowego danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="04b86-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="04b86-117">W tym przykładzie można przekształcić bardzo duży dokument przy zachowaniu małej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="04b86-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="04b86-118">Należy zauważyć, że niestandardowa oś () została zaprojektowana w `StreamCustomerItem` taki sposób, aby oczekuje dokumentu, `Customer` `Name` , i `Item` elementów, i że te elementy będą ułożone jak w poniższym dokumencie source. XML.</span><span class="sxs-lookup"><span data-stu-id="04b86-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="04b86-119">Jednak bardziej niezawodna implementacja zostanie przygotowana do analizy nieprawidłowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="04b86-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="04b86-120">Poniżej znajduje się dokument źródłowy source. XML:</span><span class="sxs-lookup"><span data-stu-id="04b86-120">The following is the source document, Source.xml:</span></span>  
  
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
  
```vb  
Module Module1  
    Sub Main()  
        Dim root = New XStreamingElement("Root",  
            From el In New StreamCustomerItem("Source.xml")  
            Select <Item>  
                       <Customer><%= el.Parent.<Name>.Value %></Customer>  
                       <%= el.<Key> %>  
                   </Item>  
            )  
        root.Save("Test.xml")  
        Console.WriteLine(My.Computer.FileSystem.ReadAllText("Test.xml"))  
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
  
 <span data-ttu-id="04b86-121">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="04b86-121">This code produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
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
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="04b86-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="04b86-122">Example</span></span>  
 <span data-ttu-id="04b86-123">Poniższy przykład kompiluje się również na przykład w [instrukcje: Stream fragmenty XML z dostępem do informacji nagłówka (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="04b86-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="04b86-124">Ten przykład używa funkcji, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Aby pisać elementy do <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="04b86-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="04b86-125">W tym przykładzie można przekształcić bardzo duży dokument przy zachowaniu małej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="04b86-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="04b86-126">Należy zauważyć, że niestandardowa oś () została zaprojektowana w `StreamCustomerItem` taki sposób, aby oczekuje dokumentu, `Customer` `Name` , i `Item` elementów, i że te elementy będą ułożone jak w poniższym dokumencie source. XML.</span><span class="sxs-lookup"><span data-stu-id="04b86-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="04b86-127">Bardziej niezawodna implementacja może jednak spowodować sprawdzenie poprawności dokumentu źródłowego przy użyciu XSD lub przygotowania do przeanalizowania nieprawidłowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="04b86-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="04b86-128">Ten przykład używa tego samego dokumentu źródłowego, source. XML, jak w poprzednim przykładzie w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="04b86-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="04b86-129">Generuje również dokładnie te same dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="04b86-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="04b86-130">Użycie <xref:System.Xml.Linq.XStreamingElement> do przesyłania strumieniowego wyjściowego pliku XML jest preferowany przez zapis do <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="04b86-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim srcTree =  
            From el In New StreamCustomerItem("Source.xml")  
            Select <Item>  
                       <Customer><%= el.Parent.<Name>.Value %></Customer>  
                       <%= el.<Key> %>  
                   </Item>  
  
        Dim xws = New Xml.XmlWriterSettings()  
        xws.OmitXmlDeclaration = True  
        xws.Indent = True  
        Using xw = Xml.XmlWriter.Create("Output.xml", xws)  
            xw.WriteStartElement("Root")  
            For Each el In srcTree  
                el.WriteTo(xw)  
            Next  
            xw.WriteEndElement()  
        End Using  
  
        Dim s = My.Computer.FileSystem.ReadAllText("Output.xml")  
        Console.WriteLine(s)  
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
  
 <span data-ttu-id="04b86-131">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="04b86-131">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
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
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="04b86-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04b86-132">See also</span></span>

- [<span data-ttu-id="04b86-133">Zaawansowane programowanie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04b86-133">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
