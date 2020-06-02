---
title: Przechodzenie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
ms.openlocfilehash: 0951e83c3035de751801d194696eb64993260ef8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289840"
---
# <a name="traversing-xml-schemas"></a>Przechodzenie schematów XML

Przechodzenie przez schemat XML za pomocą interfejsu API modelu obiektów schematu (SOM) zapewnia dostęp do elementów, atrybutów i typów przechowywanych w modelu SOM. Przechodzenie schematu XML załadowanego do modelu SOM jest również pierwszym krokiem w edycji schematu XML przy użyciu interfejsu API modelu SOM.

## <a name="traversing-an-xml-schema"></a>Przechodzenie schematu XML

Następujące właściwości <xref:System.Xml.Schema.XmlSchema> klasy zapewniają dostęp do kolekcji wszystkich elementów globalnych dodanych do schematu XML.

|Właściwość|Typ obiektu przechowywany w kolekcji lub tablicy|
|--------------|---------------------------------------------------|
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude> , <xref:System.Xml.Schema.XmlSchemaImport> lub<xref:System.Xml.Schema.XmlSchemaRedefine>|
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject>(zapewnia dostęp do wszystkich elementów poziomu globalnego, atrybutów i typów).|
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute>(zapewnia dostęp do atrybutów, które nie należą do przestrzeni nazw schematu)|

> [!NOTE]
> Wszystkie właściwości wymienione w powyższej tabeli, z wyjątkiem właściwości <xref:System.Xml.Schema.XmlSchema.Items%2A> , są właściwościami po schemacie kompilacja-sprawdzonych (PSCI), które nie są dostępne, dopóki schemat nie zostanie skompilowany. <xref:System.Xml.Schema.XmlSchema.Items%2A>Właściwość jest właściwością prekompilowania schematu, której można użyć przed skompilowaniem schematu w celu uzyskania dostępu do wszystkich elementów poziomu globalnego, atrybutów i typów oraz edytowania ich.
>
> <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>Właściwość zapewnia dostęp do wszystkich atrybutów, które nie należą do przestrzeni nazw schematu. Te atrybuty nie są przetwarzane przez procesor schematu.

Poniższy przykład kodu demonstruje przechodzenie przez schemat klienta utworzony w temacie [Tworzenie schematów XML](building-xml-schemas.md) . Przykład kodu demonstruje przechodzenie schematu przy użyciu kolekcji opisanych powyżej i zapisuje wszystkie elementy i atrybuty w schemacie do konsoli programu.

Przykład przechodzi przez schemat klienta w poniższych krokach.

1. Dodaje schemat klienta do nowego <xref:System.Xml.Schema.XmlSchemaSet> obiektu, a następnie kompiluje go. Wszystkie ostrzeżenia i błędy walidacji schematu napotkane podczas odczytywania lub kompilowania schematu są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegata.

2. Pobiera skompilowany <xref:System.Xml.Schema.XmlSchema> obiekt z obiektu <xref:System.Xml.Schema.XmlSchemaSet> przez iterację we <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości. Ze względu na to, że schemat jest skompilowany, dostępne są właściwości po schemacie kompilacja-sprawdzonych (PSCI).

3. Wykonuje iterację na każdym <xref:System.Xml.Schema.XmlSchemaElement> z <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekcji kolekcji po schemacie, <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> tworząc nazwę każdego elementu w konsoli.

4. Pobiera typ złożony `Customer` elementu przy użyciu <xref:System.Xml.Schema.XmlSchemaComplexType> klasy.

5. Jeśli typ złożony ma jakiekolwiek atrybuty, pobiera <xref:System.Collections.IDictionaryEnumerator> <xref:System.Xml.Schema.XmlSchemaAttribute> i zapisuje jego nazwę w konsoli programu.

6. Pobiera cząstkę sekwencji typu złożonego przy użyciu <xref:System.Xml.Schema.XmlSchemaSequence> klasy.

7. Iteruje każde <xref:System.Xml.Schema.XmlSchemaElement> w kolekcji, <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> pisząc nazwę każdego elementu podrzędnego w konsoli.

Poniżej znajduje się kompletny przykład kodu.

[!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
[!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
[!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]

<xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType>Właściwość może być <xref:System.Xml.Schema.XmlSchemaSimpleType> lub <xref:System.Xml.Schema.XmlSchemaComplexType> Jeśli jest typem prostym zdefiniowanym przez użytkownika lub typu złożonego. Może to być również, <xref:System.Xml.Schema.XmlSchemaDatatype> Jeśli jest to jeden z wbudowanych typów danych zdefiniowanych w rekomendacji schematu W3C XML. W schemacie klienta <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> `Customer` element jest <xref:System.Xml.Schema.XmlSchemaComplexType> , a `FirstName` `LastName` elementy i <xref:System.Xml.Schema.XmlSchemaSimpleType> .

Przykład kodu w temacie [Building schematy XML](building-xml-schemas.md) użył <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> kolekcji, aby dodać atrybut `CustomerId` do `Customer` elementu. Jest to właściwość kompilacji poprzedzającej schemat. Odpowiednia właściwość po schemacie kompilacja-sprawdzonych jest <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> kolekcją, która zawiera wszystkie atrybuty typu złożonego, łącznie z tymi, które są dziedziczone za pomocą typu pochodnego.

## <a name="see-also"></a>Zobacz także

- [Model SOM (XML Schema Object Model) ― omówienie](xml-schema-object-model-overview.md)
- [Odczytywanie i zapisywanie schematów XML](reading-and-writing-xml-schemas.md)
- [Tworzenie schematów XML](building-xml-schemas.md)
- [Edytowanie schematów XML](editing-xml-schemas.md)
- [Uwzględnianie lub importowanie schematów XML](including-or-importing-xml-schemas.md)
- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](xmlschemaset-for-schema-compilation.md)
- [Zestaw informacji po kompilacji schematu](post-schema-compilation-infoset.md)
