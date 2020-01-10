---
title: Edytowanie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
ms.openlocfilehash: d7d9f8e0d4ec2f343b50e68e942bf94e93576f25
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710950"
---
# <a name="editing-xml-schemas"></a>Edytowanie schematów XML

Edytowanie schematu XML jest jedną z najważniejszych funkcji modelu obiektów schematu (SOM). Wszystkie właściwości kompilacji przed schematem modelu SOM mogą służyć do zmiany istniejących wartości w schemacie XML. Schemat XML można następnie ponownie skompilować, aby odzwierciedlić zmiany.

Pierwszym krokiem podczas edytowania schematu załadowanego do modelu SOM jest przechodzenie przez schemat. Przed podjęciem próby edycji schematu należy zapoznać się z przechodzeniem schematu przy użyciu interfejsu API modelu SOM. Należy również zapoznać się z właściwościami prekompilowania i po schemacie kompilacji sprawdzonych (PSCI).

## <a name="editing-an-xml-schema"></a>Edytowanie schematu XML

W tej sekcji przedstawiono dwa przykłady kodu, z których każda edytuje schemat klienta utworzony w temacie [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) . Pierwszy przykład kodu dodaje nowy element `PhoneNumber` do elementu `Customer`, a drugi przykład kodu dodaje nowy atrybut `Title` do elementu `FirstName`. Pierwszy przykład używa również kolekcji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kompilacji po schemacie jako metody przechodzenia przez schemat klienta, podczas gdy drugi przykład kodu używa kolekcji przed<xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType>owej kompilacji.

### <a name="phonenumber-element-example"></a>Przykład elementu nr telefonu

Ten pierwszy przykład kodu dodaje nowy element `PhoneNumber` do elementu `Customer` schematu klienta. Przykładowy kod edytuje schemat klienta w poniższych krokach.

1. Dodaje schemat klienta do nowego obiektu <xref:System.Xml.Schema.XmlSchemaSet>, a następnie kompiluje go. Wszystkie ostrzeżenia i błędy walidacji schematu napotkane podczas odczytywania lub kompilowania schematu są obsługiwane przez delegata <xref:System.Xml.Schema.ValidationEventHandler>.

2. Pobiera skompilowany obiekt <xref:System.Xml.Schema.XmlSchema> z <xref:System.Xml.Schema.XmlSchemaSet> przez iterację we właściwości <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>. Ze względu na to, że schemat jest skompilowany, dostępne są właściwości po schemacie kompilacja-sprawdzonych (PSCI).

3. Tworzy element `PhoneNumber` przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaElement>, `xs:string` ograniczenie typu prostego przy użyciu klas <xref:System.Xml.Schema.XmlSchemaSimpleType> i <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction>, dodaje aspekt wzorca do właściwości <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> ograniczenia i dodaje ograniczenie do właściwości <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> typu prostego i typu prostego do <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> elementu `PhoneNumber`.

4. Wykonuje iterację dla każdego <xref:System.Xml.Schema.XmlSchemaElement> w kolekcji <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekcji po kompilacji schematu <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>.

5. Jeśli <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> elementu jest `"Customer"`, pobiera typ złożony elementu `Customer` przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaComplexType> i cząstki sekwencji typu złożonego przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaSequence>.

6. Dodaje nowy element `PhoneNumber` do sekwencji zawierającej istniejące `FirstName` i `LastName` elementy przy użyciu kolekcji sekwencji poprzedzającej <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> kompilację ze schematu.

7. Na koniec przetwarza i kompiluje zmodyfikowany obiekt <xref:System.Xml.Schema.XmlSchema> przy użyciu metod <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> klasy <xref:System.Xml.Schema.XmlSchemaSet> i zapisuje je w konsoli programu.

Poniżej znajduje się kompletny przykład kodu.

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

Poniżej przedstawiono zmodyfikowany schemat klienta utworzony w temacie [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="xs:string" />
        <xs:element name="LastName" type="tns:LastNameType" />
        <xs:element name="PhoneNumber">           <xs:simpleType>             <xs:restriction base="xs:string">               <xs:pattern value="\d{3}-\d{3}-\d(4)" />             </xs:restriction>           </xs:simpleType>         </xs:element>
      </xs:sequence>
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /
>
    </xs:complexType>
  </xs:element>
  <xs:simpleType name="LastNameType">
    <xs:restriction base="xs:string">
      <xs:maxLength value="20" />
    </xs:restriction>
  </xs:simpleType>
</xs:schema>
```

### <a name="title-attribute-example"></a>Przykład atrybutu tytułu

Ten drugi przykład kodu dodaje nowy atrybut `Title` do elementu `FirstName` schematu klienta. W pierwszym przykładzie kodu, typ elementu `FirstName` jest `xs:string`. Aby element `FirstName` miał atrybut wraz z zawartością ciągu, jego typ musi być zmieniony na typ złożony z prostym modelem zawartości o rozszerzeniu zawartości.

Przykładowy kod edytuje schemat klienta w poniższych krokach.

1. Dodaje schemat klienta do nowego obiektu <xref:System.Xml.Schema.XmlSchemaSet>, a następnie kompiluje go. Wszystkie ostrzeżenia i błędy walidacji schematu napotkane podczas odczytywania lub kompilowania schematu są obsługiwane przez delegata <xref:System.Xml.Schema.ValidationEventHandler>.

2. Pobiera skompilowany obiekt <xref:System.Xml.Schema.XmlSchema> z <xref:System.Xml.Schema.XmlSchemaSet> przez iterację we właściwości <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>. Ze względu na to, że schemat jest skompilowany, dostępne są właściwości po schemacie kompilacja-sprawdzonych (PSCI).

3. Tworzy nowy typ złożony dla elementu `FirstName` przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaComplexType>.

4. Tworzy nowe proste rozszerzenie zawartości z typem podstawowym `xs:string`przy użyciu klas <xref:System.Xml.Schema.XmlSchemaSimpleContent> i <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension>.

5. Tworzy nowy atrybut `Title` przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaAttribute> z <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> `xs:string` i dodaje atrybut do prostego rozszerzenia zawartości.

6. Ustawia model zawartości prostej zawartości na proste rozszerzenie zawartości oraz model zawartości typu złożonego na zawartość prostą.

7. Dodaje nowy typ złożony do kolekcji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> przedprodukcyjnej kompilacji.

8. Wykonuje iterację dla każdego <xref:System.Xml.Schema.XmlSchemaObject> w kolekcji przedprodukcyjnej kompilacja <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType>.

> [!NOTE]
> Ponieważ element `FirstName` nie jest elementem globalnym w schemacie, nie jest dostępny w kolekcjach <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> i <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>. Przykładowy kod lokalizuje element `FirstName`, najpierw lokalizowanie elementu `Customer`.
>
> Pierwszy przykładowy kod przechodzą przez schemat przy użyciu kolekcji po kompilacji schematu <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>. W tym przykładzie kolekcja <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kompilacji przed schematem jest używana do przechodzenia przez schemat. Chociaż obie kolekcje zapewniają dostęp do elementów globalnych w schemacie, Iterowanie przez kolekcję <xref:System.Xml.Schema.XmlSchema.Items%2A> jest bardziej czasochłonne, ponieważ należy wykonać iterację wszystkich elementów globalnych w schemacie i nie ma żadnych właściwości PSCI. Kolekcje PSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>itd.) zapewniają bezpośredni dostęp do swoich elementów globalnych, atrybutów i typów oraz ich właściwości PSCI.

1. Jeśli <xref:System.Xml.Schema.XmlSchemaObject> jest elementem, którego <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> jest `"Customer"`, pobiera typ złożony elementu `Customer` przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaComplexType> i cząstki sekwencji typu złożonego przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaSequence>.

2. Wykonuje iterację dla każdego <xref:System.Xml.Schema.XmlSchemaParticle> w kolekcji przedprodukcyjnej kompilacja <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType>.

3. Jeśli <xref:System.Xml.Schema.XmlSchemaParticle> jest elementem, który jest <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> jest `"FirstName"`, ustawia <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> elementu `FirstName` do nowego `FirstName` typu złożonego.

4. Na koniec przetwarza i kompiluje zmodyfikowany obiekt <xref:System.Xml.Schema.XmlSchema> przy użyciu metod <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> klasy <xref:System.Xml.Schema.XmlSchemaSet> i zapisuje je w konsoli programu.

Poniżej znajduje się kompletny przykład kodu.

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

Poniżej przedstawiono zmodyfikowany schemat klienta utworzony w temacie [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .

```xml
<?xml version="1.0" encoding=" utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />
        <xs:element name="LastName" type="tns:LastNameType" />
      </xs:sequence>
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /
>
    </xs:complexType>
  </xs:element>
  <xs:simpleType name="LastNameType">
    <xs:restriction base="xs:string">
      <xs:maxLength value="20" />
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a>Zobacz także

- [Model SOM (XML Schema Object Model) ― omówienie](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Odczytywanie i zapisywanie schematów XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Przechodzenie schematów XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Uwzględnianie lub importowanie schematów XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Zestaw informacji po kompilacji schematu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
