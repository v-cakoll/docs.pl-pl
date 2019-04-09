---
title: Dokumenty i dane XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e96515240cdbc1cb05c4d58aee6eb2500e0e313
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171174"
---
# <a name="xml-documents-and-data"></a>Dokumenty i dane XML
.NET Framework zapewnia kompleksowego i zintegrowanego zestaw klas, które umożliwiają łatwe tworzenie aplikacji z obsługą XML. Klasy w następujące przestrzenie nazw obsługują analizowania i zapisywania, edytowania plików XML danych XML w pamięci, sprawdzanie poprawności danych i transformacji XSLT.  
  
-   <xref:System.Xml>  
  
-   <xref:System.Xml.XPath>  
  
-   <xref:System.Xml.Xsl>  
  
-   <xref:System.Xml.Schema>  
  
-   <xref:System.Xml.Linq>  
  
 Aby uzyskać pełną listę, wyszukaj "System.Xml" na [przeglądarka interfejsu API .NET](https://docs.microsoft.com/dotnet/api/?term=system.xml).  
  
 Klasy w te przestrzenie nazw obsługują zalecenia konsorcjum World Wide Web Consortium (W3C). Na przykład:  
  
-   <xref:System.Xml.XmlDocument?displayProperty=nameWithType> Klasy implementuje [W3C Document Object Model (DOM) poziom 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) i [Core 2 na poziomie modelu DOM](https://www.w3.org/TR/DOM-Level-2-Core/) zalecenia.  
  
-   <xref:System.Xml.XmlReader?displayProperty=nameWithType> i <xref:System.Xml.XmlWriter?displayProperty=nameWithType> klasy pomocy technicznej [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) i [przestrzeni nazw w kodzie XML](https://www.w3.org/TR/REC-xml-names/) zalecenia.  
  
-   Schematy w <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> klasy pomocy technicznej [W3C XML schematu część 1: Struktury](https://www.w3.org/TR/xmlschema-1/) i [XML schematu część 2: Typy danych](https://www.w3.org/TR/xmlschema-2/) zalecenia.  
  
-   Klasy w <xref:System.Xml.Xsl?displayProperty=nameWithType> przekształcenia XSLT obsługi przestrzeni nazw, które są zgodne z [W3C specyfikacji XSLT 1.0](https://www.w3.org/TR/xslt) zalecenia.  
  
 Klasy XML w programie .NET Framework zapewniają następujące korzyści:  
  
-   **Wydajność.** [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) ułatwia program za pomocą XML i zapewnia środowisko zapytania, które są podobne do bazy danych SQL.  
  
-   **Rozszerzalność.** Klasy XML w programie .NET Framework można rozszerzać za pomocą abstrakcyjnych klas bazowych i metod wirtualnych. Na przykład można utworzyć pochodnej klasy <xref:System.Xml.XmlUrlResolver> klasę, która przechowuje strumień pamięci podręcznej na dysku lokalnym.  
  
-   **Architektura obsługująca dodatki.** .NET Framework zapewnia architekturę, w którym składniki mogą korzystać z sobą, a danych może być przesyłany strumieniowo między składnikami. Na przykład magazyn danych, takich jak <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektów, mogą zostać przekształcone z <xref:System.Xml.Xsl.XslCompiledTransform> klasy, a dane wyjściowe można je strumieniowo albo do innego magazynu lub zwracane jako strumienia z usługi sieci web.  
  
-   **Wydajność.** Lepszą wydajność aplikacji niektóre z klas XML w programie .NET Framework obsługuje model oparty na przesyłania strumieniowego o następującej charakterystyce:  
  
    -   Minimalne buforowanie tylko do przodu, model ściągania podczas analizowania (<xref:System.Xml.XmlReader>).  
  
    -   Sprawdzanie poprawności tylko do przodu (<xref:System.Xml.XmlReader>).  
  
    -   Kursor styl nawigacji, które minimalizuje tworzenia węzła do pojedynczego wirtualnego węzła przy jednoczesnym zapewnieniu dostępie do dokumentu (<xref:System.Xml.XPath.XPathNavigator>).  
  
     Lepszą wydajność w każdym przypadku, gdy przetwarzania XSLT jest wymagany, można użyć <xref:System.Xml.XPath.XPathDocument> klasy, która jest zoptymalizowany, tylko do odczytu magazynu dla kwerendy XPath, które mają pracować wydajnie <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
-   **Integracja za pomocą narzędzia ADO.NET.** Klasy XML i [ADO.NET](../../../../docs/framework/data/adonet/index.md) są ściśle zintegrowane ze sobą opartego na danych relacyjnych i XML. <xref:System.Data.DataSet> Klasy jest w pamięci podręcznej informacje o danych pobranych z bazy danych. <xref:System.Data.DataSet> Klasa ma możliwość odczytu i zapisu XML przy użyciu <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> klasy, aby zachować strukturę wewnętrznego schemat relacyjny jako schematów XML (XSD) i na potrzeby wnioskowania dotyczącego schematu struktury dokumentu XML.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Opcje przetwarzania XML](../../../../docs/standard/data/xml/xml-processing-options.md)  
 W tym artykule omówiono opcje związane z przetwarzaniem danych XML.  
  
 [Przetwarzanie danych XML w pamięci](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)  
 W tym artykule omówiono trzy modele dla przetwarzania XML danych w pamięci: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), <xref:System.Xml.XmlDocument> klasy (oparty na formacie W3C Document Object Model) i <xref:System.Xml.XPath.XPathDocument> klasy (oparty na modelu danych XPath).  
  
 [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 W tym artykule opisano sposób użycia procesora XSLT.  
  
 [Model SOM (XML Schema Object Model)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 W tym artykule opisano klasy, służące do tworzenia i manipulowania schematów XML (XSD), zapewniając <xref:System.Xml.Schema.XmlSchema> klasy, aby ładować i edytować schemat.  
  
 [Integracja XML z danymi relacyjnymi i sterownikiem ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)  
 W tym artykule opisano, jak .NET Framework udostępnia w czasie rzeczywistym, synchronicznej relacyjne i hierarchiczne reprezentacje danych za pośrednictwem <xref:System.Data.DataSet> obiektu i <xref:System.Xml.XmlDataDocument> obiektu.  
  
 [Zarządzanie przestrzeniami nazw w dokumencie XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)  
 W tym artykule opisano sposób, w jaki <xref:System.Xml.XmlNamespaceManager> klasa jest używana do przechowywania i obsługi informacji dotyczących przestrzeni nazw.  
  
 [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 W tym artykule opisano, jak typy mapowania typów danych XML do CLR, jak konwertować typów danych XML i inne funkcje pomocy technicznej typu w <xref:System.Xml> klasy.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 Zawiera informacje na temat dostępu do danych za pomocą platformy ADO.NET.  
  
 [Zabezpieczenia](../../../../docs/standard/security/index.md)  
 Omówienie systemu zabezpieczeń .NET Framework.  
