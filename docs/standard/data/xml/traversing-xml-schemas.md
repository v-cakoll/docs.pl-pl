---
title: Przechodzenie przez schematy XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b02fd72c705d264394b83b89fc7ec802be7e502a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="traversing-xml-schemas"></a>Przechodzenie przez schematy XML
Przechodzenie przez schemat XML przy użyciu schematu obiektu modelu (SOM) interfejsu API zapewnia dostęp do elementy, atrybuty i przechowywane w SOM. typów Przechodzenie XML schematu ładowane do SOM jest również pierwszym etapem schematu XML przy użyciu interfejsu API SOM edycji.  
  
## <a name="traversing-an-xml-schema"></a>Przechodzenie przez schematu XML  
 Następujące właściwości <xref:System.Xml.Schema.XmlSchema> klasy zapewniają dostęp do kolekcji wszystkie globalne elementy dodane do schematu XML.  
  
|Właściwość|Typ obiektu w kolekcji lub tablicy|  
|--------------|---------------------------------------------------|  
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|  
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|  
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport>, lub <xref:System.Xml.Schema.XmlSchemaRedefine>|  
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject> (umożliwia dostęp do globalnego poziomu elementy, atrybuty i typy).|  
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|  
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|  
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute> (umożliwia dostęp do atrybutów, które nie należą do schematu przestrzeni nazw)|  
  
> [!NOTE]
>  Wszystkie właściwości wymienione w powyższej tabeli, z wyjątkiem <xref:System.Xml.Schema.XmlSchema.Items%2A> właściwość nie ma właściwości po-Schema-kompilacji-typu Infoset (PSCI), które nie są dostępne, dopóki nie został skompilowany schematu. <xref:System.Xml.Schema.XmlSchema.Items%2A> Właściwość jest właściwością wstępnie przygotowany schema kompilacji, która może zostać użyta przed dostępu i edytować wszystkie globalne poziomu elementy, atrybuty i typów została skompilowana schematu.  
>   
>  <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> Właściwości zapewnia dostęp do wszystkich atrybutów, które nie należą do schematu przestrzeni nazw. Te atrybuty nie są przetwarzane przez procesor schematu.  
  
 Przykładowy kod, który następuje pokazuje przechodzących przez schemat klienta utworzone w [schematów XML budynku](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu. Przykładowy kod przedstawia przechodzenie schematu za pomocą kolekcji opisane powyżej i zapisuje wszystkie elementy i atrybuty w schemacie konsoli.  
  
 Próbki są przesyłane za pośrednictwem schematu klienta w kolejnych krokach.  
  
1.  Dodaje do nowego schematu klienta <xref:System.Xml.Schema.XmlSchemaSet> obiekt, a następnie kompiluje go. Wszelkie ostrzeżenia dotyczące sprawdzania poprawności schematu i błędów napotkanych odczytu lub kompilowania schematu są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegowanie.  
  
2.  Pobiera skompilowanych <xref:System.Xml.Schema.XmlSchema> obiekt z <xref:System.Xml.Schema.XmlSchemaSet> przez Iterowanie po <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości. Ponieważ skompilować schematu, po-Schema-kompilacji-typu Infoset właściwości (PSCI) są dostępne.  
  
3.  Wykonuje iterację na każdym <xref:System.Xml.Schema.XmlSchemaElement> w <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekcji po-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji pisania nazwa każdego elementu w konsoli.  
  
4.  Pobiera typ złożony `Customer` przy użyciu elementu <xref:System.Xml.Schema.XmlSchemaComplexType> klasy.  
  
5.  Jeśli typ złożony wszelkie atrybuty, pobiera <xref:System.Collections.IDictionaryEnumerator> wyliczyć za pośrednictwem każdej <xref:System.Xml.Schema.XmlSchemaAttribute> i zapisuje jego nazwę w konsoli.  
  
6.  Pobiera cząstka sequence użycia typu złożonego <xref:System.Xml.Schema.XmlSchemaSequence> klasy.  
  
7.  Wykonuje iterację na każdym <xref:System.Xml.Schema.XmlSchemaElement> w <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> kolekcji pisania nazwę każdego elementu podrzędnego w konsoli.  
  
 Poniżej znajduje się pełny przykład kodu.  
  
 [!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
 [!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
 [!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]  
  
 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> Właściwość może być <xref:System.Xml.Schema.XmlSchemaSimpleType>, lub <xref:System.Xml.Schema.XmlSchemaComplexType> Jeśli jest zdefiniowana przez użytkownika typu prostego lub typu złożonego. Może to być także <xref:System.Xml.Schema.XmlSchemaDatatype> , jeśli jest to jeden z wbudowanych typów danych zdefiniowanych w zaleceń schematu W3C XML. W schemacie klienta <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> z `Customer` jest element <xref:System.Xml.Schema.XmlSchemaComplexType>i `FirstName` i `LastName` elementy są <xref:System.Xml.Schema.XmlSchemaSimpleType>.  
  
 Przykładowy kod w [schematów XML budynku](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu używane <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> kolekcji można dodać atrybutu `CustomerId` do `Customer` elementu. Jest to właściwość wstępnie przygotowany schema kompilacji. Jest odpowiadającą właściwością po-Schema-kompilacji-typu Infoset <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> kolekcji, która zawiera wszystkie atrybuty typu złożonego, w tym te, które są dziedziczone przez wyprowadzenie typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Model SOM (XML Schema Object Model) ― omówienie](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [Odczytywanie i zapisywanie schematów XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [Edytowanie schematów XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [Uwzględnianie lub importowanie schematów XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Zestaw informacji po kompilacji schematu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
