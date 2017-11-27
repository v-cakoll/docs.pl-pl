---
title: "Porady: strumienia fragmenty XML z dostępem do informacji w nagłówku (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f745d0725b9b05620b4b967e51b452e54fe5e6d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a><span data-ttu-id="20d80-102">Porady: strumienia fragmenty XML z dostępem do informacji w nagłówku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20d80-102">How to: Stream XML Fragments with Access to Header Information (Visual Basic)</span></span>
<span data-ttu-id="20d80-103">Czasami trzeba arbitralnie duże pliki XML do odczytu i zapisu aplikacji, dzięki czemu zużycie pamięci aplikacji jest atrybutem wartości prognozowanych.</span><span class="sxs-lookup"><span data-stu-id="20d80-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="20d80-104">Przy próbie wypełnić drzewo XML z dużego pliku XML, użycie pamięci będzie proporcjonalny do rozmiaru pliku — to znaczy nadmierne.</span><span class="sxs-lookup"><span data-stu-id="20d80-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="20d80-105">W związku z tym należy w zamian użyj technika przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="20d80-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="20d80-106">Jedną z opcji jest napisanie swojej aplikacji za pomocą <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="20d80-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="20d80-107">Jednak możesz chcieć użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do badania drzewo składni XML.</span><span class="sxs-lookup"><span data-stu-id="20d80-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="20d80-108">Jeśli jest to możliwe, można napisać metodę niestandardowych osi.</span><span class="sxs-lookup"><span data-stu-id="20d80-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="20d80-109">Aby uzyskać więcej informacji, zobacz [porady: pisanie LINQ do metody osi XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="20d80-109">For more information, see [How to: Write a LINQ to XML Axis Method (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="20d80-110">Aby napisać metodę osi, zapisu małych metody, która używa <xref:System.Xml.XmlReader> odczytać węzłów, dopóki nie osiągnie jednego z węzłów, w których jesteś zainteresowany.</span><span class="sxs-lookup"><span data-stu-id="20d80-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="20d80-111">Następnie wywołuje metodę <xref:System.Xml.Linq.XNode.ReadFrom%2A>, która odczytuje z <xref:System.Xml.XmlReader> i tworzy XML fragment.</span><span class="sxs-lookup"><span data-stu-id="20d80-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="20d80-112">Następnie można pisać zapytania LINQ metodę niestandardowych osi.</span><span class="sxs-lookup"><span data-stu-id="20d80-112">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="20d80-113">Techniki przesyłania strumieniowego najlepiej są stosowane w sytuacji, gdy musisz przetworzyć dokumentu źródłowego tylko raz i może przetwarzać elementów w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="20d80-113">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="20d80-114">Niektóre standardowy kwerendy operatorów, takich jak <xref:System.Linq.Enumerable.OrderBy%2A>, iteracji ich źródłem Zbieraj wszystkie dane, sortowanie ich i ostatecznie yield pierwszego elementu w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="20d80-114">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="20d80-115">Należy pamiętać, że użycie operatora zapytania, który zostaje źródła przed reaguje pierwszy element, możesz nie zostaną zachowane zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="20d80-115">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20d80-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="20d80-116">Example</span></span>  
 <span data-ttu-id="20d80-117">Czasami problem pobiera małą ilością interesujące więcej.</span><span class="sxs-lookup"><span data-stu-id="20d80-117">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="20d80-118">W następującym dokumencie XML konsumenta metodę niestandardowych osi również musi znać nazwę każdego elementu należącego do klienta.</span><span class="sxs-lookup"><span data-stu-id="20d80-118">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="20d80-119">Podejście, które przyjmuje w tym przykładzie jest również obejrzeć takie informacje nagłówka, Zapisz informacje nagłówka i późniejszego kompilowania małych drzewa XML, który zawiera informacje o nagłówku i szczegóły są wyliczania.</span><span class="sxs-lookup"><span data-stu-id="20d80-119">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="20d80-120">Metoda osi następnie daje w wyniku tego nowego, mała drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="20d80-120">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="20d80-121">Zapytanie następnie ma dostęp do informacji w nagłówku, a także szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="20d80-121">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="20d80-122">Takie podejście charakteryzuje się zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="20d80-122">This approach has a small memory footprint.</span></span> <span data-ttu-id="20d80-123">Jak każdego fragmentu XML szczegółów jest zwróciło, nie będą przechowywane żadnych odwołań do poprzedniego fragmentu, i jest dostępny dla wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="20d80-123">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="20d80-124">Należy pamiętać, że ta metoda tworzy wiele obiektów krótko na stosie.</span><span class="sxs-lookup"><span data-stu-id="20d80-124">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="20d80-125">Poniższy przykład pokazuje, jak do wdrożenia i używa metody osi niestandardowych strumieni fragmenty XML z pliku określonego przez identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="20d80-125">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="20d80-126">Tej osi niestandardowe są zapisywane w szczególności taki sposób, że oczekuje, że dokument, który ma `Customer`, `Name`, i `Item` elementów i rozmieszczenia elementów jak powyższych `Source.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="20d80-126">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="20d80-127">Jest simplistic implementacji.</span><span class="sxs-lookup"><span data-stu-id="20d80-127">It is a simplistic implementation.</span></span> <span data-ttu-id="20d80-128">Czy można przygotować bardziej niezawodne implementacji przeanalizować nieprawidłowy dokument.</span><span class="sxs-lookup"><span data-stu-id="20d80-128">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
  
 <span data-ttu-id="20d80-129">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="20d80-129">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20d80-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20d80-130">See Also</span></span>  
 [<span data-ttu-id="20d80-131">Zaawansowane LINQ do XML programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20d80-131">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
