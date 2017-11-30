---
title: "Przetwarzanie danych XML w pamięci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ec4ccbff095071b279e07cee6a1aab3ca830423f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="processing-xml-data-in-memory"></a>Przetwarzanie danych XML w pamięci
Microsoft .NET Framework obejmuje trzy modele przetwarzania danych XML: <xref:System.Xml.XmlDocument> klasy <xref:System.Xml.XPath.XPathDocument> klasy, a [LINQ do XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).  
  
 <xref:System.Xml.XmlDocument> Klasa implementuje rdzeń poziom 1 W3C dokumentu obiektu modelu (DOM) oraz modelu DOM core poziomu 2 zalecenia. Model DOM jest w pamięci (pamięć podręczna) drzewa reprezentację dokumentu XML. Z <xref:System.Xml.XmlDocument> oraz ich powiązanymi klasami, możesz utworzyć dokumentów XML, obciążenia i uzyskać dostęp do danych, modyfikować dane i zapisać zmiany.  
  
 <xref:System.Xml.XPath.XPathDocument> Klasy jest magazynem danych tylko do odczytu, w pamięci, który jest oparty na modelu danych XPath. <xref:System.Xml.XPath.XPathNavigator> Klasa zapewnia kilka opcji edycji i możliwości nawigacji przy użyciu modelu kursor nad dokumentów XML zawarte w tylko do odczytu <xref:System.Xml.XPath.XPathDocument> klasy, jak również <xref:System.Xml.XmlDocument> klasy.  
  
 [LINQ do XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) jest nowy model w programie .NET Framework w wersji 3.5 przetwarzania danych XML. Jest modelu w pamięci, która wykorzystuje [LINQ (zapytania język Language-Integrated)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). LINQ rozszerza składnię języka C# i Visual Basic zapewnienie nowe możliwości zapytania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przetwarzania danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 Omówienie korzystania z <xref:System.Xml.XmlDocument>oraz ich powiązanymi klasami do przetworzenia danych XML.  
  
 [Przetwarzania danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 Omówienie korzystania z <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, i <xref:System.Xml.XPath.XPathNavigator> klasy do przetwarzania danych XML.  
  
 [Dane XML procesu za pomocą LINQ do XML](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 Zawiera krótki przegląd LINQ do XML i łącza do LINQ do dokumentacji XML.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dokumenty XML i dane](../../../../docs/standard/data/xml/index.md)
