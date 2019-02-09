---
title: Przetwarzanie danych XML w pamięci
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e6e89cafeb4cc580edb9630ba7415a669ea750c
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904410"
---
# <a name="processing-xml-data-in-memory"></a>Przetwarzanie danych XML w pamięci
Microsoft .NET Framework zawiera trzy modele związane z przetwarzaniem danych XML: <xref:System.Xml.XmlDocument> klasy <xref:System.Xml.XPath.XPathDocument> klasy, a [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).  
  
 <xref:System.Xml.XmlDocument> Klasa implementuje W3C dokumentu object model (DOM) poziom 1 core i core modelu DOM na poziomie 2 zalecenia. Model DOM jest w pamięci (pamięć podręczna) drzewa reprezentacja dokumentu XML. Za pomocą <xref:System.Xml.XmlDocument> i jej klasy pokrewne można konstruowania, dokumentów XML, obciążenia i uzyskiwać dostęp do danych i modyfikować dane i zapisać zmiany.  
  
 <xref:System.Xml.XPath.XPathDocument> Klasa jest magazyn danych tylko do odczytu, w pamięci, który jest oparty na modelu danych XPath. <xref:System.Xml.XPath.XPathNavigator> Klasa oferuje kilka opcji edycji i możliwości nawigacji przy użyciu modelu kursor nad dokumentami XML zawartych w trybie tylko do odczytu <xref:System.Xml.XPath.XPathDocument> klasy, jak również <xref:System.Xml.XmlDocument> klasy.  
  
 [LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) jest modelem wprowadzone w programie .NET Framework w wersji 3.5 do przetwarzania danych XML. Jest modelu w pamięci, który wykorzystuje [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md). LINQ rozszerza składni języka C# i Visual Basic, aby zapewnić nowe możliwości zapytania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 Omawia przy użyciu <xref:System.Xml.XmlDocument>oraz ich powiązanymi klasami do przetwarzania danych XML.  
  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 Omawia przy użyciu <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, i <xref:System.Xml.XPath.XPathNavigator> klasy do przetwarzania danych XML.  
  
 [Przetwarzanie danych XML przy użyciu modelu LINQ to XML](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 Krótki przegląd LINQ to XML i zawiera łącza do programu LINQ to XML dokumentacji.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dokumenty i dane XML](../../../../docs/standard/data/xml/index.md)
