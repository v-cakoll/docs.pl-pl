---
title: Dokumenty i dane XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
ms.openlocfilehash: e0c3f3e99b06b65caf79d87a7831369f6fb33b08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75710794"
---
# <a name="xml-documents-and-data"></a>Dokumenty i dane XML

.NET Framework zapewnia kompleksowy i zintegrowany zestaw klas, które umożliwiają łatwe tworzenie aplikacji obsługujących kod XML. Klasy w następujących przestrzeniach nazw obsługują analizowanie i zapisywanie XML, edytowanie danych XML w pamięci, sprawdzanie poprawności danych i transformację XSLT.

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

Aby uzyskać pełną listę, wyszukaj ciąg "System. xml" w [przeglądarce interfejsów API platformy .NET](https://docs.microsoft.com/dotnet/api/?term=system.xml).

Klasy w tych obszarach nazw obsługują zalecenia dotyczące organizacja World Wide Web Consortium (W3C). Przykład:

- <xref:System.Xml.XmlDocument?displayProperty=nameWithType> Klasa implementuje podstawowe zalecenia [poziomu 1 dla W3C Document Object Model (dom)](https://www.w3.org/TR/REC-DOM-Level-1/) i [poziom dom 2](https://www.w3.org/TR/DOM-Level-2-Core/) .

- Klasy <xref:System.Xml.XmlReader?displayProperty=nameWithType> i <xref:System.Xml.XmlWriter?displayProperty=nameWithType> obsługują [W3C XML 1,0](https://www.w3.org/TR/2006/REC-xml-20060816/) i [przestrzenie nazw w](https://www.w3.org/TR/REC-xml-names/) zaleceniach XML.

- Schematy w <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> klasie obsługują [plik W3C XML schematu część 1: struktury](https://www.w3.org/TR/xmlschema-1/) i [XML schematu część 2:](https://www.w3.org/TR/xmlschema-2/) zalecenia dotyczące typów danych.

- Klasy w <xref:System.Xml.Xsl?displayProperty=nameWithType> przestrzeni nazw obsługują przekształcenia XSLT zgodne z zaleceniem [W3C XSLT 1,0](https://www.w3.org/TR/xslt) .

Klasy XML w .NET Framework zapewniają następujące korzyści:

- **Zwiększając.** [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) ułatwiają programowanie w języku XML i udostępniają środowisko zapytań podobne do języka SQL.

- **Rozszerzaln.** Klasy XML w .NET Framework są rozszerzalne przy użyciu abstrakcyjnych klas podstawowych i metod wirtualnych. Na przykład można utworzyć klasę pochodną <xref:System.Xml.XmlUrlResolver> klasy, która przechowuje strumień pamięci podręcznej na dysku lokalnym.

- **Architektura podłączana.** .NET Framework zapewnia architekturę, w której składniki mogą korzystać ze sobą, a dane mogą być przesyłane strumieniowo między składnikami. Na przykład magazyn danych, taki jak obiekt <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> , może być przekształcony z <xref:System.Xml.Xsl.XslCompiledTransform> klasą, a dane wyjściowe można przesłać strumieniowo do innego magazynu lub zwrócić jako strumień z usługi sieci Web.

- **Skuteczności.** W celu uzyskania lepszej wydajności aplikacji niektóre klasy XML w .NET Framework obsługują model oparty na strumieniu o następujących cechach:

  - Minimalna pamięć podręczna do analizy modelu ściągania (<xref:System.Xml.XmlReader>).

  - Walidacja tylko do przodu<xref:System.Xml.XmlReader>().

  - Nawigacja w stylu kursora, która minimalizuje Tworzenie węzłów w jednym węźle wirtualnym, a jednocześnie zapewnia losowy<xref:System.Xml.XPath.XPathNavigator>dostęp do dokumentu ().

  Aby zapewnić lepszą wydajność, gdy jest wymagane przetwarzanie XSLT, można użyć <xref:System.Xml.XPath.XPathDocument> klasy, która jest zoptymalizowanym magazynem tylko do odczytu dla zapytań XPath zaprojektowanych do wydajnej pracy <xref:System.Xml.Xsl.XslCompiledTransform> z klasą.

- **Integracja z usługą ADO.NET.** Klasy XML i [ADO.NET](../../../../docs/framework/data/adonet/index.md) są ściśle zintegrowane do łączenia danych relacyjnych i XML. <xref:System.Data.DataSet> Klasa to pamięć podręczna danych pobieranych z bazy danych. <xref:System.Data.DataSet> Klasa ma możliwość odczytywania i pisania XML przy użyciu klas <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> , aby zachować wewnętrzną strukturę schematu relacyjnego jako schematy XML (XSD) i wywnioskować strukturę schematu dokumentu XML.

## <a name="in-this-section"></a>W tej sekcji

[Opcje przetwarzania XML](../../../../docs/standard/data/xml/xml-processing-options.md) W tym artykule omówiono opcje przetwarzania danych XML.

[Przetwarzanie danych XML w pamięci](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) Omawia trzy modele przetwarzania danych XML w pamięci: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), <xref:System.Xml.XmlDocument> klasy (na podstawie Document Object Model W3C) i <xref:System.Xml.XPath.XPathDocument> klasy (na podstawie modelu danych XPath).

[Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)\
Opisuje sposób korzystania z procesora XSLT.

[Model obiektów schematu XML (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)\
Opisuje klasy używane do kompilowania schematów XML (XSD) i manipulowania nimi przez udostępnienie <xref:System.Xml.Schema.XmlSchema> klasy w celu załadowania i edytowania schematu.

[Integracja XML z danymi relacyjnymi i ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)\
Opisuje, w jaki sposób .NET Framework umożliwia dostęp synchroniczny do relacyjnych i hierarchicznych reprezentacji danych za pomocą <xref:System.Data.DataSet> obiektu i <xref:System.Xml.XmlDataDocument> obiektu.

[Zarządzanie przestrzeniami nazw w dokumencie XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)\
Opisuje, <xref:System.Xml.XmlNamespaceManager> w jaki sposób Klasa jest używana do przechowywania i konserwowania informacji o przestrzeni nazw.

[Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)\
Opisuje sposób mapowania typów danych XML na typy CLR, sposób konwersji typów danych XML i inne funkcje obsługi typu w <xref:System.Xml> klasach.

## <a name="related-sections"></a>Sekcje pokrewne

[ADO.NET](../../../../docs/framework/data/adonet/index.md)\
Zawiera informacje na temat sposobu uzyskiwania dostępu do danych za pomocą ADO.NET.

[Bezpieczeństw](../../../../docs/standard/security/index.md)\
Zawiera omówienie systemu zabezpieczeń .NET Framework.
