---
title: "Przetwarzania danych XML przy użyciu modelu danych XPath"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9992efa209773a6e9f74050183260346f7f1f0ed
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="process-xml-data-using-the-xpath-data-model"></a>Przetwarzania danych XML przy użyciu modelu danych XPath
<xref:System.Xml?displayProperty=nameWithType> Przestrzeń nazw zapewnia programowy reprezentację dokumenty XML, fragmenty, węzły lub zestaw węzłów w pamięci, za pomocą <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument> klasy.  
  
 <xref:System.Xml.XPath.XPathDocument> Klasa udostępnia reprezentację dokumentu XML za pomocą wyrażenia XPath modelu danych, szybka i tylko do odczytu w pamięci. <xref:System.Xml.XmlDocument> Klasa udostępnia można edytować w pamięci reprezentację w postaci dokumentu XML wykonania W3C modelu DOM (Document Object) poziom 1 Core i Core DOM poziomu 2. Zarówno klasy implementować <xref:System.Xml.XPath.IXPathNavigable> interfejsu i zwracać <xref:System.Xml.XPath.XPathNavigator> obiekt używany do wybierz oceny, przejdź, a w niektórych przypadkach edytowanie danych XML.  
  
 W poniższych sekcjach opisano funkcje <xref:System.Xml.XPath.XPathNavigator> klasy oparte na klasie zwraca go.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 Opisuje sposób tworzenia tylko do odczytu <xref:System.Xml.XPath.XPathDocument> obiektu klasy do odczytu dokumentu XML oraz sposobu tworzenia, edycji <xref:System.Xml.XmlDocument> obiektu klasy do odczytu i edycji dokumentu XML. W tym temacie opisano sposób zwracany <xref:System.Xml.XPath.XPathNavigator> obiektu z każdej klasy do nawigowania i edytować dokument XML.  
  
 [Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 Opisuje metody <xref:System.Xml.XPath.XPathNavigator> klasa używana do wybierania węzłów w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> przy użyciu zapytania XPath, oceny i przejrzeć wyniki wyrażenia XPath i ustalić, czy węzeł w dokumencie XML zgodne danego języka XPath wyrażenie.  
  
 [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 Opisuje metody <xref:System.Xml.XPath.XPathNavigator> klasa używana do nawigowania węzłów, wyodrębnić dane XML i dostępu jednoznacznie danych XML w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu.  
  
 [Edytowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 Opisuje metody <xref:System.Xml.XPath.XPathNavigator> klasa służy do wstawiania, modyfikowania i usuwania węzłów i wartości z dokumentu XML zawartych w <xref:System.Xml.XmlDocument> obiektu.  
  
 [Weryfikacja schematu przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Zawiera opis sposobów sprawdzania poprawności zawartości XML zawartych w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
