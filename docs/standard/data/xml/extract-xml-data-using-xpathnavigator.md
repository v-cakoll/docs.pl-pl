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
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47157080"
---
# <a name="extract-xml-data-using-xpathnavigator"></a>Wyodrębnianie danych XML przy użyciu klasy XPathNavigator
Istnieje kilka różnych sposobów, aby przedstawić dokumentu XML w programie Microsoft .NET Framework. W tym za pomocą <xref:System.String>, lub za pomocą <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, lub <xref:System.Xml.XPath.XPathDocument> klasy. Aby ułatwić przenoszenie między te różne reprezentacje dokumentu XML <xref:System.Xml.XPath.XPathNavigator> klasy udostępnia kilka metod i właściwości XML jako wyodrębniania <xref:System.String>, <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XmlWriter> obiektu.  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a>Konwertuj na ciąg parametrem XPathNavigator  
 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> klasa jest używana do pobrania znaczników całego dokumentu w formacie XML lub po prostu znaczników jeden węzeł i jego podrzędny węzłów.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Właściwości pobiera znaczniki po prostu podrzędne węzły węzła.  
  
 Poniższy przykład kodu pokazuje sposób zapisywania całego dokumentu XML zawartych w <xref:System.Xml.XPath.XPathNavigator> obiektu jako <xref:System.String>, a także jeden węzeł i jego węzłami podrzędnymi.  
  
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
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a>Konwertuj Element XPathNavigator do elementu XmlReader  
 <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda jest używana do przesyłania strumieniowego całą zawartość dokumentu XML lub jeden węzeł i jego węzłami podrzędnymi, aby <xref:System.Xml.XmlReader> obiektu.  
  
 Gdy <xref:System.Xml.XmlReader> obiekt zostanie utworzony przy użyciu bieżącego węzła i jego węzłów podrzędnych <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader.ReadState%2A> właściwość jest ustawiona na <xref:System.Xml.ReadState.Initial>. Gdy <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader.Read%2A> metoda jest wywoływana po raz pierwszy <xref:System.Xml.XmlReader> zostanie przeniesiony do bieżącego węzła <xref:System.Xml.XPath.XPathNavigator>. Nowy <xref:System.Xml.XmlReader> obiektu w dalszym ciągu odczyt aż do osiągnięcia końca drzewa XML. W tym momencie <xref:System.Xml.XmlReader.Read%2A> metoda zwraca `false` i <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader.ReadState%2A> właściwość jest ustawiona na <xref:System.Xml.ReadState.EndOfFile>.  
  
 <xref:System.Xml.XPath.XPathNavigator> Położenie obiektu są takie same jak za tworzenie i przenoszenie <xref:System.Xml.XmlReader> obiektu. <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda jest tylko prawidłowy w przypadku umieszczony na węźle element lub katalogu głównego.  
  
 Poniższy przykład pokazuje, jak uzyskać <xref:System.Xml.XmlReader> obiekt zawierający cały dokument w <xref:System.Xml.XPath.XPathDocument> obiektu, a także jeden węzeł i jego węzłami podrzędnymi.  
  
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
  
 Przykład przyjmuje `books.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a>Konwertowanie XmlWriter parametrem XPathNavigator  
 <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> Metoda jest używana do przesyłania strumieniowego całą zawartość dokumentu XML lub jeden węzeł i jego węzłami podrzędnymi, aby <xref:System.Xml.XmlWriter> obiektu.  
  
 <xref:System.Xml.XPath.XPathNavigator> Położenie obiektu są takie same jak przez utworzenie <xref:System.Xml.XmlWriter> obiektu.  
  
 Poniższy przykład pokazuje, jak uzyskać <xref:System.Xml.XmlWriter> obiekt zawierający cały dokument w <xref:System.Xml.XPath.XPathDocument> obiektu, a także jeden węzeł i jego węzłami podrzędnymi.  
  
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
  
 Przykład przyjmuje `books.xml` znaleźć pliku wcześniej w tym temacie jako dane wejściowe.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
- [Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
- [Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
