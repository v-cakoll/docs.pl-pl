---
title: Edytowanie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
ms.openlocfilehash: b309c390ede3afc38122188337fa0dc3336e3ad5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292062"
---
# <a name="editing-xml-schemas"></a>Edytowanie schematów XML

Edytowanie schematu XML jest jedną z najważniejszych funkcji modelu obiektów schematu (SOM). Wszystkie właściwości kompilacji przed schematem modelu SOM mogą służyć do zmiany istniejących wartości w schemacie XML. Schemat XML można następnie ponownie skompilować, aby odzwierciedlić zmiany.

Pierwszym krokiem podczas edytowania schematu załadowanego do modelu SOM jest przechodzenie przez schemat. Przed podjęciem próby edycji schematu należy zapoznać się z przechodzeniem schematu przy użyciu interfejsu API modelu SOM. Należy również zapoznać się z właściwościami prekompilowania i po schemacie kompilacji sprawdzonych (PSCI).

## <a name="editing-an-xml-schema"></a>Edytowanie schematu XML

W tej sekcji przedstawiono dwa przykłady kodu, z których każda edytuje schemat klienta utworzony w temacie [Tworzenie schematów XML](building-xml-schemas.md) . Pierwszy przykład kodu dodaje nowy `PhoneNumber` element do `Customer` elementu, a drugi przykład kodu dodaje nowy `Title` atrybut do `FirstName` elementu. Pierwszy przykład używa również kolekcji po schemacie kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> jako metody przechodzenia przez schemat klienta, podczas gdy drugi przykład kodu używa kolekcji przedprodukcyjnej kompilacji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .

### <a name="phonenumber-element-example"></a>Przykład elementu nr telefonu

Ten pierwszy przykład kodu dodaje nowy `PhoneNumber` element do `Customer` elementu schematu klienta. Przykładowy kod edytuje schemat klienta w poniższych krokach.

1. Dodaje schemat klienta do nowego <xref:System.Xml.Schema.XmlSchemaSet> obiektu, a następnie kompiluje go. Wszystkie ostrzeżenia i błędy walidacji schematu napotkane podczas odczytywania lub kompilowania schematu są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegata.

2. Pobiera skompilowany <xref:System.Xml.Schema.XmlSchema> obiekt z obiektu <xref:System.Xml.Schema.XmlSchemaSet> przez iterację we <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości. Ze względu na to, że schemat jest skompilowany, dostępne są właściwości po schemacie kompilacja-sprawdzonych (PSCI).

3. Tworzy `PhoneNumber` element przy użyciu <xref:System.Xml.Schema.XmlSchemaElement> klasy, `xs:string` ograniczenie typu prostego przy użyciu <xref:System.Xml.Schema.XmlSchemaSimpleType> <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> klas i, dodaje zestaw reguł wzorców do <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> właściwości ograniczenia i dodaje ograniczenie do <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> właściwości typu prostego i typu prostego do <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> `PhoneNumber` elementu.

4. Wykonuje iterację na każdym <xref:System.Xml.Schema.XmlSchemaElement> z <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekcji kolekcji po schemacie kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> .

5. Jeśli <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> element jest `"Customer"` , pobiera typ złożony `Customer` elementu przy użyciu <xref:System.Xml.Schema.XmlSchemaComplexType> klasy i cząstki sekwencji typu złożonego przy użyciu <xref:System.Xml.Schema.XmlSchemaSequence> klasy.

6. Dodaje nowy `PhoneNumber` element do sekwencji zawierającej istniejące `FirstName` `LastName` elementy i przy użyciu kolekcji przedprodukcyjnej kompilacja <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> sekwencji.

7. Na koniec przetwarza i kompiluje zmodyfikowany <xref:System.Xml.Schema.XmlSchema> Obiekt przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metod i <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisuje je w konsoli programu.

Poniżej znajduje się kompletny przykład kodu.

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

Poniżej przedstawiono zmodyfikowany schemat klienta utworzony w temacie [Tworzenie schematów XML](building-xml-schemas.md) .

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
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />
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

Ten drugi przykład kodu dodaje nowy `Title` atrybut do `FirstName` elementu schematu klienta. W pierwszym przykładzie kodu, typ `FirstName` elementu to `xs:string` . Aby `FirstName` element miał atrybut wraz z zawartością ciągu, jego typ musi być zmieniony na typ złożony z prostym modelem zawartości o rozszerzeniu zawartości.

Przykładowy kod edytuje schemat klienta w poniższych krokach.

1. Dodaje schemat klienta do nowego <xref:System.Xml.Schema.XmlSchemaSet> obiektu, a następnie kompiluje go. Wszystkie ostrzeżenia i błędy walidacji schematu napotkane podczas odczytywania lub kompilowania schematu są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegata.

2. Pobiera skompilowany <xref:System.Xml.Schema.XmlSchema> obiekt z obiektu <xref:System.Xml.Schema.XmlSchemaSet> przez iterację we <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości. Ze względu na to, że schemat jest skompilowany, dostępne są właściwości po schemacie kompilacja-sprawdzonych (PSCI).

3. Tworzy nowy typ złożony dla `FirstName` elementu przy użyciu <xref:System.Xml.Schema.XmlSchemaComplexType> klasy.

4. Tworzy nowe proste rozszerzenie zawartości z typem podstawowym `xs:string` , korzystając z <xref:System.Xml.Schema.XmlSchemaSimpleContent> <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> klas i.

5. Tworzy nowy `Title` atrybut przy użyciu <xref:System.Xml.Schema.XmlSchemaAttribute> klasy, z <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> `xs:string` i dodaje atrybut do prostego rozszerzenia zawartości.

6. Ustawia model zawartości prostej zawartości na proste rozszerzenie zawartości oraz model zawartości typu złożonego na zawartość prostą.

7. Dodaje nowy typ złożony do kolekcji pre-Schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .

8. Wykonuje iterację <xref:System.Xml.Schema.XmlSchemaObject> dla każdego w kolekcji przedprodukcyjnej kompilacji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .

> [!NOTE]
> Ponieważ `FirstName` element nie jest elementem globalnym w schemacie, nie jest dostępny w <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcjach ani. Przykładowy kod lokalizuje `FirstName` element przez pierwsze lokalizowanie `Customer` elementu.
>
> Pierwszy przykładowy kod przechodzą przez schemat przy użyciu kolekcji po schemacie kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> . W tym przykładzie kolekcja pre-Schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> jest używana do przechodzenia przez schemat. Chociaż obie kolekcje zapewniają dostęp do elementów globalnych w schemacie, Iterowanie przez <xref:System.Xml.Schema.XmlSchema.Items%2A> kolekcję jest bardziej czasochłonne, ponieważ należy wykonać iterację wszystkich elementów globalnych w schemacie i nie ma żadnych właściwości PSCI. Kolekcje PSCI ( <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> ,,, itd <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType> <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType> .) zapewniają bezpośredni dostęp do swoich elementów globalnych, atrybutów i typów oraz ich właściwości PSCI.

1. Jeśli <xref:System.Xml.Schema.XmlSchemaObject> jest elementem, którego <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> jest `"Customer"` , pobiera typ złożony `Customer` elementu przy użyciu <xref:System.Xml.Schema.XmlSchemaComplexType> klasy i cząstki sekwencji typu złożonego przy użyciu <xref:System.Xml.Schema.XmlSchemaSequence> klasy.

2. Wykonuje iterację <xref:System.Xml.Schema.XmlSchemaParticle> dla każdego w kolekcji przedprodukcyjnej kompilacji <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> .

3. Jeśli <xref:System.Xml.Schema.XmlSchemaParticle> jest elementem, to <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> jest `"FirstName"` , ustawia <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> `FirstName` element na nowy `FirstName` typ złożony.

4. Na koniec przetwarza i kompiluje zmodyfikowany <xref:System.Xml.Schema.XmlSchema> Obiekt przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metod i <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisuje je w konsoli programu.

Poniżej znajduje się kompletny przykład kodu.

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

Poniżej przedstawiono zmodyfikowany schemat klienta utworzony w temacie [Tworzenie schematów XML](building-xml-schemas.md) .

```xml
<?xml version="1.0" encoding=" utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />
        <xs:element name="LastName" type="tns:LastNameType" />
      </xs:sequence>
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />
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

- [Model SOM (XML Schema Object Model) ― omówienie](xml-schema-object-model-overview.md)
- [Odczytywanie i zapisywanie schematów XML](reading-and-writing-xml-schemas.md)
- [Tworzenie schematów XML](building-xml-schemas.md)
- [Przechodzenie schematów XML](traversing-xml-schemas.md)
- [Uwzględnianie lub importowanie schematów XML](including-or-importing-xml-schemas.md)
- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](xmlschemaset-for-schema-compilation.md)
- [Zestaw informacji po kompilacji schematu](post-schema-compilation-infoset.md)
