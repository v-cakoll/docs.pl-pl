---
title: Przegląd modelu obiektów schematu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab7f3075d46ef0e8b98af471ae3943f7500128e5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080049"
---
# <a name="xml-schema-object-model-overview"></a>Przegląd modelu obiektów schematu XML
Model obiektu schematu (SOM) w programie Microsoft .NET Framework to zaawansowane interfejsy API, która pozwala na tworzenie, edytowanie i sprawdź poprawność schematów programowo. Model SOM działa na dokumentów schematu XML, podobnie jak sposób, w jaki Document Object Model (DOM) działa w dokumentach XML. Dokumentów schematu XML są prawidłowe pliki XML, które po załadowaniu do SOM, zmienić znaczenie dotyczące struktury i ważności innych dokumentów XML, które są zgodne ze schematem.  
  
 Schemat jest dokument XML, który definiuje klasę dokumentów XML przez określenie struktury lub modelu dokumentów XML dla określonego schematu. Schemat wymieniono ograniczenia dotyczące zawartości dokumentów XML i opisano słownika (reguły lub gramatyki), który jest zgodny z dokumentów XML należy wykonać, aby można je było uważać schematu prawidłowy z określonego schematu. Sprawdzanie poprawności dokumentu XML to proces, który zapewnia, że dokument jest zgodny ze gramatyki, określonego przez schemat.  
  
 Poniżej przedstawiono sposoby SOM interfejsu API na platformie .NET Framework umożliwia tworzenie, edytowanie i sprawdź poprawność schematów.  
  
-   Ładuje i zapisuje prawidłowe schematy do i z plików.  
  
-   Tworzenie schematów w pamięci, za pomocą silnie typizowanej klasy.  
  
-   Interakcja z <xref:System.Xml.Schema.XmlSchemaSet> klasy do pamięci podręcznej, kompilowania i pobrać schematów.  
  
-   Interakcja z <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy do weryfikacji dokumentów wystąpienia XML względem schematów.  
  
-   Twórz edytory za utworzenie i utrzymywanie schematów.  
  
-   Dynamicznie edytować schemat, który może być spełnione i zapisać do użycia podczas sprawdzania poprawności, dokumentów wystąpienia XML.  
  
## <a name="the-schema-object-model"></a>Model obiektu schematu  
 Model SOM składa się z obszerny zestaw klas w <xref:System.Xml.Schema?displayProperty=nameWithType> odpowiadające elementom w schematu XML przestrzeń nazw. Na przykład `<xsd:schema>...</xsd:schema>` mapuje element <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> klasy i wszystkie informacje, które mogą być zawarte w obrębie `<xsd:schema/>` element może być reprezentowany za pomocą <xref:System.Xml.Schema.XmlSchema> klasy. Podobnie `<xsd:element>...</xsd:element>` i `<xsd:attribute>...</xsd:attribute>` mapowania elementów <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> i <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> klasy odpowiednio. To mapowanie jest kontynuowany dla wszystkich elementów schematu XML, tworzenie modelu obiektu schematu XML w <xref:System.Xml.Schema> przedstawione na diagramie, który następuje po przestrzeni nazw.  
  
 ![Model obiektu System.Xml.Schema](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")  
  
 Aby uzyskać więcej informacji na temat każdej klasy w <xref:System.Xml.Schema> przestrzeni nazw, zobacz <xref:System.Xml.Schema> dokumentacja przestrzeni nazw w bibliotece klas programu .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- [Odczytywanie i zapisywanie schematów XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
- [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
- [Przechodzenie schematów XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
- [Edytowanie schematów XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
- [Uwzględnianie lub importowanie schematów XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [Zestaw informacji po kompilacji schematu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
