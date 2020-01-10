---
title: Przetwarzanie danych XML przy użyciu modelu danych XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
ms.openlocfilehash: f964864577cf08eb074bdfb9af7f7daf3ffb37b9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710443"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a>Przetwarzanie danych XML przy użyciu modelu danych XPath
Przestrzeń nazw <xref:System.Xml?displayProperty=nameWithType> umożliwia programową reprezentację dokumentów XML, fragmentów, węzłów lub zestawów węzłów w pamięci przy użyciu klas <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument>.  
  
 Klasa <xref:System.Xml.XPath.XPathDocument> zapewnia szybką, tylko do odczytu, reprezentację w pamięci dokumentu XML przy użyciu modelu danych XPath. Klasa <xref:System.Xml.XmlDocument> udostępnia edytowalną reprezentację w pamięci dokumentu XML implementującą W3C Document Object Model (DOM) Level 1 rdzeń i podstawowy poziom DOM 2. Obie klasy implementują interfejs <xref:System.Xml.XPath.IXPathNavigable> i zwracają obiekt <xref:System.Xml.XPath.XPathNavigator> używany do zaznaczania, obliczania, nawigowania i w niektórych przypadkach, edytowania źródłowych danych XML.  
  
 W poniższych sekcjach opisano funkcjonalność klasy <xref:System.Xml.XPath.XPathNavigator> opartej na klasie, która ją zwraca.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 Opisuje sposób tworzenia obiektu klasy <xref:System.Xml.XPath.XPathDocument> tylko do odczytu w celu odczytania dokumentu XML i utworzenia edytowalnego obiektu klasy <xref:System.Xml.XmlDocument> w celu odczytania i edytowania dokumentu XML. W tym temacie opisano również sposób zwrócenia obiektu <xref:System.Xml.XPath.XPathNavigator> z każdej klasy w celu nawigowania i edytowania dokumentu XML.  
  
 [Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 Opisuje metody klasy <xref:System.Xml.XPath.XPathNavigator> używane do wybierania węzłów w obiekcie <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> przy użyciu zapytania XPath, oceniają i sprawdzają wyniki wyrażenia XPath i określają, czy węzeł w dokumencie XML odpowiada danemu wyrażeniu XPath.  
  
 [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 Opisuje metody klasy <xref:System.Xml.XPath.XPathNavigator> używane do nawigowania po węzłach, wyodrębniania danych XML i uzyskiwania dostępu do jednoznacznie wpisanych danych XML w obiekcie <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument>.  
  
 [Edytowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 Opisuje metody klasy <xref:System.Xml.XPath.XPathNavigator> używane do wstawiania, modyfikowania i usuwania węzłów oraz wartości z dokumentu XML zawartego w obiekcie <xref:System.Xml.XmlDocument>.  
  
 [Weryfikacja schematu przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Opisuje sposoby sprawdzania poprawności zawartości XML zawartej w obiekcie <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
