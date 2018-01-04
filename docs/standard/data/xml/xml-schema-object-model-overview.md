---
title: "Omówienie modelu obiektu schematu XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e18a3151228ea7edb5a8380f6ed707ee88d369e5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xml-schema-object-model-overview"></a>Omówienie modelu obiektu schematu XML
Model obiektu schematu (SOM) w programie Microsoft .NET Framework jest sformatowany interfejs API, który służy do tworzenia, edytowania i Zweryfikuj schematy programowo. SOM działa na dokumentach schematów XML w sposób podobny do modelu DOM (Document Object) funkcjonowania w dokumentach XML. Dokumenty XML schematu są prawidłowe pliki XML, które po załadowaniu do SOM, zmienić znaczenie dotyczących struktury i ważności inne dokumenty XML, które są zgodne ze schematem.  
  
 Schemat jest dokument XML, który definiuje klasę dokumentów XML, określając struktury lub modelu dokumentów XML dla określonego schematu. Schemat wymieniono ograniczenia dotyczące zawartość dokumentów XML i opisano słownictwa (reguły lub gramatyki), który dokumentów XML zgodne należy wykonać, aby można je było uważać schematu prawidłowe z określonego schematu. Weryfikacja dokumentu XML jest proces, który zapewnia, że dokument odpowiada gramatyki określonej w schemacie.  
  
 Poniżej przedstawiono sposoby SOM interfejsu API w programie .NET Framework umożliwia tworzenie, edytowanie i Zweryfikuj schematy.  
  
-   Załaduj i Zapisz prawidłowe schematy do i z plików.  
  
-   Tworzenie przy użyciu klasy jednoznacznie schematów w pamięci.  
  
-   Interakcje z <xref:System.Xml.Schema.XmlSchemaSet> klasy do pamięci podręcznej, kompilowania i pobrać schematów.  
  
-   Interakcje z <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy do sprawdzania poprawności dokumentów wystąpienie XML względem schematów.  
  
-   Tworzenie edytory za tworzenie i obsługę schematów.  
  
-   Edytuj dynamicznie schematu, które mogą być spełnione i zapisywane do użycia w weryfikacji dokumentów wystąpienie XML.  
  
## <a name="the-schema-object-model"></a>Model obiektu schematu  
 SOM składa się z rozbudowany zestaw klas w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw odpowiadające elementom w schemacie XML. Na przykład `<xsd:schema>...</xsd:schema>` mapuje element <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> klasy i wszystkie informacje, które mogą być zawarte w `<xsd:schema/>` elementu można przedstawić przy użyciu <xref:System.Xml.Schema.XmlSchema> klasy. Podobnie `<xsd:element>...</xsd:element>` i `<xsd:attribute>...</xsd:attribute>` elementy mapy do <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> i <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> odpowiednio klasy. To mapowanie nadal dla wszystkich elementów schematu XML tworzenia modelu obiektu schematu XML w <xref:System.Xml.Schema> przedstawione na diagramie, znajdujący się w przestrzeni nazw.  
  
 ![Model obiektu System.Xml.Schema](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")  
  
 Aby uzyskać więcej informacji o poszczególnych klasach w <xref:System.Xml.Schema> przestrzeni nazw, zobacz <xref:System.Xml.Schema> przestrzeni nazw dokumentacji w bibliotece klas programu .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 [Odczytywanie i zapisywanie schematów XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [Przechodzenie schematów XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [Edytowanie schematów XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [Uwzględnianie lub importowanie schematów XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Zestaw informacji po kompilacji schematu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
