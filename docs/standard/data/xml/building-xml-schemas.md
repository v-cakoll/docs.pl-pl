---
title: Tworzenie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: c921331b00fe137d4ad52d62951e8c161768dfae
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711145"
---
# <a name="building-xml-schemas"></a><span data-ttu-id="70e3d-102">Tworzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="70e3d-102">Building XML Schemas</span></span>
<span data-ttu-id="70e3d-103">Klasy w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw są mapowane na struktury zdefiniowane w zaleceniu schematu XML organizacja World Wide Web Consortium (W3C) i mogą być używane do kompilowania schematów XML w pamięci.</span><span class="sxs-lookup"><span data-stu-id="70e3d-103">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="70e3d-104">Kompilowanie schematu XML</span><span class="sxs-lookup"><span data-stu-id="70e3d-104">Building an XML Schema</span></span>  
 <span data-ttu-id="70e3d-105">W poniższym przykładzie kodu model API SOM jest używany do kompilowania schematu XML klienta w pamięci.</span><span class="sxs-lookup"><span data-stu-id="70e3d-105">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="70e3d-106">Tworzenie elementu i atrybutów</span><span class="sxs-lookup"><span data-stu-id="70e3d-106">Creating Element and Attributes</span></span>  
 <span data-ttu-id="70e3d-107">Przykłady kodu kompilują schemat klienta od dołu, tworzą elementy podrzędne, atrybuty i odpowiadające im typy najpierw, a następnie elementy najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="70e3d-107">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="70e3d-108">W poniższym przykładzie kodu elementy `FirstName` i `LastName`, a także atrybut `CustomerId` schematu klienta są tworzone przy użyciu klas <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAttribute> modelu SOM.</span><span class="sxs-lookup"><span data-stu-id="70e3d-108">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="70e3d-109">Niezależnie od właściwości <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> klas <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAttribute>, które odpowiadają atrybutowi "name" elementów `<xs:element />` i `<xs:attribute />` w schemacie XML, wszystkie inne atrybuty dozwolone przez schemat (`defaultValue`, `fixedValue`, `form`itd.) mają odpowiednie właściwości w klasach <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAttribute>.</span><span class="sxs-lookup"><span data-stu-id="70e3d-109">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="70e3d-110">Tworzenie typów schematów</span><span class="sxs-lookup"><span data-stu-id="70e3d-110">Creating Schema Types</span></span>  
 <span data-ttu-id="70e3d-111">Zawartość elementów i atrybutów jest definiowana przez ich typy.</span><span class="sxs-lookup"><span data-stu-id="70e3d-111">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="70e3d-112">Aby utworzyć elementy i atrybuty, których typy są jednym z wbudowanych typów schematu, właściwość <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> klas <xref:System.Xml.Schema.XmlSchemaElement> lub <xref:System.Xml.Schema.XmlSchemaAttribute> jest ustawiana z odpowiadającą kwalifikowaną nazwą typu wbudowanego przy użyciu klasy <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="70e3d-112">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="70e3d-113">Aby utworzyć typ zdefiniowany przez użytkownika dla elementów i atrybutów, tworzony jest nowy typ prosty lub złożony przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaSimpleType> lub <xref:System.Xml.Schema.XmlSchemaComplexType>.</span><span class="sxs-lookup"><span data-stu-id="70e3d-113">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70e3d-114">Aby utworzyć nienazwane typy proste lub złożone, które są anonimowymi elementami podrzędnymi elementu lub atrybutu (tylko proste typy są stosowane dla atrybutów), należy ustawić właściwość <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> klas <xref:System.Xml.Schema.XmlSchemaElement> lub <xref:System.Xml.Schema.XmlSchemaAttribute> na typ prosty lub złożony bez nazwy, a nie Właściwość <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> klas <xref:System.Xml.Schema.XmlSchemaElement> lub <xref:System.Xml.Schema.XmlSchemaAttribute>.</span><span class="sxs-lookup"><span data-stu-id="70e3d-114">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="70e3d-115">Schematy XML zezwalają na wyprowadzanie anonimowych i nazwanych typów prostych przez ograniczenie z innych typów prostych (wbudowane lub zdefiniowane przez użytkownika) lub skonstruowane jako lista lub związek innych typów prostych.</span><span class="sxs-lookup"><span data-stu-id="70e3d-115">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="70e3d-116">Klasa <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> jest używana do tworzenia typu prostego przez ograniczenie wbudowanego typu `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="70e3d-116">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="70e3d-117">Można również użyć klas <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> lub <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> do tworzenia typów list lub Unii.</span><span class="sxs-lookup"><span data-stu-id="70e3d-117">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="70e3d-118">Właściwość <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> określa, czy jest to proste ograniczenie typu, lista czy Unia.</span><span class="sxs-lookup"><span data-stu-id="70e3d-118">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="70e3d-119">W poniższym przykładzie kodu typ elementu `FirstName` jest typem wbudowanym `xs:string`, typ elementu `LastName` jest nazwanym typem prostym, który jest ograniczeniem typu wbudowanego `xs:string`, z wartością aspektu `MaxLength` równą 20, a typ atrybutu `CustomerId` jest typem wbudowanym `xs:positiveInteger`.</span><span class="sxs-lookup"><span data-stu-id="70e3d-119">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="70e3d-120">Element `Customer` to anonimowy typ złożony, którego cząstka jest sekwencją `FirstName` i `LastName` elementów, których atrybuty zawierają atrybut `CustomerId`.</span><span class="sxs-lookup"><span data-stu-id="70e3d-120">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70e3d-121">Można również użyć klas <xref:System.Xml.Schema.XmlSchemaChoice> lub <xref:System.Xml.Schema.XmlSchemaAll> jako cząstki typu złożonego do replikowania `<xs:choice />` lub semantyki `<xs:all />`.</span><span class="sxs-lookup"><span data-stu-id="70e3d-121">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="70e3d-122">Tworzenie i kompilowanie schematów</span><span class="sxs-lookup"><span data-stu-id="70e3d-122">Creating and Compiling Schemas</span></span>  
 <span data-ttu-id="70e3d-123">W tym momencie elementy podrzędne i atrybuty, odpowiadające im typy i element najwyższego poziomu `Customer` zostały utworzone w pamięci za pomocą interfejsu API modelu SOM.</span><span class="sxs-lookup"><span data-stu-id="70e3d-123">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="70e3d-124">W poniższym przykładzie kodu element schematu jest tworzony przy użyciu klasy <xref:System.Xml.Schema.XmlSchema>, elementy najwyższego poziomu i typy są dodawane do niego przy użyciu właściwości <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> i kompletny schemat jest kompilowany przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaSet> i zapisywana w konsoli.</span><span class="sxs-lookup"><span data-stu-id="70e3d-124">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="70e3d-125">Metoda <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> sprawdza poprawność schematu klienta względem reguł dla schematu XML i umożliwia dostęp do właściwości kompilacji po schemacie.</span><span class="sxs-lookup"><span data-stu-id="70e3d-125">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70e3d-126">Wszystkie właściwości kompilacji po schemacie w interfejsie API modelu SOM różnią się w zależności od posprawdzonych.</span><span class="sxs-lookup"><span data-stu-id="70e3d-126">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="70e3d-127"><xref:System.Xml.Schema.ValidationEventHandler> dodana do <xref:System.Xml.Schema.XmlSchemaSet> jest delegatem, który wywołuje metodę wywołania zwrotnego `ValidationCallback` do obsługi ostrzeżeń i błędów walidacji schematu.</span><span class="sxs-lookup"><span data-stu-id="70e3d-127">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="70e3d-128">Poniżej znajduje się kompletny przykład kodu i schemat klienta zapisany w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="70e3d-128">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
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
```  
  
## <a name="see-also"></a><span data-ttu-id="70e3d-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70e3d-129">See also</span></span>

- [<span data-ttu-id="70e3d-130">Model SOM (XML Schema Object Model) ― omówienie</span><span class="sxs-lookup"><span data-stu-id="70e3d-130">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="70e3d-131">Odczytywanie i zapisywanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="70e3d-131">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="70e3d-132">Przechodzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="70e3d-132">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="70e3d-133">Edytowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="70e3d-133">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [<span data-ttu-id="70e3d-134">Uwzględnianie lub importowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="70e3d-134">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="70e3d-135">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="70e3d-135">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="70e3d-136">Zestaw informacji po kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="70e3d-136">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
