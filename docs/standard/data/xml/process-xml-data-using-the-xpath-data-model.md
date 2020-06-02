---
title: Przetwarzanie danych XML przy użyciu modelu danych XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
ms.openlocfilehash: d449fe19640b19b1417c41b3a1ac7bd3a4de907a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291295"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a>Przetwarzanie danych XML przy użyciu modelu danych XPath
<xref:System.Xml?displayProperty=nameWithType>Przestrzeń nazw zapewnia programistyczną reprezentację dokumentów XML, fragmentów, węzłów lub zestawów węzłów w pamięci przy użyciu <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathDocument> klas lub.  
  
 <xref:System.Xml.XPath.XPathDocument>Klasa zapewnia szybką, tylko do odczytu, reprezentację w pamięci dokumentu XML przy użyciu modelu danych XPath. <xref:System.Xml.XmlDocument>Klasa udostępnia edytowalną reprezentację w pamięci dokumentu XML implementującą W3C Document Object Model (dom) Level 1 rdzeń i podstawowy poziom dom 2. Obie klasy implementują <xref:System.Xml.XPath.IXPathNavigable> interfejs i zwracają <xref:System.Xml.XPath.XPathNavigator> obiekt używany do zaznaczania, szacowania, nawigowania i w niektórych przypadkach, edytowania źródłowych danych XML.  
  
 W poniższych sekcjach opisano funkcjonalność <xref:System.Xml.XPath.XPathNavigator> klasy na podstawie klasy, która zwraca ją.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 Opisuje sposób tworzenia <xref:System.Xml.XPath.XPathDocument> obiektu klasy tylko do odczytu w celu odczytania dokumentu XML i sposobu tworzenia edytowalnego <xref:System.Xml.XmlDocument> obiektu klasy w celu odczytywania i EDYTOWANIA dokumentu XML. W tym temacie opisano również, jak zwrócić <xref:System.Xml.XPath.XPathNavigator> obiekt z każdej klasy w celu nawigowania i edytowania dokumentu XML.  
  
 [Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 Opisuje metody <xref:System.Xml.XPath.XPathNavigator> klasy używane do wybierania węzłów w <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> obiekcie lub przy użyciu kwerendy XPath, oceniają i sprawdzają wyniki wyrażenia XPath i określają, czy węzeł w dokumencie XML odpowiada danemu wyrażeniu XPath.  
  
 [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](accessing-xml-data-using-xpathnavigator.md)  
 Opisuje metody <xref:System.Xml.XPath.XPathNavigator> klasy używane do nawigowania po węzłach, wyodrębniania danych XML i uzyskiwania dostępu do jednoznacznie wpisanych danych XML w <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> obiekcie lub.  
  
 [Edytowanie danych XML przy użyciu klasy XPathNavigator](editing-xml-data-using-xpathnavigator.md)  
 Opisuje metody <xref:System.Xml.XPath.XPathNavigator> klasy używane do wstawiania, modyfikowania i usuwania węzłów oraz wartości z dokumentu XML zawartego w <xref:System.Xml.XmlDocument> obiekcie.  
  
 [Weryfikacja schematu przy użyciu klasy XPathNavigator](schema-validation-using-xpathnavigator.md)  
 Opisuje sposoby sprawdzania poprawności zawartości XML zawartej w <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> obiekcie lub.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu DOM](process-xml-data-using-the-dom-model.md)
