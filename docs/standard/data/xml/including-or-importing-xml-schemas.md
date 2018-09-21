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
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540164"
---
# <a name="including-or-importing-xml-schemas"></a><span data-ttu-id="72d2f-102">Uwzględnianie lub Importowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="72d2f-102">Including or Importing XML Schemas</span></span>
<span data-ttu-id="72d2f-103">Schemat XML może zawierać `<xs:import />`, `<xs:include />`, i `<xs:redefine />` elementów.</span><span class="sxs-lookup"><span data-stu-id="72d2f-103">An XML schema may contain `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements.</span></span> <span data-ttu-id="72d2f-104">Te elementy schematu odnoszą się do innych schematów XML, które mogą służyć jako uzupełnienie strukturę schematu, który zawiera lub importuje je.</span><span class="sxs-lookup"><span data-stu-id="72d2f-104">These schema elements refer to other XML schemas that can be used to supplement the structure of the schema that includes or imports them.</span></span> <span data-ttu-id="72d2f-105"><xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> i <xref:System.Xml.Schema.XmlSchemaRedefine> klas, mapy do tych elementów w schemacie obiektu Model (model SOM) interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="72d2f-105">The <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, map to these elements in the Schema Object Model (SOM) API.</span></span>  
  
## <a name="including-or-importing-an-xml-schema"></a><span data-ttu-id="72d2f-106">Uwzględnianie lub importowanie schematu XML</span><span class="sxs-lookup"><span data-stu-id="72d2f-106">Including or Importing an XML Schema</span></span>  
 <span data-ttu-id="72d2f-107">Poniższy kod stanowi uzupełnienie schematu klientów utworzonych w [tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu przy użyciu schematów adresów.</span><span class="sxs-lookup"><span data-stu-id="72d2f-107">The following code example supplements the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic with the address schema.</span></span> <span data-ttu-id="72d2f-108">Uzupełniające schematu klienta ze schematem adres udostępnia typy adresów w schemacie klienta.</span><span class="sxs-lookup"><span data-stu-id="72d2f-108">Supplementing the customer schema with the address schema makes address types available in the customer schema.</span></span>  
  
 <span data-ttu-id="72d2f-109">Schemat adresu należy włączyć za pomocą `<xs:include />` lub `<xs:import />` elementy, aby używać składników schematu adresacji jako — jest lub przy użyciu `<xs:redefine />` element, aby zmodyfikować dowolne jego składniki do własnych potrzebę schematu klienta.</span><span class="sxs-lookup"><span data-stu-id="72d2f-109">The address schema can be incorporated using either `<xs:include />` or `<xs:import />` elements to use the components of the address schema as-is, or using an `<xs:redefine />` element to modify any of its components to suit the need of the customer schema.</span></span> <span data-ttu-id="72d2f-110">Ponieważ schematu adresacji `targetNamespace` , różni się od schematu klienta `<xs:import />` element i w związku z tym semantyki importu jest używany.</span><span class="sxs-lookup"><span data-stu-id="72d2f-110">Because the address schema has a `targetNamespace` that is different from that of the customer schema, the `<xs:import />` element and therefore import semantics is used.</span></span>  
  
 <span data-ttu-id="72d2f-111">Przykładowy kod zawiera schemat adresu w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="72d2f-111">The code example includes the address schema in the following steps.</span></span>  
  
1.  <span data-ttu-id="72d2f-112">Dodaje nowy schemat klienta i schemat adresu <xref:System.Xml.Schema.XmlSchemaSet> obiektu, a następnie kompiluje je.</span><span class="sxs-lookup"><span data-stu-id="72d2f-112">Adds the customer schema and the address schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles them.</span></span> <span data-ttu-id="72d2f-113">Wszelkie ostrzeżenia sprawdzania poprawności schematu i błędów napotkanych odczytywania lub kompilowania schematów są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegować.</span><span class="sxs-lookup"><span data-stu-id="72d2f-113">Any schema validation warnings and errors encountered reading or compiling the schemas are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2.  <span data-ttu-id="72d2f-114">Pobiera skompilowana klasa <xref:System.Xml.Schema.XmlSchema> obiektów dla klienta i adresem schematów z <xref:System.Xml.Schema.XmlSchemaSet> przez Iterowanie <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="72d2f-114">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> objects for both the customer and address schemas from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="72d2f-115">Ponieważ schematy są kompilowane, właściwości (PSCI) po-Schema-kompilacja-zestaw informacji są dostępne.</span><span class="sxs-lookup"><span data-stu-id="72d2f-115">Because the schemas are compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3.  <span data-ttu-id="72d2f-116">Tworzy <xref:System.Xml.Schema.XmlSchemaImport> obiektu, zestawy <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> ustawia właściwość importu obszaru nazw schematu adresacji <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> właściwość importu <xref:System.Xml.Schema.XmlSchema> obiektu schematu adresacji i dodaje importu <xref:System.Xml.Schema.XmlSchema.Includes%2A> Właściwość schematu klienta.</span><span class="sxs-lookup"><span data-stu-id="72d2f-116">Creates an <xref:System.Xml.Schema.XmlSchemaImport> object, sets the <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> property of the import to the namespace of the address schema, sets the <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> property of the import to the <xref:System.Xml.Schema.XmlSchema> object of the address schema, and adds the import to the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span>  
  
4.  <span data-ttu-id="72d2f-117">Ponownego przetwarzania oraz kompiluje zmodyfikowanego <xref:System.Xml.Schema.XmlSchema> obiektu przy użyciu schematu klienta <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisuje go w konsoli.</span><span class="sxs-lookup"><span data-stu-id="72d2f-117">Reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object of the customer schema using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
5.  <span data-ttu-id="72d2f-118">Na koniec rekursywnie zapisuje schematy zaimportowane do schematu klienta za pomocą konsoli <xref:System.Xml.Schema.XmlSchema.Includes%2A> właściwości schematu klienta.</span><span class="sxs-lookup"><span data-stu-id="72d2f-118">Finally, recursively writes all of the schemas imported into the customer schema to the console using the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span> <span data-ttu-id="72d2f-119"><xref:System.Xml.Schema.XmlSchema.Includes%2A> Właściwości zapewnia dostęp do wszystkich zawiera, imports lub ponownie zdefiniowanych wystąpień dodane do schematu.</span><span class="sxs-lookup"><span data-stu-id="72d2f-119">The <xref:System.Xml.Schema.XmlSchema.Includes%2A> property provides access to all the includes, imports, or redefines added to a schema.</span></span>  
  
 <span data-ttu-id="72d2f-120">Poniżej znajduje się pełny przykład kodu i schematy klientów i adresu, wyświetlony w konsoli.</span><span class="sxs-lookup"><span data-stu-id="72d2f-120">The following is the complete code example and the customer and address schemas written to the console.</span></span>  
  
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
  
 <span data-ttu-id="72d2f-121">Aby uzyskać więcej informacji na temat `<xs:import />`, `<xs:include />`, i `<xs:redefine />` elementy i <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> i <xref:System.Xml.Schema.XmlSchemaRedefine> klas, zobacz [schematu XML W3C](https://www.w3.org/XML/Schema) i <xref:System.Xml.Schema?displayProperty=nameWithType> Dokumentacja referencyjna klasy w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="72d2f-121">For more information about the `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements and the <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, see the [W3C XML Schema](https://www.w3.org/XML/Schema) and the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace class reference documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d2f-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72d2f-122">See also</span></span>

- [<span data-ttu-id="72d2f-123">Model SOM (XML Schema Object Model) ― omówienie</span><span class="sxs-lookup"><span data-stu-id="72d2f-123">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
- [<span data-ttu-id="72d2f-124">Odczytywanie i zapisywanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="72d2f-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
- [<span data-ttu-id="72d2f-125">Tworzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="72d2f-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
- [<span data-ttu-id="72d2f-126">Przechodzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="72d2f-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
- [<span data-ttu-id="72d2f-127">Edytowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="72d2f-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
- [<span data-ttu-id="72d2f-128">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="72d2f-128">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
