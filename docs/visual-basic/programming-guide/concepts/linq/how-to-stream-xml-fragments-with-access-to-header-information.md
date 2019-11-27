---
title: 'Instrukcje: strumieniowe fragmenty XML z dostępem do informacji nagłówka'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: 489e128e86a47e0e7f76c14a6cf1baf80fb0c406
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332451"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a><span data-ttu-id="dcd40-102">Instrukcje: strumieniowe fragmenty XML z dostępem do informacji nagłówka (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcd40-102">How to: Stream XML Fragments with Access to Header Information (Visual Basic)</span></span>
<span data-ttu-id="dcd40-103">Czasami konieczne jest odczytanie arbitralnie dużych plików XML i zapisanie aplikacji w celu przewidzenia rozmiaru pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dcd40-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="dcd40-104">W przypadku próby wypełnienia drzewa XML przy użyciu dużego pliku XML użycie pamięci będzie proporcjonalne do rozmiaru pliku, czyli nadmierne.</span><span class="sxs-lookup"><span data-stu-id="dcd40-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="dcd40-105">W związku z tym należy zamiast tego użyć techniki przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="dcd40-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="dcd40-106">Jedną z opcji jest zapisanie aplikacji przy użyciu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="dcd40-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="dcd40-107">Można jednak użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], aby zbadać drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="dcd40-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="dcd40-108">W takim przypadku można napisać własną metodę osi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="dcd40-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="dcd40-109">Aby uzyskać więcej informacji, zobacz [How to: Write a LINQ to XML osi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="dcd40-109">For more information, see [How to: Write a LINQ to XML Axis Method (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="dcd40-110">Aby napisać własną metodę osi, napisz małą metodę, która używa <xref:System.Xml.XmlReader> do odczytywania węzłów do momentu osiągnięcia jednego z węzłów, w których interesują Cię zainteresowania.</span><span class="sxs-lookup"><span data-stu-id="dcd40-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="dcd40-111">Metoda następnie wywołuje <xref:System.Xml.Linq.XNode.ReadFrom%2A>, który odczytuje z <xref:System.Xml.XmlReader> i tworzy wystąpienie fragmentu XML.</span><span class="sxs-lookup"><span data-stu-id="dcd40-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="dcd40-112">Następnie można napisać zapytania LINQ na niestandardowej metodzie osi.</span><span class="sxs-lookup"><span data-stu-id="dcd40-112">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="dcd40-113">Techniki przesyłania strumieniowego najlepiej zastosować w sytuacjach, gdy trzeba przetwarzać dokument źródłowy tylko raz i można przetwarzać elementy w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="dcd40-113">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="dcd40-114">Niektóre standardowe operatory zapytań, takie jak <xref:System.Linq.Enumerable.OrderBy%2A>, iteracji ich źródła, zbierają wszystkie dane, sortują je, a następnie zwracają pierwszy element w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dcd40-114">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="dcd40-115">Należy pamiętać, że jeśli używasz operatora zapytania, który materializuje jego źródło przed uzyskaniem pierwszego elementu, nie będzie zachowana mała ilość pamięci.</span><span class="sxs-lookup"><span data-stu-id="dcd40-115">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcd40-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="dcd40-116">Example</span></span>  
 <span data-ttu-id="dcd40-117">Czasami problem jest znacznie bardziej interesujący.</span><span class="sxs-lookup"><span data-stu-id="dcd40-117">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="dcd40-118">W poniższym dokumencie XML konsument niestandardowej metody osi musi znać nazwę klienta, do którego należy każdy element.</span><span class="sxs-lookup"><span data-stu-id="dcd40-118">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="dcd40-119">Podejście, które ten przykład przyjmuje, ma również na celu śledzenie informacji o tym nagłówku, zapisanie informacji nagłówka, a następnie utworzenie małego drzewa XML zawierającego zarówno informacje nagłówka, jak i szczegóły wyliczane.</span><span class="sxs-lookup"><span data-stu-id="dcd40-119">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="dcd40-120">Następnie metoda osi daje nowe, małe drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="dcd40-120">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="dcd40-121">Następnie zapytanie ma dostęp do informacji nagłówka oraz informacji szczegółowych.</span><span class="sxs-lookup"><span data-stu-id="dcd40-121">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="dcd40-122">Takie podejście ma niewielkie rozmiary pamięci.</span><span class="sxs-lookup"><span data-stu-id="dcd40-122">This approach has a small memory footprint.</span></span> <span data-ttu-id="dcd40-123">Ze względu na to, że każdy szczegółowy fragment kodu XML jest przewidziany, żadne odwołania nie są przechowywane w poprzednim fragmencie i jest dostępny do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dcd40-123">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="dcd40-124">Należy zauważyć, że ta technika tworzy wiele obiektów krótkotrwałych na stercie.</span><span class="sxs-lookup"><span data-stu-id="dcd40-124">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="dcd40-125">Poniższy przykład przedstawia sposób implementacji i używania niestandardowej metody osi, która strumieniuje fragmenty XML z pliku określonego przez identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="dcd40-125">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="dcd40-126">Ta oś niestandardowa jest zapisywana w taki sposób, że oczekuje dokumentu, który ma `Customer`, `Name`i `Item` elementów oraz że te elementy zostaną ułożone tak jak w powyższym `Source.xml` dokumencie.</span><span class="sxs-lookup"><span data-stu-id="dcd40-126">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="dcd40-127">Jest to implementacja uproszczony.</span><span class="sxs-lookup"><span data-stu-id="dcd40-127">It is a simplistic implementation.</span></span> <span data-ttu-id="dcd40-128">Bardziej niezawodna implementacja zostanie przygotowana do analizy nieprawidłowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="dcd40-128">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
  
 <span data-ttu-id="dcd40-129">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="dcd40-129">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dcd40-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcd40-130">See also</span></span>

- [<span data-ttu-id="dcd40-131">Zaawansowane programowanie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcd40-131">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
