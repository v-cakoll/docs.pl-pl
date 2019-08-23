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
ms.openlocfilehash: 3d0d67c82e753b044f759b4d1139c5f6b4837b31
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948481"
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="5ff83-102">Edytowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="5ff83-102">Editing XML Schemas</span></span>
<span data-ttu-id="5ff83-103">Edytowanie schematu XML jest jedną z najważniejszych funkcji modelu obiektów schematu (SOM).</span><span class="sxs-lookup"><span data-stu-id="5ff83-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="5ff83-104">Wszystkie właściwości kompilacji przed schematem modelu SOM mogą służyć do zmiany istniejących wartości w schemacie XML.</span><span class="sxs-lookup"><span data-stu-id="5ff83-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="5ff83-105">Schemat XML można następnie ponownie skompilować, aby odzwierciedlić zmiany.</span><span class="sxs-lookup"><span data-stu-id="5ff83-105">The XML schema can then be recompiled to reflect the changes.</span></span>  
  
 <span data-ttu-id="5ff83-106">Pierwszym krokiem podczas edytowania schematu załadowanego do modelu SOM jest przechodzenie przez schemat.</span><span class="sxs-lookup"><span data-stu-id="5ff83-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="5ff83-107">Przed podjęciem próby edycji schematu należy zapoznać się z przechodzeniem schematu przy użyciu interfejsu API modelu SOM.</span><span class="sxs-lookup"><span data-stu-id="5ff83-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="5ff83-108">Należy również zapoznać się z właściwościami prekompilowania i po schemacie kompilacji sprawdzonych (PSCI).</span><span class="sxs-lookup"><span data-stu-id="5ff83-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>  
  
## <a name="editing-an-xml-schema"></a><span data-ttu-id="5ff83-109">Edytowanie schematu XML</span><span class="sxs-lookup"><span data-stu-id="5ff83-109">Editing an XML Schema</span></span>  
 <span data-ttu-id="5ff83-110">W tej sekcji przedstawiono dwa przykłady kodu, z których każda edytuje schemat klienta utworzony w temacie [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .</span><span class="sxs-lookup"><span data-stu-id="5ff83-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span> <span data-ttu-id="5ff83-111">Pierwszy przykład kodu dodaje `PhoneNumber` nowy element `Customer` do elementu, a drugi przykład kodu dodaje nowy `Title` atrybut do `FirstName` elementu.</span><span class="sxs-lookup"><span data-stu-id="5ff83-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="5ff83-112">Pierwszy przykład używa również kolekcji po schemacie kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> jako metody przechodzenia przez schemat klienta, podczas gdy drugi przykład kodu używa kolekcji przedprodukcyjnej kompilacji. <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5ff83-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
### <a name="phonenumber-element-example"></a><span data-ttu-id="5ff83-113">Przykład elementu nr telefonu</span><span class="sxs-lookup"><span data-stu-id="5ff83-113">PhoneNumber Element Example</span></span>  
 <span data-ttu-id="5ff83-114">Ten pierwszy przykład kodu dodaje nowy `PhoneNumber` element `Customer` do elementu schematu klienta.</span><span class="sxs-lookup"><span data-stu-id="5ff83-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="5ff83-115">Przykładowy kod edytuje schemat klienta w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="5ff83-115">The code example edits the customer schema in the following steps.</span></span>  
  
1. <span data-ttu-id="5ff83-116">Dodaje schemat klienta do nowego <xref:System.Xml.Schema.XmlSchemaSet> obiektu, a następnie kompiluje go.</span><span class="sxs-lookup"><span data-stu-id="5ff83-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="5ff83-117">Wszystkie ostrzeżenia i błędy walidacji schematu napotkane podczas odczytywania lub kompilowania schematu <xref:System.Xml.Schema.ValidationEventHandler> są obsługiwane przez delegata.</span><span class="sxs-lookup"><span data-stu-id="5ff83-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="5ff83-118">Pobiera skompilowany <xref:System.Xml.Schema.XmlSchema> obiekt <xref:System.Xml.Schema.XmlSchemaSet> z obiektu przez iterację <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> we właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ff83-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="5ff83-119">Ze względu na to, że schemat jest skompilowany, dostępne są właściwości po schemacie kompilacja-sprawdzonych (PSCI).</span><span class="sxs-lookup"><span data-stu-id="5ff83-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="5ff83-120">`xs:string` <xref:System.Xml.Schema.XmlSchemaSimpleType> <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> Tworzy element przy użyciu klasy,ograniczenietypuprostegoprzyużyciuklasi,dodajezestawregułwzorcówdowłaściwościograniczeniaidodaje<xref:System.Xml.Schema.XmlSchemaElement> `PhoneNumber` ograniczenie do <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> właściwości typu prostego i typu prostego <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> do `PhoneNumber` elementu.</span><span class="sxs-lookup"><span data-stu-id="5ff83-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>  
  
4. <span data-ttu-id="5ff83-121">Wykonuje iterację na <xref:System.Xml.Schema.XmlSchemaElement> każdym <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> z kolekcji kolekcji po schemacie kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5ff83-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>  
  
5. <span data-ttu-id="5ff83-122">`"Customer"` `Customer` <xref:System.Xml.Schema.XmlSchemaComplexType> Jeśli element jest, pobiera typ złożony elementu przy użyciu <xref:System.Xml.Schema.XmlSchemaSequence> klasy i cząstki sekwencji typu złożonego przy użyciu klasy. <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A></span><span class="sxs-lookup"><span data-stu-id="5ff83-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
6. <span data-ttu-id="5ff83-123">Dodaje nowy `PhoneNumber` element do sekwencji zawierającej istniejące `FirstName` elementy i `LastName` przy użyciu kolekcji przedprodukcyjnej kompilacja <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5ff83-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>  
  
7. <span data-ttu-id="5ff83-124">Na koniec przetwarza <xref:System.Xml.Schema.XmlSchema> i kompiluje zmodyfikowany obiekt <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> przy użyciu metod <xref:System.Xml.Schema.XmlSchemaSet> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> klasy i zapisuje je w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="5ff83-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="5ff83-125">Poniżej znajduje się kompletny przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="5ff83-125">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 <span data-ttu-id="5ff83-126">Poniżej przedstawiono zmodyfikowany schemat klienta utworzony w temacie [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .</span><span class="sxs-lookup"><span data-stu-id="5ff83-126">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
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
  
### <a name="title-attribute-example"></a><span data-ttu-id="5ff83-127">Przykład atrybutu tytułu</span><span class="sxs-lookup"><span data-stu-id="5ff83-127">Title Attribute Example</span></span>  
 <span data-ttu-id="5ff83-128">Ten drugi przykład kodu dodaje nowy `Title` atrybut `FirstName` do elementu schematu klienta.</span><span class="sxs-lookup"><span data-stu-id="5ff83-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="5ff83-129">W pierwszym przykładzie kodu, typ `FirstName` elementu to. `xs:string`</span><span class="sxs-lookup"><span data-stu-id="5ff83-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="5ff83-130">`FirstName` Aby element miał atrybut wraz z zawartością ciągu, jego typ musi być zmieniony na typ złożony z prostym modelem zawartości o rozszerzeniu zawartości.</span><span class="sxs-lookup"><span data-stu-id="5ff83-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>  
  
 <span data-ttu-id="5ff83-131">Przykładowy kod edytuje schemat klienta w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="5ff83-131">The code example edits the customer schema in the following steps.</span></span>  
  
1. <span data-ttu-id="5ff83-132">Dodaje schemat klienta do nowego <xref:System.Xml.Schema.XmlSchemaSet> obiektu, a następnie kompiluje go.</span><span class="sxs-lookup"><span data-stu-id="5ff83-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="5ff83-133">Wszystkie ostrzeżenia i błędy walidacji schematu napotkane podczas odczytywania lub kompilowania schematu <xref:System.Xml.Schema.ValidationEventHandler> są obsługiwane przez delegata.</span><span class="sxs-lookup"><span data-stu-id="5ff83-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="5ff83-134">Pobiera skompilowany <xref:System.Xml.Schema.XmlSchema> obiekt <xref:System.Xml.Schema.XmlSchemaSet> z obiektu przez iterację <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> we właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ff83-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="5ff83-135">Ze względu na to, że schemat jest skompilowany, dostępne są właściwości po schemacie kompilacja-sprawdzonych (PSCI).</span><span class="sxs-lookup"><span data-stu-id="5ff83-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="5ff83-136">Tworzy nowy typ złożony dla `FirstName` elementu <xref:System.Xml.Schema.XmlSchemaComplexType> przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="5ff83-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
4. <span data-ttu-id="5ff83-137">Tworzy nowe proste rozszerzenie zawartości z typem `xs:string`podstawowym, <xref:System.Xml.Schema.XmlSchemaSimpleContent> korzystając z klas i <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> .</span><span class="sxs-lookup"><span data-stu-id="5ff83-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>  
  
5. <span data-ttu-id="5ff83-138">Tworzy nowy `Title` atrybut <xref:System.Xml.Schema.XmlSchemaAttribute> przy <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> użyciu`xs:string` klasy, z i dodaje atrybut do prostego rozszerzenia zawartości.</span><span class="sxs-lookup"><span data-stu-id="5ff83-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>  
  
6. <span data-ttu-id="5ff83-139">Ustawia model zawartości prostej zawartości na proste rozszerzenie zawartości oraz model zawartości typu złożonego na zawartość prostą.</span><span class="sxs-lookup"><span data-stu-id="5ff83-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>  
  
7. <span data-ttu-id="5ff83-140">Dodaje nowy typ złożony do kolekcji pre-Schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5ff83-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
8. <span data-ttu-id="5ff83-141">Wykonuje iterację dla <xref:System.Xml.Schema.XmlSchemaObject> każdego w kolekcji przedprodukcyjnej kompilacji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5ff83-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ff83-142">Ponieważ element nie jest elementem globalnym w schemacie, nie jest dostępny <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> w kolekcjach ani <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>. `FirstName`</span><span class="sxs-lookup"><span data-stu-id="5ff83-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="5ff83-143">Przykładowy kod lokalizuje `FirstName` element przez pierwsze lokalizowanie `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="5ff83-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>  
>   
>  <span data-ttu-id="5ff83-144">Pierwszy przykładowy kod przechodzą przez schemat przy użyciu kolekcji po schemacie kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5ff83-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="5ff83-145">W tym przykładzie kolekcja pre-Schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> jest używana do przechodzenia przez schemat.</span><span class="sxs-lookup"><span data-stu-id="5ff83-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="5ff83-146">Chociaż obie kolekcje zapewniają dostęp do elementów globalnych w schemacie, Iterowanie przez <xref:System.Xml.Schema.XmlSchema.Items%2A> kolekcję jest bardziej czasochłonne, ponieważ należy wykonać iterację wszystkich elementów globalnych w schemacie i nie ma żadnych właściwości PSCI.</span><span class="sxs-lookup"><span data-stu-id="5ff83-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="5ff83-147">Kolekcje PSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, itd.) zapewniają bezpośredni dostęp do swoich elementów globalnych, atrybutów i typów oraz ich właściwości PSCI.</span><span class="sxs-lookup"><span data-stu-id="5ff83-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>  
  
1. <span data-ttu-id="5ff83-148">`"Customer"` <xref:System.Xml.Schema.XmlSchemaSequence> <xref:System.Xml.Schema.XmlSchemaComplexType> Jeśli jest elementem, którego <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> jest, pobiera typ `Customer` złożony elementu przy użyciu klasy i cząstki sekwencji typu złożonego przy użyciu klasy. <xref:System.Xml.Schema.XmlSchemaObject></span><span class="sxs-lookup"><span data-stu-id="5ff83-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
2. <span data-ttu-id="5ff83-149">Wykonuje iterację dla <xref:System.Xml.Schema.XmlSchemaParticle> każdego w kolekcji przedprodukcyjnej kompilacji <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5ff83-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
3. <span data-ttu-id="5ff83-150"><xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> `"FirstName"` <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> Jeśli jest elementem, to jest, `FirstName` ustawia `FirstName` element na nowy typ złożony. <xref:System.Xml.Schema.XmlSchemaParticle></span><span class="sxs-lookup"><span data-stu-id="5ff83-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>  
  
4. <span data-ttu-id="5ff83-151">Na koniec przetwarza <xref:System.Xml.Schema.XmlSchema> i kompiluje zmodyfikowany obiekt <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> przy użyciu metod <xref:System.Xml.Schema.XmlSchemaSet> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> klasy i zapisuje je w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="5ff83-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="5ff83-152">Poniżej znajduje się kompletny przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="5ff83-152">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 <span data-ttu-id="5ff83-153">Poniżej przedstawiono zmodyfikowany schemat klienta utworzony w temacie [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md) .</span><span class="sxs-lookup"><span data-stu-id="5ff83-153">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ff83-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ff83-154">See also</span></span>

- [<span data-ttu-id="5ff83-155">Model SOM (XML Schema Object Model) ― omówienie</span><span class="sxs-lookup"><span data-stu-id="5ff83-155">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="5ff83-156">Odczytywanie i zapisywanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="5ff83-156">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="5ff83-157">Tworzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="5ff83-157">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="5ff83-158">Przechodzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="5ff83-158">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="5ff83-159">Uwzględnianie lub importowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="5ff83-159">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [<span data-ttu-id="5ff83-160">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="5ff83-160">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="5ff83-161">Zestaw informacji po kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="5ff83-161">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
