---
title: Wyodrębnianie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
ms.openlocfilehash: e639931204a416c3cde87044730364a4f387799a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287769"
---
# <a name="extract-xml-data-using-xpathnavigator"></a>Wyodrębnianie danych XML przy użyciu klasy XPathNavigator
Istnieje kilka różnych sposobów reprezentowania dokumentu XML w strukturze Microsoft .NET. Obejmuje to korzystanie z <xref:System.String> , lub przy użyciu <xref:System.Xml.XmlReader> klas, <xref:System.Xml.XmlWriter> , <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument> . Aby ułatwić przechodzenie między różnymi reprezentacjami dokumentu XML, <xref:System.Xml.XPath.XPathNavigator> Klasa zawiera wiele metod i właściwości wyodrębniania XML jako <xref:System.String> <xref:System.Xml.XmlReader> obiekt lub <xref:System.Xml.XmlWriter> obiekt.  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a>Konwertuj Element XPathNavigator na ciąg  
 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A>Właściwość <xref:System.Xml.XPath.XPathNavigator> klasy służy do uzyskiwania adiustacji całego dokumentu XML lub tylko znaczników jednego węzła i jego węzłów podrzędnych.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Właściwość pobiera adiustację tylko węzłów podrzędnych węzła.  
  
 Poniższy przykład kodu pokazuje, jak zapisać cały dokument XML zawarty w <xref:System.Xml.XPath.XPathNavigator> obiekcie jako <xref:System.String> , a także pojedynczy węzeł i jego węzły podrzędne.  
  
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
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a>Konwertuj Element XPathNavigator na element XmlReader  
 <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A>Metoda jest używana do przesyłania strumieniowego całej zawartości dokumentu XML lub tylko jednego węzła i jego węzłów podrzędnych do <xref:System.Xml.XmlReader> obiektu.  
  
 Gdy <xref:System.Xml.XmlReader> obiekt zostanie utworzony z bieżącym węzłem i jego węzłami podrzędnymi, <xref:System.Xml.XmlReader> właściwość obiektu <xref:System.Xml.XmlReader.ReadState%2A> jest ustawiona na <xref:System.Xml.ReadState.Initial> . Gdy <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader.Read%2A> Metoda obiektu jest wywoływana po raz pierwszy, <xref:System.Xml.XmlReader> jest przenoszona do bieżącego węzła <xref:System.Xml.XPath.XPathNavigator> . Nowy <xref:System.Xml.XmlReader> obiekt jest nadal odczytywany, dopóki nie zostanie osiągnięty koniec drzewa XML. W tym momencie <xref:System.Xml.XmlReader.Read%2A> Metoda zwraca `false` i <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader.ReadState%2A> właściwość obiektu jest ustawiona na <xref:System.Xml.ReadState.EndOfFile> .  
  
 <xref:System.Xml.XPath.XPathNavigator>Położenie obiektu jest niezmienione przez utworzenie lub przemieszczenie <xref:System.Xml.XmlReader> obiektu. <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A>Metoda jest prawidłowa tylko wtedy, gdy jest umieszczona w węźle elementu lub głównego.  
  
 Poniższy przykład pokazuje, jak uzyskać <xref:System.Xml.XmlReader> obiekt zawierający cały dokument XML w <xref:System.Xml.XPath.XPathDocument> obiekcie, a także pojedynczy węzeł i jego węzły podrzędne.  
  
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
  
 Przykład pobiera `books.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a>Konwertowanie elementu XPathNavigator na element XmlWriter  
 <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A>Metoda jest używana do przesyłania strumieniowego całej zawartości dokumentu XML lub tylko jednego węzła i jego węzłów podrzędnych do <xref:System.Xml.XmlWriter> obiektu.  
  
 <xref:System.Xml.XPath.XPathNavigator>Położenie obiektu jest niezmienione przez utworzenie <xref:System.Xml.XmlWriter> obiektu.  
  
 Poniższy przykład pokazuje, jak uzyskać <xref:System.Xml.XmlWriter> obiekt zawierający cały dokument XML w <xref:System.Xml.XPath.XPathDocument> obiekcie, a także pojedynczy węzeł i jego węzły podrzędne.  
  
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
  
 Przykład pobiera `books.xml` plik znaleziony wcześniej w tym temacie jako dane wejściowe.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](process-xml-data-using-the-xpath-data-model.md)
- [Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator](node-set-navigation-using-xpathnavigator.md)
- [Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
