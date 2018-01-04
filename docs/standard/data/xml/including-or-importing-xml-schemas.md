---
title: W tym lub importowanie schematy XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ce86969bb9dc4a8db4359afa333d1f003c767895
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="including-or-importing-xml-schemas"></a>W tym lub importowanie schematy XML
Schemat XML mogą zawierać `<xs:import />`, `<xs:include />`, i `<xs:redefine />` elementy. Te elementy schematu odwoływać się do innych schematów XML, które może służyć do uzupełnienia struktury schematu, która obejmuje lub importowane. <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> i <xref:System.Xml.Schema.XmlSchemaRedefine> klasy, mapy do tych elementów w schematu obiektu modelu (SOM) interfejsu API.  
  
## <a name="including-or-importing-an-xml-schema"></a>W tym lub importowanie schematu XML  
 Poniższy przykład kodu uzupełniają schematu klienta utworzone w [schematów XML budynku](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu ze schematem adresu. Uzupełniające schematu klienta ze schematem adresu udostępnia typy adresów w schemacie klienta.  
  
 Schemat adresu należy włączyć za pomocą `<xs:include />` lub `<xs:import />` elementy, aby użyć składników schematu adresu jako — jest lub przy użyciu `<xs:redefine />` element, aby zmodyfikować dowolne jego składniki do własnych potrzeb schematu klienta. Ponieważ schemat adresu `targetNamespace` różni się od elementu schematu klienta `<xs:import />` element i w związku z tym semantyki importu jest używany.  
  
 Przykładowy kod zawiera schemat adresu w kolejnych krokach.  
  
1.  Dodaje nowy schemat klienta i schemat adresu <xref:System.Xml.Schema.XmlSchemaSet> obiekt, a następnie kompiluje je. Wszelkie ostrzeżenia dotyczące sprawdzania poprawności schematu i błędów napotkanych odczytu lub kompilowania schematów są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegowanie.  
  
2.  Pobiera skompilowanych <xref:System.Xml.Schema.XmlSchema> obiektów dla schematów zarówno klient, jak i adresu z <xref:System.Xml.Schema.XmlSchemaSet> przez Iterowanie po <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości. Ponieważ schematy są kompilowane, po-Schema-kompilacji-typu Infoset właściwości (PSCI) są dostępne.  
  
3.  Tworzy <xref:System.Xml.Schema.XmlSchemaImport> obiektu, zestawy <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> ustawia właściwość importu do przestrzeni nazw schematu adres <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> właściwości importu do <xref:System.Xml.Schema.XmlSchema> obiektu schematu adres i dodaje importu <xref:System.Xml.Schema.XmlSchema.Includes%2A> Właściwość schematu klienta.  
  
4.  Przetwarza ponownie i kompiluje zmodyfikowanych <xref:System.Xml.Schema.XmlSchema> obiektu przy użyciu schematu klienta <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisuje go w konsoli.  
  
5.  Na koniec rekursywnie zapisuje schematy zaimportowane do schematu klienta przy użyciu konsoli <xref:System.Xml.Schema.XmlSchema.Includes%2A> właściwości schematu klienta. <xref:System.Xml.Schema.XmlSchema.Includes%2A> Właściwość zapewnia dostęp do wszystkich obejmuje importów lub ponownych definicji dodane do schematu.  
  
 Poniżej znajduje się pełny przykład kodu i schematów klienta i adresem wyświetlony w konsoli.  
  
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
  
 Aby uzyskać więcej informacji na temat `<xs:import />`, `<xs:include />`, i `<xs:redefine />` elementów i <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> i <xref:System.Xml.Schema.XmlSchemaRedefine> klas, zobacz [schematu W3C XML](http://go.microsoft.com/fwlink/?LinkId=45242) i <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeń nazw klasy dokumentacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Model SOM (XML Schema Object Model) ― omówienie](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [Odczytywanie i zapisywanie schematów XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [Przechodzenie schematów XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [Edytowanie schematów XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
