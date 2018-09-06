---
title: Odczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69e22328c39ae68acc4baff12775b49fbac80696
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869970"
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a>Odczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument
Istnieją dwa sposoby, które można odczytać dokumentu XML w <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw. Jeden jest do odczytu dokumentu XML przy użyciu tylko do odczytu <xref:System.Xml.XPath.XPathDocument> klasy, a drugi jest do odczytu dokumentu XML przy użyciu edytowalne <xref:System.Xml.XmlDocument> klasy w <xref:System.Xml?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>Odczytywanie dokumentów XML przy użyciu klas XPathDocument klasy  
 <xref:System.Xml.XPath.XPathDocument> Klasa udostępnia reprezentację dokumentu XML przy użyciu modelu danych XPath, szybka i tylko do odczytu w pamięci. Wystąpienia elementu <xref:System.Xml.XPath.XPathDocument> klasy są tworzone przy użyciu jednej z jego sześciu konstruktorów. Te konstruktory umożliwiają odczytać dokument XML za pomocą <xref:System.IO.Stream>, <xref:System.IO.TextReader>, lub <xref:System.Xml.XmlReader> obiektu, jak również `string` ścieżkę do pliku XML.  
  
 Poniższy przykład ilustruje użycie <xref:System.Xml.XPath.XPathDocument> klasy `string` konstruktora do odczytu dokumentu XML.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>Odczytywanie dokumentów XML za pomocą klasy XmlDocument  
 <xref:System.Xml.XmlDocument> Klasa jest można edytować w pamięci reprezentację w postaci dokumentu XML, implementowanie W3C Document Object Model (DOM) poziom 1 Core i Core DOM poziomu 2. Wystąpienia elementu <xref:System.Xml.XmlDocument> klasy są tworzone przy użyciu jednej z jego trzy konstruktory. Możesz utworzyć nowy, pusty <xref:System.Xml.XmlDocument> obiektu przez wywołanie metody <xref:System.Xml.XmlDocument> klasa konstruktor bez parametrów. Po wywołaniu konstruktora, należy użyć <xref:System.Xml.XmlDocument.Load%2A> metodę, aby załadować dane XML do nowego <xref:System.Xml.XmlDocument> obiektu z <xref:System.IO.Stream>, <xref:System.IO.TextReader>, lub <xref:System.Xml.XmlReader> obiektu, jak również `string` ścieżkę do pliku XML.  
  
 Poniższy przykład ilustruje użycie <xref:System.Xml.XmlDocument> klasa konstruktor bez parametrów i <xref:System.Xml.XmlDocument.Load%2A> metodę w celu odczytania dokumentu XML.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>Określanie kodowania dokumentu XML  
 <xref:System.Xml.XmlReader> Obiekt może być używany do odczytu dokumentu XML i Utwórz <xref:System.Xml.XPath.XPathDocument> i <xref:System.Xml.XmlDocument> obiekty, jak pokazano w poprzednich sekcjach. Jednak <xref:System.Xml.XmlReader> obiektu może odczytywać dane, które nie jest zaszyfrowana i w rezultacie nie zawierają żadnych informacji kodowania.  
  
 <xref:System.Xml.XmlTextReader> Klasa dziedziczy <xref:System.Xml.XmlReader> klasy, oferuje kodowania za pomocą informacji o jego <xref:System.Xml.XmlTextReader.Encoding%2A> właściwości i może służyć do tworzenia <xref:System.Xml.XPath.XPathDocument> obiektu lub <xref:System.Xml.XmlDocument> obiektu.  
  
 Aby uzyskać więcej informacji na temat kodowania informacji dostarczonych przez <xref:System.Xml.XmlTextReader> klasy, zobacz <xref:System.Xml.XmlTextReader.Encoding%2A> właściwość <xref:System.Xml.XmlTextReader> klasy dokumentację referencyjną.  
  
## <a name="creating-xpathnavigator-objects"></a>Tworzenie obiektów klasy XPathNavigator  
 Po przeczytaniu dokumentu XML do którejkolwiek <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu, możesz utworzyć <xref:System.Xml.XPath.XPathNavigator> obiektu, wybierz, oceny i przejść, a w niektórych przypadkach, Edytuj podstawowych danych XML.  
  
 Zarówno <xref:System.Xml.XPath.XPathDocument> i <xref:System.Xml.XmlDocument> klasy dodatkowo do <xref:System.Xml.XmlNode> klasy, implementować <xref:System.Xml.XPath.IXPathNavigable> interfejsu <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw. W rezultacie zapewnienia wszystkich trzech klasach <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> metodę, która zwraca <xref:System.Xml.XPath.XPathNavigator> obiektu.  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>Edytowanie dokumentów XML za pomocą klasy parametrem XPathNavigator  
 Oprócz wybierając, oceniania i nawigowanie wśród danych XML <xref:System.Xml.XPath.XPathNavigator> klasy może służyć do edycji dokumentu XML, w niektórych przypadkach, w oparciu o obiekt, który go utworzył.  
  
 <xref:System.Xml.XPath.XPathDocument> Klasy jest tylko do odczytu podczas <xref:System.Xml.XmlDocument> klasy są edytowalne i w rezultacie <xref:System.Xml.XPath.XPathNavigator> obiekty utworzone na podstawie <xref:System.Xml.XPath.XPathDocument> obiektu nie można użyć do edytowania dokumentu XML, a te utworzone na podstawie <xref:System.Xml.XmlDocument> obiekt może. <xref:System.Xml.XPath.XPathDocument> Klasy mają być używane do odczytu tylko dokumentu XML. W przypadkach, w których trzeba edytować dokumentu XML lub wymagają dostępu do dodatkowych funkcji zapewnianych przez <xref:System.Xml.XmlDocument> klasy, takie jak obsługa zdarzeń <xref:System.Xml.XmlDocument> klasa powinna być używana.  
  
 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> Określa klasę, jeśli <xref:System.Xml.XPath.XPathNavigator> obiektu może edytować dane XML.  
  
 W poniższej tabeli opisano wartość <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwości dla każdej klasy.  
  
|<xref:System.Xml.XPath.IXPathNavigable> Implementacja|<xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Wartość|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [Edytowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
- [Weryfikacja schematu przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
