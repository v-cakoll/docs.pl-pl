---
title: Przetwarzanie danych XML przy użyciu modelu danych XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da8b623d3a73ca8791a0619c67b0ed3bd42447d3
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216256"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a>Przetwarzanie danych XML przy użyciu modelu danych XPath
<xref:System.Xml?displayProperty=nameWithType> Przestrzeń nazw zawiera reprezentację programistyczne dokumenty XML, fragmenty, węzłów lub zestaw węzłów w pamięci, za pomocą <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument> klasy.  
  
 <xref:System.Xml.XPath.XPathDocument> Klasa udostępnia reprezentację dokumentu XML przy użyciu modelu danych XPath, szybka i tylko do odczytu w pamięci. <xref:System.Xml.XmlDocument> Klasa udostępnia można edytować w pamięci reprezentację w postaci dokumentu XML, implementowanie W3C Document Object Model (DOM) poziom 1 Core i Core DOM poziomu 2. Zarówno klasy implementować <xref:System.Xml.XPath.IXPathNavigable> interfejsu i zwracają <xref:System.Xml.XPath.XPathNavigator> obiekt używany do Wybierz ocenę, przejdź i w niektórych przypadkach, Edytuj podstawowych danych XML.  
  
 W poniższych sekcjach opisano funkcje <xref:System.Xml.XPath.XPathNavigator> klasy oparte na klasę, która zwraca go.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 W tym artykule opisano sposób tworzenia tylko do odczytu <xref:System.Xml.XPath.XPathDocument> obiektu klasy do odczytu dokumentu XML oraz sposób tworzenia edytowalne <xref:System.Xml.XmlDocument> obiektu klasy na odczytywanie i edytowanie dokumentu XML. W tym temacie opisano sposób zwracany <xref:System.Xml.XPath.XPathNavigator> obiekt z każdej klasy do nawigowania po edycji dokumentu XML.  
  
 [Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 W tym artykule opisano metody <xref:System.Xml.XPath.XPathNavigator> klasę używaną do wybierania węzłów w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> przy użyciu zapytania XPath, oceny i sprawdź wyniki wyrażenia XPath i ustalić, czy węzeł w dokumencie XML odpowiada danym XPath wyrażenie.  
  
 [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 W tym artykule opisano metody <xref:System.Xml.XPath.XPathNavigator> klasy, które umożliwiają przejście węzłów, wyodrębnianie danych XML i dostęp do silnie typizowanych danych XML w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu.  
  
 [Edytowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 W tym artykule opisano metody <xref:System.Xml.XPath.XPathNavigator> klasa służy do wstawiania, modyfikowanie i usuwanie węzłów oraz wartości z dokumentu XML zawartych w <xref:System.Xml.XmlDocument> obiektu.  
  
 [Weryfikacja schematu przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 W tym artykule opisano sposób, aby walidować zawartość XML zawartych w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
