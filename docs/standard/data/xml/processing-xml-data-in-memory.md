---
title: Przetwarzanie danych XML w pamięci
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 317021318153cc87b2eab3db508a9dede9dc05e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569645"
---
# <a name="processing-xml-data-in-memory"></a>Przetwarzanie danych XML w pamięci
Microsoft .NET Framework obejmuje trzy modele przetwarzania danych XML: <xref:System.Xml.XmlDocument> klasy <xref:System.Xml.XPath.XPathDocument> klasy, a [LINQ do XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).  
  
 <xref:System.Xml.XmlDocument> Klasa implementuje rdzeń poziom 1 W3C dokumentu obiektu modelu (DOM) oraz modelu DOM core poziomu 2 zalecenia. Model DOM jest w pamięci (pamięć podręczna) drzewa reprezentację dokumentu XML. Z <xref:System.Xml.XmlDocument> oraz ich powiązanymi klasami, możesz utworzyć dokumentów XML, obciążenia i uzyskać dostęp do danych, modyfikować dane i zapisać zmiany.  
  
 <xref:System.Xml.XPath.XPathDocument> Klasy jest magazynem danych tylko do odczytu, w pamięci, który jest oparty na modelu danych XPath. <xref:System.Xml.XPath.XPathNavigator> Klasa zapewnia kilka opcji edycji i możliwości nawigacji przy użyciu modelu kursor nad dokumentów XML zawarte w tylko do odczytu <xref:System.Xml.XPath.XPathDocument> klasy, jak również <xref:System.Xml.XmlDocument> klasy.  
  
 [LINQ do XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) jest nowy model w programie .NET Framework w wersji 3.5 przetwarzania danych XML. Jest modelu w pamięci, która wykorzystuje [LINQ (zapytania język Language-Integrated)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). LINQ rozszerza składnię języka C# i Visual Basic zapewnienie nowe możliwości zapytania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 Omówienie korzystania z <xref:System.Xml.XmlDocument>oraz ich powiązanymi klasami do przetworzenia danych XML.  
  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 Omówienie korzystania z <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, i <xref:System.Xml.XPath.XPathNavigator> klasy do przetwarzania danych XML.  
  
 [Przetwarzanie danych XML przy użyciu modelu LINQ to XML](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 Zawiera krótki przegląd LINQ do XML i łącza do LINQ do dokumentacji XML.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dokumenty i dane XML](../../../../docs/standard/data/xml/index.md)
