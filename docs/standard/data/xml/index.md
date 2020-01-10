---
title: Dokumenty i dane XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
ms.openlocfilehash: e0c3f3e99b06b65caf79d87a7831369f6fb33b08
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
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

Klasy w tych obszarach nazw obsługują zalecenia dotyczące organizacja World Wide Web Consortium (W3C). Na przykład:

- Klasa <xref:System.Xml.XmlDocument?displayProperty=nameWithType> implementuje [podstawowe zalecenia poziomu](https://www.w3.org/TR/DOM-Level-2-Core/) [1 dla W3C Document Object Model (dom)](https://www.w3.org/TR/REC-DOM-Level-1/) .

- Klasy <xref:System.Xml.XmlReader?displayProperty=nameWithType> i <xref:System.Xml.XmlWriter?displayProperty=nameWithType> obsługują [W3C xml 1,0](https://www.w3.org/TR/2006/REC-xml-20060816/) i [przestrzenie nazw w](https://www.w3.org/TR/REC-xml-names/) zaleceniach XML.

- Schematy w klasie <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> obsługują [W3C XML schematu część 1: struktury](https://www.w3.org/TR/xmlschema-1/) i [XML schematu część 2:](https://www.w3.org/TR/xmlschema-2/) zalecenia dotyczące typów danych.

- Klasy w przestrzeni nazw <xref:System.Xml.Xsl?displayProperty=nameWithType> obsługują przekształcenia XSLT zgodne z zaleceniem [W3C xslt 1,0](https://www.w3.org/TR/xslt) .

Klasy XML w .NET Framework zapewniają następujące korzyści:

- **Zwiększając.** [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) ułatwiają programowanie w języku XML i udostępniają środowisko zapytań podobne do języka SQL.

- **Rozszerzaln.** Klasy XML w .NET Framework są rozszerzalne przy użyciu abstrakcyjnych klas podstawowych i metod wirtualnych. Na przykład można utworzyć klasę pochodną klasy <xref:System.Xml.XmlUrlResolver>, która przechowuje strumień pamięci podręcznej na dysku lokalnym.

- **Architektura podłączana.** .NET Framework zapewnia architekturę, w której składniki mogą korzystać ze sobą, a dane mogą być przesyłane strumieniowo między składnikami. Na przykład magazyn danych, taki jak <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument>, może być przekształcony z klasą <xref:System.Xml.Xsl.XslCompiledTransform>, a dane wyjściowe można następnie przesłać do innego magazynu lub zwrócić jako strumień z usługi sieci Web.

- **Wydajność.** W celu uzyskania lepszej wydajności aplikacji niektóre klasy XML w .NET Framework obsługują model oparty na strumieniu o następujących cechach:

  - Minimalne buforowanie na potrzeby analizy modelu ściągania (<xref:System.Xml.XmlReader>) tylko do przodu.

  - Weryfikacja tylko do przodu (<xref:System.Xml.XmlReader>).

  - Nawigacja w stylu kursora, która minimalizuje Tworzenie węzłów w jednym węźle wirtualnym, a jednocześnie zapewnia losowy dostęp do dokumentu (<xref:System.Xml.XPath.XPathNavigator>).

  Aby zapewnić lepszą wydajność, gdy jest wymagane przetwarzanie XSLT, można użyć klasy <xref:System.Xml.XPath.XPathDocument>, która jest zoptymalizowanym magazynem tylko do odczytu dla zapytań XPath zaprojektowanych do wydajnej pracy z klasą <xref:System.Xml.Xsl.XslCompiledTransform>.

- **Integracja z usługą ADO.NET.** Klasy XML i [ADO.NET](../../../../docs/framework/data/adonet/index.md) są ściśle zintegrowane do łączenia danych relacyjnych i XML. Klasa <xref:System.Data.DataSet> to pamięć podręczna danych pobieranych z bazy danych. Klasa <xref:System.Data.DataSet> może odczytywać i zapisywać dane XML przy użyciu klas <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>, aby zachować wewnętrzną strukturę schematu relacyjnego jako schematy XML (XSD) i wywnioskować strukturę schematu dokumentu XML.

## <a name="in-this-section"></a>W tej sekcji

[Opcje przetwarzania XML](../../../../docs/standard/data/xml/xml-processing-options.md) W tym artykule omówiono opcje przetwarzania danych XML.

[Przetwarzanie danych XML w pamięci](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) Omawia trzy modele służące do przetwarzania danych XML w pamięci: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), Klasa <xref:System.Xml.XmlDocument> (oparta na Document Object Model W3C) i Klasa <xref:System.Xml.XPath.XPathDocument> (na podstawie modelu danych XPath).

[Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)\
Opisuje sposób korzystania z procesora XSLT.

[Model obiektów schematu XML (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)\
Opisuje klasy używane do kompilowania schematów XML (XSD) i manipulowania nimi przez udostępnienie klasy <xref:System.Xml.Schema.XmlSchema> w celu załadowania i edytowania schematu.

[Integracja XML z danymi relacyjnymi i ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)\
Opisuje, w jaki sposób .NET Framework umożliwia dostęp synchroniczny do relacyjnych i hierarchicznych reprezentacji danych za pomocą obiektu <xref:System.Data.DataSet> i obiektu <xref:System.Xml.XmlDataDocument>.

[Zarządzanie przestrzeniami nazw w dokumencie XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)\
Opisuje, w jaki sposób Klasa <xref:System.Xml.XmlNamespaceManager> jest używana do przechowywania i konserwowania informacji o przestrzeni nazw.

[Obsługa typów w klasach system. Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)\
Opisuje, jak typy danych XML są mapowane na typy CLR, jak konwertować typy danych XML i inne funkcje obsługi typu w klasach <xref:System.Xml>.

## <a name="related-sections"></a>Sekcje pokrewne

[ADO.NET](../../../../docs/framework/data/adonet/index.md)\
Zawiera informacje na temat sposobu uzyskiwania dostępu do danych za pomocą ADO.NET.

[Zabezpieczenia](../../../../docs/standard/security/index.md)\
Zawiera omówienie systemu zabezpieczeń .NET Framework.
