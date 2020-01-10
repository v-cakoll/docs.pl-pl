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
Istnieją dwa sposoby odczytywania dokumentu XML w przestrzeni nazw <xref:System.Xml.XPath?displayProperty=nameWithType>. Jeden polega na odczytaniu dokumentu XML przy użyciu klasy <xref:System.Xml.XPath.XPathDocument> tylko do odczytu, a drugi to odczytanie dokumentu XML przy użyciu edytowalnej klasy <xref:System.Xml.XmlDocument> w przestrzeni nazw <xref:System.Xml?displayProperty=nameWithType>.  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>Odczytywanie dokumentów XML przy użyciu klasy XPathDocument  
 Klasa <xref:System.Xml.XPath.XPathDocument> zapewnia szybką, tylko do odczytu, reprezentację w pamięci dokumentu XML przy użyciu modelu danych XPath. Wystąpienia klasy <xref:System.Xml.XPath.XPathDocument> są tworzone przy użyciu jednego z sześciu konstruktorów. Te konstruktory umożliwiają odczytywanie dokumentu XML przy użyciu obiektu <xref:System.IO.Stream>, <xref:System.IO.TextReader>lub <xref:System.Xml.XmlReader>, a także ścieżkę `string` do pliku XML.  
  
 Poniższy przykład ilustruje użycie konstruktora `string` klasy <xref:System.Xml.XPath.XPathDocument>, aby odczytać dokument XML.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>Odczytywanie dokumentów XML przy użyciu klasy XmlDocument  
 Klasa <xref:System.Xml.XmlDocument> jest edytowalną reprezentacją w pamięci dokumentu XML implementującą W3C Document Object Model (DOM) Level 1 rdzeń i podstawowy poziom DOM 2. Wystąpienia klasy <xref:System.Xml.XmlDocument> są tworzone przy użyciu jednego z trzech konstruktorów. Można utworzyć nowy, pusty obiekt <xref:System.Xml.XmlDocument>, wywołując Konstruktor klasy <xref:System.Xml.XmlDocument> bez parametrów. Po wywołaniu konstruktora Użyj metody <xref:System.Xml.XmlDocument.Load%2A> do załadowania danych XML do nowego obiektu <xref:System.Xml.XmlDocument> z obiektu <xref:System.IO.Stream>, <xref:System.IO.TextReader>lub <xref:System.Xml.XmlReader>, a także ścieżki `string` do pliku XML.  
  
 Poniższy przykład ilustruje użycie konstruktora klasy <xref:System.Xml.XmlDocument> bez parametrów i metody <xref:System.Xml.XmlDocument.Load%2A>, aby odczytać dokument XML.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>Określanie kodowania dokumentu XML  
 Obiekt <xref:System.Xml.XmlReader> może służyć do odczytywania dokumentu XML oraz do tworzenia obiektów <xref:System.Xml.XPath.XPathDocument> i <xref:System.Xml.XmlDocument>, jak pokazano w poprzednich sekcjach. Jednak obiekt <xref:System.Xml.XmlReader> może odczytywać dane, które nie są zakodowane i w związku z tym nie udostępniają żadnych informacji o kodowaniu.  
  
 Klasa <xref:System.Xml.XmlTextReader> dziedziczy z klasy <xref:System.Xml.XmlReader>, zapewnia informacje o kodowaniu przy użyciu właściwości <xref:System.Xml.XmlTextReader.Encoding%2A> i może służyć do tworzenia obiektu <xref:System.Xml.XPath.XPathDocument> lub obiektu <xref:System.Xml.XmlDocument>.  
  
 Aby uzyskać więcej informacji na temat informacji o kodowaniu dostarczonych przez klasę <xref:System.Xml.XmlTextReader>, zobacz Właściwość <xref:System.Xml.XmlTextReader.Encoding%2A> w dokumentacji dotyczącej klasy <xref:System.Xml.XmlTextReader>.  
  
## <a name="creating-xpathnavigator-objects"></a>Tworzenie obiektów XPathNavigator  
 Po przeczytaniu dokumentu XML do obiektu <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument>, można utworzyć obiekt <xref:System.Xml.XPath.XPathNavigator> do wyboru, szacowania, nawigowania i w niektórych przypadkach edytować bazowe dane XML.  
  
 Klasy <xref:System.Xml.XPath.XPathDocument> i <xref:System.Xml.XmlDocument>, oprócz klasy <xref:System.Xml.XmlNode>, implementują interfejs <xref:System.Xml.XPath.IXPathNavigable> przestrzeni nazw <xref:System.Xml.XPath?displayProperty=nameWithType>. W związku z tym wszystkie trzy klasy zapewniają metodę <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A>, która zwraca obiekt <xref:System.Xml.XPath.XPathNavigator>.  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>Edytowanie dokumentów XML przy użyciu klasy XPathNavigator  
 Oprócz wyboru, oceny i nawigowania po danych XML, Klasa <xref:System.Xml.XPath.XPathNavigator> może służyć do edycji dokumentu XML w niektórych przypadkach na podstawie obiektu, który go utworzył.  
  
 Klasa <xref:System.Xml.XPath.XPathDocument> jest tylko do odczytu, podczas gdy Klasa <xref:System.Xml.XmlDocument> jest edytowalna, a w związku z tym obiekty <xref:System.Xml.XPath.XPathNavigator> utworzone na podstawie obiektu <xref:System.Xml.XPath.XPathDocument> nie mogą być używane do edytowania dokumentu XML, podczas gdy te utworzone na podstawie obiektu <xref:System.Xml.XmlDocument> mogą. Aby można było odczytać tylko dokument XML, należy użyć klasy <xref:System.Xml.XPath.XPathDocument>. W przypadkach, gdy konieczne jest edytowanie dokumentu XML lub wymaganie dostępu do dodatkowych funkcji udostępnianych przez klasę <xref:System.Xml.XmlDocument>, takich jak obsługa zdarzeń, należy użyć klasy <xref:System.Xml.XmlDocument>.  
  
 Właściwość <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> klasy <xref:System.Xml.XPath.XPathNavigator> określa, czy obiekt <xref:System.Xml.XPath.XPathNavigator> może edytować dane XML.  
  
 W poniższej tabeli opisano wartość właściwości <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> dla każdej klasy.  
  
|Implementacja <xref:System.Xml.XPath.IXPathNavigable>|Wartość <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A>|  
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
