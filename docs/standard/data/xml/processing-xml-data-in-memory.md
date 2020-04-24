---
title: Przetwarzanie danych XML w pamięci
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 038bcfcb9d40ee6087efa3487b6f27f252393f2c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710430"
---
# <a name="processing-xml-data-in-memory"></a>Przetwarzanie danych XML w pamięci
Microsoft .NET Framework <xref:System.Xml.XmlDocument> zawiera trzy modele do przetwarzania danych XML: Klasa, <xref:System.Xml.XPath.XPathDocument> Klasa i [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 <xref:System.Xml.XmlDocument> Klasa implementuje podstawowe elementy poziomu modelu DOM (Document Object Model) 1 i podstawowe zalecenia poziomu 2 modelu DOM. DOM jest reprezentacją drzewa w pamięci (pamięć podręczna) dokumentu XML. Za pomocą <xref:System.Xml.XmlDocument> i pokrewnych klas można tworzyć dokumenty XML, ładować i uzyskiwać dostęp do danych, modyfikować dane i zapisywać zmiany.  
  
 <xref:System.Xml.XPath.XPathDocument> Klasa jest magazynem danych tylko do odczytu, który jest oparty na modelu danych XPath. <xref:System.Xml.XPath.XPathNavigator> Klasa oferuje kilka opcji edycji i możliwości nawigacji przy użyciu modelu kursorów na dokumentach XML zawartych w klasie tylko <xref:System.Xml.XPath.XPathDocument> do odczytu, a także <xref:System.Xml.XmlDocument> klasy.  
  
 [LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) jest modelem wprowadzonym w .NET Framework wersji 3,5 na potrzeby przetwarzania danych XML. Jest to model znajdujący się w pamięci, który korzysta z [zapytań zintegrowanych z językiem (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md). LINQ rozszerza składnię języka C# i Visual Basic, aby zapewnić nowe możliwości zapytań.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 W tym artykule <xref:System.Xml.XmlDocument>omówiono użycie i powiązane z nim klasy do przetwarzania danych XML.  
  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 W tym artykule <xref:System.Xml.XPath.XPathDocument>omówiono <xref:System.Xml.XmlDocument>korzystanie z <xref:System.Xml.XPath.XPathNavigator> klas, i do przetwarzania danych XML.  
  
 [Przetwarzanie danych XML przy użyciu modelu LINQ to XML](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 Zawiera krótkie omówienie LINQ to XML i zawiera linki do dokumentacji LINQ to XMLowej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dokumenty i dane XML](../../../../docs/standard/data/xml/index.md)
