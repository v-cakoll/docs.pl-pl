---
title: 'Instrukcje: Wykonywanie przekształceń strumieniowych dużych dokumentów XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 3d954cc9-4b3c-4b47-8132-ff7541cff53b
ms.openlocfilehash: 8761f5fbf4e6137c1ae6b202b6717579c6f78d4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789132"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-visual-basic"></a><span data-ttu-id="49bd3-102">Instrukcje: Wykonywanie przekształceń strumieniowych dużych dokumentów XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49bd3-102">How to: Perform Streaming Transform of Large XML Documents (Visual Basic)</span></span>
<span data-ttu-id="49bd3-103">Czasami trzeba Przekształcanie dużych plików XML i pisania aplikacji, więc, że zużycie pamięci aplikacji jest przewidywalne.</span><span class="sxs-lookup"><span data-stu-id="49bd3-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="49bd3-104">Jeśli zostanie podjęta próba wypełnianie drzewa XML z bardzo dużego pliku XML, wykorzystanie pamięci będzie proporcjonalny do rozmiaru pliku (oznacza to, że nadmierne).</span><span class="sxs-lookup"><span data-stu-id="49bd3-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="49bd3-105">W związku z tym należy zamiast tego użyj technika przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="49bd3-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="49bd3-106">Techniki przesyłania strumieniowego najlepiej są stosowane w sytuacji, gdy trzeba przetworzyć tylko jeden raz w dokumencie źródłowym i pozwala na przetwarzanie elementów w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="49bd3-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="49bd3-107">Niektóre standardowe zapytanie operatorów, takich jak <xref:System.Linq.Enumerable.OrderBy%2A>iteracji ich źródła, zbieraj wszystkie dane, ją posortować i na koniec uzyskanie pierwszego elementu w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="49bd3-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="49bd3-108">Należy pamiętać, że użycie operatora zapytania, który materializuje źródła przed reaguje na pierwszy element, możesz nie zostaną zachowane zużycie pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49bd3-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="49bd3-109">Nawet w przypadku używania techniki opisanej w [jak: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), Jeśli spróbujesz utworzyć drzewa XML zawierający przekształcone dokumentu jest zbyt duże użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="49bd3-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="49bd3-110">Dostępne są dwie główne opcje.</span><span class="sxs-lookup"><span data-stu-id="49bd3-110">There are two main approaches.</span></span> <span data-ttu-id="49bd3-111">Jedno z podejść jest użycie właściwości przetwarzanie odroczone <xref:System.Xml.Linq.XStreamingElement>.</span><span class="sxs-lookup"><span data-stu-id="49bd3-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="49bd3-112">Innym rozwiązaniem jest utworzenie <xref:System.Xml.XmlWriter>oraz korzystać z możliwości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do zapisania elementów <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="49bd3-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="49bd3-113">W tym temacie przedstawiono oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="49bd3-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49bd3-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="49bd3-114">Example</span></span>  
 <span data-ttu-id="49bd3-115">Poniższy przykład opiera się na przykład w [jak: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="49bd3-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="49bd3-116">W tym przykładzie użyto funkcji odroczonego wykonania <xref:System.Xml.Linq.XStreamingElement> do przesyłania strumieniowego danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="49bd3-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="49bd3-117">W tym przykładzie można przekształcać bardzo dużych dokumentów przy zachowaniu zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="49bd3-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="49bd3-118">Należy pamiętać, że niestandardowe osi (`StreamCustomerItem`) napisano specjalnie tak, aby oczekuje, że dokument zawierający `Customer`, `Name`, i `Item` elementów i że tak jak w następującym dokumencie Source.xml rozmieszczenia tych elementów.</span><span class="sxs-lookup"><span data-stu-id="49bd3-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="49bd3-119">Bardziej niezawodna implementacji będzie jednak przygotowane przeanalizować nieprawidłowy dokument.</span><span class="sxs-lookup"><span data-stu-id="49bd3-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="49bd3-120">Dokument źródłowy Source.xml jest następująca:</span><span class="sxs-lookup"><span data-stu-id="49bd3-120">The following is the source document, Source.xml:</span></span>  
  
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
  
 <span data-ttu-id="49bd3-121">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="49bd3-121">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="49bd3-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="49bd3-122">Example</span></span>  
 <span data-ttu-id="49bd3-123">Poniższy przykład opiera się również na przykład w [jak: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="49bd3-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="49bd3-124">W tym przykładzie użyto możliwości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do zapisania elementów <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="49bd3-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="49bd3-125">W tym przykładzie można przekształcać bardzo dużych dokumentów przy zachowaniu zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="49bd3-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="49bd3-126">Należy pamiętać, że niestandardowe osi (`StreamCustomerItem`) napisano specjalnie tak, aby oczekuje, że dokument zawierający `Customer`, `Name`, i `Item` elementów i że tak jak w następującym dokumencie Source.xml rozmieszczenia tych elementów.</span><span class="sxs-lookup"><span data-stu-id="49bd3-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="49bd3-127">Jednak implementacja bardziej niezawodne, albo czy sprawdzanie poprawności dokumentu źródłowego przy użyciu XSD lub jest gotowy do analizowania nieprawidłowy dokument.</span><span class="sxs-lookup"><span data-stu-id="49bd3-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="49bd3-128">W tym przykładzie użyto tego samego dokumentu źródłowego Source.xml, jak w poprzednim przykładzie w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="49bd3-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="49bd3-129">Generuje ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="49bd3-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="49bd3-130">Za pomocą <xref:System.Xml.Linq.XStreamingElement> dla przesyłania strumieniowego wyjściowy plik XML jest preferowana względem zapisywania <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="49bd3-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="49bd3-131">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="49bd3-131">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="49bd3-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49bd3-132">See also</span></span>

- [<span data-ttu-id="49bd3-133">Zaawansowane LINQ to XML programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49bd3-133">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
