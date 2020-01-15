---
title: Odwołanie do schematu kontraktu danych
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: af183fa02ea3ec98f316979198624351d9b25f21
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963370"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="f9e6e-102">Odwołanie do schematu kontraktu danych</span><span class="sxs-lookup"><span data-stu-id="f9e6e-102">Data Contract Schema Reference</span></span>

<span data-ttu-id="f9e6e-103">W tym temacie opisano podzestaw schematu XML (XSD) używany przez <xref:System.Runtime.Serialization.DataContractSerializer> do opisywania typów środowiska uruchomieniowego języka wspólnego (CLR) na potrzeby serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>

## <a name="datacontractserializer-mappings"></a><span data-ttu-id="f9e6e-104">Mapowania DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="f9e6e-104">DataContractSerializer Mappings</span></span>

<span data-ttu-id="f9e6e-105">`DataContractSerializer` mapuje typy CLR na XSD, gdy metadane są eksportowane z usługi Windows Communication Foundation (WCF) za pomocą punktu końcowego metadanych lub [Narzędzia do obsługi metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="f9e6e-106">Aby uzyskać więcej informacji, zobacz [serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-106">For more information, see [Data Contract Serializer](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span></span>

<span data-ttu-id="f9e6e-107">`DataContractSerializer` również mapuje XSD na typy CLR, gdy Svcutil. exe jest używany do uzyskiwania dostępu do Web Services Description Language (WSDL) lub dokumentów XSD i generują Kontrakty danych dla usług lub klientów.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>

<span data-ttu-id="f9e6e-108">Tylko wystąpienia schematu XML, które są zgodne z wymaganiami podanymi w tym dokumencie, można mapować na typy CLR przy użyciu `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>

### <a name="support-levels"></a><span data-ttu-id="f9e6e-109">Poziomy pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="f9e6e-109">Support Levels</span></span>

<span data-ttu-id="f9e6e-110">`DataContractSerializer` udostępnia następujące poziomy obsługi dla danej funkcji schematu XML:</span><span class="sxs-lookup"><span data-stu-id="f9e6e-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>

- <span data-ttu-id="f9e6e-111">**Obsługiwane**.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-111">**Supported**.</span></span> <span data-ttu-id="f9e6e-112">Istnieje jawne mapowanie od tej funkcji do typów CLR lub atrybutów (lub obu) przy użyciu `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>

- <span data-ttu-id="f9e6e-113">**Zignorowano**.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-113">**Ignored**.</span></span> <span data-ttu-id="f9e6e-114">Funkcja jest dozwolona w schematach importowanych przez `DataContractSerializer`, ale nie ma wpływu na generowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>

- <span data-ttu-id="f9e6e-115">**Zabronione**.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-115">**Forbidden**.</span></span> <span data-ttu-id="f9e6e-116">`DataContractSerializer` nie obsługuje importowania schematu przy użyciu funkcji.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="f9e6e-117">Na przykład Svcutil. exe podczas uzyskiwania dostępu do języka WSDL ze schematem, który używa takich funkcji, powraca do korzystania z <xref:System.Xml.Serialization.XmlSerializer> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="f9e6e-118">Jest to domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-118">This is by default.</span></span>

## <a name="general-information"></a><span data-ttu-id="f9e6e-119">Informacje ogólne</span><span class="sxs-lookup"><span data-stu-id="f9e6e-119">General Information</span></span>

- <span data-ttu-id="f9e6e-120">Przestrzeń nazw schematu jest opisana w [schemacie XML](https://www.w3.org/2001/XMLSchema).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-120">The schema namespace is described at [XML Schema](https://www.w3.org/2001/XMLSchema).</span></span> <span data-ttu-id="f9e6e-121">Prefiks "XS" jest używany w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-121">The prefix "xs" is used in this document.</span></span>

- <span data-ttu-id="f9e6e-122">Wszystkie atrybuty z przestrzeni nazw nienależących do schematu są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-122">Any attributes with a non-schema namespace are ignored.</span></span>

- <span data-ttu-id="f9e6e-123">Wszelkie adnotacje (z wyjątkiem tych opisanych w tym dokumencie) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-123">Any annotations (except for those described in this document) are ignored.</span></span>

### <a name="xsschema-attributes"></a><span data-ttu-id="f9e6e-124">\<xs: schemat >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="f9e6e-124">\<xs:schema>: attributes</span></span>

|<span data-ttu-id="f9e6e-125">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9e6e-125">Attribute</span></span>|<span data-ttu-id="f9e6e-126">Contract</span><span class="sxs-lookup"><span data-stu-id="f9e6e-126">DataContract</span></span>|
|---------------|------------------|
|`attributeFormDefault`|<span data-ttu-id="f9e6e-127">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-127">Ignored.</span></span>|
|`blockDefault`|<span data-ttu-id="f9e6e-128">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-128">Ignored.</span></span>|
|`elementFormDefault`|<span data-ttu-id="f9e6e-129">Musi być kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-129">Must be qualified.</span></span> <span data-ttu-id="f9e6e-130">Wszystkie elementy muszą być kwalifikowane, aby schemat był obsługiwany przez `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="f9e6e-131">Można to osiągnąć przez ustawienie xs:schema/@elementFormDefault na "kwalifikowany" lub przez ustawienie xs:element/@form na "kwalifikowany" dla każdej deklaracji poszczególnych elementów.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|
|`finalDefault`|<span data-ttu-id="f9e6e-132">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-132">Ignored.</span></span>|
|`Id`|<span data-ttu-id="f9e6e-133">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-133">Ignored.</span></span>|
|`targetNamespace`|<span data-ttu-id="f9e6e-134">Obsługiwane i mapowane do przestrzeni nazw kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="f9e6e-135">Jeśli ten atrybut nie jest określony, zostanie użyta pusta przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="f9e6e-136">Nie może być zarezerwowaną przestrzenią nazw `http://schemas.microsoft.com/2003/10/Serialization/`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-136">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|
|`version`|<span data-ttu-id="f9e6e-137">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-137">Ignored.</span></span>|

### <a name="xsschema-contents"></a><span data-ttu-id="f9e6e-138">\<xs: schemat >: zawartość</span><span class="sxs-lookup"><span data-stu-id="f9e6e-138">\<xs:schema>: contents</span></span>

|<span data-ttu-id="f9e6e-139">Spis treści</span><span class="sxs-lookup"><span data-stu-id="f9e6e-139">Contents</span></span>|<span data-ttu-id="f9e6e-140">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-140">Schema</span></span>|
|--------------|------------|
|`include`|<span data-ttu-id="f9e6e-141">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-141">Supported.</span></span> <span data-ttu-id="f9e6e-142">`DataContractSerializer` obsługuje polecenie XS: include i xs: import.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="f9e6e-143">Jednak Svcutil. exe ogranicza następujące `xs:include/@schemaLocation` i `xs:import/@location` odwołań, gdy metadane są ładowane z pliku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="f9e6e-144">Lista plików schematu musi być przenoszona przez mechanizm poza pasmem, a nie za pomocą `include` w tym przypadku; dokumenty schematu `include`d zostały zignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`redefine`|<span data-ttu-id="f9e6e-145">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-145">Forbidden.</span></span> <span data-ttu-id="f9e6e-146">Użycie `xs:redefine` jest zabronione przez `DataContractSerializer` ze względów bezpieczeństwa: `x:redefine` wymaga, aby `schemaLocation`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="f9e6e-147">W pewnych okolicznościach Svcutil. exe przy użyciu funkcji DataContract ogranicza użycie `schemaLocation`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|
|`import`|<span data-ttu-id="f9e6e-148">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-148">Supported.</span></span> <span data-ttu-id="f9e6e-149">`DataContractSerializer` obsługuje `xs:include` i `xs:import`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="f9e6e-150">Jednak Svcutil. exe ogranicza następujące `xs:include/@schemaLocation` i `xs:import/@location` odwołań, gdy metadane są ładowane z pliku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="f9e6e-151">Lista plików schematu musi być przenoszona przez mechanizm poza pasmem, a nie za pomocą `include` w tym przypadku; dokumenty schematu `include`d zostały zignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`simpleType`|<span data-ttu-id="f9e6e-152">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-152">Supported.</span></span> <span data-ttu-id="f9e6e-153">Zapoznaj się z sekcją `xs:simpleType`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-153">See the `xs:simpleType` section.</span></span>|
|`complexType`|<span data-ttu-id="f9e6e-154">Obsługiwane mapowania do kontraktów danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="f9e6e-155">Zapoznaj się z sekcją `xs:complexType`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-155">See the `xs:complexType` section.</span></span>|
|`group`|<span data-ttu-id="f9e6e-156">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-156">Ignored.</span></span> <span data-ttu-id="f9e6e-157">`DataContractSerializer` nie obsługuje używania `xs:group`, `xs:attributeGroup`i `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="f9e6e-158">Te deklaracje są ignorowane jako elementy podrzędne `xs:schema`, ale nie można się do nich odwoływać z poziomu `complexType` lub innych obsługiwanych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`attributeGroup`|<span data-ttu-id="f9e6e-159">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-159">Ignored.</span></span> <span data-ttu-id="f9e6e-160">`DataContractSerializer` nie obsługuje używania `xs:group`, `xs:attributeGroup`i `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="f9e6e-161">Te deklaracje są ignorowane jako elementy podrzędne `xs:schema`, ale nie można się do nich odwoływać z poziomu `complexType` lub innych obsługiwanych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`element`|<span data-ttu-id="f9e6e-162">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-162">Supported.</span></span> <span data-ttu-id="f9e6e-163">Zobacz globalna Deklaracja elementu (JŚCIOWA).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-163">See Global Element Declaration (GED).</span></span>|
|`attribute`|<span data-ttu-id="f9e6e-164">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-164">Ignored.</span></span> <span data-ttu-id="f9e6e-165">`DataContractSerializer` nie obsługuje używania `xs:group`, `xs:attributeGroup`i `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="f9e6e-166">Te deklaracje są ignorowane jako elementy podrzędne `xs:schema`, ale nie można się do nich odwoływać z poziomu `complexType` lub innych obsługiwanych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`notation`|<span data-ttu-id="f9e6e-167">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-167">Ignored.</span></span>|

## <a name="complex-types--xscomplextype"></a><span data-ttu-id="f9e6e-168">Typy złożone — \<xs: complexType ></span><span class="sxs-lookup"><span data-stu-id="f9e6e-168">Complex Types – \<xs:complexType></span></span>

### <a name="general-information"></a><span data-ttu-id="f9e6e-169">Informacje ogólne</span><span class="sxs-lookup"><span data-stu-id="f9e6e-169">General Information</span></span>

<span data-ttu-id="f9e6e-170">Każdy typ złożony \<xs: complexType > mapowany do kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>

### <a name="xscomplextype-attributes"></a><span data-ttu-id="f9e6e-171">\<xs: complexType >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="f9e6e-171">\<xs:complexType>: attributes</span></span>

|<span data-ttu-id="f9e6e-172">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9e6e-172">Attribute</span></span>|<span data-ttu-id="f9e6e-173">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-173">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="f9e6e-174">Musi mieć wartość false (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-174">Must be false (default).</span></span>|
|`block`|<span data-ttu-id="f9e6e-175">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-175">Forbidden.</span></span>|
|`final`|<span data-ttu-id="f9e6e-176">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-176">Ignored.</span></span>|
|`id`|<span data-ttu-id="f9e6e-177">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-177">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="f9e6e-178">Musi mieć wartość false (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-178">Must be false (default).</span></span>|
|`name`|<span data-ttu-id="f9e6e-179">Obsługiwane i zamapowane na nazwę kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="f9e6e-180">Jeśli nazwa zawiera kilka kropek, podejmowana jest próba mapowania typu na typ wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="f9e6e-181">Na przykład typ złożony o nazwie `A.B` mapuje do typu kontraktu danych, który jest typem wewnętrznym typu z nazwą kontraktu danych `A`, ale tylko wtedy, gdy istnieje taki typ kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="f9e6e-182">Możliwe jest więcej niż jeden poziom zagnieżdżenia: na przykład `A.B.C` może być typem wewnętrznym, ale tylko wtedy, gdy istnieją zarówno `A`, jak i `A.B`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|

### <a name="xscomplextype-contents"></a><span data-ttu-id="f9e6e-183">\<xs: complexType >: Contents</span><span class="sxs-lookup"><span data-stu-id="f9e6e-183">\<xs:complexType>: contents</span></span>

|<span data-ttu-id="f9e6e-184">Spis treści</span><span class="sxs-lookup"><span data-stu-id="f9e6e-184">Contents</span></span>|<span data-ttu-id="f9e6e-185">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-185">Schema</span></span>|
|--------------|------------|
|`simpleContent`|<span data-ttu-id="f9e6e-186">Rozszerzenia są zabronione.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="f9e6e-187">Ograniczenie jest dozwolone tylko w `anySimpleType`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-187">Restriction is allowed only from `anySimpleType`.</span></span>|
|`complexContent`|<span data-ttu-id="f9e6e-188">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-188">Supported.</span></span> <span data-ttu-id="f9e6e-189">Zobacz "dziedziczenie".</span><span class="sxs-lookup"><span data-stu-id="f9e6e-189">See "Inheritance".</span></span>|
|`group`|<span data-ttu-id="f9e6e-190">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-190">Forbidden.</span></span>|
|`all`|<span data-ttu-id="f9e6e-191">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-191">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="f9e6e-192">Zabroniony</span><span class="sxs-lookup"><span data-stu-id="f9e6e-192">Forbidden</span></span>|
|`sequence`|<span data-ttu-id="f9e6e-193">Obsługiwane, mapuje do członków danych kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-193">Supported, maps to data members of a data contract.</span></span>|
|`attribute`|<span data-ttu-id="f9e6e-194">Zabronione, nawet jeśli użycie = "zabronione" (z jednym wyjątkiem).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="f9e6e-195">Obsługiwane są tylko opcjonalne atrybuty z przestrzeni nazw schematu serializacji standardowej.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="f9e6e-196">Nie są one mapowane na elementy członkowskie danych w modelu programowania kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="f9e6e-197">Obecnie tylko jeden taki atrybut ma znaczenie i został omówiony w sekcji ISerializable.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="f9e6e-198">Wszystkie pozostałe są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-198">All others are ignored.</span></span>|
|`attributeGroup`|<span data-ttu-id="f9e6e-199">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-199">Forbidden.</span></span> <span data-ttu-id="f9e6e-200">W wersji 1 programu WCF wersja `DataContractSerializer` ignoruje obecność `attributeGroup` w `xs:complexType`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-200">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|
|`anyAttribute`|<span data-ttu-id="f9e6e-201">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-201">Forbidden.</span></span>|
|<span data-ttu-id="f9e6e-202">ciągiem</span><span class="sxs-lookup"><span data-stu-id="f9e6e-202">(empty)</span></span>|<span data-ttu-id="f9e6e-203">Mapuje do kontraktu danych bez składowych danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-203">Maps to a data contract with no data members.</span></span>|

### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="f9e6e-204">\<xs: > sekwencji w typie złożonym: atrybuty</span><span class="sxs-lookup"><span data-stu-id="f9e6e-204">\<xs:sequence> in a complex type: attributes</span></span>

|<span data-ttu-id="f9e6e-205">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9e6e-205">Attribute</span></span>|<span data-ttu-id="f9e6e-206">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-206">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="f9e6e-207">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-207">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="f9e6e-208">Musi mieć wartość 1 (domyślna).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-208">Must be 1 (default).</span></span>|
|`minOccurs`|<span data-ttu-id="f9e6e-209">Musi mieć wartość 1 (domyślna).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-209">Must be 1 (default).</span></span>|

### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="f9e6e-210">\<xs: > sekwencji w typie złożonym: zawartość</span><span class="sxs-lookup"><span data-stu-id="f9e6e-210">\<xs:sequence> in a complex type: contents</span></span>

|<span data-ttu-id="f9e6e-211">Spis treści</span><span class="sxs-lookup"><span data-stu-id="f9e6e-211">Contents</span></span>|<span data-ttu-id="f9e6e-212">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-212">Schema</span></span>|
|--------------|------------|
|`element`|<span data-ttu-id="f9e6e-213">Każde wystąpienie jest mapowane na element członkowski danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-213">Each instance maps to a data member.</span></span>|
|`group`|<span data-ttu-id="f9e6e-214">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-214">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="f9e6e-215">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-215">Forbidden.</span></span>|
|`sequence`|<span data-ttu-id="f9e6e-216">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-216">Forbidden.</span></span>|
|`any`|<span data-ttu-id="f9e6e-217">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-217">Forbidden.</span></span>|
|<span data-ttu-id="f9e6e-218">ciągiem</span><span class="sxs-lookup"><span data-stu-id="f9e6e-218">(empty)</span></span>|<span data-ttu-id="f9e6e-219">Mapuje do kontraktu danych bez składowych danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-219">Maps to a data contract with no data members.</span></span>|

## <a name="elements--xselement"></a><span data-ttu-id="f9e6e-220">Elementy — \<xs: element ></span><span class="sxs-lookup"><span data-stu-id="f9e6e-220">Elements – \<xs:element></span></span>

### <a name="general-information"></a><span data-ttu-id="f9e6e-221">Informacje ogólne</span><span class="sxs-lookup"><span data-stu-id="f9e6e-221">General Information</span></span>

<span data-ttu-id="f9e6e-222">`<xs:element>` mogą wystąpić w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="f9e6e-222">`<xs:element>` can occur in the following contexts:</span></span>

- <span data-ttu-id="f9e6e-223">Może wystąpić w ramach `<xs:sequence>`, który opisuje element członkowski danych regularnego (niebędącego kolekcją) kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="f9e6e-224">W takim przypadku atrybut `maxOccurs` musi mieć wartość 1.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="f9e6e-225">(Wartość 0 jest niedozwolona).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-225">(A value of 0 is not allowed).</span></span>

- <span data-ttu-id="f9e6e-226">Może wystąpić w `<xs:sequence>`, który opisuje element członkowski danych w ramach kontraktu danych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="f9e6e-227">W tym przypadku atrybut `maxOccurs` musi mieć wartość większą niż 1 lub "Unbounded".</span><span class="sxs-lookup"><span data-stu-id="f9e6e-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>

- <span data-ttu-id="f9e6e-228">Może wystąpić w `<xs:schema>` jako deklaracja elementu globalnego (JŚCIOWA).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="f9e6e-229">\<xs: element > z atrybutami maxOccurs = 1 w elemencie \<xs: Sequence > (składowe danych)</span><span class="sxs-lookup"><span data-stu-id="f9e6e-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>

|<span data-ttu-id="f9e6e-230">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9e6e-230">Attribute</span></span>|<span data-ttu-id="f9e6e-231">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-231">Schema</span></span>|
|---------------|------------|
|`ref`|<span data-ttu-id="f9e6e-232">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-232">Forbidden.</span></span>|
|`name`|<span data-ttu-id="f9e6e-233">Obsługiwane, mapuje na nazwę elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-233">Supported, maps to the data member name.</span></span>|
|`type`|<span data-ttu-id="f9e6e-234">Obsługiwane, mapuje do typu elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="f9e6e-235">Aby uzyskać więcej informacji, zobacz Mapowanie typu/elementu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="f9e6e-236">Jeśli nie zostanie określony (a element nie zawiera typu anonimowego), przyjmuje się `xs:anyType`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|
|`block`|<span data-ttu-id="f9e6e-237">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-237">Ignored.</span></span>|
|`default`|<span data-ttu-id="f9e6e-238">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-238">Forbidden.</span></span>|
|`fixed`|<span data-ttu-id="f9e6e-239">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-239">Forbidden.</span></span>|
|`form`|<span data-ttu-id="f9e6e-240">Musi być kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-240">Must be qualified.</span></span> <span data-ttu-id="f9e6e-241">Ten atrybut można ustawić za `elementFormDefault` `xs:schema`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|
|`id`|<span data-ttu-id="f9e6e-242">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-242">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="f9e6e-243">1</span><span class="sxs-lookup"><span data-stu-id="f9e6e-243">1</span></span>|
|`minOccurs`|<span data-ttu-id="f9e6e-244">Mapuje na Właściwość <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> elementu członkowskiego danych (`IsRequired` ma wartość true, jeśli `minOccurs` wynosi 1).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|
|`nillable`|<span data-ttu-id="f9e6e-245">Ma wpływ na mapowanie typu.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-245">Affects type mapping.</span></span> <span data-ttu-id="f9e6e-246">Zobacz mapowanie typu/elementu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-246">See Type/primitive mapping.</span></span>|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="f9e6e-247">\<xs: element > z maxOccurs > 1 w \<xs: Sequence > (Kolekcje)</span><span class="sxs-lookup"><span data-stu-id="f9e6e-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>

- <span data-ttu-id="f9e6e-248">Mapuje do <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>

- <span data-ttu-id="f9e6e-249">W przypadku typów kolekcji tylko jeden element xs: jest dozwolony w obrębie sekwencji xs:.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>

 <span data-ttu-id="f9e6e-250">Kolekcje mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="f9e6e-250">Collections can be of the following types:</span></span>

- <span data-ttu-id="f9e6e-251">Regularne kolekcje (na przykład tablice).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-251">Regular collections (for example, arrays).</span></span>

- <span data-ttu-id="f9e6e-252">Kolekcje słowników (mapowanie jednej wartości na inną, na przykład <xref:System.Collections.Hashtable>).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>

- <span data-ttu-id="f9e6e-253">Jedyna różnica między słownikiem i tablicą typu pary klucz/wartość znajduje się w wygenerowanym modelu programowania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="f9e6e-254">Istnieje mechanizm adnotacji schematu, którego można użyć, aby wskazać, że dany typ jest kolekcją słownika.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>

<span data-ttu-id="f9e6e-255">Reguły dla atrybutów `ref`, `block`, `default`, `fixed`, `form`i `id` są takie same jak w przypadku przypadków niezwiązanych z kolekcją.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="f9e6e-256">Inne atrybuty obejmują te zawarte w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-256">Other attributes include those in the following table.</span></span>

|<span data-ttu-id="f9e6e-257">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9e6e-257">Attribute</span></span>|<span data-ttu-id="f9e6e-258">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-258">Schema</span></span>|
|---------------|------------|
|`name`|<span data-ttu-id="f9e6e-259">Obsługiwane, mapuje do właściwości <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> w atrybucie `CollectionDataContractAttribute`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|
|`type`|<span data-ttu-id="f9e6e-260">Obsługiwane, mapuje do typu przechowywanego w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-260">Supported, maps to the type stored in the collection.</span></span>|
|`maxOccurs`|<span data-ttu-id="f9e6e-261">Większe niż 1 lub "niepowiązane".</span><span class="sxs-lookup"><span data-stu-id="f9e6e-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="f9e6e-262">Schemat kontrolera domeny powinien używać "Unbounded".</span><span class="sxs-lookup"><span data-stu-id="f9e6e-262">The DC schema should use "unbounded".</span></span>|
|`minOccurs`|<span data-ttu-id="f9e6e-263">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-263">Ignored.</span></span>|
|`nillable`|<span data-ttu-id="f9e6e-264">Ma wpływ na mapowanie typu.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-264">Affects type mapping.</span></span> <span data-ttu-id="f9e6e-265">Ten atrybut jest ignorowany dla kolekcji słowników.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-265">This attribute is ignored for dictionary collections.</span></span>|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="f9e6e-266">\<xs: element > w \<xs: Schema > Deklaracja elementu globalnego</span><span class="sxs-lookup"><span data-stu-id="f9e6e-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>

- <span data-ttu-id="f9e6e-267">Deklaracja elementu globalnego (JŚCIOWA), która ma taką samą nazwę i przestrzeń nazw, jak typ w schemacie lub definiuje typ anonimowy wewnątrz siebie, jest określana jako skojarzona z typem.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>

- <span data-ttu-id="f9e6e-268">Eksport schematu: skojarzone GEDs są generowane dla każdego wygenerowanego typu, zarówno proste, jak i złożone.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>

- <span data-ttu-id="f9e6e-269">Deserializacja/Serializacja: skojarzone GEDs są używane jako elementy główne dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>

- <span data-ttu-id="f9e6e-270">Importowanie schematu: skojarzone GEDs nie są wymagane i są ignorowane, jeśli są zgodne z następującymi regułami (chyba że definiują typy).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>

|<span data-ttu-id="f9e6e-271">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9e6e-271">Attribute</span></span>|<span data-ttu-id="f9e6e-272">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-272">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="f9e6e-273">Dla skojarzonych GEDs należy określić wartość false.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-273">Must be false for associated GEDs.</span></span>|
|`block`|<span data-ttu-id="f9e6e-274">Niedozwolone w skojarzonych GEDs.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-274">Forbidden in associated GEDs.</span></span>|
|`default`|<span data-ttu-id="f9e6e-275">Niedozwolone w skojarzonych GEDs.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-275">Forbidden in associated GEDs.</span></span>|
|`final`|<span data-ttu-id="f9e6e-276">Dla skojarzonych GEDs należy określić wartość false.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-276">Must be false for associated GEDs.</span></span>|
|`fixed`|<span data-ttu-id="f9e6e-277">Niedozwolone w skojarzonych GEDs.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-277">Forbidden in associated GEDs.</span></span>|
|`id`|<span data-ttu-id="f9e6e-278">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-278">Ignored.</span></span>|
|`name`|<span data-ttu-id="f9e6e-279">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-279">Supported.</span></span> <span data-ttu-id="f9e6e-280">Zobacz definicję skojarzonych GEDs.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-280">See the definition of associated GEDs.</span></span>|
|`nillable`|<span data-ttu-id="f9e6e-281">Dla skojarzonych GEDs należy mieć wartość true.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-281">Must be true for associated GEDs.</span></span>|
|`substitutionGroup`|<span data-ttu-id="f9e6e-282">Niedozwolone w skojarzonych GEDs.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-282">Forbidden in associated GEDs.</span></span>|
|`type`|<span data-ttu-id="f9e6e-283">Obsługiwane i muszą być zgodne z skojarzonym typem dla skojarzonych GEDs (chyba że element zawiera typ anonimowy).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|

### <a name="xselement-contents"></a><span data-ttu-id="f9e6e-284">\<xs: element >: Contents</span><span class="sxs-lookup"><span data-stu-id="f9e6e-284">\<xs:element>: contents</span></span>

|<span data-ttu-id="f9e6e-285">Spis treści</span><span class="sxs-lookup"><span data-stu-id="f9e6e-285">Contents</span></span>|<span data-ttu-id="f9e6e-286">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-286">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="f9e6e-287">Obsługiwane. \*</span><span class="sxs-lookup"><span data-stu-id="f9e6e-287">Supported.\*</span></span>|
|`complexType`|<span data-ttu-id="f9e6e-288">Obsługiwane. \*</span><span class="sxs-lookup"><span data-stu-id="f9e6e-288">Supported.\*</span></span>|
|`unique`|<span data-ttu-id="f9e6e-289">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-289">Ignored.</span></span>|
|`key`|<span data-ttu-id="f9e6e-290">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-290">Ignored.</span></span>|
|`keyref`|<span data-ttu-id="f9e6e-291">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-291">Ignored.</span></span>|
|<span data-ttu-id="f9e6e-292">(pusty)</span><span class="sxs-lookup"><span data-stu-id="f9e6e-292">(blank)</span></span>|<span data-ttu-id="f9e6e-293">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-293">Supported.</span></span>|

<span data-ttu-id="f9e6e-294">\*, gdy użycie mapowania `simpleType` i `complexType,` dla typów anonimowych jest takie samo jak w przypadku typów nieanonimowych, z tą różnicą, że nie ma żadnych kontraktów danych anonimowych i dlatego jest tworzony nazwany kontrakt danych, z wygenerowaną nazwą pochodną od nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="f9e6e-295">Reguły dla typów anonimowych znajdują się na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="f9e6e-295">The rules for anonymous types are in the following list:</span></span>

- <span data-ttu-id="f9e6e-296">Szczegóły implementacji WCF: Jeśli nazwa `xs:element` nie zawiera kropek, typ anonimowy jest mapowany na typ wewnętrzny zewnętrznego kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-296">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="f9e6e-297">Jeśli nazwa zawiera okresy, typ kontraktu danych będących wynikiem jest niezależny (nie jest typem wewnętrznym).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>

- <span data-ttu-id="f9e6e-298">Nazwa wygenerowanej kontraktu danych typu wewnętrznego to nazwa kontraktu danych typu zewnętrznego, po którym następuje kropka, nazwa elementu i ciąg "Type".</span><span class="sxs-lookup"><span data-stu-id="f9e6e-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>

- <span data-ttu-id="f9e6e-299">Jeśli kontrakt danych o takiej nazwie już istnieje, nazwa jest unikatowa poprzez dołączenie "1", "2", "3" i tak dalej, aż do utworzenia unikatowej nazwy.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>

## <a name="simple-types---xssimpletype"></a><span data-ttu-id="f9e6e-300">Typy proste — \<xs: simpleType ></span><span class="sxs-lookup"><span data-stu-id="f9e6e-300">Simple Types - \<xs:simpleType></span></span>

### <a name="xssimpletype-attributes"></a><span data-ttu-id="f9e6e-301">\<xs: simpleType >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="f9e6e-301">\<xs:simpleType>: attributes</span></span>

|<span data-ttu-id="f9e6e-302">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9e6e-302">Attribute</span></span>|<span data-ttu-id="f9e6e-303">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-303">Schema</span></span>|
|---------------|------------|
|`final`|<span data-ttu-id="f9e6e-304">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-304">Ignored.</span></span>|
|`id`|<span data-ttu-id="f9e6e-305">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-305">Ignored.</span></span>|
|`name`|<span data-ttu-id="f9e6e-306">Obsługiwane, mapuje do nazwy kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-306">Supported, maps to the data contract name.</span></span>|

### <a name="xssimpletype-contents"></a><span data-ttu-id="f9e6e-307">\<xs: simpleType >: Contents</span><span class="sxs-lookup"><span data-stu-id="f9e6e-307">\<xs:simpleType>: contents</span></span>

|<span data-ttu-id="f9e6e-308">Spis treści</span><span class="sxs-lookup"><span data-stu-id="f9e6e-308">Contents</span></span>|<span data-ttu-id="f9e6e-309">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-309">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="f9e6e-310">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-310">Supported.</span></span> <span data-ttu-id="f9e6e-311">Mapuje na kontrakty danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="f9e6e-312">Ten atrybut jest ignorowany, jeśli nie pasuje do wzorca wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="f9e6e-313">Zapoznaj się z sekcją ograniczenia `xs:simpleType`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-313">See the `xs:simpleType` restrictions section.</span></span>|
|`list`|<span data-ttu-id="f9e6e-314">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-314">Supported.</span></span> <span data-ttu-id="f9e6e-315">Mapuje, aby oflagować Kontrakty danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="f9e6e-316">Zapoznaj się z sekcją `xs:simpleType` lists.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-316">See the `xs:simpleType` lists section.</span></span>|
|`union`|<span data-ttu-id="f9e6e-317">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-317">Forbidden.</span></span>|

### <a name="xsrestriction"></a><span data-ttu-id="f9e6e-318">\<polecenie XS: ograniczenia ></span><span class="sxs-lookup"><span data-stu-id="f9e6e-318">\<xs:restriction></span></span>

- <span data-ttu-id="f9e6e-319">Ograniczenia typu złożonego są obsługiwane tylko dla elementu Base = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="f9e6e-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>

- <span data-ttu-id="f9e6e-320">Ograniczenia typu prostego `xs:string`, które nie mają żadnych aspektów ograniczeń innych niż `xs:enumeration` są mapowane na kontrakty danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>

- <span data-ttu-id="f9e6e-321">Wszystkie inne ograniczenia typu prostego są mapowane na typy, które ograniczają.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="f9e6e-322">Na przykład ograniczenie `xs:int` jest mapowane na liczbę całkowitą, tak jak `xs:int` same.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="f9e6e-323">Aby uzyskać więcej informacji na temat mapowania typu pierwotnego, zobacz Mapowanie typu/elementu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-323">For more information about primitive type mapping, see Type/primitive mapping.</span></span>

### <a name="xsrestriction-attributes"></a><span data-ttu-id="f9e6e-324">\<xs: ograniczenia >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="f9e6e-324">\<xs:restriction>: attributes</span></span>

|<span data-ttu-id="f9e6e-325">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9e6e-325">Attribute</span></span>|<span data-ttu-id="f9e6e-326">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-326">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="f9e6e-327">Musi być obsługiwanym typem prostym lub `xs:anyType`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-327">Must be a supported simple type or `xs:anyType`.</span></span>|
|`id`|<span data-ttu-id="f9e6e-328">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-328">Ignored.</span></span>|

### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="f9e6e-329">\<xs: ograniczenia > we wszystkich innych przypadkach: zawartość</span><span class="sxs-lookup"><span data-stu-id="f9e6e-329">\<xs:restriction> for all other cases: contents</span></span>

|<span data-ttu-id="f9e6e-330">Spis treści</span><span class="sxs-lookup"><span data-stu-id="f9e6e-330">Contents</span></span>|<span data-ttu-id="f9e6e-331">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-331">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="f9e6e-332">Jeśli jest obecny, musi pochodzić od obsługiwanego typu pierwotnego.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-332">If present, must be derived from a supported primitive type.</span></span>|
|`minExclusive`|<span data-ttu-id="f9e6e-333">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-333">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="f9e6e-334">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-334">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="f9e6e-335">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-335">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="f9e6e-336">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-336">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="f9e6e-337">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-337">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="f9e6e-338">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-338">Ignored.</span></span>|
|`length`|<span data-ttu-id="f9e6e-339">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-339">Ignored.</span></span>|
|`minLength`|<span data-ttu-id="f9e6e-340">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-340">Ignored.</span></span>|
|`maxLength`|<span data-ttu-id="f9e6e-341">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-341">Ignored.</span></span>|
|`enumeration`|<span data-ttu-id="f9e6e-342">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-342">Ignored.</span></span>|
|`whiteSpace`|<span data-ttu-id="f9e6e-343">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-343">Ignored.</span></span>|
|`pattern`|<span data-ttu-id="f9e6e-344">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-344">Ignored.</span></span>|
|<span data-ttu-id="f9e6e-345">(pusty)</span><span class="sxs-lookup"><span data-stu-id="f9e6e-345">(blank)</span></span>|<span data-ttu-id="f9e6e-346">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-346">Supported.</span></span>|

## <a name="enumeration"></a><span data-ttu-id="f9e6e-347">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f9e6e-347">Enumeration</span></span>

### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="f9e6e-348">\<xs: > ograniczeń dla wyliczeń: atrybuty</span><span class="sxs-lookup"><span data-stu-id="f9e6e-348">\<xs:restriction> for enumerations: attributes</span></span>

|<span data-ttu-id="f9e6e-349">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9e6e-349">Attribute</span></span>|<span data-ttu-id="f9e6e-350">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-350">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="f9e6e-351">Jeśli jest obecny, musi być `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-351">If present, must be `xs:string`.</span></span>|
|`id`|<span data-ttu-id="f9e6e-352">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-352">Ignored.</span></span>|

### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="f9e6e-353">\<xs: > ograniczeń dla wyliczeń: zawartość</span><span class="sxs-lookup"><span data-stu-id="f9e6e-353">\<xs:restriction> for enumerations: contents</span></span>

|<span data-ttu-id="f9e6e-354">Spis treści</span><span class="sxs-lookup"><span data-stu-id="f9e6e-354">Contents</span></span>|<span data-ttu-id="f9e6e-355">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-355">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="f9e6e-356">Jeśli jest obecny, musi to być ograniczenie wyliczenia obsługiwane przez umowę danych (w tej sekcji).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|
|`minExclusive`|<span data-ttu-id="f9e6e-357">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-357">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="f9e6e-358">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-358">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="f9e6e-359">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-359">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="f9e6e-360">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-360">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="f9e6e-361">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-361">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="f9e6e-362">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-362">Ignored.</span></span>|
|`length`|<span data-ttu-id="f9e6e-363">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-363">Forbidden.</span></span>|
|`minLength`|<span data-ttu-id="f9e6e-364">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-364">Forbidden.</span></span>|
|`maxLength`|<span data-ttu-id="f9e6e-365">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-365">Forbidden.</span></span>|
|`enumeration`|<span data-ttu-id="f9e6e-366">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-366">Supported.</span></span> <span data-ttu-id="f9e6e-367">Wyliczenie "ID" jest ignorowane, a "value" mapuje do nazwy wartości w kontrakcie danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|
|`whiteSpace`|<span data-ttu-id="f9e6e-368">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-368">Forbidden.</span></span>|
|`pattern`|<span data-ttu-id="f9e6e-369">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-369">Forbidden.</span></span>|
|<span data-ttu-id="f9e6e-370">ciągiem</span><span class="sxs-lookup"><span data-stu-id="f9e6e-370">(empty)</span></span>|<span data-ttu-id="f9e6e-371">Obsługiwane, mapuje do pustego typu wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-371">Supported, maps to empty enumeration type.</span></span>|

 <span data-ttu-id="f9e6e-372">Poniższy kod przedstawia klasę C# wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-372">The following code shows a C# enumeration class.</span></span>

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

<span data-ttu-id="f9e6e-373">Ta klasa mapuje do poniższego schematu przez `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-373">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="f9e6e-374">Jeśli wartości wyliczenia zaczynają się od 1, bloki `xs:annotation` nie są generowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-374">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>

```xml
<xs:simpleType name="MyEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="first">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          3
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
    <xs:enumeration value="second">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          4
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
  </xs:restriction>
</xs:simpleType>
```

### <a name="xslist"></a><span data-ttu-id="f9e6e-375">\<xs:list></span><span class="sxs-lookup"><span data-stu-id="f9e6e-375">\<xs:list></span></span>

<span data-ttu-id="f9e6e-376">`DataContractSerializer` mapuje typy wyliczeniowe oznaczone `System.FlagsAttribute` na `xs:list` pochodne od `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-376">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="f9e6e-377">Nie są obsługiwane żadne inne odmiany `xs:list`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-377">No other `xs:list` variations are supported.</span></span>

### <a name="xslist-attributes"></a><span data-ttu-id="f9e6e-378">\<xs: list >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="f9e6e-378">\<xs:list>: attributes</span></span>

|<span data-ttu-id="f9e6e-379">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9e6e-379">Attribute</span></span>|<span data-ttu-id="f9e6e-380">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-380">Schema</span></span>|
|---------------|------------|
|`itemType`|<span data-ttu-id="f9e6e-381">Zabrania.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-381">Forbidden.</span></span>|
|`id`|<span data-ttu-id="f9e6e-382">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-382">Ignored.</span></span>|

### <a name="xslist-contents"></a><span data-ttu-id="f9e6e-383">\<xs: list >: Contents</span><span class="sxs-lookup"><span data-stu-id="f9e6e-383">\<xs:list>: contents</span></span>

|<span data-ttu-id="f9e6e-384">Spis treści</span><span class="sxs-lookup"><span data-stu-id="f9e6e-384">Contents</span></span>|<span data-ttu-id="f9e6e-385">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-385">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="f9e6e-386">Musi być ograniczeniem `xs:string` przy użyciu `xs:enumeration` aspektu.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-386">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|

<span data-ttu-id="f9e6e-387">Jeśli wartość wyliczenia nie jest zgodna z potęgą 2 postępu (domyślnie dla flag), wartość jest przechowywana w elemencie `xs:annotation/xs:appInfo/ser:EnumerationValue`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-387">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>

<span data-ttu-id="f9e6e-388">Na przykład poniższy kod oznacza typ wyliczeniowy.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-388">For example, the following code flags an enumeration type.</span></span>

```csharp
[Flags]
public enum AuthFlags
{
  AuthAnonymous = 1,
  AuthBasic = 2,
  AuthNTLM = 4,
  AuthMD5 = 16,
  AuthWindowsLiveID = 64,
}
```

<span data-ttu-id="f9e6e-389">Ten typ jest mapowany na poniższy schemat.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-389">This type maps to the following schema.</span></span>

```xml
<xs:simpleType name="AuthFlags">
    <xs:list>
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="AuthAnonymous" />
          <xs:enumeration value="AuthBasic" />
          <xs:enumeration value="AuthNTLM" />
          <xs:enumeration value="AuthMD5">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
          <xs:enumeration value="AuthWindowsLiveID">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
        </xs:restriction>
      </xs:simpleType>
    </xs:list>
  </xs:simpleType>
```

## <a name="inheritance"></a><span data-ttu-id="f9e6e-390">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="f9e6e-390">Inheritance</span></span>

### <a name="general-rules"></a><span data-ttu-id="f9e6e-391">Reguły ogólne</span><span class="sxs-lookup"><span data-stu-id="f9e6e-391">General rules</span></span>

<span data-ttu-id="f9e6e-392">Kontrakt danych może dziedziczyć z innego kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-392">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="f9e6e-393">Takie Kontrakty danych są mapowane na bazę i są wyprowadzane przez typy rozszerzeń przy użyciu konstrukcji schematu XML `<xs:extension>`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-393">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>

<span data-ttu-id="f9e6e-394">Kontrakt danych nie może dziedziczyć z kontraktu danych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-394">A data contract cannot inherit from a collection data contract.</span></span>

<span data-ttu-id="f9e6e-395">Na przykład poniższy kod jest kontraktem danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-395">For example, the following code is a data contract.</span></span>

```csharp
[DataContract]
public class Person
{
  [DataMember]
  public string Name;
}
[DataContract]
public class Employee : Person
{
  [DataMember]
  public int ID;
}
```

<span data-ttu-id="f9e6e-396">Ten kontrakt danych mapuje do następującej deklaracji typu schematu XML.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-396">This data contract maps to the following XML Schema type declaration.</span></span>

```xml
<xs:complexType name="Employee">
 <xs:complexContent mixed="false">
  <xs:extension base="tns:Person">
   <xs:sequence>
    <xs:element minOccurs="0" name="ID" type="xs:int"/>
   </xs:sequence>
  </xs:extension>
 </xs:complexContent>
</xs:complexType>
<xs:complexType name="Person">
 <xs:sequence>
  <xs:element minOccurs="0" name="Name"
    nillable="true" type="xs:string"/>
 </xs:sequence>
</xs:complexType>
```

### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="f9e6e-397">\<xs: complexContent >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="f9e6e-397">\<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="f9e6e-398">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9e6e-398">Attribute</span></span>|<span data-ttu-id="f9e6e-399">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-399">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="f9e6e-400">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-400">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="f9e6e-401">Musi mieć wartość false.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-401">Must be false.</span></span>|

### <a name="xscomplexcontent-contents"></a><span data-ttu-id="f9e6e-402">\<xs: complexContent >: Contents</span><span class="sxs-lookup"><span data-stu-id="f9e6e-402">\<xs:complexContent>: contents</span></span>

|<span data-ttu-id="f9e6e-403">Spis treści</span><span class="sxs-lookup"><span data-stu-id="f9e6e-403">Contents</span></span>|<span data-ttu-id="f9e6e-404">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-404">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="f9e6e-405">Zabronione, chyba że Base = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="f9e6e-405">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="f9e6e-406">Drugie jest równoważne umieszczaniu zawartości `xs:restriction` bezpośrednio w kontenerze `xs:complexContent`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-406">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|
|`extension`|<span data-ttu-id="f9e6e-407">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-407">Supported.</span></span> <span data-ttu-id="f9e6e-408">Mapuje na dziedziczenie kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-408">Maps to data contract inheritance.</span></span>|

### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="f9e6e-409">\<xs: Extension > w \<xs: complexContent >: Attributes</span><span class="sxs-lookup"><span data-stu-id="f9e6e-409">\<xs:extension> in \<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="f9e6e-410">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9e6e-410">Attribute</span></span>|<span data-ttu-id="f9e6e-411">Schemat</span><span class="sxs-lookup"><span data-stu-id="f9e6e-411">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="f9e6e-412">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-412">Ignored.</span></span>|
|`base`|<span data-ttu-id="f9e6e-413">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-413">Supported.</span></span> <span data-ttu-id="f9e6e-414">Mapuje do typu kontraktu danych podstawowych, z którego dziedziczy ten typ.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-414">Maps to the base data contract type that this type inherits from.</span></span>|

### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="f9e6e-415">\<xs: Extension > w \<xs: complexContent >: Contents</span><span class="sxs-lookup"><span data-stu-id="f9e6e-415">\<xs:extension> in \<xs:complexContent>: contents</span></span>

<span data-ttu-id="f9e6e-416">Reguły są takie same jak dla `<xs:complexType>` zawartości.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-416">The rules are the same as for `<xs:complexType>` contents.</span></span>

<span data-ttu-id="f9e6e-417">Jeśli `<xs:sequence>` jest podany, jego elementy członkowskie są mapowane na dodatkowe składowe danych, które znajdują się w umowie danych pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-417">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>

<span data-ttu-id="f9e6e-418">Jeśli typ pochodny zawiera element o takiej samej nazwie jak element w typie podstawowym, deklaracja duplikatu elementu mapuje do składowej danych o nazwie, która jest generowana jako unikatowa.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-418">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="f9e6e-419">Dodatnie liczby całkowite są dodawane do nazwy elementu członkowskiego danych ("member1", "member2" itd.), dopóki nie zostanie znaleziona unikatowa nazwa.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-419">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="f9e6e-420">Drugiej</span><span class="sxs-lookup"><span data-stu-id="f9e6e-420">Conversely:</span></span>

- <span data-ttu-id="f9e6e-421">Jeśli kontrakt danych pochodnych zawiera element członkowski danych o tej samej nazwie i typie co element członkowski danych w ramach kontraktu danych podstawowych, `DataContractSerializer` generuje ten odpowiadający element w typie pochodnym.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-421">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>

- <span data-ttu-id="f9e6e-422">Jeśli kontrakt danych pochodnych ma element członkowski danych o takiej samej nazwie jak element członkowski danych w podstawowej umowie danych, ale inny typ, `DataContractSerializer` importuje schemat z elementem typu `xs:anyType` w deklaracjach typu podstawowego i pochodnym.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-422">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="f9e6e-423">Oryginalna nazwa typu jest zachowywana w `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-423">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>

<span data-ttu-id="f9e6e-424">Obie warianty mogą prowadzić do schematu z niejednoznacznym modelem zawartości, który zależy od kolejności odpowiednich elementów członkowskich danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-424">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>

## <a name="typeprimitive-mapping"></a><span data-ttu-id="f9e6e-425">Typ/mapowanie pierwotne</span><span class="sxs-lookup"><span data-stu-id="f9e6e-425">Type/primitive mapping</span></span>

<span data-ttu-id="f9e6e-426">`DataContractSerializer` używa następującego mapowania dla typów pierwotnych schematu XML.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-426">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>

|<span data-ttu-id="f9e6e-427">Typ XSD</span><span class="sxs-lookup"><span data-stu-id="f9e6e-427">XSD type</span></span>|<span data-ttu-id="f9e6e-428">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="f9e6e-428">.NET type</span></span>|
|--------------|---------------|
|`anyType`|<span data-ttu-id="f9e6e-429"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-429"><xref:System.Object>.</span></span>|
|`anySimpleType`|<span data-ttu-id="f9e6e-430"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-430"><xref:System.String>.</span></span>|
|`duration`|<span data-ttu-id="f9e6e-431"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-431"><xref:System.TimeSpan>.</span></span>|
|`dateTime`|<span data-ttu-id="f9e6e-432"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-432"><xref:System.DateTime>.</span></span>|
|`dateTimeOffset`|<span data-ttu-id="f9e6e-433"><xref:System.DateTime> i <xref:System.TimeSpan> do przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-433"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="f9e6e-434">Zobacz serializacji DateTimeOffset poniżej.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-434">See DateTimeOffset Serialization below.</span></span>|
|`time`|<span data-ttu-id="f9e6e-435"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-435"><xref:System.String>.</span></span>|
|`date`|<span data-ttu-id="f9e6e-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-436"><xref:System.String>.</span></span>|
|`gYearMonth`|<span data-ttu-id="f9e6e-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-437"><xref:System.String>.</span></span>|
|`gYear`|<span data-ttu-id="f9e6e-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-438"><xref:System.String>.</span></span>|
|`gMonthDay`|<span data-ttu-id="f9e6e-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-439"><xref:System.String>.</span></span>|
|`gDay`|<span data-ttu-id="f9e6e-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-440"><xref:System.String>.</span></span>|
|`gMonth`|<span data-ttu-id="f9e6e-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-441"><xref:System.String>.</span></span>|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<span data-ttu-id="f9e6e-442"><xref:System.Byte> tablicę.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-442"><xref:System.Byte> array.</span></span>|
|`hexBinary`|<span data-ttu-id="f9e6e-443"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-443"><xref:System.String>.</span></span>|
|`float`|<span data-ttu-id="f9e6e-444"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-444"><xref:System.Single>.</span></span>|
|`double`|<span data-ttu-id="f9e6e-445"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-445"><xref:System.Double>.</span></span>|
|`anyURI`|<span data-ttu-id="f9e6e-446"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-446"><xref:System.Uri>.</span></span>|
|`QName`|<span data-ttu-id="f9e6e-447"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-447"><xref:System.Xml.XmlQualifiedName>.</span></span>|
|`string`|<span data-ttu-id="f9e6e-448"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-448"><xref:System.String>.</span></span>|
|`normalizedString`|<span data-ttu-id="f9e6e-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-449"><xref:System.String>.</span></span>|
|`token`|<span data-ttu-id="f9e6e-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-450"><xref:System.String>.</span></span>|
|`language`|<span data-ttu-id="f9e6e-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-451"><xref:System.String>.</span></span>|
|`Name`|<span data-ttu-id="f9e6e-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-452"><xref:System.String>.</span></span>|
|`NCName`|<span data-ttu-id="f9e6e-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-453"><xref:System.String>.</span></span>|
|`ID`|<span data-ttu-id="f9e6e-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-454"><xref:System.String>.</span></span>|
|`IDREF`|<span data-ttu-id="f9e6e-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-455"><xref:System.String>.</span></span>|
|`IDREFS`|<span data-ttu-id="f9e6e-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-456"><xref:System.String>.</span></span>|
|`ENTITY`|<span data-ttu-id="f9e6e-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-457"><xref:System.String>.</span></span>|
|`ENTITIES`|<span data-ttu-id="f9e6e-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-458"><xref:System.String>.</span></span>|
|`NMTOKEN`|<span data-ttu-id="f9e6e-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-459"><xref:System.String>.</span></span>|
|`NMTOKENS`|<span data-ttu-id="f9e6e-460"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-460"><xref:System.String>.</span></span>|
|`decimal`|<span data-ttu-id="f9e6e-461"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-461"><xref:System.Decimal>.</span></span>|
|`integer`|<span data-ttu-id="f9e6e-462"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-462"><xref:System.Int64>.</span></span>|
|`nonPositiveInteger`|<span data-ttu-id="f9e6e-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-463"><xref:System.Int64>.</span></span>|
|`negativeInteger`|<span data-ttu-id="f9e6e-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-464"><xref:System.Int64>.</span></span>|
|`long`|<span data-ttu-id="f9e6e-465"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-465"><xref:System.Int64>.</span></span>|
|`int`|<span data-ttu-id="f9e6e-466"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-466"><xref:System.Int32>.</span></span>|
|`short`|<span data-ttu-id="f9e6e-467"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-467"><xref:System.Int16>.</span></span>|
|`Byte`|<span data-ttu-id="f9e6e-468"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-468"><xref:System.SByte>.</span></span>|
|`nonNegativeInteger`|<span data-ttu-id="f9e6e-469"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-469"><xref:System.Int64>.</span></span>|
|`unsignedLong`|<span data-ttu-id="f9e6e-470"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-470"><xref:System.UInt64>.</span></span>|
|`unsignedInt`|<span data-ttu-id="f9e6e-471"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-471"><xref:System.UInt32>.</span></span>|
|`unsignedShort`|<span data-ttu-id="f9e6e-472"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-472"><xref:System.UInt16>.</span></span>|
|`unsignedByte`|<span data-ttu-id="f9e6e-473"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-473"><xref:System.Byte>.</span></span>|
|`positiveInteger`|<span data-ttu-id="f9e6e-474"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-474"><xref:System.Int64>.</span></span>|

## <a name="iserializable-types-mapping"></a><span data-ttu-id="f9e6e-475">Mapowanie typów ISerializable</span><span class="sxs-lookup"><span data-stu-id="f9e6e-475">ISerializable types mapping</span></span>

<span data-ttu-id="f9e6e-476">W .NET Framework w wersji 1,0 <xref:System.Runtime.Serialization.ISerializable> został wprowadzony jako ogólny mechanizm serializacji obiektów w celu zapewnienia trwałości lub transferu danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-476">In .NET Framework version 1.0, <xref:System.Runtime.Serialization.ISerializable> was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="f9e6e-477">Istnieje wiele typów .NET Framework, które implementują `ISerializable` i mogą być przesyłane między aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-477">There are many .NET Framework types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="f9e6e-478"><xref:System.Runtime.Serialization.DataContractSerializer> naturalnie zapewnia obsługę klas `ISerializable`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-478"><xref:System.Runtime.Serialization.DataContractSerializer> naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="f9e6e-479">`DataContractSerializer` mapuje `ISerializable` typy schematu implementacji, które różnią się tylko nazwą QName (kwalifikowana nazwa) typu i są efektywnymi kolekcjami właściwości.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-479">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="f9e6e-480">Na przykład `DataContractSerializer` mapuje <xref:System.Exception> do następującego typu XSD w `http://schemas.datacontract.org/2004/07/System` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-480">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

<span data-ttu-id="f9e6e-481">Opcjonalny atrybut `ser:FactoryType` zadeklarowany w schemacie serializacji kontraktu danych odwołuje się do klasy fabryki, która może deserializować typ.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-481">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="f9e6e-482">Klasa fabryki musi być częścią kolekcji znanych typów w używanym wystąpieniu `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-482">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="f9e6e-483">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-483">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>

## <a name="datacontract-serialization-schema"></a><span data-ttu-id="f9e6e-484">Schemat serializacji schematu DataContract</span><span class="sxs-lookup"><span data-stu-id="f9e6e-484">DataContract Serialization Schema</span></span>

<span data-ttu-id="f9e6e-485">Wiele schematów wyeksportowanych przez `DataContractSerializer` używać typów, elementów i atrybutów z obszaru nazw serializacji kontraktu danych:</span><span class="sxs-lookup"><span data-stu-id="f9e6e-485">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>

`http://schemas.microsoft.com/2003/10/Serialization`

<span data-ttu-id="f9e6e-486">Poniżej przedstawiono kompletną deklarację schematu serializacji kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-486">The following is a complete Data Contract Serialization schema declaration.</span></span>

```xml
<xs:schema attributeFormDefault="qualified"
   elementFormDefault="qualified"
   targetNamespace =
    "http://schemas.microsoft.com/2003/10/Serialization/"
   xmlns:xs="http://www.w3.org/2001/XMLSchema"
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">

 <!-- Top-level elements for primitive types. -->
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>
 <xs:element name="base64Binary"
       nillable="true" type="xs:base64Binary"/>
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>
 <xs:element name="byte" nillable="true" type="xs:byte"/>
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>
 <xs:element name="double" nillable="true" type="xs:double"/>
 <xs:element name="float" nillable="true" type="xs:float"/>
 <xs:element name="int" nillable="true" type="xs:int"/>
 <xs:element name="long" nillable="true" type="xs:long"/>
 <xs:element name="QName" nillable="true" type="xs:QName"/>
 <xs:element name="short" nillable="true" type="xs:short"/>
 <xs:element name="string" nillable="true" type="xs:string"/>
 <xs:element name="unsignedByte"
       nillable="true" type="xs:unsignedByte"/>
 <xs:element name="unsignedInt"
       nillable="true" type="xs:unsignedInt"/>
 <xs:element name="unsignedLong"
       nillable="true" type="xs:unsignedLong"/>
 <xs:element name="unsignedShort"
       nillable="true" type="xs:unsignedShort"/>

 <!-- Primitive types introduced for certain .NET simple types. -->
 <xs:element name="char" nillable="true" type="tns:char"/>
 <xs:simpleType name="char">
  <xs:restriction base="xs:int"/>
 </xs:simpleType>

 <!-- xs:duration is restricted to an ordered value space,
    to map to System.TimeSpan -->
 <xs:element name="duration" nillable="true" type="tns:duration"/>
 <xs:simpleType name="duration">
  <xs:restriction base="xs:duration">
   <xs:pattern
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>
  </xs:restriction>
 </xs:simpleType>

 <xs:element name="guid" nillable="true" type="tns:guid"/>
 <xs:simpleType name="guid">
  <xs:restriction base="xs:string">
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>
  </xs:restriction>
 </xs:simpleType>

 <!-- This is used for schemas exported from ISerializable type. -->
 <xs:attribute name="FactoryType" type="xs:QName"/>
</xs:schema>
```

<span data-ttu-id="f9e6e-487">Należy zwrócić uwagę na następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="f9e6e-487">The following should be noted:</span></span>

- <span data-ttu-id="f9e6e-488">`ser:char` jest wprowadzany do reprezentowania znaków Unicode typu <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-488">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>

- <span data-ttu-id="f9e6e-489">`valuespace` `xs:duration` zostanie zredukowany do uporządkowanego zestawu, aby można było go mapować do <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-489">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>

- <span data-ttu-id="f9e6e-490">`FactoryType` jest używany w schematach wyeksportowanych z typów, które pochodzą z <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-490">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>

## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="f9e6e-491">Importowanie schematów nienależących do schematu DataContract</span><span class="sxs-lookup"><span data-stu-id="f9e6e-491">Importing non-DataContract schemas</span></span>

<span data-ttu-id="f9e6e-492">`DataContractSerializer` ma opcję `ImportXmlTypes`, która umożliwia importowanie schematów, które nie są zgodne z profilem XSD `DataContractSerializer` (zobacz Właściwość <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A>).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-492">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="f9e6e-493">Ustawienie tej opcji na `true` umożliwia akceptowanie niezgodnych typów schematów i mapowanie ich do następującej implementacji, <xref:System.Xml.Serialization.IXmlSerializable> Zawijanie tablicy <xref:System.Xml.XmlNode> (tylko nazwa klasy różni się).</span><span class="sxs-lookup"><span data-stu-id="f9e6e-493">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>

```csharp
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]
public partial class Person : object, IXmlSerializable
{
  private XmlNode[] nodesField;
  private static XmlQualifiedName typeName =
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");
  public XmlNode[] Nodes
  {
    get {return this.nodesField;}
    set {this.nodesField = value;}
  }
  public void ReadXml(XmlReader reader)
  {
    this.nodesField = XmlSerializableServices.ReadNodes(reader);
  }
  public void WriteXml(XmlWriter writer)
  {
    XmlSerializableServices.WriteNodes(writer, this.Nodes);
  }
  public System.Xml.Schema.XmlSchema GetSchema()
  {
    return null;
  }
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)
  {
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);
    return typeName;
  }
}
```

## <a name="datetimeoffset-serialization"></a><span data-ttu-id="f9e6e-494">Serializacja DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="f9e6e-494">DateTimeOffset Serialization</span></span>

<span data-ttu-id="f9e6e-495"><xref:System.DateTimeOffset> nie jest traktowana jako typ pierwotny.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-495">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="f9e6e-496">Zamiast tego jest serializowany jako element złożony z dwiema częściami.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-496">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="f9e6e-497">Pierwsza część reprezentuje datę i godzinę, a druga część reprezentuje przesunięcie od daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-497">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="f9e6e-498">Przykład serializowanej wartości DateTimeOffset jest przedstawiony w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f9e6e-498">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>

```xml
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">
  <DateTime i:type="b:dateTime" xmlns=""
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00
  </DateTime>
  <OffsetMinutes i:type="b:short" xmlns=""
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480
   </OffsetMinutes>
</OffSet>
```

<span data-ttu-id="f9e6e-499">Schemat jest następujący:</span><span class="sxs-lookup"><span data-stu-id="f9e6e-499">The schema is as follows.</span></span>

```xml
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">
   <xs:complexType name="DateTimeOffset">
      <xs:sequence minOccurs="1" maxOccurs="1">
         <xs:element name="DateTime" type="xs:dateTime"
         minOccurs="1" maxOccurs="1" />
         <xs:element name="OffsetMinutes" type="xs:short"
         minOccurs="1" maxOccurs="1" />
      </xs:sequence>
   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a><span data-ttu-id="f9e6e-500">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9e6e-500">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [<span data-ttu-id="f9e6e-501">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="f9e6e-501">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
