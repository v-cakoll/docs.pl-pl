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
<xref:System.Xml?displayProperty=nameWithType> Przestrzeń nazw zapewnia programistyczną reprezentację dokumentów XML, fragmentów, węzłów lub zestawów węzłów w pamięci przy użyciu klas <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument> .  
  
 <xref:System.Xml.XPath.XPathDocument> Klasa zapewnia szybką, tylko do odczytu, reprezentację w pamięci dokumentu XML przy użyciu modelu danych XPath. <xref:System.Xml.XmlDocument> Klasa udostępnia edytowalną reprezentację w pamięci dokumentu XML implementującą W3C Document Object Model (dom) Level 1 rdzeń i podstawowy poziom dom 2. Obie klasy implementują <xref:System.Xml.XPath.IXPathNavigable> interfejs i zwracają <xref:System.Xml.XPath.XPathNavigator> obiekt używany do zaznaczania, szacowania, nawigowania i w niektórych przypadkach, edytowania źródłowych danych XML.  
  
 W poniższych sekcjach opisano funkcjonalność <xref:System.Xml.XPath.XPathNavigator> klasy na podstawie klasy, która zwraca ją.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 Opisuje sposób tworzenia obiektu klasy tylko <xref:System.Xml.XPath.XPathDocument> do odczytu w celu odczytania dokumentu XML i sposobu tworzenia edytowalnego <xref:System.Xml.XmlDocument> obiektu klasy w celu odczytywania i edytowania dokumentu XML. W tym temacie opisano również, jak <xref:System.Xml.XPath.XPathNavigator> zwrócić obiekt z każdej klasy w celu nawigowania i EDYTOWANIA dokumentu XML.  
  
 [Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 Opisuje metody <xref:System.Xml.XPath.XPathNavigator> klasy używane do wybierania węzłów w obiekcie <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> przy użyciu kwerendy XPath, oceniają i sprawdzają wyniki wyrażenia XPath i określają, czy węzeł w dokumencie XML odpowiada danemu wyrażeniu XPath.  
  
 [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 Opisuje metody <xref:System.Xml.XPath.XPathNavigator> klasy używane do nawigowania po węzłach, wyodrębniania danych XML i uzyskiwania dostępu do jednoznacznie WPISANYCH danych <xref:System.Xml.XPath.XPathDocument> XML <xref:System.Xml.XmlDocument> w obiekcie lub.  
  
 [Edytowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 Opisuje metody <xref:System.Xml.XPath.XPathNavigator> klasy używane do wstawiania, modyfikowania i usuwania węzłów oraz wartości z dokumentu XML zawartego w <xref:System.Xml.XmlDocument> obiekcie.  
  
 [Weryfikacja schematu przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Opisuje sposoby sprawdzania poprawności zawartości XML zawartej w obiekcie <xref:System.Xml.XPath.XPathDocument> lub. <xref:System.Xml.XmlDocument>  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
