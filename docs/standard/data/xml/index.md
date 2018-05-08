---
title: Dokumenty i dane XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f286d0f64478bfc46ca207086e4a6b918ee47b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xml-documents-and-data"></a>Dokumenty i dane XML
.NET Framework zapewnia kompleksowy, zintegrowany zestaw klas, które umożliwiają łatwe tworzenie aplikacji obsługującym kod XML. Klasy w następujących przestrzeni nazw obsługuje analizowania i zapisywanie edytowania plików XML, dane XML w pamięci, sprawdzanie poprawności danych i przekształcenie XSLT.  
  
-   <xref:System.Xml>  
  
-   <xref:System.Xml.XPath>  
  
-   <xref:System.Xml.Xsl>  
  
-   <xref:System.Xml.Schema>  
  
-   <xref:System.Xml.Linq>  
  
 Aby uzyskać pełną listę, zobacz [przestrzenie nazw System.Xml](https://msdn.microsoft.com/library/gg145036.aspx) strony sieci Web.  
  
 Klasy w tych obszarach nazw obsługuje zalecenia konsorcjum World Wide Web (W3C). Na przykład:  
  
-   <xref:System.Xml.XmlDocument?displayProperty=nameWithType> Klasa implementuje [W3C modelu DOM (Document Object) poziom 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) i [DOM poziom 2 rdzenie](https://www.w3.org/TR/DOM-Level-2-Core/) zalecenia.  
  
-   <xref:System.Xml.XmlReader?displayProperty=nameWithType> i <xref:System.Xml.XmlWriter?displayProperty=nameWithType> klas pomocy technicznej [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) i [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/) zalecenia.  
  
-   Schematów w <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> klas pomocy technicznej [W3C XML schematu część 1: struktury](https://www.w3.org/TR/xmlschema-1/) i [XML schematu część 2: typy danych](https://www.w3.org/TR/xmlschema-2/) zalecenia.  
  
-   Klasy w <xref:System.Xml.Xsl?displayProperty=nameWithType> przekształcenia XSLT pomocy technicznej przestrzeni nazw, które są zgodne z [W3C XSLT 1.0](http://www.w3.org/TR/xslt) zalecenia.  
  
 Klasy XML w programie .NET Framework zapewniają następujące korzyści:  
  
-   **Wydajność.** [LINQ do XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) ułatwia program za pomocą XML i zapewnia obsługę zapytania podobne do bazy danych SQL.  
  
-   **Rozszerzalność.** Klasy XML w programie .NET Framework są rozszerzalne abstrakcyjnych klas podstawowych i metodach wirtualnych. Na przykład można utworzyć klasy pochodnej z <xref:System.Xml.XmlUrlResolver> klasy, która przechowuje strumienia pamięci podręcznej na dysk lokalny.  
  
-   **Architektura obsługująca dodatki.** .NET Framework zapewnia architekturę, w którym składniki mogą korzystać z sobą i danych mogą być przesyłane strumieniowo między składnikami. Na przykład magazyn danych, takich jak <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektów, można je przekształcać z <xref:System.Xml.Xsl.XslCompiledTransform> klasy i dane wyjściowe następnie mogą być przesyłane strumieniowo albo do innego magazynu lub zwrócony jako strumienia z usługą sieci web.  
  
-   **Wydajność.** W celu poprawy wydajności aplikacji niektóre klasy XML w programie .NET Framework obsługuje model na podstawie przesyłania strumieniowego o następującej charakterystyce:  
  
    -   Minimalny buforowanie tylko do przodu, model ściągania analizy (<xref:System.Xml.XmlReader>).  
  
    -   Sprawdzanie poprawności tylko do przodu (<xref:System.Xml.XmlReader>).  
  
    -   Kursor styl nawigacji, który minimalizuje tworzenia węzła do jednego wirtualnego węzła zapewniając dostępie do dokumentu (<xref:System.Xml.XPath.XPathNavigator>).  
  
     W celu poprawy wydajności przy każdym przetwarzania XSLT jest wymagany, korzystając z <xref:System.Xml.XPath.XPathDocument> klasy, która jest zoptymalizowana, jako tylko do odczytu magazynu dla zapytania XPath umożliwia wydajną pracę z <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
-   **Integracja z ADO.NET.** Klasy XML i [ADO.NET](../../../../docs/framework/data/adonet/index.md) są ściśle powiązane ze sobą danych relacyjnych i XML. <xref:System.Data.DataSet> Klasa znajduje się w pamięci podręcznej dane pobrane z bazy danych. <xref:System.Data.DataSet> Klasa ma możliwość odczytywania i zapisywania XML przy użyciu <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> klasy, aby utrwalić jego struktury wewnętrznej schemat relacyjny jako schematów XML (XSD) i na potrzeby wnioskowania dotyczącego schematu strukturę dokumentu XML.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Opcje przetwarzania XML](../../../../docs/standard/data/xml/xml-processing-options.md)  
 W tym artykule omówiono opcje przetwarzania danych XML.  
  
 [Przetwarzanie danych XML w pamięci](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)  
 W tym artykule omówiono trzy modele przetwarzania XML danych w pamięci. [LINQ do XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), <xref:System.Xml.XmlDocument> (oparte na modelu obiektu dokumentu W3C), klasy i <xref:System.Xml.XPath.XPathDocument> klasy (oparte na modelu danych XPath).  
  
 [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 W tym artykule opisano sposób użycia procesora XSLT.  
  
 [Model SOM (XML Schema Object Model)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 W tym artykule opisano klasy, służące do tworzenia i operowanie nimi schematów XML (XSD), zapewniając <xref:System.Xml.Schema.XmlSchema> klasy obciążenia i Edytuj schematu.  
  
 [Integracja XML z danymi relacyjnymi i sterownikiem ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)  
 W tym artykule opisano, jak programu .NET Framework udostępnia w czasie rzeczywistym, synchronicznej relacyjnych i hierarchicznych reprezentacje danych za pośrednictwem <xref:System.Data.DataSet> obiektu i <xref:System.Xml.XmlDataDocument> obiektu.  
  
 [Zarządzanie przestrzeniami nazw w dokumencie XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)  
 Opisuje sposób <xref:System.Xml.XmlNamespaceManager> klasa jest używana do przechowywania i obsługi informacji dotyczących przestrzeni nazw.  
  
 [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 W tym artykule opisano, jak typy mapowania typów danych XML do środowiska CLR, jak przekonwertować typów danych XML i innymi funkcjami pomocy technicznej typu <xref:System.Xml> klasy.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 Zawiera informacje na temat dostępu do danych za pomocą ADO.NET.  
  
 [Zabezpieczenia](../../../../docs/standard/security/index.md)  
 Omówienie systemu zabezpieczeń .NET Framework.  
  