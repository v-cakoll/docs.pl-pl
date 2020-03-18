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

.NET Framework zapewnia kompleksowy i zintegrowany zestaw klas, które umożliwiają tworzenie aplikacji obsługujących XML łatwo. Klasy w następujących przestrzeniach nazw obsługują analizowanie i zapisywanie języka XML, edytowanie danych XML w pamięci, sprawdzanie poprawności danych i transformację XSLT.

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

Aby uzyskać pełną listę, wyszukaj hasło "System.Xml" w [przeglądarce interfejsu API .NET](https://docs.microsoft.com/dotnet/api/?term=system.xml).

Klasy w tych przestrzeniach nazw obsługują zalecenia world wide web consortium (W3C). Przykład:

- Klasa <xref:System.Xml.XmlDocument?displayProperty=nameWithType> implementuje [W3C Document Object Model (DOM) Poziom 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) i [DOM Poziom 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) zalecenia.

- I <xref:System.Xml.XmlReader?displayProperty=nameWithType> <xref:System.Xml.XmlWriter?displayProperty=nameWithType> klasy obsługują [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) i [Przestrzenie nazw w zaleceniach XML.](https://www.w3.org/TR/REC-xml-names/)

- Schematy w <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> klasie obsługują [Schemat XML W3C Część 1: Struktury](https://www.w3.org/TR/xmlschema-1/) i Schemat [XML Część 2: Zalecenia typy danych.](https://www.w3.org/TR/xmlschema-2/)

- Klasy w <xref:System.Xml.Xsl?displayProperty=nameWithType> przestrzeni nazw obsługują przekształcenia XSLT zgodne z zaleceniem [W3C XSLT 1.0.](https://www.w3.org/TR/xslt)

Klasy XML w platformie .NET Framework zapewniają następujące korzyści:

- **Wydajność.** [LINQ do XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [LINQ do XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) ułatwia programowanie za pomocą języka XML i zapewnia środowisko zapytania, które jest podobne do SQL.

- **Rozszerzalności.** Klasy XML w platformie .NET Framework są rozszerzalne za pomocą abstrakcyjnych klas podstawowych i metod wirtualnych. Na przykład można utworzyć klasę pochodną <xref:System.Xml.XmlUrlResolver> klasy, która przechowuje strumień pamięci podręcznej na dysku lokalnym.

- **Podłączana architektura.** .NET Framework zapewnia architekturę, w której składniki mogą korzystać ze sobą, a dane mogą być przesyłane strumieniowo między składnikami. Na przykład magazyn danych, takich <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> jak lub obiektu, mogą <xref:System.Xml.Xsl.XslCompiledTransform> być przekształcane z klasą, a dane wyjściowe mogą być następnie przesyłane strumieniowo do innego magazynu lub zwracane jako strumień z usługi sieci web.

- **Wydajności.** Aby uzyskać lepszą wydajność aplikacji, niektóre klasy XML w platformie .NET Framework obsługują model oparty na przesyłaniu strumieniowym o następujących cechach:

  - Minimalne buforowanie do analizy modelu ściągania tylko<xref:System.Xml.XmlReader>do przodu ( ).

  - Sprawdzanie poprawności<xref:System.Xml.XmlReader>tylko do przodu ( ).

  - Nawigacja w stylu kursora, która minimalizuje tworzenie węzła do pojedynczego<xref:System.Xml.XPath.XPathNavigator>węzła wirtualnego, zapewniając jednocześnie losowy dostęp do dokumentu ( ).

  Aby uzyskać lepszą wydajność, gdy wymagane jest przetwarzanie <xref:System.Xml.XPath.XPathDocument> XSLT, można użyć klasy, która jest zoptymalizowanym magazynem tylko <xref:System.Xml.Xsl.XslCompiledTransform> do odczytu dla zapytań XPath zaprojektowanych do efektywnej pracy z klasą.

- **Integracja z ADO.NET.** Klasy XML i [ADO.NET](../../../../docs/framework/data/adonet/index.md) są ściśle zintegrowane w celu zebrania danych relacyjnych i XML. Klasa <xref:System.Data.DataSet> jest pamięci podręcznej w pamięci danych pobranych z bazy danych. Klasa <xref:System.Data.DataSet> ma możliwość odczytu i zapisu <xref:System.Xml.XmlReader> XML przy użyciu i <xref:System.Xml.XmlWriter> klas, aby utrwalić swoją wewnętrzną strukturę schematu relacyjnego jako schematy XML (XSD) i wywnioskować strukturę schematu dokumentu XML.

## <a name="in-this-section"></a>W tej sekcji

[Opcje przetwarzania XML](../../../../docs/standard/data/xml/xml-processing-options.md) W tym artykule omówiono opcje przetwarzania danych XML.

[Przetwarzanie danych XML w pamięci](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) W tym artykule omówiono trzy modele przetwarzania danych XML w pamięci: [LINQ do XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [LINQ do XML (Visual Basic),](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) <xref:System.Xml.XmlDocument> klasę (na podstawie modelu obiektu dokumentu W3C) i <xref:System.Xml.XPath.XPathDocument> klasę (na podstawie modelu danych XPath).

[Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)\
W tym artykule opisano sposób używania procesora XSLT.

[Model obiektu schematu XML (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)\
Opisuje klasy używane do tworzenia i manipulowania Schematami XML (XSD), udostępniając <xref:System.Xml.Schema.XmlSchema> klasę do ładowania i edytowania schematu.

[Integracja XML z danymi relacyjnymi i ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)\
Opisuje, jak .NET Framework umożliwia synchroniczny dostęp w czasie rzeczywistym zarówno relacyjne <xref:System.Data.DataSet> i <xref:System.Xml.XmlDataDocument> hierarchiczne reprezentacje danych za pośrednictwem obiektu i obiektu.

[Zarządzanie obszarami nazw w dokumencie XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)\
Opisuje sposób, w <xref:System.Xml.XmlNamespaceManager> jaki klasa jest używana do przechowywania i przechowywania informacji o obszarze nazw.

[Obsługa typów w klasach System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)\
Opisuje sposób mapowania typów danych XML na typy clr, sposób konwertowania <xref:System.Xml> typów danych XML i inne funkcje obsługi typów w klasach.

## <a name="related-sections"></a>Sekcje pokrewne

[ADO.NET](../../../../docs/framework/data/adonet/index.md)\
Zawiera informacje dotyczące uzyskiwania dostępu do danych przy użyciu ADO.NET.

[Zabezpieczeń](../../../../docs/standard/security/index.md)\
Zawiera omówienie systemu zabezpieczeń .NET Framework.
