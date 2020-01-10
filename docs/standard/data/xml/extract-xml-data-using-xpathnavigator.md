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
# <a name="extract-xml-data-using-xpathnavigator"></a>Wyodrębnianie danych XML przy użyciu klasy XPathNavigator
Istnieje kilka różnych sposobów reprezentowania dokumentu XML w strukturze Microsoft .NET. Obejmuje to użycie <xref:System.String>lub za pomocą klas <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>i <xref:System.Xml.XPath.XPathDocument>. Aby ułatwić przechodzenie między różnymi reprezentacjami dokumentu XML, Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia wiele metod i właściwości wyodrębniania kodu XML jako <xref:System.String>, <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XmlWriter> obiektu.  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a>Konwertuj Element XPathNavigator na ciąg  
 Właściwość <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> klasy <xref:System.Xml.XPath.XPathNavigator> służy do uzyskiwania adiustacji całego dokumentu XML lub tylko znaczników jednego węzła i jego węzłów podrzędnych.  
  
> [!NOTE]
> Właściwość <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> pobiera adiustację tylko węzłów podrzędnych węzła.  
  
 Poniższy przykład kodu pokazuje, jak zapisać cały dokument XML zawarty w obiekcie <xref:System.Xml.XPath.XPathNavigator> jako <xref:System.String>, a także pojedynczy węzeł i jego węzły podrzędne.  
  
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
 Metoda <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> służy do przesyłania strumieniowego całej zawartości dokumentu XML lub tylko jednego węzła i jego węzłów podrzędnych do obiektu <xref:System.Xml.XmlReader>.  
  
 Gdy obiekt <xref:System.Xml.XmlReader> jest tworzony z bieżącym węzłem i jego węzłami podrzędnymi, właściwość <xref:System.Xml.XmlReader.ReadState%2A> obiektu <xref:System.Xml.XmlReader> zostanie ustawiona na <xref:System.Xml.ReadState.Initial>. Gdy metoda <xref:System.Xml.XmlReader.Read%2A> <xref:System.Xml.XmlReader> obiektu jest wywoływana po raz pierwszy, <xref:System.Xml.XmlReader> jest przenoszona do bieżącego węzła <xref:System.Xml.XPath.XPathNavigator>. Nowy obiekt <xref:System.Xml.XmlReader> będzie nadal odczytywany, dopóki nie zostanie osiągnięty koniec drzewa XML. W tym momencie Metoda <xref:System.Xml.XmlReader.Read%2A> zwraca `false`, a właściwość <xref:System.Xml.XmlReader.ReadState%2A> obiektu <xref:System.Xml.XmlReader> jest ustawiona na <xref:System.Xml.ReadState.EndOfFile>.  
  
 Położenie obiektu <xref:System.Xml.XPath.XPathNavigator> jest niezmienione przez utworzenie lub przemieszczenie <xref:System.Xml.XmlReader> obiektu. Metoda <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> jest prawidłowa tylko wtedy, gdy jest umieszczona w węźle elementu lub głównego.  
  
 Poniższy przykład pokazuje, jak uzyskać <xref:System.Xml.XmlReader> obiekt zawierający cały dokument XML w obiekcie <xref:System.Xml.XPath.XPathDocument>, a także pojedynczy węzeł i jego węzły podrzędne.  
  
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
 Metoda <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> służy do przesyłania strumieniowego całej zawartości dokumentu XML lub tylko jednego węzła i jego węzłów podrzędnych do obiektu <xref:System.Xml.XmlWriter>.  
  
 Położenie obiektu <xref:System.Xml.XPath.XPathNavigator> jest niezmienione przez utworzenie obiektu <xref:System.Xml.XmlWriter>.  
  
 Poniższy przykład pokazuje, jak uzyskać <xref:System.Xml.XmlWriter> obiekt zawierający cały dokument XML w obiekcie <xref:System.Xml.XPath.XPathDocument>, a także pojedynczy węzeł i jego węzły podrzędne.  
  
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
  
 Przykład pobiera plik `books.xml` znajdujący się wcześniej w tym temacie jako dane wejściowe.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
