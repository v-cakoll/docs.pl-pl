---
title: Wyodrębnianie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
ms.openlocfilehash: 627da3c8c45d007e677c4f92f4d5cd602d34ae84
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710859"
---
# <a name="extract-xml-data-using-xpathnavigator"></a><span data-ttu-id="cee61-102">Wyodrębnianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cee61-102">Extract XML Data Using XPathNavigator</span></span>
<span data-ttu-id="cee61-103">Istnieje kilka różnych sposobów reprezentowania dokumentu XML w strukturze Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="cee61-103">There are several different ways to represent an XML document in the Microsoft .NET Framework.</span></span> <span data-ttu-id="cee61-104">Obejmuje to korzystanie z <xref:System.String>, lub przy użyciu klas <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlDocument>, lub <xref:System.Xml.XPath.XPathDocument> .</span><span class="sxs-lookup"><span data-stu-id="cee61-104">This includes using a <xref:System.String>, or by using the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, or <xref:System.Xml.XPath.XPathDocument> classes.</span></span> <span data-ttu-id="cee61-105">Aby ułatwić przechodzenie między różnymi reprezentacjami <xref:System.Xml.XPath.XPathNavigator> dokumentu XML, Klasa zawiera wiele metod i właściwości wyodrębniania XML jako <xref:System.String> <xref:System.Xml.XmlReader> obiekt lub <xref:System.Xml.XmlWriter> obiekt.</span><span class="sxs-lookup"><span data-stu-id="cee61-105">To facilitate moving between these different representations of an XML document, the <xref:System.Xml.XPath.XPathNavigator> class provides a number of methods and properties for extracting the XML as a <xref:System.String>, <xref:System.Xml.XmlReader> object or <xref:System.Xml.XmlWriter> object.</span></span>  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a><span data-ttu-id="cee61-106">Konwertuj Element XPathNavigator na ciąg</span><span class="sxs-lookup"><span data-stu-id="cee61-106">Convert an XPathNavigator to a String</span></span>  
 <span data-ttu-id="cee61-107"><xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> klasy służy do uzyskiwania adiustacji całego dokumentu XML lub tylko znaczników jednego węzła i jego węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="cee61-107">The <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class is used to get the markup of the entire XML document or just the markup of a single node and its child nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cee61-108"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Właściwość pobiera adiustację tylko węzłów podrzędnych węzła.</span><span class="sxs-lookup"><span data-stu-id="cee61-108">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property gets the markup of just the child nodes of a node.</span></span>  
  
 <span data-ttu-id="cee61-109">Poniższy przykład kodu pokazuje <xref:System.Xml.XPath.XPathNavigator> <xref:System.String>, jak zapisać cały dokument XML zawarty w obiekcie jako, a także pojedynczy węzeł i jego węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="cee61-109">The following code example shows how to save an entire XML document contained in an <xref:System.Xml.XPath.XPathNavigator> object as a <xref:System.String>, as well as a single node and its child nodes.</span></span>  
  
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
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a><span data-ttu-id="cee61-110">Konwertuj Element XPathNavigator na element XmlReader</span><span class="sxs-lookup"><span data-stu-id="cee61-110">Convert an XPathNavigator to an XmlReader</span></span>  
 <span data-ttu-id="cee61-111"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda jest używana do przesyłania strumieniowego całej zawartości dokumentu XML lub tylko jednego węzła i jego węzłów podrzędnych do <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cee61-111">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlReader> object.</span></span>  
  
 <span data-ttu-id="cee61-112">Gdy <xref:System.Xml.XmlReader> obiekt zostanie utworzony z bieżącym węzłem i jego węzłami podrzędnymi, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader.ReadState%2A> właściwość obiektu jest ustawiona na <xref:System.Xml.ReadState.Initial>.</span><span class="sxs-lookup"><span data-stu-id="cee61-112">When the <xref:System.Xml.XmlReader> object is created with the current node and its child nodes, the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.Initial>.</span></span> <span data-ttu-id="cee61-113">Gdy <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader.Read%2A> metoda obiektu jest wywoływana po raz pierwszy, <xref:System.Xml.XmlReader> jest przenoszona do bieżącego węzła. <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="cee61-113">When the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.Read%2A> method is called for the first time, the <xref:System.Xml.XmlReader> is moved to the current node of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="cee61-114">Nowy <xref:System.Xml.XmlReader> obiekt jest nadal odczytywany, dopóki nie zostanie osiągnięty koniec drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="cee61-114">The new <xref:System.Xml.XmlReader> object continues to read until the end of the XML tree is reached.</span></span> <span data-ttu-id="cee61-115">W tym momencie <xref:System.Xml.XmlReader.Read%2A> Metoda zwraca `false` i <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader.ReadState%2A> właściwość obiektu jest ustawiona na. <xref:System.Xml.ReadState.EndOfFile></span><span class="sxs-lookup"><span data-stu-id="cee61-115">At this point, the <xref:System.Xml.XmlReader.Read%2A> method returns `false` and the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.EndOfFile>.</span></span>  
  
 <span data-ttu-id="cee61-116">Położenie <xref:System.Xml.XPath.XPathNavigator> obiektu jest niezmienione przez utworzenie lub przemieszczenie <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cee61-116">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation or movement of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="cee61-117"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda jest prawidłowa tylko wtedy, gdy jest umieszczona w węźle elementu lub głównego.</span><span class="sxs-lookup"><span data-stu-id="cee61-117">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is only valid when positioned on an element or root node.</span></span>  
  
 <span data-ttu-id="cee61-118">Poniższy przykład pokazuje, jak uzyskać <xref:System.Xml.XmlReader> obiekt zawierający cały dokument XML w <xref:System.Xml.XPath.XPathDocument> obiekcie, a także pojedynczy węzeł i jego węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="cee61-118">The following example shows how to get an <xref:System.Xml.XmlReader> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
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
  
 <span data-ttu-id="cee61-119">Przykład pobiera `books.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="cee61-119">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a><span data-ttu-id="cee61-120">Konwertowanie elementu XPathNavigator na element XmlWriter</span><span class="sxs-lookup"><span data-stu-id="cee61-120">Converting an XPathNavigator to an XmlWriter</span></span>  
 <span data-ttu-id="cee61-121"><xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> Metoda jest używana do przesyłania strumieniowego całej zawartości dokumentu XML lub tylko jednego węzła i jego węzłów podrzędnych do <xref:System.Xml.XmlWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cee61-121">The <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="cee61-122">Położenie <xref:System.Xml.XPath.XPathNavigator> obiektu jest niezmienione przez utworzenie <xref:System.Xml.XmlWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cee61-122">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation of the <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="cee61-123">Poniższy przykład pokazuje, jak uzyskać <xref:System.Xml.XmlWriter> obiekt zawierający cały dokument XML w <xref:System.Xml.XPath.XPathDocument> obiekcie, a także pojedynczy węzeł i jego węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="cee61-123">The following example shows how to get an <xref:System.Xml.XmlWriter> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
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
  
 <span data-ttu-id="cee61-124">Przykład pobiera `books.xml` plik znaleziony wcześniej w tym temacie jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="cee61-124">The example takes the `books.xml` file found earlier in this topic as input.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cee61-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cee61-125">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="cee61-126">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="cee61-126">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="cee61-127">Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cee61-127">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="cee61-128">Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cee61-128">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="cee61-129">Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cee61-129">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
