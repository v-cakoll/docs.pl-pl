---
title: 'Jak: Wykonywanie transformacji przesyłania strumieniowego dużych dokumentów XML'
ms.date: 07/20/2015
ms.assetid: 3d954cc9-4b3c-4b47-8132-ff7541cff53b
ms.openlocfilehash: f5e6063f0a850c03a605d75b0cbdc0bf9e03b325
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78267018"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-visual-basic"></a><span data-ttu-id="64e35-102">Jak: Wykonywanie transformacji przesyłania strumieniowego dużych dokumentów XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64e35-102">How to: Perform Streaming Transform of Large XML Documents (Visual Basic)</span></span>
<span data-ttu-id="64e35-103">Czasami trzeba przekształcić duże pliki XML i napisać aplikację, tak aby rozmiar pamięci aplikacji jest przewidywalny.</span><span class="sxs-lookup"><span data-stu-id="64e35-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="64e35-104">Jeśli spróbujesz wypełnić drzewo XML bardzo dużym plikiem XML, użycie pamięci będzie proporcjonalne do rozmiaru pliku (czyli nadmiernego).</span><span class="sxs-lookup"><span data-stu-id="64e35-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="64e35-105">W związku z tym należy użyć techniki przesyłania strumieniowego zamiast.</span><span class="sxs-lookup"><span data-stu-id="64e35-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="64e35-106">Techniki przesyłania strumieniowego są najlepiej stosowane w sytuacjach, w których trzeba przetworzyć dokument źródłowy tylko raz i można przetwarzać elementy w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="64e35-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="64e35-107">Niektóre standardowe operatory <xref:System.Linq.Enumerable.OrderBy%2A>zapytań, takie jak , iteracji ich źródła, zbierać wszystkie dane, sortować go, a następnie ostatecznie dać pierwszy element w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="64e35-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="64e35-108">Należy zauważyć, że jeśli używasz operatora kwerendy, który materializuje jego źródła przed uzyskaniem pierwszego elementu, nie zachowa mały ślad pamięci dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64e35-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="64e35-109">Nawet jeśli używasz techniki opisanej w [Jak: Przesyłanie strumieniowe fragmentów XML z dostępem do informacji nagłówka (Visual Basic),](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)jeśli spróbujesz zebrać drzewo XML, który zawiera przekształcony dokument, użycie pamięci będzie zbyt duże.</span><span class="sxs-lookup"><span data-stu-id="64e35-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="64e35-110">Istnieją dwa główne podejścia.</span><span class="sxs-lookup"><span data-stu-id="64e35-110">There are two main approaches.</span></span> <span data-ttu-id="64e35-111">Jednym z podejść jest stosowanie <xref:System.Xml.Linq.XStreamingElement>odroczonych cech przetwarzania .</span><span class="sxs-lookup"><span data-stu-id="64e35-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="64e35-112">Innym podejściem <xref:System.Xml.XmlWriter>jest stworzenie programu , [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] i wykorzystanie możliwości <xref:System.Xml.XmlWriter>pisania elementów do pliku .</span><span class="sxs-lookup"><span data-stu-id="64e35-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="64e35-113">W tym temacie przedstawiono oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="64e35-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64e35-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="64e35-114">Example</span></span>  
 <span data-ttu-id="64e35-115">Poniższy przykład opiera się na przykładzie [jak: Przesyłanie strumieniowe fragmentów XML z dostępem do informacji nagłówka (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="64e35-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="64e35-116">W tym przykładzie użyto możliwości <xref:System.Xml.Linq.XStreamingElement> odroczonego wykonania do przesyłania strumieniowego danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="64e35-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="64e35-117">W tym przykładzie można przekształcić bardzo duży dokument przy zachowaniu niewielki ślad pamięci.</span><span class="sxs-lookup"><span data-stu-id="64e35-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="64e35-118">Należy zauważyć, że`StreamCustomerItem`oś niestandardowa ( ) jest specjalnie `Customer`napisana, tak aby oczekiwała dokumentu, `Name`który ma , i `Item` elementy, i że te elementy będą rozmieszczone tak jak w poniższym dokumencie Source.xml.</span><span class="sxs-lookup"><span data-stu-id="64e35-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="64e35-119">Bardziej niezawodne wdrożenie, jednak byłoby przygotowane do analizy nieprawidłowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="64e35-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="64e35-120">Poniżej znajduje się dokument źródłowy Source.xml:</span><span class="sxs-lookup"><span data-stu-id="64e35-120">The following is the source document, Source.xml:</span></span>  
  
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
  
 <span data-ttu-id="64e35-121">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="64e35-121">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="64e35-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="64e35-122">Example</span></span>  
 <span data-ttu-id="64e35-123">Poniższy przykład opiera się również na przykładzie [jak: Przesyłanie strumieniowe fragmentów XML z dostępem do informacji nagłówka (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="64e35-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="64e35-124">W tym przykładzie użyto możliwości zapisu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] elementów do pliku <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="64e35-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="64e35-125">W tym przykładzie można przekształcić bardzo duży dokument przy zachowaniu niewielki ślad pamięci.</span><span class="sxs-lookup"><span data-stu-id="64e35-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="64e35-126">Należy zauważyć, że`StreamCustomerItem`oś niestandardowa ( ) jest specjalnie `Customer`napisana, tak aby oczekiwała dokumentu, `Name`który ma , i `Item` elementy, i że te elementy będą rozmieszczone tak jak w poniższym dokumencie Source.xml.</span><span class="sxs-lookup"><span data-stu-id="64e35-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="64e35-127">Bardziej niezawodna implementacja, jednak albo sprawdzić poprawność dokumentu źródłowego z XSD lub byłby przygotowany do analizy nieprawidłowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="64e35-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="64e35-128">W tym przykładzie użyto tego samego dokumentu źródłowego Source.xml, jak w poprzednim przykładzie w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="64e35-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="64e35-129">Produkuje również dokładnie takie same dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="64e35-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="64e35-130">Używanie <xref:System.Xml.Linq.XStreamingElement> do przesyłania strumieniowego wyjściowego kodu <xref:System.Xml.XmlWriter>XML jest preferowane niż zapisywanie w pliku .</span><span class="sxs-lookup"><span data-stu-id="64e35-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="64e35-131">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="64e35-131">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64e35-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64e35-132">See also</span></span>

- [<span data-ttu-id="64e35-133">Zaawansowane programowanie LINQ na XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64e35-133">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
