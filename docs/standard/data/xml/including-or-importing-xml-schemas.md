---
title: Uwzględnianie lub importowanie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
ms.openlocfilehash: d9a18876d8a5ba3067aa35c617b1e20fce0411f5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710781"
---
# <a name="including-or-importing-xml-schemas"></a>Uwzględnianie lub importowanie schematów XML
Schemat XML może zawierać `<xs:import />`elementy, `<xs:include />`, i `<xs:redefine />` . Te elementy schematu odwołują się do innych schematów XML, które mogą służyć do uzupełniania struktury schematu, który zawiera lub importuje. <xref:System.Xml.Schema.XmlSchemaImport>Klasy <xref:System.Xml.Schema.XmlSchemaInclude> i <xref:System.Xml.Schema.XmlSchemaRedefine> mapują do tych elementów w interfejsie API modelu obiektów schematu (SOM).  
  
## <a name="including-or-importing-an-xml-schema"></a>Dołączanie lub importowanie schematu XML  
 Poniższy przykład kodu uzupełnia schemat klienta utworzony w temacie [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) ze schematem adresu. Uzupełnienie schematu klienta przy użyciu schematu adresu sprawia, że typy adresów są dostępne w schemacie klienta.  
  
 Schemat adresów może być dołączany przy `<xs:include />` użyciu `<xs:import />` albo elementów, aby użyć składników schematu adresu jako-lub za pomocą `<xs:redefine />` elementu, aby zmodyfikować dowolny składnik, aby odpowiadał potrzebom schematu klienta. Ze względu na to, `targetNamespace` że schemat adresu różni się od schematu klienta, jest używany `<xs:import />` element i dlatego semantyka importu.  
  
 Przykład kodu zawiera schemat adresu w poniższych krokach.  
  
1. Dodaje schemat klienta i schemat adresu do nowego <xref:System.Xml.Schema.XmlSchemaSet> obiektu, a następnie kompiluje je. Wszystkie ostrzeżenia i błędy walidacji schematu napotkane podczas odczytywania lub kompilowania schematów <xref:System.Xml.Schema.ValidationEventHandler> są obsługiwane przez delegata.  
  
2. Pobiera skompilowane <xref:System.Xml.Schema.XmlSchema> obiekty dla obu schematów klienta i adresu z obiektu <xref:System.Xml.Schema.XmlSchemaSet> przez iterację nad <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwością. Ze względu na to, że schematy są kompilowane, właściwości po schemacie kompilacja-sprawdzonych (PSCI) są dostępne.  
  
3. <xref:System.Xml.Schema.XmlSchemaImport> Tworzy obiekt <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> , ustawia właściwość importu do przestrzeni nazw schematu adresu, ustawia <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> Właściwość importu do <xref:System.Xml.Schema.XmlSchema> obiektu schematu adresu i dodaje import do <xref:System.Xml.Schema.XmlSchema.Includes%2A> właściwości schematu klienta...  
  
4. Przetwarza <xref:System.Xml.Schema.XmlSchema> i kompiluje zmodyfikowany obiekt schematu klienta przy użyciu metod <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisuje je w konsoli programu.  
  
5. Na koniec cyklicznie zapisuje wszystkie schematy zaimportowane do schematu klienta w konsoli programu przy użyciu <xref:System.Xml.Schema.XmlSchema.Includes%2A> właściwości schematu klienta. <xref:System.Xml.Schema.XmlSchema.Includes%2A> Właściwość umożliwia dostęp do wszystkich dołączanych, importowanych lub ponownie zdefiniowanych w schemacie.  
  
 Poniżej znajduje się kompletny przykład kodu oraz schemat klienta i adresu zapisany w konsoli programu.  
  
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
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
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
  
 Aby uzyskać więcej informacji na `<xs:import />`temat `<xs:include />`elementów, `<xs:redefine />` , i i <xref:System.Xml.Schema.XmlSchemaImport> <xref:System.Xml.Schema.XmlSchemaInclude> <xref:System.Xml.Schema.XmlSchemaRedefine> klasy, zobacz [schemat XML W3C](https://www.w3.org/XML/Schema) i dokumentacja klasy <xref:System.Xml.Schema?displayProperty=nameWithType> Namespace.  
  
## <a name="see-also"></a>Zobacz też

- [Model SOM (XML Schema Object Model) ― omówienie](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Odczytywanie i zapisywanie schematów XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Przechodzenie schematów XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Edytowanie schematów XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
