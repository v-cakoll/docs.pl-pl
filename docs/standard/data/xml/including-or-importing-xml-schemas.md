---
title: Uwzględnianie lub importowanie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
ms.openlocfilehash: f6c2829d45db147c81592c00710f04168b40679e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287704"
---
# <a name="including-or-importing-xml-schemas"></a><span data-ttu-id="7fe1d-102">Uwzględnianie lub importowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="7fe1d-102">Including or Importing XML Schemas</span></span>
<span data-ttu-id="7fe1d-103">Schemat XML może zawierać `<xs:import />` elementy, `<xs:include />` , i `<xs:redefine />` .</span><span class="sxs-lookup"><span data-stu-id="7fe1d-103">An XML schema may contain `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements.</span></span> <span data-ttu-id="7fe1d-104">Te elementy schematu odwołują się do innych schematów XML, które mogą służyć do uzupełniania struktury schematu, który zawiera lub importuje.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-104">These schema elements refer to other XML schemas that can be used to supplement the structure of the schema that includes or imports them.</span></span> <span data-ttu-id="7fe1d-105"><xref:System.Xml.Schema.XmlSchemaImport> <xref:System.Xml.Schema.XmlSchemaInclude> <xref:System.Xml.Schema.XmlSchemaRedefine> Klasy i mapują do tych elementów w interfejsie API modelu obiektów schematu (SOM).</span><span class="sxs-lookup"><span data-stu-id="7fe1d-105">The <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, map to these elements in the Schema Object Model (SOM) API.</span></span>  
  
## <a name="including-or-importing-an-xml-schema"></a><span data-ttu-id="7fe1d-106">Dołączanie lub importowanie schematu XML</span><span class="sxs-lookup"><span data-stu-id="7fe1d-106">Including or Importing an XML Schema</span></span>  
 <span data-ttu-id="7fe1d-107">Poniższy przykład kodu uzupełnia schemat klienta utworzony w temacie [Tworzenie schematów XML](building-xml-schemas.md) ze schematem adresu.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-107">The following code example supplements the customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic with the address schema.</span></span> <span data-ttu-id="7fe1d-108">Uzupełnienie schematu klienta przy użyciu schematu adresu sprawia, że typy adresów są dostępne w schemacie klienta.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-108">Supplementing the customer schema with the address schema makes address types available in the customer schema.</span></span>  
  
 <span data-ttu-id="7fe1d-109">Schemat adresów może być dołączany przy użyciu albo `<xs:include />` `<xs:import />` elementów, aby użyć składników schematu adresu jako-lub za pomocą elementu, aby `<xs:redefine />` zmodyfikować dowolny składnik, aby odpowiadał potrzebom schematu klienta.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-109">The address schema can be incorporated using either `<xs:include />` or `<xs:import />` elements to use the components of the address schema as-is, or using an `<xs:redefine />` element to modify any of its components to suit the need of the customer schema.</span></span> <span data-ttu-id="7fe1d-110">Ze względu na to, `targetNamespace` że schemat adresu różni się od schematu klienta, `<xs:import />` jest używany element i dlatego semantyka importu.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-110">Because the address schema has a `targetNamespace` that is different from that of the customer schema, the `<xs:import />` element and therefore import semantics is used.</span></span>  
  
 <span data-ttu-id="7fe1d-111">Przykład kodu zawiera schemat adresu w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-111">The code example includes the address schema in the following steps.</span></span>  
  
1. <span data-ttu-id="7fe1d-112">Dodaje schemat klienta i schemat adresu do nowego <xref:System.Xml.Schema.XmlSchemaSet> obiektu, a następnie kompiluje je.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-112">Adds the customer schema and the address schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles them.</span></span> <span data-ttu-id="7fe1d-113">Wszystkie ostrzeżenia i błędy walidacji schematu napotkane podczas odczytywania lub kompilowania schematów są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegata.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-113">Any schema validation warnings and errors encountered reading or compiling the schemas are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="7fe1d-114">Pobiera skompilowane <xref:System.Xml.Schema.XmlSchema> obiekty dla obu schematów klienta i adresu z obiektu <xref:System.Xml.Schema.XmlSchemaSet> przez iterację nad <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwością.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-114">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> objects for both the customer and address schemas from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="7fe1d-115">Ze względu na to, że schematy są kompilowane, właściwości po schemacie kompilacja-sprawdzonych (PSCI) są dostępne.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-115">Because the schemas are compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="7fe1d-116">Tworzy <xref:System.Xml.Schema.XmlSchemaImport> obiekt, ustawia <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> Właściwość importu do przestrzeni nazw schematu adresu, ustawia <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> Właściwość importu do <xref:System.Xml.Schema.XmlSchema> obiektu schematu adresu i dodaje import do <xref:System.Xml.Schema.XmlSchema.Includes%2A> właściwości schematu klienta...</span><span class="sxs-lookup"><span data-stu-id="7fe1d-116">Creates an <xref:System.Xml.Schema.XmlSchemaImport> object, sets the <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> property of the import to the namespace of the address schema, sets the <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> property of the import to the <xref:System.Xml.Schema.XmlSchema> object of the address schema, and adds the import to the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span>  
  
4. <span data-ttu-id="7fe1d-117">Przetwarza i kompiluje zmodyfikowany <xref:System.Xml.Schema.XmlSchema> obiekt schematu klienta przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metod i klasy i <xref:System.Xml.Schema.XmlSchemaSet> zapisuje je w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-117">Reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object of the customer schema using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
5. <span data-ttu-id="7fe1d-118">Na koniec cyklicznie zapisuje wszystkie schematy zaimportowane do schematu klienta w konsoli programu przy użyciu <xref:System.Xml.Schema.XmlSchema.Includes%2A> właściwości schematu klienta.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-118">Finally, recursively writes all of the schemas imported into the customer schema to the console using the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span> <span data-ttu-id="7fe1d-119"><xref:System.Xml.Schema.XmlSchema.Includes%2A>Właściwość umożliwia dostęp do wszystkich dołączanych, importowanych lub ponownie zdefiniowanych w schemacie.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-119">The <xref:System.Xml.Schema.XmlSchema.Includes%2A> property provides access to all the includes, imports, or redefines added to a schema.</span></span>  
  
 <span data-ttu-id="7fe1d-120">Poniżej znajduje się kompletny przykład kodu oraz schemat klienta i adresu zapisany w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-120">The following is the complete code example and the customer and address schemas written to the console.</span></span>  
  
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
  
 <span data-ttu-id="7fe1d-121">Aby uzyskać więcej informacji na `<xs:import />` temat `<xs:include />` elementów,, i `<xs:redefine />` i <xref:System.Xml.Schema.XmlSchemaImport> <xref:System.Xml.Schema.XmlSchemaInclude> klasy, <xref:System.Xml.Schema.XmlSchemaRedefine> Zobacz [schemat XML W3C](https://www.w3.org/XML/Schema) i <xref:System.Xml.Schema?displayProperty=nameWithType> Dokumentacja klasy Namespace.</span><span class="sxs-lookup"><span data-stu-id="7fe1d-121">For more information about the `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements and the <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, see the [W3C XML Schema](https://www.w3.org/XML/Schema) and the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace class reference documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe1d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fe1d-122">See also</span></span>

- [<span data-ttu-id="7fe1d-123">Model SOM (XML Schema Object Model) ― omówienie</span><span class="sxs-lookup"><span data-stu-id="7fe1d-123">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="7fe1d-124">Odczytywanie i zapisywanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="7fe1d-124">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="7fe1d-125">Tworzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="7fe1d-125">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="7fe1d-126">Przechodzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="7fe1d-126">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="7fe1d-127">Edytowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="7fe1d-127">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="7fe1d-128">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="7fe1d-128">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
