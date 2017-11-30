---
title: "Wyodrębnianie danych XML przy użyciu parametrem XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c42539db3750ebc2a4220ef776b89bbabe6aaca3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="extract-xml-data-using-xpathnavigator"></a><span data-ttu-id="27f88-102">Wyodrębnianie danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="27f88-102">Extract XML Data Using XPathNavigator</span></span>
<span data-ttu-id="27f88-103">Istnieje kilka różnych sposobów do reprezentowania dokumentu XML w programie Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27f88-103">There are several different ways to represent an XML document in the Microsoft .NET Framework.</span></span> <span data-ttu-id="27f88-104">Obejmuje to przy użyciu <xref:System.String>, lub za pomocą <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, lub <xref:System.Xml.XPath.XPathDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="27f88-104">This includes using a <xref:System.String>, or by using the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, or <xref:System.Xml.XPath.XPathDocument> classes.</span></span> <span data-ttu-id="27f88-105">Ułatwia przenoszenie między tymi różne reprezentacje dokumentu XML <xref:System.Xml.XPath.XPathNavigator> klasa udostępnia szereg metod i właściwości dla wyodrębniania XML jako <xref:System.String>, <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XmlWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="27f88-105">To facilitate moving between these different representations of an XML document, the <xref:System.Xml.XPath.XPathNavigator> class provides a number of methods and properties for extracting the XML as a <xref:System.String>, <xref:System.Xml.XmlReader> object or <xref:System.Xml.XmlWriter> object.</span></span>  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a><span data-ttu-id="27f88-106">Konwertuj Element XPathNavigator na ciąg</span><span class="sxs-lookup"><span data-stu-id="27f88-106">Convert an XPathNavigator to a String</span></span>  
 <span data-ttu-id="27f88-107"><xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> klasy jest używany do pobierania znaczników całego dokumentu w formacie XML lub po prostu znaczników jeden węzeł i jego podrzędny węzłów.</span><span class="sxs-lookup"><span data-stu-id="27f88-107">The <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class is used to get the markup of the entire XML document or just the markup of a single node and its child nodes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27f88-108"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Właściwość pobiera kod znaczników właśnie podrzędnych węzłów węzła.</span><span class="sxs-lookup"><span data-stu-id="27f88-108">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property gets the markup of just the child nodes of a node.</span></span>  
  
 <span data-ttu-id="27f88-109">Poniższy przykład kodu pokazuje sposób zapisywania całego dokumentu XML zawartych w <xref:System.Xml.XPath.XPathNavigator> obiekt jako <xref:System.String>, a także jeden węzeł i jego węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="27f88-109">The following code example shows how to save an entire XML document contained in an <xref:System.Xml.XPath.XPathNavigator> object as a <xref:System.String>, as well as a single node and its child nodes.</span></span>  
  
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
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a><span data-ttu-id="27f88-110">Konwertuj element XmlReader parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="27f88-110">Convert an XPathNavigator to an XmlReader</span></span>  
 <span data-ttu-id="27f88-111"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda jest używana do przesyłania strumieniowego całą zawartość dokumentu XML lub jeden węzeł i jego węzły podrzędne <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="27f88-111">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlReader> object.</span></span>  
  
 <span data-ttu-id="27f88-112">Gdy <xref:System.Xml.XmlReader> obiekt jest tworzony z bieżącego węzła i jego węzły podrzędne <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader.ReadState%2A> właściwość jest ustawiona na <xref:System.Xml.ReadState.Initial>.</span><span class="sxs-lookup"><span data-stu-id="27f88-112">When the <xref:System.Xml.XmlReader> object is created with the current node and its child nodes, the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.Initial>.</span></span> <span data-ttu-id="27f88-113">Gdy <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader.Read%2A> metoda jest wywoływana po raz pierwszy, <xref:System.Xml.XmlReader> zostanie przeniesiony do bieżącego węzła <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="27f88-113">When the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.Read%2A> method is called for the first time, the <xref:System.Xml.XmlReader> is moved to the current node of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="27f88-114">Nowe <xref:System.Xml.XmlReader> obiektu w dalszym ciągu do odczytu do momentu osiągnięcia końca drzewo składni XML.</span><span class="sxs-lookup"><span data-stu-id="27f88-114">The new <xref:System.Xml.XmlReader> object continues to read until the end of the XML tree is reached.</span></span> <span data-ttu-id="27f88-115">W tym momencie <xref:System.Xml.XmlReader.Read%2A> metoda zwraca `false` i <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader.ReadState%2A> właściwość jest ustawiona na <xref:System.Xml.ReadState.EndOfFile>.</span><span class="sxs-lookup"><span data-stu-id="27f88-115">At this point, the <xref:System.Xml.XmlReader.Read%2A> method returns `false` and the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.EndOfFile>.</span></span>  
  
 <span data-ttu-id="27f88-116"><xref:System.Xml.XPath.XPathNavigator> Położenie obiektu jest taki sam jak przez utworzenie lub przepływ <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="27f88-116">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation or movement of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="27f88-117"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda jest prawidłowa, gdy znajduje się w węźle elementu lub głównego tylko.</span><span class="sxs-lookup"><span data-stu-id="27f88-117">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is only valid when positioned on an element or root node.</span></span>  
  
 <span data-ttu-id="27f88-118">Poniższy przykład przedstawia sposób uzyskać <xref:System.Xml.XmlReader> obiekt zawierający XML całego dokumentu w <xref:System.Xml.XPath.XPathDocument> obiektów oraz jeden węzeł i jego węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="27f88-118">The following example shows how to get an <xref:System.Xml.XmlReader> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
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
  
 <span data-ttu-id="27f88-119">Przykład przyjmuje `books.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="27f88-119">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a><span data-ttu-id="27f88-120">Konwertowanie do XmlWriter parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="27f88-120">Converting an XPathNavigator to an XmlWriter</span></span>  
 <span data-ttu-id="27f88-121"><xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> Metoda jest używana do przesyłania strumieniowego całą zawartość dokumentu XML lub jeden węzeł i jego węzły podrzędne <xref:System.Xml.XmlWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="27f88-121">The <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="27f88-122"><xref:System.Xml.XPath.XPathNavigator> Położenie obiektu jest taki sam jak przez utworzenie <xref:System.Xml.XmlWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="27f88-122">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation of the <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="27f88-123">Poniższy przykład przedstawia sposób uzyskać <xref:System.Xml.XmlWriter> obiekt zawierający XML całego dokumentu w <xref:System.Xml.XPath.XPathDocument> obiektów oraz jeden węzeł i jego węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="27f88-123">The following example shows how to get an <xref:System.Xml.XmlWriter> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
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
  
 <span data-ttu-id="27f88-124">Przykład przyjmuje `books.xml` odnaleźć pliku wcześniej w tym temacie jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="27f88-124">The example takes the `books.xml` file found earlier in this topic as input.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f88-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27f88-125">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="27f88-126">Przetwarzania danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="27f88-126">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="27f88-127">Węzeł nawigacji zestawu użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="27f88-127">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="27f88-128">Atrybut i Namespace węzła nawigacji użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="27f88-128">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="27f88-129">Uzyskiwanie dostępu do silnie typu danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="27f88-129">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
