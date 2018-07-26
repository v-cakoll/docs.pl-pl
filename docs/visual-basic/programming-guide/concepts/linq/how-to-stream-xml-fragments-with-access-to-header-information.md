---
title: 'Porady: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: 60ec63c33d20fa38bed32d9c46c4acfe649ecd15
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245188"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a><span data-ttu-id="277dc-102">Porady: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="277dc-102">How to: Stream XML Fragments with Access to Header Information (Visual Basic)</span></span>
<span data-ttu-id="277dc-103">Czasami trzeba przeczytać arbitralnie dużych plików XML i zapisu aplikacji, tak aby zużycie pamięci aplikacji jest przewidywalne.</span><span class="sxs-lookup"><span data-stu-id="277dc-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="277dc-104">Jeśli użytkownik podejmie próbę wypełnianie drzewa XML przy użyciu dużego pliku XML, wykorzystanie pamięci będzie proporcjonalny do rozmiaru pliku — oznacza to, że nadmierne.</span><span class="sxs-lookup"><span data-stu-id="277dc-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="277dc-105">W związku z tym należy zamiast tego użyj technika przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="277dc-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="277dc-106">Jedną z opcji jest do zapisu w swojej aplikacji za pomocą <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="277dc-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="277dc-107">Jednakże, możesz chcieć użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kwerendy drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="277dc-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="277dc-108">Jeśli jest to możliwe, można napisać metodę niestandardowe osi.</span><span class="sxs-lookup"><span data-stu-id="277dc-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="277dc-109">Aby uzyskać więcej informacji, zobacz [porady: pisanie LINQ do metody osi XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="277dc-109">For more information, see [How to: Write a LINQ to XML Axis Method (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="277dc-110">Aby napisać własne metody osi, zapisu małych metody, która używa <xref:System.Xml.XmlReader> odczytać węzły, aż do napotkania jednego z węzłów, w których interesuje Cię.</span><span class="sxs-lookup"><span data-stu-id="277dc-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="277dc-111">Następnie wywołuje metodę <xref:System.Xml.Linq.XNode.ReadFrom%2A>, która odczytuje z <xref:System.Xml.XmlReader> i tworzy XML fragment.</span><span class="sxs-lookup"><span data-stu-id="277dc-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="277dc-112">Następnie można pisać zapytania LINQ metodę niestandardowe osi.</span><span class="sxs-lookup"><span data-stu-id="277dc-112">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="277dc-113">Techniki przesyłania strumieniowego najlepiej są stosowane w sytuacji, gdy trzeba przetworzyć tylko jeden raz w dokumencie źródłowym i pozwala na przetwarzanie elementów w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="277dc-113">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="277dc-114">Niektóre standardowe zapytanie operatorów, takich jak <xref:System.Linq.Enumerable.OrderBy%2A>iteracji ich źródła, zbieraj wszystkie dane, ją posortować i na koniec uzyskanie pierwszego elementu w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="277dc-114">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="277dc-115">Należy pamiętać, że użycie operatora zapytania, który materializuje źródła przed reaguje na pierwszy element, możesz nie zostaną zachowane zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="277dc-115">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="277dc-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="277dc-116">Example</span></span>  
 <span data-ttu-id="277dc-117">Czasami problem pobiera nieco więcej interesujące.</span><span class="sxs-lookup"><span data-stu-id="277dc-117">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="277dc-118">W następującym dokumencie XML konsumenta metodę niestandardowe osi ma również znać nazwę klienta, który należy do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="277dc-118">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="277dc-119">Metody, która przyjmuje w tym przykładzie jest również obejrzeć te informacje nagłówka, Zapisz informacje nagłówka, a następnie skompilować małych drzewa XML, który zawiera zarówno informacje nagłówka, jak i szczegółów, które wyliczają to.</span><span class="sxs-lookup"><span data-stu-id="277dc-119">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="277dc-120">Metody osi następnie daje to nowe, małe drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="277dc-120">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="277dc-121">Zapytanie uzyska dostęp do informacji nagłówka, a także szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="277dc-121">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="277dc-122">Takie podejście ma zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="277dc-122">This approach has a small memory footprint.</span></span> <span data-ttu-id="277dc-123">Zgodnie z każdego fragmentu XML szczegółów jest uzyskane, pozostają żadnych odwołań do poprzedniego fragmentu i jest dostępny dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="277dc-123">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="277dc-124">Należy pamiętać, że ta technika tworzy wiele krótki czas życia obiektów na stosie.</span><span class="sxs-lookup"><span data-stu-id="277dc-124">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="277dc-125">Poniższy przykład pokazuje, jak implementować oraz użyć metody osi niestandardowej, która przesyła strumieniowo fragmentów kodu XML z pliku określonego przez identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="277dc-125">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="277dc-126">Ta oś niestandardowe specjalnie są zapisywane, w której oczekuje, że dokument, który ma `Customer`, `Name`, i `Item` elementów i rozmieszczenia elementów tak jak w powyższym `Source.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="277dc-126">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="277dc-127">Jest uproszczony implementacji.</span><span class="sxs-lookup"><span data-stu-id="277dc-127">It is a simplistic implementation.</span></span> <span data-ttu-id="277dc-128">Bardziej niezawodne wdrożenia będzie przygotowana do analizowania nieprawidłowy dokument.</span><span class="sxs-lookup"><span data-stu-id="277dc-128">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
  
 <span data-ttu-id="277dc-129">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="277dc-129">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="277dc-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="277dc-130">See Also</span></span>  
 [<span data-ttu-id="277dc-131">Zaawansowane LINQ to XML programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="277dc-131">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
