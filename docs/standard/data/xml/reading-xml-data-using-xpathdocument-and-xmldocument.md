---
title: Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
ms.openlocfilehash: 87ae96944f9a9f2bbcefb54c343f429c75c3022d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710391"
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a>Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument
Istnieją dwa sposoby odczytywania dokumentu XML w <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw. Jeden polega na odczytaniu dokumentu XML przy użyciu klasy tylko <xref:System.Xml.XPath.XPathDocument> do odczytu, a druga — do odczytywania dokumentu XML przy użyciu <xref:System.Xml.XmlDocument> klasy edytowalnej <xref:System.Xml?displayProperty=nameWithType> w przestrzeni nazw.  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>Odczytywanie dokumentów XML przy użyciu klasy XPathDocument  
 <xref:System.Xml.XPath.XPathDocument> Klasa zapewnia szybką, tylko do odczytu, reprezentację w pamięci dokumentu XML przy użyciu modelu danych XPath. Wystąpienia <xref:System.Xml.XPath.XPathDocument> klasy są tworzone przy użyciu jednego z sześciu konstruktorów. <xref:System.IO.Stream>Te konstruktory umożliwiają odczytywanie dokumentu XML przy użyciu obiektu, <xref:System.IO.TextReader>, lub <xref:System.Xml.XmlReader> , a także `string` ścieżkę do pliku XML.  
  
 Poniższy przykład ilustruje użycie <xref:System.Xml.XPath.XPathDocument> `string` konstruktora klasy w celu odczytania dokumentu XML.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>Odczytywanie dokumentów XML przy użyciu klasy XmlDocument  
 <xref:System.Xml.XmlDocument> Klasa jest edytowalną reprezentacją w pamięci dokumentu XML implementującą W3C Document Object Model (dom) Level 1 Core i Core dom Level 2. Wystąpienia <xref:System.Xml.XmlDocument> klasy są tworzone przy użyciu jednego z trzech konstruktorów. Można utworzyć nowy pusty <xref:System.Xml.XmlDocument> obiekt, wywołując Konstruktor <xref:System.Xml.XmlDocument> klasy bez parametrów. <xref:System.Xml.XmlDocument.Load%2A> Po wywołaniu konstruktora Użyj metody, aby załadować dane XML do nowego <xref:System.Xml.XmlDocument> obiektu z <xref:System.IO.Stream>obiektu, <xref:System.IO.TextReader>, lub <xref:System.Xml.XmlReader> , a także `string` ścieżkę do pliku XML.  
  
 Poniższy przykład ilustruje użycie konstruktora <xref:System.Xml.XmlDocument> klasy bez parametrów i <xref:System.Xml.XmlDocument.Load%2A> metody w celu odczytania dokumentu XML.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>Określanie kodowania dokumentu XML  
 <xref:System.Xml.XmlReader> Obiekt może służyć do odczytywania dokumentu XML oraz do tworzenia <xref:System.Xml.XPath.XPathDocument> i <xref:System.Xml.XmlDocument> obiektów, jak pokazano w poprzednich sekcjach. Jednak <xref:System.Xml.XmlReader> obiekt może odczytywać dane, które nie są zakodowane i w związku z tym nie udostępniają żadnych informacji o kodowaniu.  
  
 <xref:System.Xml.XmlTextReader> Klasa dziedziczy z <xref:System.Xml.XmlReader> klasy, dostarcza informacje o kodowaniu przy użyciu jej <xref:System.Xml.XmlTextReader.Encoding%2A> właściwości i może służyć do tworzenia <xref:System.Xml.XPath.XPathDocument> obiektu lub <xref:System.Xml.XmlDocument> obiektu.  
  
 Aby uzyskać więcej informacji na temat informacji o kodowaniu dostarczonych <xref:System.Xml.XmlTextReader> przez klasę, zapoznaj się <xref:System.Xml.XmlTextReader.Encoding%2A> z <xref:System.Xml.XmlTextReader> właściwością w dokumentacji dotyczącej klasy.  
  
## <a name="creating-xpathnavigator-objects"></a>Tworzenie obiektów XPathNavigator  
 Po przeczytaniu dokumentu XML do obiektu <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> , można utworzyć <xref:System.Xml.XPath.XPathNavigator> obiekt do wyboru, szacowania, nawigowania i w niektórych przypadkach, edytować bazowe dane XML.  
  
 <xref:System.Xml.XPath.XPathDocument> Klasy <xref:System.Xml.XmlDocument> i, <xref:System.Xml.XmlNode> oprócz klasy, implementują <xref:System.Xml.XPath.IXPathNavigable> Interfejs <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw. W związku z tym wszystkie trzy klasy zapewniają <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> metodę, która zwraca <xref:System.Xml.XPath.XPathNavigator> obiekt.  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>Edytowanie dokumentów XML przy użyciu klasy XPathNavigator  
 Oprócz wyboru, oceny i nawigowania po <xref:System.Xml.XPath.XPathNavigator> danych XML, Klasa może być używana do edycji dokumentu XML w niektórych przypadkach na podstawie obiektu, który go utworzył.  
  
 <xref:System.Xml.XPath.XPathDocument> Klasa jest tylko do odczytu, podczas gdy <xref:System.Xml.XmlDocument> Klasa jest edytowalna i w związku z <xref:System.Xml.XPath.XPathNavigator> tym obiekty utworzone na <xref:System.Xml.XPath.XPathDocument> podstawie obiektu nie mogą być używane do edytowania dokumentu XML, podczas gdy mogą <xref:System.Xml.XmlDocument> one być utworzone na podstawie obiektu. <xref:System.Xml.XPath.XPathDocument> Klasa powinna być używana do odczytu tylko dokumentu XML. W przypadkach, gdy konieczne jest edytowanie dokumentu XML lub wymaganie dostępu do dodatkowych funkcji udostępnianych przez <xref:System.Xml.XmlDocument> klasę, takich jak obsługa zdarzeń, należy użyć <xref:System.Xml.XmlDocument> klasy.  
  
 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> klasy określa, czy <xref:System.Xml.XPath.XPathNavigator> obiekt może edytować dane XML.  
  
 W poniższej tabeli opisano wartość <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwości dla każdej klasy.  
  
|<xref:System.Xml.XPath.IXPathNavigable>Realizacji|<xref:System.Xml.XPath.XPathNavigator.CanEdit%2A>Wartościami|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [Edytowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
- [Weryfikacja schematu przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
