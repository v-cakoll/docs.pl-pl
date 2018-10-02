---
title: Wyodrębnianie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d838f3d9f4c9400fbbef0fb24f5275eff2038c49
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863512"
---
# <a name="extract-xml-data-using-xpathnavigator"></a><span data-ttu-id="3a486-102">Wyodrębnianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3a486-102">Extract XML Data Using XPathNavigator</span></span>
<span data-ttu-id="3a486-103">Istnieje kilka różnych sposobów, aby przedstawić dokumentu XML w programie Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3a486-103">There are several different ways to represent an XML document in the Microsoft .NET Framework.</span></span> <span data-ttu-id="3a486-104">W tym za pomocą <xref:System.String>, lub za pomocą <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, lub <xref:System.Xml.XPath.XPathDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="3a486-104">This includes using a <xref:System.String>, or by using the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, or <xref:System.Xml.XPath.XPathDocument> classes.</span></span> <span data-ttu-id="3a486-105">Aby ułatwić przenoszenie między te różne reprezentacje dokumentu XML <xref:System.Xml.XPath.XPathNavigator> klasy udostępnia kilka metod i właściwości XML jako wyodrębniania <xref:System.String>, <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XmlWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3a486-105">To facilitate moving between these different representations of an XML document, the <xref:System.Xml.XPath.XPathNavigator> class provides a number of methods and properties for extracting the XML as a <xref:System.String>, <xref:System.Xml.XmlReader> object or <xref:System.Xml.XmlWriter> object.</span></span>  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a><span data-ttu-id="3a486-106">Konwertuj na ciąg parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3a486-106">Convert an XPathNavigator to a String</span></span>  
 <span data-ttu-id="3a486-107"><xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> klasa jest używana do pobrania znaczników całego dokumentu w formacie XML lub po prostu znaczników jeden węzeł i jego podrzędny węzłów.</span><span class="sxs-lookup"><span data-stu-id="3a486-107">The <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class is used to get the markup of the entire XML document or just the markup of a single node and its child nodes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a486-108"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Właściwości pobiera znaczniki po prostu podrzędne węzły węzła.</span><span class="sxs-lookup"><span data-stu-id="3a486-108">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property gets the markup of just the child nodes of a node.</span></span>  
  
 <span data-ttu-id="3a486-109">Poniższy przykład kodu pokazuje sposób zapisywania całego dokumentu XML zawartych w <xref:System.Xml.XPath.XPathNavigator> obiektu jako <xref:System.String>, a także jeden węzeł i jego węzłami podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="3a486-109">The following code example shows how to save an entire XML document contained in an <xref:System.Xml.XPath.XPathNavigator> object as a <xref:System.String>, as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("input.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Save the entire input.xml document to a string.  
Dim xml As String = navigator.OuterXml  
  
' Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element)  
Dim root As String = navigator.OuterXml  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Save the entire input.xml document to a string.  
string xml = navigator.OuterXml;  
  
// Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element);  
string root = navigator.OuterXml;  
```  
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a><span data-ttu-id="3a486-110">Konwertuj Element XPathNavigator do elementu XmlReader</span><span class="sxs-lookup"><span data-stu-id="3a486-110">Convert an XPathNavigator to an XmlReader</span></span>  
 <span data-ttu-id="3a486-111"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda jest używana do przesyłania strumieniowego całą zawartość dokumentu XML lub jeden węzeł i jego węzłami podrzędnymi, aby <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3a486-111">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlReader> object.</span></span>  
  
 <span data-ttu-id="3a486-112">Gdy <xref:System.Xml.XmlReader> obiekt zostanie utworzony przy użyciu bieżącego węzła i jego węzłów podrzędnych <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader.ReadState%2A> właściwość jest ustawiona na <xref:System.Xml.ReadState.Initial>.</span><span class="sxs-lookup"><span data-stu-id="3a486-112">When the <xref:System.Xml.XmlReader> object is created with the current node and its child nodes, the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.Initial>.</span></span> <span data-ttu-id="3a486-113">Gdy <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader.Read%2A> metoda jest wywoływana po raz pierwszy <xref:System.Xml.XmlReader> zostanie przeniesiony do bieżącego węzła <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="3a486-113">When the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.Read%2A> method is called for the first time, the <xref:System.Xml.XmlReader> is moved to the current node of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="3a486-114">Nowy <xref:System.Xml.XmlReader> obiektu w dalszym ciągu odczyt aż do osiągnięcia końca drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="3a486-114">The new <xref:System.Xml.XmlReader> object continues to read until the end of the XML tree is reached.</span></span> <span data-ttu-id="3a486-115">W tym momencie <xref:System.Xml.XmlReader.Read%2A> metoda zwraca `false` i <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader.ReadState%2A> właściwość jest ustawiona na <xref:System.Xml.ReadState.EndOfFile>.</span><span class="sxs-lookup"><span data-stu-id="3a486-115">At this point, the <xref:System.Xml.XmlReader.Read%2A> method returns `false` and the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.EndOfFile>.</span></span>  
  
 <span data-ttu-id="3a486-116"><xref:System.Xml.XPath.XPathNavigator> Położenie obiektu są takie same jak za tworzenie i przenoszenie <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3a486-116">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation or movement of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="3a486-117"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda jest tylko prawidłowy w przypadku umieszczony na węźle element lub katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="3a486-117">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is only valid when positioned on an element or root node.</span></span>  
  
 <span data-ttu-id="3a486-118">Poniższy przykład pokazuje, jak uzyskać <xref:System.Xml.XmlReader> obiekt zawierający cały dokument w <xref:System.Xml.XPath.XPathDocument> obiektu, a także jeden węzeł i jego węzłami podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="3a486-118">The following example shows how to get an <xref:System.Xml.XmlReader> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlReader.  
Dim xml As XmlReader = navigator.ReadSubtree()  
  
While xml.Read()  
    Console.WriteLine(xml.ReadInnerXml())  
End While  
  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlReader = navigator.ReadSubtree()  
  
While book.Read()  
    Console.WriteLine(book.ReadInnerXml())  
End While  
  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlReader.  
XmlReader xml = navigator.ReadSubtree();  
  
while (xml.Read())  
{  
    Console.WriteLine(xml.ReadInnerXml());  
}  
  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlReader book = navigator.ReadSubtree();  
  
while (book.Read())  
{  
    Console.WriteLine(book.ReadInnerXml());  
}  
  
book.Close();  
```  
  
 <span data-ttu-id="3a486-119">Przykład przyjmuje `books.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="3a486-119">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a><span data-ttu-id="3a486-120">Konwertowanie XmlWriter parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3a486-120">Converting an XPathNavigator to an XmlWriter</span></span>  
 <span data-ttu-id="3a486-121"><xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> Metoda jest używana do przesyłania strumieniowego całą zawartość dokumentu XML lub jeden węzeł i jego węzłami podrzędnymi, aby <xref:System.Xml.XmlWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3a486-121">The <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="3a486-122"><xref:System.Xml.XPath.XPathNavigator> Położenie obiektu są takie same jak przez utworzenie <xref:System.Xml.XmlWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3a486-122">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation of the <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="3a486-123">Poniższy przykład pokazuje, jak uzyskać <xref:System.Xml.XmlWriter> obiekt zawierający cały dokument w <xref:System.Xml.XPath.XPathDocument> obiektu, a także jeden węzeł i jego węzłami podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="3a486-123">The following example shows how to get an <xref:System.Xml.XmlWriter> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlWriter.  
Dim xml As XmlWriter = XmlWriter.Create("newbooks.xml")  
navigator.WriteSubtree(xml)  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlWriter = XmlWriter.Create("book.xml")  
navigator.WriteSubtree(book)  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlWriter.  
XmlWriter xml = XmlWriter.Create("newbooks.xml");  
navigator.WriteSubtree(xml);  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlWriter book = XmlWriter.Create("book.xml");  
navigator.WriteSubtree(book);  
book.Close();  
```  
  
 <span data-ttu-id="3a486-124">Przykład przyjmuje `books.xml` znaleźć pliku wcześniej w tym temacie jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="3a486-124">The example takes the `books.xml` file found earlier in this topic as input.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a486-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a486-125">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="3a486-126">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="3a486-126">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="3a486-127">Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3a486-127">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
- [<span data-ttu-id="3a486-128">Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3a486-128">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
- [<span data-ttu-id="3a486-129">Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3a486-129">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
