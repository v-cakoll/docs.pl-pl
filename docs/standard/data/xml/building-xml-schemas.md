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
# <a name="building-xml-schemas"></a><span data-ttu-id="73611-102">Tworzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="73611-102">Building XML Schemas</span></span>
<span data-ttu-id="73611-103">Klasy w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw są mapowane na struktury zdefiniowane w organizacja World Wide Web Consortium (W3C) zalecenia schematu XML i mogą być używane do kompilowania schematów XML w pamięci.</span><span class="sxs-lookup"><span data-stu-id="73611-103">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="73611-104">Kompilowanie schematu XML</span><span class="sxs-lookup"><span data-stu-id="73611-104">Building an XML Schema</span></span>  
 <span data-ttu-id="73611-105">W poniższym przykładzie kodu model API SOM jest używany do kompilowania schematu XML klienta w pamięci.</span><span class="sxs-lookup"><span data-stu-id="73611-105">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="73611-106">Tworzenie elementu i atrybutów</span><span class="sxs-lookup"><span data-stu-id="73611-106">Creating Element and Attributes</span></span>  
 <span data-ttu-id="73611-107">Przykłady kodu kompilują schemat klienta od dołu, tworzą elementy podrzędne, atrybuty i odpowiadające im typy najpierw, a następnie elementy najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="73611-107">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="73611-108">W poniższym przykładzie kodu `FirstName` elementy i, a `LastName` także `CustomerId` atrybut schematu klienta są tworzone przy użyciu klas <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAttribute> modelu Som.</span><span class="sxs-lookup"><span data-stu-id="73611-108">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="73611-109"><xref:System.Xml.Schema.XmlSchemaElement.Name%2A> Oprócz <xref:System.Xml.Schema.XmlSchemaElement> właściwości i <xref:System.Xml.Schema.XmlSchemaAttribute> klasy, które odpowiadają atrybutowi "name" elementów `<xs:element />` i `<xs:attribute />` w schemacie XML, wszystkie inne atrybuty dozwolone przez schemat (`defaultValue`, `fixedValue`, `form`, i tak dalej) mają odpowiednie właściwości w klasach <xref:System.Xml.Schema.XmlSchemaElement> i. <xref:System.Xml.Schema.XmlSchemaAttribute></span><span class="sxs-lookup"><span data-stu-id="73611-109">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="73611-110">Tworzenie typów schematów</span><span class="sxs-lookup"><span data-stu-id="73611-110">Creating Schema Types</span></span>  
 <span data-ttu-id="73611-111">Zawartość elementów i atrybutów jest definiowana przez ich typy.</span><span class="sxs-lookup"><span data-stu-id="73611-111">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="73611-112">Aby utworzyć elementy i atrybuty, których typy są jednym z wbudowanych typów schematu <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> , właściwość <xref:System.Xml.Schema.XmlSchemaElement> lub <xref:System.Xml.Schema.XmlSchemaAttribute> klasy są ustawiane za pomocą odpowiedniej kwalifikowanej nazwy typu wbudowanego przy użyciu <xref:System.Xml.XmlQualifiedName> klasy.</span><span class="sxs-lookup"><span data-stu-id="73611-112">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="73611-113">Aby utworzyć typ zdefiniowany przez użytkownika dla elementów i atrybutów, nowy typ prosty lub złożony jest tworzony przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaSimpleType> or. <xref:System.Xml.Schema.XmlSchemaComplexType></span><span class="sxs-lookup"><span data-stu-id="73611-113">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73611-114">Aby utworzyć nienazwane proste lub złożone typy, które są anonimowymi elementami podrzędnymi elementu lub atrybutu (tylko proste typy są stosowane dla atrybutów) <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> , należy ustawić <xref:System.Xml.Schema.XmlSchemaElement> Właściwość <xref:System.Xml.Schema.XmlSchemaAttribute> lub klasy na typ prosty lub złożony, zamiast <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> właściwości <xref:System.Xml.Schema.XmlSchemaElement> lub <xref:System.Xml.Schema.XmlSchemaAttribute> klas.</span><span class="sxs-lookup"><span data-stu-id="73611-114">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="73611-115">Schematy XML zezwalają na wyprowadzanie anonimowych i nazwanych typów prostych przez ograniczenie z innych typów prostych (wbudowane lub zdefiniowane przez użytkownika) lub skonstruowane jako lista lub związek innych typów prostych.</span><span class="sxs-lookup"><span data-stu-id="73611-115">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="73611-116"><xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Klasa jest używana do tworzenia typu prostego przez ograniczenie wbudowanego `xs:string` typu.</span><span class="sxs-lookup"><span data-stu-id="73611-116">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="73611-117">Można również użyć klas <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> lub <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> do tworzenia typów list lub Unii.</span><span class="sxs-lookup"><span data-stu-id="73611-117">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="73611-118"><xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Właściwość określa, czy jest to proste ograniczenie typu, lista lub Unia.</span><span class="sxs-lookup"><span data-stu-id="73611-118">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="73611-119">W poniższym przykładzie `FirstName` kodu typ elementu jest typem wbudowanym `xs:string`, typ `LastName` elementu jest nazwanym typem prostym, który jest ograniczeniem typu `xs:string`wbudowanego, z wartością `MaxLength` aspektu 20, a typ `CustomerId` atrybutu jest typem `xs:positiveInteger`wbudowanym.</span><span class="sxs-lookup"><span data-stu-id="73611-119">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="73611-120">`Customer` Element to anonimowy typ złożony, którego cząstka jest sekwencją elementów `FirstName` i `LastName` i których atrybuty zawiera `CustomerId` atrybut.</span><span class="sxs-lookup"><span data-stu-id="73611-120">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73611-121">Można również użyć <xref:System.Xml.Schema.XmlSchemaChoice> klas lub <xref:System.Xml.Schema.XmlSchemaAll> jako cząsteczek typu złożonego do replikowania `<xs:choice />` lub `<xs:all />` semantyki.</span><span class="sxs-lookup"><span data-stu-id="73611-121">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="73611-122">Tworzenie i kompilowanie schematów</span><span class="sxs-lookup"><span data-stu-id="73611-122">Creating and Compiling Schemas</span></span>  
 <span data-ttu-id="73611-123">W tym momencie elementy podrzędne i atrybuty, ich odpowiednie typy i element najwyższego poziomu `Customer` zostały utworzone w pamięci za pomocą interfejsu API modelu Som.</span><span class="sxs-lookup"><span data-stu-id="73611-123">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="73611-124">W poniższym przykładzie kodu element schematu jest tworzony przy użyciu <xref:System.Xml.Schema.XmlSchema> klasy, elementy najwyższego poziomu i typy są dodawane do niego przy użyciu <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> właściwości, a kompletny schemat jest kompilowany przy użyciu <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisywana w konsoli.</span><span class="sxs-lookup"><span data-stu-id="73611-124">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="73611-125"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Metoda sprawdza poprawność schematu klienta względem reguł schematu XML i umożliwia dostęp do właściwości kompilacji po schemacie.</span><span class="sxs-lookup"><span data-stu-id="73611-125">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73611-126">Wszystkie właściwości kompilacji po schemacie w interfejsie API modelu SOM różnią się w zależności od posprawdzonych.</span><span class="sxs-lookup"><span data-stu-id="73611-126">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="73611-127"><xref:System.Xml.Schema.ValidationEventHandler> Dodanie do obiektu <xref:System.Xml.Schema.XmlSchemaSet> jest delegatem, który wywołuje metodę `ValidationCallback` wywołania zwrotnego w celu obsługi ostrzeżeń i błędów walidacji schematu.</span><span class="sxs-lookup"><span data-stu-id="73611-127">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="73611-128">Poniżej znajduje się kompletny przykład kodu i schemat klienta zapisany w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="73611-128">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73611-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73611-129">See also</span></span>

- [<span data-ttu-id="73611-130">Model SOM (XML Schema Object Model) ― omówienie</span><span class="sxs-lookup"><span data-stu-id="73611-130">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="73611-131">Odczytywanie i zapisywanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="73611-131">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="73611-132">Przechodzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="73611-132">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="73611-133">Edytowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="73611-133">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [<span data-ttu-id="73611-134">Uwzględnianie lub importowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="73611-134">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="73611-135">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="73611-135">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="73611-136">Zestaw informacji po kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="73611-136">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
