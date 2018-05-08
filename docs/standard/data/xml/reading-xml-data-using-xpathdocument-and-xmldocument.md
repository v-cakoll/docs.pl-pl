---
title: Odczytywanie danych XML przy użyciu XPathDocument i XmlDocument
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc8e1b85543fca0281b6433dd5c87c28b37818db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a>Odczytywanie danych XML przy użyciu XPathDocument i XmlDocument
Istnieją dwa sposoby przeczytaj dokument XML w <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw. Jeden jest przeznaczony do odczytu dokumentu XML przy użyciu tylko do odczytu <xref:System.Xml.XPath.XPathDocument> klasy, a druga jest do odczytu dokumentu XML przy użyciu edytowalne <xref:System.Xml.XmlDocument> klasy w <xref:System.Xml?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>Odczytywanie dokumentów XML za pomocą klasy XPathDocument  
 <xref:System.Xml.XPath.XPathDocument> Klasa udostępnia reprezentację dokumentu XML za pomocą wyrażenia XPath modelu danych, szybka i tylko do odczytu w pamięci. Wystąpienia <xref:System.Xml.XPath.XPathDocument> klasy są tworzone przy użyciu jednej z jego sześciu konstruktorów. Konstruktory te umożliwiają odczytać dokument XML przy użyciu <xref:System.IO.Stream>, <xref:System.IO.TextReader>, lub <xref:System.Xml.XmlReader> obiektu, jak również `string` ścieżka do pliku XML.  
  
 Poniższy przykład przedstawia przy użyciu <xref:System.Xml.XPath.XPathDocument> klasy `string` konstruktora, aby odczytać dokument XML.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>Odczytywanie dokumentów XML za pomocą klasy XmlDocument  
 <xref:System.Xml.XmlDocument> Klasa jest edytowalny reprezentacji w pamięci dokumentu XML wykonania W3C modelu DOM (Document Object) poziom 1 Core i Core DOM poziom 2. Wystąpienia <xref:System.Xml.XmlDocument> klasy są tworzone przy użyciu jednej z jego trzy konstruktorów. Możesz utworzyć nowy, pusty <xref:System.Xml.XmlDocument> obiektu przez wywołanie metody <xref:System.Xml.XmlDocument> klasy konstruktora bez parametrów. Po wywołaniu metody konstruktora, użyj <xref:System.Xml.XmlDocument.Load%2A> metody do ładowania danych XML do nowej <xref:System.Xml.XmlDocument> obiekt z <xref:System.IO.Stream>, <xref:System.IO.TextReader>, lub <xref:System.Xml.XmlReader> obiektu, jak również `string` ścieżka do pliku XML.  
  
 Poniższy przykład przedstawia przy użyciu <xref:System.Xml.XmlDocument> klasy konstruktor bez parametrów i <xref:System.Xml.XmlDocument.Load%2A> metody do odczytu dokumentu XML.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>Określanie kodowania dokumentu XML  
 <xref:System.Xml.XmlReader> Obiekt może służyć do odczytu dokumentu XML i utworzyć <xref:System.Xml.XPath.XPathDocument> i <xref:System.Xml.XmlDocument> obiektów, jak pokazano w poprzednich sekcjach. Jednak <xref:System.Xml.XmlReader> obiektu może odczytać dane, które nie jest zaszyfrowana i w związku z tym nie zapewnia żadnych informacji kodowania.  
  
 <xref:System.Xml.XmlTextReader> Klasa dziedziczy <xref:System.Xml.XmlReader> klasy, oferuje kodowania informacji za pomocą jego <xref:System.Xml.XmlTextReader.Encoding%2A> właściwości i może służyć do tworzenia <xref:System.Xml.XPath.XPathDocument> obiektu lub <xref:System.Xml.XmlDocument> obiektu.  
  
 Aby uzyskać więcej informacji na temat kodowania informacji dostarczonych przez <xref:System.Xml.XmlTextReader> , zobacz <xref:System.Xml.XmlTextReader.Encoding%2A> właściwości w <xref:System.Xml.XmlTextReader> klasy dokumentacji.  
  
## <a name="creating-xpathnavigator-objects"></a>Tworzenie obiektów parametrem XPathNavigator  
 Po przeczytaniu dokument XML do albo <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu, można utworzyć <xref:System.Xml.XPath.XPathNavigator> obiektu, wybierz ocenę, przejdź i w niektórych przypadkach edytowanie danych XML.  
  
 Zarówno <xref:System.Xml.XPath.XPathDocument> i <xref:System.Xml.XmlDocument> klasy dodatkowo do <xref:System.Xml.XmlNode> klasy, implementować <xref:System.Xml.XPath.IXPathNavigable> interfejsu <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw. W związku z tym podać wszystkie trzy klasy <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> metodę zwracającą <xref:System.Xml.XPath.XPathNavigator> obiektu.  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>Edytowanie dokumentów XML za pomocą klasy parametrem XPathNavigator  
 Oprócz zaznaczenie, oceny i nawigowanie po danych XML <xref:System.Xml.XPath.XPathNavigator> klasa może być używana do edycji dokumentu XML w niektórych przypadkach oparte na obiekcie, który go utworzył.  
  
 <xref:System.Xml.XPath.XPathDocument> Klasy jest tylko do odczytu podczas <xref:System.Xml.XmlDocument> klasy jest edytowalny, a w rezultacie <xref:System.Xml.XPath.XPathNavigator> obiekty utworzone na podstawie <xref:System.Xml.XPath.XPathDocument> obiektu nie można edytować dokument XML, a te utworzone na podstawie <xref:System.Xml.XmlDocument> obiekt. <xref:System.Xml.XPath.XPathDocument> Klasy powinny być używane do dokumentu XML są tylko do odczytu. W przypadkach, w których należy edytować dokument XML lub wymagają dostępu do dodatkowe funkcje udostępniane przez <xref:System.Xml.XmlDocument> klasy, takie jak obsługa zdarzeń <xref:System.Xml.XmlDocument> klasa powinna być używana.  
  
 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> klasy określa, czy <xref:System.Xml.XPath.XPathNavigator> obiektu mogą edytować dane XML.  
  
 W poniższej tabeli opisano wartość <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwości dla każdej klasy.  
  
|<xref:System.Xml.XPath.IXPathNavigable> Implementacja|<xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Wartość|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [Edytowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [Weryfikacja schematu przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
