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
# <a name="including-or-importing-xml-schemas"></a><span data-ttu-id="66f5a-102">Uwzględnianie lub importowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="66f5a-102">Including or Importing XML Schemas</span></span>
<span data-ttu-id="66f5a-103">Schemat XML może zawierać elementy `<xs:import />`, `<xs:include />`i `<xs:redefine />`.</span><span class="sxs-lookup"><span data-stu-id="66f5a-103">An XML schema may contain `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements.</span></span> <span data-ttu-id="66f5a-104">Te elementy schematu odwołują się do innych schematów XML, które mogą służyć do uzupełniania struktury schematu, który zawiera lub importuje.</span><span class="sxs-lookup"><span data-stu-id="66f5a-104">These schema elements refer to other XML schemas that can be used to supplement the structure of the schema that includes or imports them.</span></span> <span data-ttu-id="66f5a-105">Klasy <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> i <xref:System.Xml.Schema.XmlSchemaRedefine> mapują do tych elementów w interfejsie API modelu obiektów schematu (SOM).</span><span class="sxs-lookup"><span data-stu-id="66f5a-105">The <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, map to these elements in the Schema Object Model (SOM) API.</span></span>  
  
## <a name="including-or-importing-an-xml-schema"></a><span data-ttu-id="66f5a-106">Dołączanie lub importowanie schematu XML</span><span class="sxs-lookup"><span data-stu-id="66f5a-106">Including or Importing an XML Schema</span></span>  
 <span data-ttu-id="66f5a-107">Poniższy przykład kodu uzupełnia schemat klienta utworzony w temacie [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) ze schematem adresu.</span><span class="sxs-lookup"><span data-stu-id="66f5a-107">The following code example supplements the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic with the address schema.</span></span> <span data-ttu-id="66f5a-108">Uzupełnienie schematu klienta przy użyciu schematu adresu sprawia, że typy adresów są dostępne w schemacie klienta.</span><span class="sxs-lookup"><span data-stu-id="66f5a-108">Supplementing the customer schema with the address schema makes address types available in the customer schema.</span></span>  
  
 <span data-ttu-id="66f5a-109">Schemat adresów może być dołączany przy użyciu `<xs:include />` lub `<xs:import />` elementów, aby użyć składników schematu adresu jako-is lub użyć elementu `<xs:redefine />` do zmodyfikowania dowolnego z jego składników, aby odpowiadał potrzebom schematu klienta.</span><span class="sxs-lookup"><span data-stu-id="66f5a-109">The address schema can be incorporated using either `<xs:include />` or `<xs:import />` elements to use the components of the address schema as-is, or using an `<xs:redefine />` element to modify any of its components to suit the need of the customer schema.</span></span> <span data-ttu-id="66f5a-110">Ze względu na to, że schemat adresu ma `targetNamespace`, który różni się od schematu klienta, jest używany element `<xs:import />` i dlatego semantyka importu.</span><span class="sxs-lookup"><span data-stu-id="66f5a-110">Because the address schema has a `targetNamespace` that is different from that of the customer schema, the `<xs:import />` element and therefore import semantics is used.</span></span>  
  
 <span data-ttu-id="66f5a-111">Przykład kodu zawiera schemat adresu w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="66f5a-111">The code example includes the address schema in the following steps.</span></span>  
  
1. <span data-ttu-id="66f5a-112">Dodaje schemat klienta i schemat adresu do nowego obiektu <xref:System.Xml.Schema.XmlSchemaSet>, a następnie kompiluje je.</span><span class="sxs-lookup"><span data-stu-id="66f5a-112">Adds the customer schema and the address schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles them.</span></span> <span data-ttu-id="66f5a-113">Wszystkie ostrzeżenia i błędy walidacji schematu napotkane podczas odczytywania lub kompilowania schematów są obsługiwane przez delegata <xref:System.Xml.Schema.ValidationEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="66f5a-113">Any schema validation warnings and errors encountered reading or compiling the schemas are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="66f5a-114">Pobiera skompilowane obiekty <xref:System.Xml.Schema.XmlSchema> zarówno dla schematów klienta, jak i adresów z <xref:System.Xml.Schema.XmlSchemaSet> przez iterację nad właściwością <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="66f5a-114">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> objects for both the customer and address schemas from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="66f5a-115">Ze względu na to, że schematy są kompilowane, właściwości po schemacie kompilacja-sprawdzonych (PSCI) są dostępne.</span><span class="sxs-lookup"><span data-stu-id="66f5a-115">Because the schemas are compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="66f5a-116">Tworzy obiekt <xref:System.Xml.Schema.XmlSchemaImport>, ustawia właściwość <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> importu na przestrzeń nazw schematu adresu, ustawia właściwość <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> importowania na obiekt <xref:System.Xml.Schema.XmlSchema> schematu adresu i dodaje do właściwości <xref:System.Xml.Schema.XmlSchema.Includes%2A> schematu klienta....</span><span class="sxs-lookup"><span data-stu-id="66f5a-116">Creates an <xref:System.Xml.Schema.XmlSchemaImport> object, sets the <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> property of the import to the namespace of the address schema, sets the <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> property of the import to the <xref:System.Xml.Schema.XmlSchema> object of the address schema, and adds the import to the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span>  
  
4. <span data-ttu-id="66f5a-117">Przetwarza i kompiluje zmodyfikowany obiekt <xref:System.Xml.Schema.XmlSchema> schematu klienta przy użyciu metod <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> klasy <xref:System.Xml.Schema.XmlSchemaSet> i zapisuje je w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="66f5a-117">Reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object of the customer schema using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
5. <span data-ttu-id="66f5a-118">Na koniec cyklicznie zapisuje wszystkie schematy zaimportowane do schematu klienta w konsoli programu przy użyciu właściwości <xref:System.Xml.Schema.XmlSchema.Includes%2A> schematu klienta.</span><span class="sxs-lookup"><span data-stu-id="66f5a-118">Finally, recursively writes all of the schemas imported into the customer schema to the console using the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span> <span data-ttu-id="66f5a-119">Właściwość <xref:System.Xml.Schema.XmlSchema.Includes%2A> zapewnia dostęp do wszystkich dołączonych, importowanych lub ponownie zdefiniowanych do schematu.</span><span class="sxs-lookup"><span data-stu-id="66f5a-119">The <xref:System.Xml.Schema.XmlSchema.Includes%2A> property provides access to all the includes, imports, or redefines added to a schema.</span></span>  
  
 <span data-ttu-id="66f5a-120">Poniżej znajduje się kompletny przykład kodu oraz schemat klienta i adresu zapisany w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="66f5a-120">The following is the complete code example and the customer and address schemas written to the console.</span></span>  
  
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
  
 <span data-ttu-id="66f5a-121">Aby uzyskać więcej informacji na temat elementów `<xs:import />`, `<xs:include />`i `<xs:redefine />` oraz klas <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> i <xref:System.Xml.Schema.XmlSchemaRedefine>, zobacz [schemat XML W3C](https://www.w3.org/XML/Schema) i dokumentacja klasy <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="66f5a-121">For more information about the `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements and the <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, see the [W3C XML Schema](https://www.w3.org/XML/Schema) and the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace class reference documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f5a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66f5a-122">See also</span></span>

- [<span data-ttu-id="66f5a-123">Model SOM (XML Schema Object Model) ― omówienie</span><span class="sxs-lookup"><span data-stu-id="66f5a-123">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="66f5a-124">Odczytywanie i zapisywanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="66f5a-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="66f5a-125">Tworzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="66f5a-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="66f5a-126">Przechodzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="66f5a-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="66f5a-127">Edytowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="66f5a-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [<span data-ttu-id="66f5a-128">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="66f5a-128">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
