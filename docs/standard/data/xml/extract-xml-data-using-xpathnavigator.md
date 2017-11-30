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
# <a name="extract-xml-data-using-xpathnavigator"></a>Wyodrębnianie danych XML przy użyciu parametrem XPathNavigator
Istnieje kilka różnych sposobów do reprezentowania dokumentu XML w programie Microsoft .NET Framework. Obejmuje to przy użyciu <xref:System.String>, lub za pomocą <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, lub <xref:System.Xml.XPath.XPathDocument> klasy. Ułatwia przenoszenie między tymi różne reprezentacje dokumentu XML <xref:System.Xml.XPath.XPathNavigator> klasa udostępnia szereg metod i właściwości dla wyodrębniania XML jako <xref:System.String>, <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XmlWriter> obiektu.  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a>Konwertuj Element XPathNavigator na ciąg  
 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> klasy jest używany do pobierania znaczników całego dokumentu w formacie XML lub po prostu znaczników jeden węzeł i jego podrzędny węzłów.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Właściwość pobiera kod znaczników właśnie podrzędnych węzłów węzła.  
  
 Poniższy przykład kodu pokazuje sposób zapisywania całego dokumentu XML zawartych w <xref:System.Xml.XPath.XPathNavigator> obiekt jako <xref:System.String>, a także jeden węzeł i jego węzły podrzędne.  
  
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
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a>Konwertuj element XmlReader parametrem XPathNavigator  
 <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda jest używana do przesyłania strumieniowego całą zawartość dokumentu XML lub jeden węzeł i jego węzły podrzędne <xref:System.Xml.XmlReader> obiektu.  
  
 Gdy <xref:System.Xml.XmlReader> obiekt jest tworzony z bieżącego węzła i jego węzły podrzędne <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader.ReadState%2A> właściwość jest ustawiona na <xref:System.Xml.ReadState.Initial>. Gdy <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader.Read%2A> metoda jest wywoływana po raz pierwszy, <xref:System.Xml.XmlReader> zostanie przeniesiony do bieżącego węzła <xref:System.Xml.XPath.XPathNavigator>. Nowe <xref:System.Xml.XmlReader> obiektu w dalszym ciągu do odczytu do momentu osiągnięcia końca drzewo składni XML. W tym momencie <xref:System.Xml.XmlReader.Read%2A> metoda zwraca `false` i <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader.ReadState%2A> właściwość jest ustawiona na <xref:System.Xml.ReadState.EndOfFile>.  
  
 <xref:System.Xml.XPath.XPathNavigator> Położenie obiektu jest taki sam jak przez utworzenie lub przepływ <xref:System.Xml.XmlReader> obiektu. <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda jest prawidłowa, gdy znajduje się w węźle elementu lub głównego tylko.  
  
 Poniższy przykład przedstawia sposób uzyskać <xref:System.Xml.XmlReader> obiekt zawierający XML całego dokumentu w <xref:System.Xml.XPath.XPathDocument> obiektów oraz jeden węzeł i jego węzły podrzędne.  
  
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
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a>Konwertowanie do XmlWriter parametrem XPathNavigator  
 <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> Metoda jest używana do przesyłania strumieniowego całą zawartość dokumentu XML lub jeden węzeł i jego węzły podrzędne <xref:System.Xml.XmlWriter> obiektu.  
  
 <xref:System.Xml.XPath.XPathNavigator> Położenie obiektu jest taki sam jak przez utworzenie <xref:System.Xml.XmlWriter> obiektu.  
  
 Poniższy przykład przedstawia sposób uzyskać <xref:System.Xml.XmlWriter> obiekt zawierający XML całego dokumentu w <xref:System.Xml.XPath.XPathDocument> obiektów oraz jeden węzeł i jego węzły podrzędne.  
  
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
  
 Przykład przyjmuje `books.xml` odnaleźć pliku wcześniej w tym temacie jako dane wejściowe.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzania danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Węzeł nawigacji zestawu użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [Atrybut i Namespace węzła nawigacji użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [Uzyskiwanie dostępu do silnie typu danych XML przy użyciu parametrem XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
