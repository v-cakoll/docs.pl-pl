---
title: Przechodzenie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
ms.openlocfilehash: dbe02242f9bb8654e3f12d87b6ff6c2aea1f76b1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710118"
---
# <a name="traversing-xml-schemas"></a>Przechodzenie schematów XML

Przechodzenie przez schemat XML za pomocą interfejsu API modelu obiektów schematu (SOM) zapewnia dostęp do elementów, atrybutów i typów przechowywanych w modelu SOM. Przechodzenie schematu XML załadowanego do modelu SOM jest również pierwszym krokiem w edycji schematu XML przy użyciu interfejsu API modelu SOM.

## <a name="traversing-an-xml-schema"></a>Przechodzenie schematu XML

Następujące właściwości klasy <xref:System.Xml.Schema.XmlSchema> zapewniają dostęp do kolekcji wszystkich elementów globalnych dodanych do schematu XML.

|Właściwość|Typ obiektu przechowywany w kolekcji lub tablicy|
|--------------|---------------------------------------------------|
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|System <xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport> lub <xref:System.Xml.Schema.XmlSchemaRedefine>|
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject> (zapewnia dostęp do wszystkich elementów poziomu globalnego, atrybutów i typów).|
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute> (zapewnia dostęp do atrybutów, które nie należą do przestrzeni nazw schematu)|

> [!NOTE]
> Wszystkie właściwości wymienione w powyższej tabeli, z wyjątkiem właściwości <xref:System.Xml.Schema.XmlSchema.Items%2A>, są właściwościami po schemacie kompilacja-sprawdzonych (PSCI), które nie są dostępne, dopóki schemat nie zostanie skompilowany. Właściwość <xref:System.Xml.Schema.XmlSchema.Items%2A> jest właściwością prekompilowania przed schematem, która może zostać użyta przed skompilowaniem schematu w celu uzyskania dostępu do wszystkich elementów poziomu globalnego, atrybutów i typów oraz edytowania ich.
>
> Właściwość <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> zapewnia dostęp do wszystkich atrybutów, które nie należą do przestrzeni nazw schematu. Te atrybuty nie są przetwarzane przez procesor schematu.

Poniższy przykład kodu demonstruje przechodzenie przez schemat klienta utworzony w temacie [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) . Przykład kodu demonstruje przechodzenie schematu przy użyciu kolekcji opisanych powyżej i zapisuje wszystkie elementy i atrybuty w schemacie do konsoli programu.

Przykład przechodzi przez schemat klienta w poniższych krokach.

1. Dodaje schemat klienta do nowego obiektu <xref:System.Xml.Schema.XmlSchemaSet>, a następnie kompiluje go. Wszystkie ostrzeżenia i błędy walidacji schematu napotkane podczas odczytywania lub kompilowania schematu są obsługiwane przez delegata <xref:System.Xml.Schema.ValidationEventHandler>.

2. Pobiera skompilowany obiekt <xref:System.Xml.Schema.XmlSchema> z <xref:System.Xml.Schema.XmlSchemaSet> przez iterację we właściwości <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>. Ze względu na to, że schemat jest skompilowany, dostępne są właściwości po schemacie kompilacja-sprawdzonych (PSCI).

3. Wykonuje iterację dla każdego <xref:System.Xml.Schema.XmlSchemaElement> w <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekcji kolekcji po schemacie kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> zapisząc nazwę każdego elementu do konsoli.

4. Pobiera typ złożony elementu `Customer` przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaComplexType>.

5. Jeśli typ złożony ma jakiekolwiek atrybuty, pobiera <xref:System.Collections.IDictionaryEnumerator> do wyliczenia dla każdej <xref:System.Xml.Schema.XmlSchemaAttribute> i zapisuje jego nazwę w konsoli programu.

6. Pobiera cząstkę sekwencji typu złożonego przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaSequence>.

7. Wykonuje iterację dla każdego <xref:System.Xml.Schema.XmlSchemaElement> w kolekcji <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType>, pisząc nazwę każdego elementu podrzędnego w konsoli.

Poniżej znajduje się kompletny przykład kodu.

[!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
[!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
[!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]

Właściwość <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> może być <xref:System.Xml.Schema.XmlSchemaSimpleType>lub <xref:System.Xml.Schema.XmlSchemaComplexType>, jeśli jest to typ prosty zdefiniowany przez użytkownika lub typ złożony. Może być również <xref:System.Xml.Schema.XmlSchemaDatatype>, jeśli jest to jeden z wbudowanych typów danych zdefiniowanych w rekomendacji schematu W3C XML. W schemacie klienta <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> elementu `Customer` jest <xref:System.Xml.Schema.XmlSchemaComplexType>, a elementy `FirstName` i `LastName` są <xref:System.Xml.Schema.XmlSchemaSimpleType>.

Przykładowy kod w temacie [Building schematy XML](../../../../docs/standard/data/xml/building-xml-schemas.md) użył kolekcji <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType>, aby dodać atrybut `CustomerId` do elementu `Customer`. Jest to właściwość kompilacji poprzedzającej schemat. Odpowiednia właściwość po schemacie kompilacja-sprawdzonych jest kolekcją <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType>, która zawiera wszystkie atrybuty typu złożonego, łącznie z tymi, które są dziedziczone za pomocą typu pochodnego.

## <a name="see-also"></a>Zobacz także

- [Model SOM (XML Schema Object Model) ― omówienie](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Odczytywanie i zapisywanie schematów XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Edytowanie schematów XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [Uwzględnianie lub importowanie schematów XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Zestaw informacji po kompilacji schematu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
