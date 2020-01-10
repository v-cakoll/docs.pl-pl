---
title: Edytowanie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
ms.openlocfilehash: d7d9f8e0d4ec2f343b50e68e942bf94e93576f25
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710950"
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="c554c-102">Edytowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="c554c-102">Editing XML Schemas</span></span>

<span data-ttu-id="c554c-103">Edytowanie schematu XML jest jedną z najważniejszych funkcji modelu obiektów schematu (SOM).</span><span class="sxs-lookup"><span data-stu-id="c554c-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="c554c-104">Wszystkie właściwości kompilacji przed schematem modelu SOM mogą służyć do zmiany istniejących wartości w schemacie XML.</span><span class="sxs-lookup"><span data-stu-id="c554c-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="c554c-105">Schemat XML można następnie ponownie skompilować, aby odzwierciedlić zmiany.</span><span class="sxs-lookup"><span data-stu-id="c554c-105">The XML schema can then be recompiled to reflect the changes.</span></span>

<span data-ttu-id="c554c-106">Pierwszym krokiem podczas edytowania schematu załadowanego do modelu SOM jest przechodzenie przez schemat.</span><span class="sxs-lookup"><span data-stu-id="c554c-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="c554c-107">Przed podjęciem próby edycji schematu należy zapoznać się z przechodzeniem schematu przy użyciu interfejsu API modelu SOM.</span><span class="sxs-lookup"><span data-stu-id="c554c-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="c554c-108">Należy również zapoznać się z właściwościami prekompilowania i po schemacie kompilacji sprawdzonych (PSCI).</span><span class="sxs-lookup"><span data-stu-id="c554c-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>

## <a name="editing-an-xml-schema"></a><span data-ttu-id="c554c-109">Edytowanie schematu XML</span><span class="sxs-lookup"><span data-stu-id="c554c-109">Editing an XML Schema</span></span>

<span data-ttu-id="c554c-110">W tej sekcji przedstawiono dwa przykłady kodu, z których każda edytuje schemat klienta utworzony w temacie [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .</span><span class="sxs-lookup"><span data-stu-id="c554c-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span> <span data-ttu-id="c554c-111">Pierwszy przykład kodu dodaje nowy element `PhoneNumber` do elementu `Customer`, a drugi przykład kodu dodaje nowy atrybut `Title` do elementu `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="c554c-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="c554c-112">Pierwszy przykład używa również kolekcji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kompilacji po schemacie jako metody przechodzenia przez schemat klienta, podczas gdy drugi przykład kodu używa kolekcji przed<xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType>owej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c554c-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

### <a name="phonenumber-element-example"></a><span data-ttu-id="c554c-113">Przykład elementu nr telefonu</span><span class="sxs-lookup"><span data-stu-id="c554c-113">PhoneNumber Element Example</span></span>

<span data-ttu-id="c554c-114">Ten pierwszy przykład kodu dodaje nowy element `PhoneNumber` do elementu `Customer` schematu klienta.</span><span class="sxs-lookup"><span data-stu-id="c554c-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="c554c-115">Przykładowy kod edytuje schemat klienta w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="c554c-115">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="c554c-116">Dodaje schemat klienta do nowego obiektu <xref:System.Xml.Schema.XmlSchemaSet>, a następnie kompiluje go.</span><span class="sxs-lookup"><span data-stu-id="c554c-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="c554c-117">Wszystkie ostrzeżenia i błędy walidacji schematu napotkane podczas odczytywania lub kompilowania schematu są obsługiwane przez delegata <xref:System.Xml.Schema.ValidationEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="c554c-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="c554c-118">Pobiera skompilowany obiekt <xref:System.Xml.Schema.XmlSchema> z <xref:System.Xml.Schema.XmlSchemaSet> przez iterację we właściwości <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="c554c-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="c554c-119">Ze względu na to, że schemat jest skompilowany, dostępne są właściwości po schemacie kompilacja-sprawdzonych (PSCI).</span><span class="sxs-lookup"><span data-stu-id="c554c-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="c554c-120">Tworzy element `PhoneNumber` przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaElement>, `xs:string` ograniczenie typu prostego przy użyciu klas <xref:System.Xml.Schema.XmlSchemaSimpleType> i <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction>, dodaje aspekt wzorca do właściwości <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> ograniczenia i dodaje ograniczenie do właściwości <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> typu prostego i typu prostego do <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> elementu `PhoneNumber`.</span><span class="sxs-lookup"><span data-stu-id="c554c-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>

4. <span data-ttu-id="c554c-121">Wykonuje iterację dla każdego <xref:System.Xml.Schema.XmlSchemaElement> w kolekcji <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekcji po kompilacji schematu <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c554c-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>

5. <span data-ttu-id="c554c-122">Jeśli <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> elementu jest `"Customer"`, pobiera typ złożony elementu `Customer` przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaComplexType> i cząstki sekwencji typu złożonego przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaSequence>.</span><span class="sxs-lookup"><span data-stu-id="c554c-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

6. <span data-ttu-id="c554c-123">Dodaje nowy element `PhoneNumber` do sekwencji zawierającej istniejące `FirstName` i `LastName` elementy przy użyciu kolekcji sekwencji poprzedzającej <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> kompilację ze schematu.</span><span class="sxs-lookup"><span data-stu-id="c554c-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>

7. <span data-ttu-id="c554c-124">Na koniec przetwarza i kompiluje zmodyfikowany obiekt <xref:System.Xml.Schema.XmlSchema> przy użyciu metod <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> klasy <xref:System.Xml.Schema.XmlSchemaSet> i zapisuje je w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="c554c-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="c554c-125">Poniżej znajduje się kompletny przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="c554c-125">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

<span data-ttu-id="c554c-126">Poniżej przedstawiono zmodyfikowany schemat klienta utworzony w temacie [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .</span><span class="sxs-lookup"><span data-stu-id="c554c-126">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>

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

### <a name="title-attribute-example"></a><span data-ttu-id="c554c-127">Przykład atrybutu tytułu</span><span class="sxs-lookup"><span data-stu-id="c554c-127">Title Attribute Example</span></span>

<span data-ttu-id="c554c-128">Ten drugi przykład kodu dodaje nowy atrybut `Title` do elementu `FirstName` schematu klienta.</span><span class="sxs-lookup"><span data-stu-id="c554c-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="c554c-129">W pierwszym przykładzie kodu, typ elementu `FirstName` jest `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="c554c-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="c554c-130">Aby element `FirstName` miał atrybut wraz z zawartością ciągu, jego typ musi być zmieniony na typ złożony z prostym modelem zawartości o rozszerzeniu zawartości.</span><span class="sxs-lookup"><span data-stu-id="c554c-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>

<span data-ttu-id="c554c-131">Przykładowy kod edytuje schemat klienta w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="c554c-131">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="c554c-132">Dodaje schemat klienta do nowego obiektu <xref:System.Xml.Schema.XmlSchemaSet>, a następnie kompiluje go.</span><span class="sxs-lookup"><span data-stu-id="c554c-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="c554c-133">Wszystkie ostrzeżenia i błędy walidacji schematu napotkane podczas odczytywania lub kompilowania schematu są obsługiwane przez delegata <xref:System.Xml.Schema.ValidationEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="c554c-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="c554c-134">Pobiera skompilowany obiekt <xref:System.Xml.Schema.XmlSchema> z <xref:System.Xml.Schema.XmlSchemaSet> przez iterację we właściwości <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="c554c-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="c554c-135">Ze względu na to, że schemat jest skompilowany, dostępne są właściwości po schemacie kompilacja-sprawdzonych (PSCI).</span><span class="sxs-lookup"><span data-stu-id="c554c-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="c554c-136">Tworzy nowy typ złożony dla elementu `FirstName` przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaComplexType>.</span><span class="sxs-lookup"><span data-stu-id="c554c-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>

4. <span data-ttu-id="c554c-137">Tworzy nowe proste rozszerzenie zawartości z typem podstawowym `xs:string`przy użyciu klas <xref:System.Xml.Schema.XmlSchemaSimpleContent> i <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension>.</span><span class="sxs-lookup"><span data-stu-id="c554c-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>

5. <span data-ttu-id="c554c-138">Tworzy nowy atrybut `Title` przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaAttribute> z <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> `xs:string` i dodaje atrybut do prostego rozszerzenia zawartości.</span><span class="sxs-lookup"><span data-stu-id="c554c-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>

6. <span data-ttu-id="c554c-139">Ustawia model zawartości prostej zawartości na proste rozszerzenie zawartości oraz model zawartości typu złożonego na zawartość prostą.</span><span class="sxs-lookup"><span data-stu-id="c554c-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>

7. <span data-ttu-id="c554c-140">Dodaje nowy typ złożony do kolekcji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> przedprodukcyjnej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c554c-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

8. <span data-ttu-id="c554c-141">Wykonuje iterację dla każdego <xref:System.Xml.Schema.XmlSchemaObject> w kolekcji przedprodukcyjnej kompilacja <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c554c-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

> [!NOTE]
> <span data-ttu-id="c554c-142">Ponieważ element `FirstName` nie jest elementem globalnym w schemacie, nie jest dostępny w kolekcjach <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> i <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c554c-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="c554c-143">Przykładowy kod lokalizuje element `FirstName`, najpierw lokalizowanie elementu `Customer`.</span><span class="sxs-lookup"><span data-stu-id="c554c-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>
>
> <span data-ttu-id="c554c-144">Pierwszy przykładowy kod przechodzą przez schemat przy użyciu kolekcji po kompilacji schematu <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c554c-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="c554c-145">W tym przykładzie kolekcja <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kompilacji przed schematem jest używana do przechodzenia przez schemat.</span><span class="sxs-lookup"><span data-stu-id="c554c-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="c554c-146">Chociaż obie kolekcje zapewniają dostęp do elementów globalnych w schemacie, Iterowanie przez kolekcję <xref:System.Xml.Schema.XmlSchema.Items%2A> jest bardziej czasochłonne, ponieważ należy wykonać iterację wszystkich elementów globalnych w schemacie i nie ma żadnych właściwości PSCI.</span><span class="sxs-lookup"><span data-stu-id="c554c-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="c554c-147">Kolekcje PSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>itd.) zapewniają bezpośredni dostęp do swoich elementów globalnych, atrybutów i typów oraz ich właściwości PSCI.</span><span class="sxs-lookup"><span data-stu-id="c554c-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>

1. <span data-ttu-id="c554c-148">Jeśli <xref:System.Xml.Schema.XmlSchemaObject> jest elementem, którego <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> jest `"Customer"`, pobiera typ złożony elementu `Customer` przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaComplexType> i cząstki sekwencji typu złożonego przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaSequence>.</span><span class="sxs-lookup"><span data-stu-id="c554c-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

2. <span data-ttu-id="c554c-149">Wykonuje iterację dla każdego <xref:System.Xml.Schema.XmlSchemaParticle> w kolekcji przedprodukcyjnej kompilacja <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c554c-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="c554c-150">Jeśli <xref:System.Xml.Schema.XmlSchemaParticle> jest elementem, który jest <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> jest `"FirstName"`, ustawia <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> elementu `FirstName` do nowego `FirstName` typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="c554c-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>

4. <span data-ttu-id="c554c-151">Na koniec przetwarza i kompiluje zmodyfikowany obiekt <xref:System.Xml.Schema.XmlSchema> przy użyciu metod <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> klasy <xref:System.Xml.Schema.XmlSchemaSet> i zapisuje je w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="c554c-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="c554c-152">Poniżej znajduje się kompletny przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="c554c-152">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

<span data-ttu-id="c554c-153">Poniżej przedstawiono zmodyfikowany schemat klienta utworzony w temacie [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .</span><span class="sxs-lookup"><span data-stu-id="c554c-153">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c554c-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c554c-154">See also</span></span>

- [<span data-ttu-id="c554c-155">Model SOM (XML Schema Object Model) ― omówienie</span><span class="sxs-lookup"><span data-stu-id="c554c-155">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="c554c-156">Odczytywanie i zapisywanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="c554c-156">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="c554c-157">Tworzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="c554c-157">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="c554c-158">Przechodzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="c554c-158">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="c554c-159">Uwzględnianie lub importowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="c554c-159">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="c554c-160">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="c554c-160">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="c554c-161">Zestaw informacji po kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="c554c-161">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
