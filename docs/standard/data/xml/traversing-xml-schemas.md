---
title: Przechodzenie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c587f4248205251824be851c135d93784e86c2f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646636"
---
# <a name="traversing-xml-schemas"></a>Przechodzenie schematów XML
Przechodzenie przez schemat XML przy użyciu schematu Object Model (model SOM) interfejsu API zapewnia dostęp do elementów, atrybutów i typy przechowywanych w SOM. Przechodzenie przez XML schematu ładowany SOM jest także pierwszym krokiem podczas edytowania schematu XML przy użyciu interfejsu API SOM.  
  
## <a name="traversing-an-xml-schema"></a>Przechodzenie przez schemat XML  
 Następujące właściwości <xref:System.Xml.Schema.XmlSchema> klasy zapewniają dostęp do kolekcji wszystkie globalne elementy dodane do schematu XML.  
  
|Właściwość|Typ obiektu, przechowywane w kolekcji lub tablicy|  
|--------------|---------------------------------------------------|  
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|  
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|  
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport>, lub <xref:System.Xml.Schema.XmlSchemaRedefine>|  
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject> (zapewnia dostęp do globalnego poziomu elementów, atrybutów i typy).|  
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|  
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|  
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute> (zapewnia dostęp do atrybutów, które nie należą do przestrzeni nazw schematu)|  
  
> [!NOTE]
>  Wszystkie właściwości wymienione w powyższej tabeli, z wyjątkiem <xref:System.Xml.Schema.XmlSchema.Items%2A> właściwości są właściwościami odniesienie-Schema-kompilacja-zestaw informacji (PSCI), które nie są dostępne, dopóki nie został wcześniej skompilowany schematu. <xref:System.Xml.Schema.XmlSchema.Items%2A> Właściwość jest właściwością wstępnej schema kompilacji, który może służyć przed schemat został wcześniej skompilowany w celu uzyskania dostępu do globalnych poziomu elementów, atrybutów i typy.  
>   
>  <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> Właściwości zapewnia dostęp do wszystkich atrybutów, które nie należą do przestrzeni nazw schematu. Te atrybuty nie są przetwarzane przez procesor schematu.  
  
 Przykładowy kod, który następuje po pokazuje przechodzenie przez schemat klientów utworzonych w [tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu. Przykład kodu pokazuje przechodzenie schematu za pomocą kolekcji opisanych powyżej i zapisuje wszystkie elementy i atrybuty w schemacie do konsoli.  
  
 Przykład przechodzi przez schemat klienta w poniższych krokach.  
  
1.  Dodaje nowy schemat klienta <xref:System.Xml.Schema.XmlSchemaSet> obiektu, a następnie kompiluje go. Wszelkie ostrzeżenia sprawdzania poprawności schematu i błędów napotkanych odczytywania lub skompilowanie schematu są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegować.  
  
2.  Pobiera skompilowana klasa <xref:System.Xml.Schema.XmlSchema> obiektu z <xref:System.Xml.Schema.XmlSchemaSet> przez Iterowanie <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości. Ponieważ schemat jest kompilowany, właściwości (PSCI) po-Schema-kompilacja-zestaw informacji są dostępne.  
  
3.  Iteruje przez każdy <xref:System.Xml.Schema.XmlSchemaElement> w <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekcji po-schema-kompilacja <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji pisania nazwę każdego elementu w konsoli.  
  
4.  Pobiera typ złożony `Customer` elementu za pomocą <xref:System.Xml.Schema.XmlSchemaComplexType> klasy.  
  
5.  Jeśli typ złożony zawiera atrybuty, pobiera <xref:System.Collections.IDictionaryEnumerator> wyliczania każdego <xref:System.Xml.Schema.XmlSchemaAttribute> i zapisuje jego nazwę do konsoli.  
  
6.  Pobiera cząstki sequence użycia typu złożonego <xref:System.Xml.Schema.XmlSchemaSequence> klasy.  
  
7.  Iteruje przez każdy <xref:System.Xml.Schema.XmlSchemaElement> w <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> kolekcji pisania nazwę każdego elementu podrzędnego w konsoli.  
  
 Oto przykład kompletny kod.  
  
 [!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
 [!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
 [!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]  
  
 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> Właściwość może być <xref:System.Xml.Schema.XmlSchemaSimpleType>, lub <xref:System.Xml.Schema.XmlSchemaComplexType> przypadku zdefiniowanych przez użytkownika typu prostego lub typ złożony. Może to być także <xref:System.Xml.Schema.XmlSchemaDatatype> Jeśli jest to jeden z wbudowanych typów danych zdefiniowanych w zaleceniem schematu XML W3C. W schemacie klienta <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> z `Customer` element jest <xref:System.Xml.Schema.XmlSchemaComplexType>i `FirstName` i `LastName` elementy są <xref:System.Xml.Schema.XmlSchemaSimpleType>.  
  
 Przykładowy kod z [tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu używane <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> kolekcję, aby dodać atrybut `CustomerId` do `Customer` elementu. Jest to właściwość wstępnej schema kompilacji. Jest odpowiadającą właściwość odniesienie-Schema-kompilacja-zestaw informacji <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> kolekcji, która zawiera wszystkie atrybuty typu złożonego, włącznie z tymi, które są dziedziczone przez wyprowadzenie typu.  
  
## <a name="see-also"></a>Zobacz także

- [Model SOM (XML Schema Object Model) ― omówienie](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Odczytywanie i zapisywanie schematów XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Edytowanie schematów XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [Uwzględnianie lub importowanie schematów XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Zestaw informacji po kompilacji schematu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
