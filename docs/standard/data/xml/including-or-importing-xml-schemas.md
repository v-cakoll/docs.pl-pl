---
title: Uwzględnianie lub Importowanie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b26ebfa327d849f75b1ac5295b66600aeb377e1e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082620"
---
# <a name="including-or-importing-xml-schemas"></a>Uwzględnianie lub Importowanie schematów XML
Schemat XML może zawierać `<xs:import />`, `<xs:include />`, i `<xs:redefine />` elementów. Te elementy schematu odnoszą się do innych schematów XML, które mogą służyć jako uzupełnienie strukturę schematu, który zawiera lub importuje je. <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> i <xref:System.Xml.Schema.XmlSchemaRedefine> klas, mapy do tych elementów w schemacie obiektu Model (model SOM) interfejsu API.  
  
## <a name="including-or-importing-an-xml-schema"></a>Uwzględnianie lub importowanie schematu XML  
 Poniższy kod stanowi uzupełnienie schematu klientów utworzonych w [tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu przy użyciu schematów adresów. Uzupełniające schematu klienta ze schematem adres udostępnia typy adresów w schemacie klienta.  
  
 Schemat adresu należy włączyć za pomocą `<xs:include />` lub `<xs:import />` elementy, aby używać składników schematu adresacji jako — jest lub przy użyciu `<xs:redefine />` element, aby zmodyfikować dowolne jego składniki do własnych potrzebę schematu klienta. Ponieważ schematu adresacji `targetNamespace` , różni się od schematu klienta `<xs:import />` element i w związku z tym semantyki importu jest używany.  
  
 Przykładowy kod zawiera schemat adresu w poniższych krokach.  
  
1.  Dodaje nowy schemat klienta i schemat adresu <xref:System.Xml.Schema.XmlSchemaSet> obiektu, a następnie kompiluje je. Wszelkie ostrzeżenia sprawdzania poprawności schematu i błędów napotkanych odczytywania lub kompilowania schematów są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegować.  
  
2.  Pobiera skompilowana klasa <xref:System.Xml.Schema.XmlSchema> obiektów dla klienta i adresem schematów z <xref:System.Xml.Schema.XmlSchemaSet> przez Iterowanie <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości. Ponieważ schematy są kompilowane, właściwości (PSCI) po-Schema-kompilacja-zestaw informacji są dostępne.  
  
3.  Tworzy <xref:System.Xml.Schema.XmlSchemaImport> obiektu, zestawy <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> ustawia właściwość importu obszaru nazw schematu adresacji <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> właściwość importu <xref:System.Xml.Schema.XmlSchema> obiektu schematu adresacji i dodaje importu <xref:System.Xml.Schema.XmlSchema.Includes%2A> Właściwość schematu klienta.  
  
4.  Ponownego przetwarzania oraz kompiluje zmodyfikowanego <xref:System.Xml.Schema.XmlSchema> obiektu przy użyciu schematu klienta <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisuje go w konsoli.  
  
5.  Na koniec rekursywnie zapisuje schematy zaimportowane do schematu klienta za pomocą konsoli <xref:System.Xml.Schema.XmlSchema.Includes%2A> właściwości schematu klienta. <xref:System.Xml.Schema.XmlSchema.Includes%2A> Właściwości zapewnia dostęp do wszystkich zawiera, imports lub ponownie zdefiniowanych wystąpień dodane do schematu.  
  
 Poniżej znajduje się pełny przykład kodu i schematy klientów i adresu, wyświetlony w konsoli.  
  
 [!code-cpp[XmlSchemaImportExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaImportExample/CPP/XmlSchemaImportExample.cpp#1)]
 [!code-csharp[XmlSchemaImportExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaImportExample/CS/XmlSchemaImportExample.cs#1)]
 [!code-vb[XmlSchemaImportExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaImportExample/VB/XmlSchemaImportExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://www.example.com/IPO" />  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
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
</xs:schema>  
<schema targetNamespace="http://www.example.com/IPO" xmlns="http://www.w3.org/2001/XMLSchema" xmlns:ipo="http://www.example.com/IPO">  
  <annotation>  
    <documentation xml:lang="en">  
      Addresses for International Purchase order schema  
      Copyright 2000 Example.com. All rights reserved.  
    </documentation>  
  </annotation>  
  <complexType name="Address">  
    <sequence>  
      <element name="name"   type="string"/>  
      <element name="street" type="string"/>  
      <element name="city"   type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="USAddress">  
    <complexContent>  
      <extension base="ipo:Address">  
        <sequence>  
          <element name="state" type="ipo:USState"/>  
          <element name="zip"   type="positiveInteger"/>  
        </sequence>  
      </extension>  
    </complexContent>  
  </complexType>  
  <!-- other Address derivations for more countries or regions -->  
  <simpleType name="USState">  
    <restriction base="string">  
      <enumeration value="AK"/>  
      <enumeration value="AL"/>  
      <enumeration value="AR"/>  
      <!-- and so on ... -->  
    </restriction>  
  </simpleType>  
</schema>  
```  
  
 Aby uzyskać więcej informacji na temat `<xs:import />`, `<xs:include />`, i `<xs:redefine />` elementy i <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> i <xref:System.Xml.Schema.XmlSchemaRedefine> klas, zobacz [schematu XML W3C](https://www.w3.org/XML/Schema) i <xref:System.Xml.Schema?displayProperty=nameWithType> Dokumentacja referencyjna klasy w przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Model SOM (XML Schema Object Model) ― omówienie](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
- [Odczytywanie i zapisywanie schematów XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
- [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
- [Przechodzenie schematów XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
- [Edytowanie schematów XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
