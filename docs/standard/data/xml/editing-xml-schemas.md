---
title: Edytowanie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 119c4c13c90aeca8c14d2725d927c38be32212a6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308721"
---
# <a name="editing-xml-schemas"></a>Edytowanie schematów XML
Edytowanie schematu XML jest jednym z najważniejszych funkcji z modelu obiektów schematu (SOM). Wszystkie właściwości wstępnej schema kompilacji SOM można zmienić istniejące wartości w schemacie XML. Schemat XML można następnie ponownie skompilowana, aby odzwierciedlić zmiany.  
  
 Pierwszym krokiem podczas edytowania schematu ładowany SOM jest przechodzenie przez schemat. Należy zapoznać się z przechodzenie przez schemat przy użyciu interfejsu API SOM, przed przystąpieniem do edytowania schematu. Należy także zapoznać się z właściwości przed i po schema kompilacji po-schema-kompilacja-zestaw informacji (PSCI).  
  
## <a name="editing-an-xml-schema"></a>Edytowanie schematu XML  
 W tej sekcji znajdują się dwa przykłady kodu, z których oba Edytowanie schematu klientów utworzonych w [tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu. Pierwszy przykład kodu dodaje nowy `PhoneNumber` elementu `Customer` elementu i drugi przykład kodu dodaje nowy `Title` atrybutu `FirstName` elementu. W pierwszym przykładzie użyto również odniesienie-schema-kompilacja <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji, co oznacza, że jest przechodzenie przez schemat klienta podczas drugi przykład kodu używa wstępnie przygotowany-schema-kompilacja <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekcji.  
  
### <a name="phonenumber-element-example"></a>Przykład elementu numer telefonu  
 Ten pierwszy przykład kodu dodaje nowy `PhoneNumber` elementu `Customer` element schematu klienta. Przykład kodu umożliwia edytowanie schematu klienta w poniższych krokach.  
  
1. Dodaje nowy schemat klienta <xref:System.Xml.Schema.XmlSchemaSet> obiektu, a następnie kompiluje go. Wszelkie ostrzeżenia sprawdzania poprawności schematu i błędów napotkanych odczytywania lub skompilowanie schematu są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegować.  
  
2. Pobiera skompilowana klasa <xref:System.Xml.Schema.XmlSchema> obiektu z <xref:System.Xml.Schema.XmlSchemaSet> przez Iterowanie <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości. Ponieważ schemat jest kompilowany, właściwości (PSCI) po-Schema-kompilacja-zestaw informacji są dostępne.  
  
3. Tworzy `PhoneNumber` elementu za pomocą <xref:System.Xml.Schema.XmlSchemaElement> klasy `xs:string` za pomocą ograniczeń typu prostego <xref:System.Xml.Schema.XmlSchemaSimpleType> i <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> klasy, dodaje zestaw reguł wzorca w celu <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> właściwości ograniczenia i dodaje ograniczenie do <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> właściwość typu prostego i typu prostego do <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> z `PhoneNumber` elementu.  
  
4. Iteruje przez każdy <xref:System.Xml.Schema.XmlSchemaElement> w <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekcji po-schema-kompilacja <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji.  
  
5. Jeśli <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> elementu jest `"Customer"`, pobiera typ złożony `Customer` elementu za pomocą <xref:System.Xml.Schema.XmlSchemaComplexType> klasy i cząstki sequence użycia typu złożonego <xref:System.Xml.Schema.XmlSchemaSequence> klasy.  
  
6. Dodaje nowy `PhoneNumber` element sekwencji zawierające istniejący `FirstName` i `LastName` elementów za pomocą wstępnie przygotowany-schema-kompilacja <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> kolekcji sekwencji.  
  
7. Na koniec ponownego przetwarzania i kompiluje zmodyfikowanego <xref:System.Xml.Schema.XmlSchema> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisuje go w konsoli.  
  
 Oto przykład kompletny kod.  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 Poniżej przedstawiono schematu klienta zmodyfikowane, utworzone w [tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu.  
  
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
  
### <a name="title-attribute-example"></a>Przykład atrybut tytułu  
 Ten drugi przykład kodu dodaje nowy `Title` atrybutu `FirstName` element schematu klienta. W pierwszym przykładzie kodu typu `FirstName` element jest `xs:string`. Aby uzyskać `FirstName` elemencie muszą mieć atrybut wraz z ciągu zawartości, można zmienić jego typu, typ złożony z prostym rozszerzeniu zawartości modelu zawartości.  
  
 Przykład kodu umożliwia edytowanie schematu klienta w poniższych krokach.  
  
1. Dodaje nowy schemat klienta <xref:System.Xml.Schema.XmlSchemaSet> obiektu, a następnie kompiluje go. Wszelkie ostrzeżenia sprawdzania poprawności schematu i błędów napotkanych odczytywania lub skompilowanie schematu są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegować.  
  
2. Pobiera skompilowana klasa <xref:System.Xml.Schema.XmlSchema> obiektu z <xref:System.Xml.Schema.XmlSchemaSet> przez Iterowanie <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości. Ponieważ schemat jest kompilowany, właściwości (PSCI) po-Schema-kompilacja-zestaw informacji są dostępne.  
  
3. Tworzy nowy typ złożony dla `FirstName` elementu za pomocą <xref:System.Xml.Schema.XmlSchemaComplexType> klasy.  
  
4. Tworzy nowy prostym rozszerzeniu zawartości, z podstawowym typem `xs:string`przy użyciu <xref:System.Xml.Schema.XmlSchemaSimpleContent> i <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> klasy.  
  
5. Tworzy nowy `Title` atrybutu przy użyciu <xref:System.Xml.Schema.XmlSchemaAttribute> klasy, za pomocą <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> z `xs:string` i dodaje atrybut do prostym rozszerzeniu zawartości.  
  
6. Ustawia model zawartości prostej zawartości prostym rozszerzeniu zawartości i model zawartości typu złożonego do prostej zawartości.  
  
7. Dodaje nowy typ złożony do wstępnej-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekcji.  
  
8. Iteruje przez każdy <xref:System.Xml.Schema.XmlSchemaObject> w wstępnej-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekcji.  
  
> [!NOTE]
>  Ponieważ `FirstName` element nie jest element globalny w schemacie, nie jest dostępna w <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> lub <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji. Przykładowy kod wyszukuje `FirstName` element po pierwszym lokalizowanie `Customer` elementu.  
>   
>  W pierwszym przykładzie kodu przesunięta schematu za pomocą odniesienie-schema-kompilacja <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji. W tym przykładzie, wstępnie przygotowany-schema-kompilacja <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekcji umożliwia przechodzenie przez schemat. Gdy obie kolekcje zapewniają dostęp do globalnego elementów w schemacie, iteracja <xref:System.Xml.Schema.XmlSchema.Items%2A> kolekcji jest bardziej czasochłonne, ponieważ należy do iteracji wszystkich elementów globalny w schemacie, a nie ma żadnych właściwości PSCI. Kolekcje PSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>i tak dalej) zapewnia bezpośredni dostęp do globalnego elementów, atrybutów i typy oraz ich właściwości PSCI.  
  
1. Jeśli <xref:System.Xml.Schema.XmlSchemaObject> jest elementem, którego <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> jest `"Customer"`, pobiera typ złożony `Customer` elementu za pomocą <xref:System.Xml.Schema.XmlSchemaComplexType> klasy i cząstki sequence użycia typu złożonego <xref:System.Xml.Schema.XmlSchemaSequence> klasy.  
  
2. Iteruje przez każdy <xref:System.Xml.Schema.XmlSchemaParticle> w wstępnej-schema-kompilacji <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> kolekcji.  
  
3. Jeśli <xref:System.Xml.Schema.XmlSchemaParticle> jest elementem, który firmy <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> jest `"FirstName"`, ustawia <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> z `FirstName` elementu do nowego `FirstName` typu złożonego.  
  
4. Na koniec ponownego przetwarzania i kompiluje zmodyfikowanego <xref:System.Xml.Schema.XmlSchema> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisuje go w konsoli.  
  
 Oto przykład kompletny kod.  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 Poniżej przedstawiono schematu klienta zmodyfikowane, utworzone w [tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu.  
  
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
