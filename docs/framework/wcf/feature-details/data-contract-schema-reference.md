---
title: Odwołanie do schematu kontraktu danych
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: a4ddaaea2133a8adf5271628f442644194a7f453
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857184"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="5ee63-102">Odwołanie do schematu kontraktu danych</span><span class="sxs-lookup"><span data-stu-id="5ee63-102">Data Contract Schema Reference</span></span>
<span data-ttu-id="5ee63-103">W tym temacie opisano podzbioru elementu schematu XML (XSD) używane przez <xref:System.Runtime.Serialization.DataContractSerializer> do opisania wspólnego języka wspólnego (CLR) typy serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="5ee63-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>  
  
## <a name="datacontractserializer-mappings"></a><span data-ttu-id="5ee63-104">Mapowania elementu DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="5ee63-104">DataContractSerializer Mappings</span></span>  
 <span data-ttu-id="5ee63-105">`DataContractSerializer` Typy CLR jest mapowany do XSD, gdy metadane są eksportowane z usługi Windows Communication Foundation (WCF) przy użyciu punktu końcowego metadanych lub [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5ee63-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="5ee63-106">Aby uzyskać więcej informacji, zobacz [serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="5ee63-106">For more information, see [Data Contract Serializer](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span></span>  
  
 <span data-ttu-id="5ee63-107">`DataContractSerializer` Również mapuje XSD do typów CLR stosowania Svcutil.exe dostępu do sieci Web Services Description Language (WSDL) lub XSD dokumentów i generować kontrakty danych dotyczących usług i klientów.</span><span class="sxs-lookup"><span data-stu-id="5ee63-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>  
  
 <span data-ttu-id="5ee63-108">Tylko te wystąpienia schematu XML, które są zgodne z wymagania określone w tym dokumencie mogą być mapowane na typy CLR za pomocą funkcji `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>  
  
### <a name="support-levels"></a><span data-ttu-id="5ee63-109">Poziomy pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="5ee63-109">Support Levels</span></span>  
 <span data-ttu-id="5ee63-110">`DataContractSerializer` Zawiera następujące poziomy pomocy technicznej dla danej funkcji schematu XML:</span><span class="sxs-lookup"><span data-stu-id="5ee63-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>  
  
- <span data-ttu-id="5ee63-111">**Obsługiwane**.</span><span class="sxs-lookup"><span data-stu-id="5ee63-111">**Supported**.</span></span> <span data-ttu-id="5ee63-112">Brak jawnego mapowania z tej funkcji CLR typy atrybutów (lub obu tych) przy użyciu `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>  
  
- <span data-ttu-id="5ee63-113">**Ignorowane**.</span><span class="sxs-lookup"><span data-stu-id="5ee63-113">**Ignored**.</span></span> <span data-ttu-id="5ee63-114">Funkcja jest dozwolona w schematach importowane przez `DataContractSerializer`, ale nie ma wpływu na generowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="5ee63-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>  
  
- <span data-ttu-id="5ee63-115">**Dostęp zabroniony**.</span><span class="sxs-lookup"><span data-stu-id="5ee63-115">**Forbidden**.</span></span> <span data-ttu-id="5ee63-116">`DataContractSerializer` Nie obsługuje importowania schematu za pomocą funkcji.</span><span class="sxs-lookup"><span data-stu-id="5ee63-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="5ee63-117">Na przykład Svcutil.exe, podczas uzyskiwania dostępu do WSDL ze schematem, który używa takich funkcji przełączy się <xref:System.Xml.Serialization.XmlSerializer> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="5ee63-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="5ee63-118">Jest to domyślnie.</span><span class="sxs-lookup"><span data-stu-id="5ee63-118">This is by default.</span></span>  
  
## <a name="general-information"></a><span data-ttu-id="5ee63-119">Informacje ogólne</span><span class="sxs-lookup"><span data-stu-id="5ee63-119">General Information</span></span>  
  
- <span data-ttu-id="5ee63-120">Przestrzeń nazw schematu jest opisany w [schematu XML](https://go.microsoft.com/fwlink/?LinkId=95475).</span><span class="sxs-lookup"><span data-stu-id="5ee63-120">The schema namespace is described at [XML Schema](https://go.microsoft.com/fwlink/?LinkId=95475).</span></span> <span data-ttu-id="5ee63-121">Prefiks "xs" jest używany w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="5ee63-121">The prefix "xs" is used in this document.</span></span>  
  
- <span data-ttu-id="5ee63-122">Wszelkie atrybuty z przestrzeni nazw bez schematu są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-122">Any attributes with a non-schema namespace are ignored.</span></span>  
  
- <span data-ttu-id="5ee63-123">Wszystkie adnotacje (z wyjątkiem tych opisanych w tym dokumencie) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-123">Any annotations (except for those described in this document) are ignored.</span></span>  
  
### <a name="xsschema-attributes"></a><span data-ttu-id="5ee63-124">\<xs:schema>: attributes</span><span class="sxs-lookup"><span data-stu-id="5ee63-124">\<xs:schema>: attributes</span></span>  
  
|<span data-ttu-id="5ee63-125">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ee63-125">Attribute</span></span>|<span data-ttu-id="5ee63-126">DataContract</span><span class="sxs-lookup"><span data-stu-id="5ee63-126">DataContract</span></span>|  
|---------------|------------------|  
|`attributeFormDefault`|<span data-ttu-id="5ee63-127">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-127">Ignored.</span></span>|  
|`blockDefault`|<span data-ttu-id="5ee63-128">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-128">Ignored.</span></span>|  
|`elementFormDefault`|<span data-ttu-id="5ee63-129">Musi być kwalifikowany.</span><span class="sxs-lookup"><span data-stu-id="5ee63-129">Must be qualified.</span></span> <span data-ttu-id="5ee63-130">Wszystkie elementy muszą zakwalifikować się do schematu obsługiwane przez `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="5ee63-131">Można to osiągnąć przez ustawienie albo xs:schema/@elementFormDefault "kwalifikowany" lub przez ustawienie xs:element/@form pozycji "kwalifikowany" w deklaracji każdego pojedynczego elementu.</span><span class="sxs-lookup"><span data-stu-id="5ee63-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|  
|`finalDefault`|<span data-ttu-id="5ee63-132">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-132">Ignored.</span></span>|  
|`Id`|<span data-ttu-id="5ee63-133">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-133">Ignored.</span></span>|  
|`targetNamespace`|<span data-ttu-id="5ee63-134">Obsługiwane i mapowane na przestrzeń nazw kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="5ee63-135">Jeśli ten atrybut nie jest określony, pustą przestrzeń nazw jest używana.</span><span class="sxs-lookup"><span data-stu-id="5ee63-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="5ee63-136">Nie może być zarezerwowaną przestrzenią nazw `http://schemas.microsoft.com/2003/10/Serialization/`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-136">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|  
|`version`|<span data-ttu-id="5ee63-137">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-137">Ignored.</span></span>|  
  
### <a name="xsschema-contents"></a><span data-ttu-id="5ee63-138">\<xs:Schema >: zawartość</span><span class="sxs-lookup"><span data-stu-id="5ee63-138">\<xs:schema>: contents</span></span>  
  
|<span data-ttu-id="5ee63-139">Spis treści</span><span class="sxs-lookup"><span data-stu-id="5ee63-139">Contents</span></span>|<span data-ttu-id="5ee63-140">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-140">Schema</span></span>|  
|--------------|------------|  
|`include`|<span data-ttu-id="5ee63-141">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-141">Supported.</span></span> <span data-ttu-id="5ee63-142">`DataContractSerializer` obsługuje xs: obejmują i xs:import.</span><span class="sxs-lookup"><span data-stu-id="5ee63-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="5ee63-143">Jednak ogranicza Svcutil.exe następujące `xs:include/@schemaLocation` i `xs:import/@location` odwołuje się podczas ładowania metadanych z pliku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="5ee63-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="5ee63-144">Lista plików schematu muszą być przekazywane za pośrednictwem mechanizmu poza pasmem, a nie za pośrednictwem `include` w tym przypadku; `include`dokumentów schematu d są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`redefine`|<span data-ttu-id="5ee63-145">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-145">Forbidden.</span></span> <span data-ttu-id="5ee63-146">Korzystanie z `xs:redefine` jest zabroniona przez `DataContractSerializer` ze względów bezpieczeństwa: `x:redefine` wymaga `schemaLocation` postępowania.</span><span class="sxs-lookup"><span data-stu-id="5ee63-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="5ee63-147">W pewnych okolicznościach Svcutil.exe przy użyciu schematu DataContract ogranicza użycie `schemaLocation`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|  
|`import`|<span data-ttu-id="5ee63-148">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-148">Supported.</span></span> <span data-ttu-id="5ee63-149">`DataContractSerializer` obsługuje `xs:include` i `xs:import`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="5ee63-150">Jednak ogranicza Svcutil.exe następujące `xs:include/@schemaLocation` i `xs:import/@location` odwołuje się podczas ładowania metadanych z pliku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="5ee63-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="5ee63-151">Lista plików schematu muszą być przekazywane za pośrednictwem mechanizmu poza pasmem, a nie za pośrednictwem `include` w tym przypadku; `include`dokumentów schematu d są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`simpleType`|<span data-ttu-id="5ee63-152">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-152">Supported.</span></span> <span data-ttu-id="5ee63-153">Zobacz `xs:simpleType` sekcji.</span><span class="sxs-lookup"><span data-stu-id="5ee63-153">See the `xs:simpleType` section.</span></span>|  
|`complexType`|<span data-ttu-id="5ee63-154">Obsługiwane, mapy i kontrakty danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="5ee63-155">Zobacz `xs:complexType` sekcji.</span><span class="sxs-lookup"><span data-stu-id="5ee63-155">See the `xs:complexType` section.</span></span>|  
|`group`|<span data-ttu-id="5ee63-156">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-156">Ignored.</span></span> <span data-ttu-id="5ee63-157">`DataContractSerializer` nie obsługuje użycia `xs:group`, `xs:attributeGroup`, i `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="5ee63-158">Deklaracje te są ignorowane jako elementy podrzędne `xs:schema`, ale nie może być przywoływany z poziomu `complexType` lub inne konstrukcje obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`attributeGroup`|<span data-ttu-id="5ee63-159">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-159">Ignored.</span></span> <span data-ttu-id="5ee63-160">`DataContractSerializer` nie obsługuje użycia `xs:group`, `xs:attributeGroup`, i `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="5ee63-161">Deklaracje te są ignorowane jako elementy podrzędne `xs:schema`, ale nie może być przywoływany z poziomu `complexType` lub inne konstrukcje obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`element`|<span data-ttu-id="5ee63-162">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-162">Supported.</span></span> <span data-ttu-id="5ee63-163">Zobacz deklarację elementu globalnego (e).</span><span class="sxs-lookup"><span data-stu-id="5ee63-163">See Global Element Declaration (GED).</span></span>|  
|`attribute`|<span data-ttu-id="5ee63-164">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-164">Ignored.</span></span> <span data-ttu-id="5ee63-165">`DataContractSerializer` nie obsługuje użycia `xs:group`, `xs:attributeGroup`, i `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="5ee63-166">Deklaracje te są ignorowane jako elementy podrzędne `xs:schema`, ale nie może być przywoływany z poziomu `complexType` lub inne konstrukcje obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`notation`|<span data-ttu-id="5ee63-167">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-167">Ignored.</span></span>|  
  
## <a name="complex-types--xscomplextype"></a><span data-ttu-id="5ee63-168">Typy złożone — \<xs:complexType ></span><span class="sxs-lookup"><span data-stu-id="5ee63-168">Complex Types – \<xs:complexType></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="5ee63-169">Informacje ogólne</span><span class="sxs-lookup"><span data-stu-id="5ee63-169">General Information</span></span>  
 <span data-ttu-id="5ee63-170">Każdy typ złożony \<xs:complexType > mapuje kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>  
  
### <a name="xscomplextype-attributes"></a><span data-ttu-id="5ee63-171">\<xs:complexType>: attributes</span><span class="sxs-lookup"><span data-stu-id="5ee63-171">\<xs:complexType>: attributes</span></span>  
  
|<span data-ttu-id="5ee63-172">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ee63-172">Attribute</span></span>|<span data-ttu-id="5ee63-173">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-173">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="5ee63-174">Musi mieć wartość false (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="5ee63-174">Must be false (default).</span></span>|  
|`block`|<span data-ttu-id="5ee63-175">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-175">Forbidden.</span></span>|  
|`final`|<span data-ttu-id="5ee63-176">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-176">Ignored.</span></span>|  
|`id`|<span data-ttu-id="5ee63-177">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-177">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="5ee63-178">Musi mieć wartość false (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="5ee63-178">Must be false (default).</span></span>|  
|`name`|<span data-ttu-id="5ee63-179">Obsługiwane i mapowane na nazwie kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="5ee63-180">W przypadku kropki w nazwie, jest podejmowana próba mapowania typu do typu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="5ee63-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="5ee63-181">Na przykład typ złożony o nazwie `A.B` mapuje do kontraktu danych typu to znaczy wewnętrznego typu o nazwie kontraktu danych `A`, ale tylko wtedy, gdy typ kontraktu takich danych nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="5ee63-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="5ee63-182">Możliwe jest więcej niż jeden poziom zagnieżdżenia: na przykład `A.B.C` może być typu wewnętrznego, ale tylko wtedy, gdy `A` i `A.B` zarówno istnieje.</span><span class="sxs-lookup"><span data-stu-id="5ee63-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|  
  
### <a name="xscomplextype-contents"></a><span data-ttu-id="5ee63-183">\<xs:complexType>: contents</span><span class="sxs-lookup"><span data-stu-id="5ee63-183">\<xs:complexType>: contents</span></span>  
  
|<span data-ttu-id="5ee63-184">Spis treści</span><span class="sxs-lookup"><span data-stu-id="5ee63-184">Contents</span></span>|<span data-ttu-id="5ee63-185">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-185">Schema</span></span>|  
|--------------|------------|  
|`simpleContent`|<span data-ttu-id="5ee63-186">Rozszerzenia są zabronione.</span><span class="sxs-lookup"><span data-stu-id="5ee63-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="5ee63-187">Ograniczenie jest dozwolone tylko w `anySimpleType`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-187">Restriction is allowed only from `anySimpleType`.</span></span>|  
|`complexContent`|<span data-ttu-id="5ee63-188">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-188">Supported.</span></span> <span data-ttu-id="5ee63-189">Zobacz "Dziedziczenie".</span><span class="sxs-lookup"><span data-stu-id="5ee63-189">See "Inheritance".</span></span>|  
|`group`|<span data-ttu-id="5ee63-190">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-190">Forbidden.</span></span>|  
|`all`|<span data-ttu-id="5ee63-191">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-191">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="5ee63-192">Zabroniony</span><span class="sxs-lookup"><span data-stu-id="5ee63-192">Forbidden</span></span>|  
|`sequence`|<span data-ttu-id="5ee63-193">Obsługiwane mapują do elementów członkowskich danych kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-193">Supported, maps to data members of a data contract.</span></span>|  
|`attribute`|<span data-ttu-id="5ee63-194">Dostęp zabroniony, nawet w przypadku użycia = "prohibited" (z jednym wyjątkiem).</span><span class="sxs-lookup"><span data-stu-id="5ee63-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="5ee63-195">Obsługiwane są tylko opcjonalne atrybuty z przestrzeni nazw standardowego schematu serializacji.</span><span class="sxs-lookup"><span data-stu-id="5ee63-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="5ee63-196">Nie są mapowane na elementy członkowskie danych w modelu programowania kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="5ee63-197">Obecnie tylko jeden taki atrybut ma znaczenie i został opisany w sekcji ISerializable.</span><span class="sxs-lookup"><span data-stu-id="5ee63-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="5ee63-198">Wszystkie pozostałe są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-198">All others are ignored.</span></span>|  
|`attributeGroup`|<span data-ttu-id="5ee63-199">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-199">Forbidden.</span></span> <span data-ttu-id="5ee63-200">W wersji v1 usługi WCF `DataContractSerializer` ignoruje obecności `attributeGroup` wewnątrz `xs:complexType`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-200">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|  
|`anyAttribute`|<span data-ttu-id="5ee63-201">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-201">Forbidden.</span></span>|  
|<span data-ttu-id="5ee63-202">(pusty)</span><span class="sxs-lookup"><span data-stu-id="5ee63-202">(empty)</span></span>|<span data-ttu-id="5ee63-203">Mapuje do kontraktu danych za pomocą żadnych składowych danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-203">Maps to a data contract with no data members.</span></span>|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="5ee63-204">\<użyto w nim wartości > w typie złożonym: atrybuty</span><span class="sxs-lookup"><span data-stu-id="5ee63-204">\<xs:sequence> in a complex type: attributes</span></span>  
  
|<span data-ttu-id="5ee63-205">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ee63-205">Attribute</span></span>|<span data-ttu-id="5ee63-206">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-206">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="5ee63-207">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-207">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="5ee63-208">Musi mieć wartość 1 (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5ee63-208">Must be 1 (default).</span></span>|  
|`minOccurs`|<span data-ttu-id="5ee63-209">Musi mieć wartość 1 (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5ee63-209">Must be 1 (default).</span></span>|  
  
### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="5ee63-210">\<użyto w nim wartości > w typie złożonym: zawartość</span><span class="sxs-lookup"><span data-stu-id="5ee63-210">\<xs:sequence> in a complex type: contents</span></span>  
  
|<span data-ttu-id="5ee63-211">Spis treści</span><span class="sxs-lookup"><span data-stu-id="5ee63-211">Contents</span></span>|<span data-ttu-id="5ee63-212">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-212">Schema</span></span>|  
|--------------|------------|  
|`element`|<span data-ttu-id="5ee63-213">Każde wystąpienie jest mapowany na element członkowski danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-213">Each instance maps to a data member.</span></span>|  
|`group`|<span data-ttu-id="5ee63-214">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-214">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="5ee63-215">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-215">Forbidden.</span></span>|  
|`sequence`|<span data-ttu-id="5ee63-216">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-216">Forbidden.</span></span>|  
|`any`|<span data-ttu-id="5ee63-217">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-217">Forbidden.</span></span>|  
|<span data-ttu-id="5ee63-218">(pusty)</span><span class="sxs-lookup"><span data-stu-id="5ee63-218">(empty)</span></span>|<span data-ttu-id="5ee63-219">Mapuje do kontraktu danych za pomocą żadnych składowych danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-219">Maps to a data contract with no data members.</span></span>|  
  
## <a name="elements--xselement"></a><span data-ttu-id="5ee63-220">Elementy — \<elementu xs: element ></span><span class="sxs-lookup"><span data-stu-id="5ee63-220">Elements – \<xs:element></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="5ee63-221">Informacje ogólne</span><span class="sxs-lookup"><span data-stu-id="5ee63-221">General Information</span></span>  
 <span data-ttu-id="5ee63-222">`<xs:element>` może wystąpić w następujących okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="5ee63-222">`<xs:element>` can occur in the following contexts:</span></span>  
  
- <span data-ttu-id="5ee63-223">Może wystąpić w `<xs:sequence>`, która opisuje element członkowski danych kontraktu regularnych danych (bez kolekcji).</span><span class="sxs-lookup"><span data-stu-id="5ee63-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="5ee63-224">W tym przypadku `maxOccurs` atrybut musi mieć wartość 1.</span><span class="sxs-lookup"><span data-stu-id="5ee63-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="5ee63-225">(Wartość 0 nie jest dozwolona).</span><span class="sxs-lookup"><span data-stu-id="5ee63-225">(A value of 0 is not allowed).</span></span>  
  
- <span data-ttu-id="5ee63-226">Może wystąpić w `<xs:sequence>`, która opisuje składowa danych klasy kontraktu danych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5ee63-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="5ee63-227">W tym przypadku `maxOccurs` atrybut musi być większa niż 1 lub "niepowiązanego".</span><span class="sxs-lookup"><span data-stu-id="5ee63-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>  
  
- <span data-ttu-id="5ee63-228">Może wystąpić w `<xs:schema>` jako globalny Element deklaracji (e).</span><span class="sxs-lookup"><span data-stu-id="5ee63-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="5ee63-229">\<elementu xs: element > maxOccurs = 1, w ramach \<użyto w nim wartości > (elementy członkowskie danych)</span><span class="sxs-lookup"><span data-stu-id="5ee63-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>  
  
|<span data-ttu-id="5ee63-230">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ee63-230">Attribute</span></span>|<span data-ttu-id="5ee63-231">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-231">Schema</span></span>|  
|---------------|------------|  
|`ref`|<span data-ttu-id="5ee63-232">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-232">Forbidden.</span></span>|  
|`name`|<span data-ttu-id="5ee63-233">Obsługiwane, mapy i nazwę elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-233">Supported, maps to the data member name.</span></span>|  
|`type`|<span data-ttu-id="5ee63-234">Obsługiwane, mapy, element członkowski danych jest typu.</span><span class="sxs-lookup"><span data-stu-id="5ee63-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="5ee63-235">Aby uzyskać więcej informacji zobacz typ/element mapowania.</span><span class="sxs-lookup"><span data-stu-id="5ee63-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="5ee63-236">Jeśli nie określono (i elementu nie zawiera typu anonimowego) `xs:anyType` zakłada, że.</span><span class="sxs-lookup"><span data-stu-id="5ee63-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|  
|`block`|<span data-ttu-id="5ee63-237">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-237">Ignored.</span></span>|  
|`default`|<span data-ttu-id="5ee63-238">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-238">Forbidden.</span></span>|  
|`fixed`|<span data-ttu-id="5ee63-239">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-239">Forbidden.</span></span>|  
|`form`|<span data-ttu-id="5ee63-240">Musi być kwalifikowany.</span><span class="sxs-lookup"><span data-stu-id="5ee63-240">Must be qualified.</span></span> <span data-ttu-id="5ee63-241">Ten atrybut można określać za pośrednictwem `elementFormDefault` na `xs:schema`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|  
|`id`|<span data-ttu-id="5ee63-242">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-242">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="5ee63-243">1</span><span class="sxs-lookup"><span data-stu-id="5ee63-243">1</span></span>|  
|`minOccurs`|<span data-ttu-id="5ee63-244">Mapuje <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość element członkowski danych (`IsRequired` jest istotne, kiedy `minOccurs` 1).</span><span class="sxs-lookup"><span data-stu-id="5ee63-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|  
|`nillable`|<span data-ttu-id="5ee63-245">Mapowanie typu ma wpływ na.</span><span class="sxs-lookup"><span data-stu-id="5ee63-245">Affects type mapping.</span></span> <span data-ttu-id="5ee63-246">Zobacz mapowania typu/podstawowego.</span><span class="sxs-lookup"><span data-stu-id="5ee63-246">See Type/primitive mapping.</span></span>|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="5ee63-247">\<elementu xs: element > za pomocą elementu maxOccurs > 1 w ramach \<użyto w nim wartości > (kolekcji)</span><span class="sxs-lookup"><span data-stu-id="5ee63-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>  
  
- <span data-ttu-id="5ee63-248">Mapuje <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>  
  
- <span data-ttu-id="5ee63-249">Typy kolekcji tylko jednego elementu xs: element jest dozwolony w ramach użyto w nim wartości.</span><span class="sxs-lookup"><span data-stu-id="5ee63-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>  
  
 <span data-ttu-id="5ee63-250">Kolekcje mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="5ee63-250">Collections can be of the following types:</span></span>  
  
- <span data-ttu-id="5ee63-251">Kolekcje regularnie (na przykład, tablice).</span><span class="sxs-lookup"><span data-stu-id="5ee63-251">Regular collections (for example, arrays).</span></span>  
  
- <span data-ttu-id="5ee63-252">Kolekcje słownika (mapowanie jedną wartość na inny; na przykład <xref:System.Collections.Hashtable>).</span><span class="sxs-lookup"><span data-stu-id="5ee63-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>  
  
- <span data-ttu-id="5ee63-253">Jedyną różnicą między słownik i tablicę typu pary klucz/wartość jest w wygenerowanym modelu programowania.</span><span class="sxs-lookup"><span data-stu-id="5ee63-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="5ee63-254">Istnieje mechanizm adnotację schematu, który może służyć do wskazywania danego typu kolekcji słownika.</span><span class="sxs-lookup"><span data-stu-id="5ee63-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>  
  
 <span data-ttu-id="5ee63-255">Reguły dotyczące `ref`, `block`, `default`, `fixed`, `form`, i `id` atrybuty są takie same jak w przypadku innych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5ee63-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="5ee63-256">Inne atrybuty obejmuje występujące w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="5ee63-256">Other attributes include those in the following table.</span></span>  
  
|<span data-ttu-id="5ee63-257">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ee63-257">Attribute</span></span>|<span data-ttu-id="5ee63-258">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-258">Schema</span></span>|  
|---------------|------------|  
|`name`|<span data-ttu-id="5ee63-259">Obsługiwane, mapy i <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> właściwość `CollectionDataContractAttribute` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5ee63-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|  
|`type`|<span data-ttu-id="5ee63-260">Obsługiwane, mapy do typu, przechowywane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5ee63-260">Supported, maps to the type stored in the collection.</span></span>|  
|`maxOccurs`|<span data-ttu-id="5ee63-261">Większa niż 1 lub "niepowiązanego".</span><span class="sxs-lookup"><span data-stu-id="5ee63-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="5ee63-262">Schemat kontrolera domeny, należy użyć "niepowiązanego".</span><span class="sxs-lookup"><span data-stu-id="5ee63-262">The DC schema should use "unbounded".</span></span>|  
|`minOccurs`|<span data-ttu-id="5ee63-263">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-263">Ignored.</span></span>|  
|`nillable`|<span data-ttu-id="5ee63-264">Mapowanie typu ma wpływ na.</span><span class="sxs-lookup"><span data-stu-id="5ee63-264">Affects type mapping.</span></span> <span data-ttu-id="5ee63-265">Ten atrybut jest ignorowany dla kolekcji słownika.</span><span class="sxs-lookup"><span data-stu-id="5ee63-265">This attribute is ignored for dictionary collections.</span></span>|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="5ee63-266">\<elementu xs: element > w ramach \<xs:schema > deklaracji elementu globalnego</span><span class="sxs-lookup"><span data-stu-id="5ee63-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>  
  
- <span data-ttu-id="5ee63-267">Globalny Element deklaracji (Jściowa) jako typ w schemacie, ma taką samą nazwę i przestrzeń nazw lub definiujący typu anonimowego wewnątrz siebie, jest nazywany ma zostać skojarzony z typem.</span><span class="sxs-lookup"><span data-stu-id="5ee63-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>  
  
- <span data-ttu-id="5ee63-268">Eksport schematu: GEDs skojarzone są generowane dla każdego wygenerowanego typu proste i złożone.</span><span class="sxs-lookup"><span data-stu-id="5ee63-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>  
  
- <span data-ttu-id="5ee63-269">Serializacji/deserializacji: GEDs skojarzone są używane jako elementy główne dla typu.</span><span class="sxs-lookup"><span data-stu-id="5ee63-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>  
  
- <span data-ttu-id="5ee63-270">Importowanie schematu: skojarzone GEDs nie są wymagane i są ignorowane, jeśli używają następujących reguł (o ile nie mogą definiować typy).</span><span class="sxs-lookup"><span data-stu-id="5ee63-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>  
  
|<span data-ttu-id="5ee63-271">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ee63-271">Attribute</span></span>|<span data-ttu-id="5ee63-272">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-272">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="5ee63-273">Musi mieć wartość false w GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="5ee63-273">Must be false for associated GEDs.</span></span>|  
|`block`|<span data-ttu-id="5ee63-274">Dostęp zabroniony w GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="5ee63-274">Forbidden in associated GEDs.</span></span>|  
|`default`|<span data-ttu-id="5ee63-275">Dostęp zabroniony w GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="5ee63-275">Forbidden in associated GEDs.</span></span>|  
|`final`|<span data-ttu-id="5ee63-276">Musi mieć wartość false w GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="5ee63-276">Must be false for associated GEDs.</span></span>|  
|`fixed`|<span data-ttu-id="5ee63-277">Dostęp zabroniony w GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="5ee63-277">Forbidden in associated GEDs.</span></span>|  
|`id`|<span data-ttu-id="5ee63-278">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-278">Ignored.</span></span>|  
|`name`|<span data-ttu-id="5ee63-279">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-279">Supported.</span></span> <span data-ttu-id="5ee63-280">Zobacz definicję GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="5ee63-280">See the definition of associated GEDs.</span></span>|  
|`nillable`|<span data-ttu-id="5ee63-281">Muszą być spełnione GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="5ee63-281">Must be true for associated GEDs.</span></span>|  
|`substitutionGroup`|<span data-ttu-id="5ee63-282">Dostęp zabroniony w GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="5ee63-282">Forbidden in associated GEDs.</span></span>|  
|`type`|<span data-ttu-id="5ee63-283">Obsługiwane i musi odpowiadać typowi skojarzone dla skojarzonego GEDs (chyba że element zawiera typ anonimowy).</span><span class="sxs-lookup"><span data-stu-id="5ee63-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|  
  
### <a name="xselement-contents"></a><span data-ttu-id="5ee63-284">\<elementu xs: element >: zawartość</span><span class="sxs-lookup"><span data-stu-id="5ee63-284">\<xs:element>: contents</span></span>  
  
|<span data-ttu-id="5ee63-285">Spis treści</span><span class="sxs-lookup"><span data-stu-id="5ee63-285">Contents</span></span>|<span data-ttu-id="5ee63-286">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-286">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="5ee63-287">Supported.\*</span><span class="sxs-lookup"><span data-stu-id="5ee63-287">Supported.\*</span></span>|  
|`complexType`|<span data-ttu-id="5ee63-288">Supported.\*</span><span class="sxs-lookup"><span data-stu-id="5ee63-288">Supported.\*</span></span>|  
|`unique`|<span data-ttu-id="5ee63-289">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-289">Ignored.</span></span>|  
|`key`|<span data-ttu-id="5ee63-290">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-290">Ignored.</span></span>|  
|`keyref`|<span data-ttu-id="5ee63-291">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-291">Ignored.</span></span>|  
|<span data-ttu-id="5ee63-292">(pusty)</span><span class="sxs-lookup"><span data-stu-id="5ee63-292">(blank)</span></span>|<span data-ttu-id="5ee63-293">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-293">Supported.</span></span>|  
  
 <span data-ttu-id="5ee63-294">\* Korzystając z `simpleType` i `complexType,` mapowania dla typów anonimowych jest tak samo nieanonimowym typów, z tą różnicą, że nie ma żadnych umów anonimowych danych, więc kontrakt danych o podanej nazwie zostanie utworzony, z użyciem nazwy wygenerowanej pochodzi od nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="5ee63-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="5ee63-295">Na poniższej liście są następujące reguły dla typów anonimowych:</span><span class="sxs-lookup"><span data-stu-id="5ee63-295">The rules for anonymous types are in the following list:</span></span>  
  
- <span data-ttu-id="5ee63-296">Szczegóły implementacji usługi WCF: Jeśli `xs:element` nazwa nie zawiera kropek, typu anonimowego mapuje do typu wewnętrznego typu kontraktu danych zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-296">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="5ee63-297">Jeśli nazwa zawiera kropek, wynikowy typ kontraktu danych jest niezależne (nie wewnętrznego typu).</span><span class="sxs-lookup"><span data-stu-id="5ee63-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>  
  
- <span data-ttu-id="5ee63-298">Nazwa kontraktu wygenerowane dane typu wewnętrznego jest nazwie kontraktu danych typu zewnętrznego, następnie kropkę i nazwę elementu i ciągu "Type".</span><span class="sxs-lookup"><span data-stu-id="5ee63-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>  
  
- <span data-ttu-id="5ee63-299">Jeśli kontraktu danych o takiej nazwie już istnieje, nazwa jest unikatowa, dodając "1", "2", "3", i tak dalej do momentu utworzenia unikatowej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5ee63-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>  
  
## <a name="simple-types---xssimpletype"></a><span data-ttu-id="5ee63-300">Typy proste — \<xs:simpleType ></span><span class="sxs-lookup"><span data-stu-id="5ee63-300">Simple Types - \<xs:simpleType></span></span>  
  
### <a name="xssimpletype-attributes"></a><span data-ttu-id="5ee63-301">\<xs:simpleType >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="5ee63-301">\<xs:simpleType>: attributes</span></span>  
  
|<span data-ttu-id="5ee63-302">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ee63-302">Attribute</span></span>|<span data-ttu-id="5ee63-303">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-303">Schema</span></span>|  
|---------------|------------|  
|`final`|<span data-ttu-id="5ee63-304">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-304">Ignored.</span></span>|  
|`id`|<span data-ttu-id="5ee63-305">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-305">Ignored.</span></span>|  
|`name`|<span data-ttu-id="5ee63-306">Obsługiwane, mapy do danych nazwę kontraktu.</span><span class="sxs-lookup"><span data-stu-id="5ee63-306">Supported, maps to the data contract name.</span></span>|  
  
### <a name="xssimpletype-contents"></a><span data-ttu-id="5ee63-307">\<xs:simpleType >: zawartość</span><span class="sxs-lookup"><span data-stu-id="5ee63-307">\<xs:simpleType>: contents</span></span>  
  
|<span data-ttu-id="5ee63-308">Spis treści</span><span class="sxs-lookup"><span data-stu-id="5ee63-308">Contents</span></span>|<span data-ttu-id="5ee63-309">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-309">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="5ee63-310">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-310">Supported.</span></span> <span data-ttu-id="5ee63-311">Mapuje do wyliczenia kontraktów danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="5ee63-312">Ten atrybut jest ignorowany, jeśli nie jest zgodny ze wzorcem wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5ee63-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="5ee63-313">Zobacz `xs:simpleType` sekcji ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="5ee63-313">See the `xs:simpleType` restrictions section.</span></span>|  
|`list`|<span data-ttu-id="5ee63-314">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-314">Supported.</span></span> <span data-ttu-id="5ee63-315">Mapuje flagi kontraktów danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5ee63-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="5ee63-316">Zobacz `xs:simpleType` Wyświetla sekcji.</span><span class="sxs-lookup"><span data-stu-id="5ee63-316">See the `xs:simpleType` lists section.</span></span>|  
|`union`|<span data-ttu-id="5ee63-317">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-317">Forbidden.</span></span>|  
  
### <a name="xsrestriction"></a><span data-ttu-id="5ee63-318">\<xs:restriction></span><span class="sxs-lookup"><span data-stu-id="5ee63-318">\<xs:restriction></span></span>  
  
- <span data-ttu-id="5ee63-319">Ograniczenia typu złożonego są obsługiwane tylko dla podstawowego = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="5ee63-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>  
  
- <span data-ttu-id="5ee63-320">Ograniczenia typu prostego `xs:string` nie mają żadnych ograniczeń aspekty inne niż `xs:enumeration` są mapowane na wyliczenie kontraktów danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>  
  
- <span data-ttu-id="5ee63-321">Wszystkie inne ograniczenia typu prostego są mapowane na typy, które ograniczają one.</span><span class="sxs-lookup"><span data-stu-id="5ee63-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="5ee63-322">Na przykład ograniczenia `xs:int` mapuje na liczbę całkowitą, podobnie jak `xs:int` sam przeprowadza.</span><span class="sxs-lookup"><span data-stu-id="5ee63-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="5ee63-323">Aby uzyskać więcej informacji na temat mapowania typów pierwotnych Zobacz typ/element mapowania.</span><span class="sxs-lookup"><span data-stu-id="5ee63-323">For more information about primitive type mapping, see Type/primitive mapping.</span></span>  
  
### <a name="xsrestriction-attributes"></a><span data-ttu-id="5ee63-324">\<xs:restriction >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="5ee63-324">\<xs:restriction>: attributes</span></span>  
  
|<span data-ttu-id="5ee63-325">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ee63-325">Attribute</span></span>|<span data-ttu-id="5ee63-326">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-326">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="5ee63-327">Musi być obsługiwanego typu prostego lub `xs:anyType`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-327">Must be a supported simple type or `xs:anyType`.</span></span>|  
|`id`|<span data-ttu-id="5ee63-328">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-328">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="5ee63-329">\<xs:restriction > dla wszystkich innych przypadkach: zawartość</span><span class="sxs-lookup"><span data-stu-id="5ee63-329">\<xs:restriction> for all other cases: contents</span></span>  
  
|<span data-ttu-id="5ee63-330">Spis treści</span><span class="sxs-lookup"><span data-stu-id="5ee63-330">Contents</span></span>|<span data-ttu-id="5ee63-331">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-331">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="5ee63-332">Jeśli jest obecna, musi pochodzić od obsługiwanego typu pierwotnego.</span><span class="sxs-lookup"><span data-stu-id="5ee63-332">If present, must be derived from a supported primitive type.</span></span>|  
|`minExclusive`|<span data-ttu-id="5ee63-333">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-333">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="5ee63-334">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-334">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="5ee63-335">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-335">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="5ee63-336">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-336">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="5ee63-337">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-337">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="5ee63-338">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-338">Ignored.</span></span>|  
|`length`|<span data-ttu-id="5ee63-339">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-339">Ignored.</span></span>|  
|`minLength`|<span data-ttu-id="5ee63-340">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-340">Ignored.</span></span>|  
|`maxLength`|<span data-ttu-id="5ee63-341">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-341">Ignored.</span></span>|  
|`enumeration`|<span data-ttu-id="5ee63-342">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-342">Ignored.</span></span>|  
|`whiteSpace`|<span data-ttu-id="5ee63-343">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-343">Ignored.</span></span>|  
|`pattern`|<span data-ttu-id="5ee63-344">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-344">Ignored.</span></span>|  
|<span data-ttu-id="5ee63-345">(pusty)</span><span class="sxs-lookup"><span data-stu-id="5ee63-345">(blank)</span></span>|<span data-ttu-id="5ee63-346">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-346">Supported.</span></span>|  
  
## <a name="enumeration"></a><span data-ttu-id="5ee63-347">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5ee63-347">Enumeration</span></span>  
  
### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="5ee63-348">\<xs:restriction > dla wyliczenia: atrybuty</span><span class="sxs-lookup"><span data-stu-id="5ee63-348">\<xs:restriction> for enumerations: attributes</span></span>  
  
|<span data-ttu-id="5ee63-349">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ee63-349">Attribute</span></span>|<span data-ttu-id="5ee63-350">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-350">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="5ee63-351">Jeśli jest obecna, musi być `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-351">If present, must be `xs:string`.</span></span>|  
|`id`|<span data-ttu-id="5ee63-352">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-352">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="5ee63-353">\<xs:restriction > dla wyliczenia: zawartość</span><span class="sxs-lookup"><span data-stu-id="5ee63-353">\<xs:restriction> for enumerations: contents</span></span>  
  
|<span data-ttu-id="5ee63-354">Spis treści</span><span class="sxs-lookup"><span data-stu-id="5ee63-354">Contents</span></span>|<span data-ttu-id="5ee63-355">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-355">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="5ee63-356">Jeśli jest obecny, muszą być ograniczenia wyliczenia obsługiwane przez kontraktu danych (w tej sekcji).</span><span class="sxs-lookup"><span data-stu-id="5ee63-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|  
|`minExclusive`|<span data-ttu-id="5ee63-357">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-357">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="5ee63-358">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-358">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="5ee63-359">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-359">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="5ee63-360">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-360">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="5ee63-361">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-361">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="5ee63-362">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-362">Ignored.</span></span>|  
|`length`|<span data-ttu-id="5ee63-363">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-363">Forbidden.</span></span>|  
|`minLength`|<span data-ttu-id="5ee63-364">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-364">Forbidden.</span></span>|  
|`maxLength`|<span data-ttu-id="5ee63-365">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-365">Forbidden.</span></span>|  
|`enumeration`|<span data-ttu-id="5ee63-366">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-366">Supported.</span></span> <span data-ttu-id="5ee63-367">Wyliczenie "id" jest ignorowana, a "value" mapowany na nazwę wartości wyliczenia umowy danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|  
|`whiteSpace`|<span data-ttu-id="5ee63-368">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-368">Forbidden.</span></span>|  
|`pattern`|<span data-ttu-id="5ee63-369">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-369">Forbidden.</span></span>|  
|<span data-ttu-id="5ee63-370">(pusty)</span><span class="sxs-lookup"><span data-stu-id="5ee63-370">(empty)</span></span>|<span data-ttu-id="5ee63-371">Obsługiwane, mapy do typu puste wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="5ee63-371">Supported, maps to empty enumeration type.</span></span>|  
  
 <span data-ttu-id="5ee63-372">Poniższy kod przedstawia klasy wyliczenie C#.</span><span class="sxs-lookup"><span data-stu-id="5ee63-372">The following code shows a C# enumeration class.</span></span>  
  
```csharp  
public enum MyEnum  
{  
  first = 3,  
  second = 4,  
  third =5  
}  
```  
  
 <span data-ttu-id="5ee63-373">Ta klasa jest mapowany na poniższe schemat, `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-373">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="5ee63-374">Jeśli wartości wyliczenia, zacznij od 1, `xs:annotation` bloki nie są generowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-374">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>  
  
```xml  
<xs:simpleType name="MyEnum">  
<xs:restriction base="xs:string">  
 <xs:enumeration value="first">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     3  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
 <xs:enumeration value="second">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     4  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
</xs:restriction>  
</xs:simpleType>  
```  
  
### <a name="xslist"></a><span data-ttu-id="5ee63-375">\<xs:list></span><span class="sxs-lookup"><span data-stu-id="5ee63-375">\<xs:list></span></span>  
 <span data-ttu-id="5ee63-376">`DataContractSerializer` Typy wyliczeniowe mapy, oznaczone `System.FlagsAttribute` do `xs:list` pochodną `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-376">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="5ee63-377">Żadne inne `xs:list` różnice są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-377">No other `xs:list` variations are supported.</span></span>  
  
### <a name="xslist-attributes"></a><span data-ttu-id="5ee63-378">\<xs:list >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="5ee63-378">\<xs:list>: attributes</span></span>  
  
|<span data-ttu-id="5ee63-379">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ee63-379">Attribute</span></span>|<span data-ttu-id="5ee63-380">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-380">Schema</span></span>|  
|---------------|------------|  
|`itemType`|<span data-ttu-id="5ee63-381">Forbidden.</span><span class="sxs-lookup"><span data-stu-id="5ee63-381">Forbidden.</span></span>|  
|`id`|<span data-ttu-id="5ee63-382">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-382">Ignored.</span></span>|  
  
### <a name="xslist-contents"></a><span data-ttu-id="5ee63-383">\<xs:list>: contents</span><span class="sxs-lookup"><span data-stu-id="5ee63-383">\<xs:list>: contents</span></span>  
  
|<span data-ttu-id="5ee63-384">Spis treści</span><span class="sxs-lookup"><span data-stu-id="5ee63-384">Contents</span></span>|<span data-ttu-id="5ee63-385">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-385">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="5ee63-386">Musi być ograniczenie `xs:string` przy użyciu `xs:enumeration` zestawu reguł.</span><span class="sxs-lookup"><span data-stu-id="5ee63-386">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|  
  
 <span data-ttu-id="5ee63-387">Jeśli wartość wyliczenia nie jest zgodna z potęgą liczby 2 postępu (wartość domyślna dla flag), wartość jest przechowywana w `xs:annotation/xs:appInfo/ser:EnumerationValue` elementu.</span><span class="sxs-lookup"><span data-stu-id="5ee63-387">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>  
  
 <span data-ttu-id="5ee63-388">Na przykład poniższy kod flagi typem wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5ee63-388">For example, the following code flags an enumeration type.</span></span>  
  
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
  
 <span data-ttu-id="5ee63-389">Ten typ jest mapowany na zgodny z następującym schematem.</span><span class="sxs-lookup"><span data-stu-id="5ee63-389">This type maps to the following schema.</span></span>  
  
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
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">16</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
          <xs:enumeration value="AuthWindowsLiveID">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">64</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:list>  
  </xs:simpleType>  
```  
  
## <a name="inheritance"></a><span data-ttu-id="5ee63-390">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="5ee63-390">Inheritance</span></span>  
  
### <a name="general-rules"></a><span data-ttu-id="5ee63-391">Ogólne zasady</span><span class="sxs-lookup"><span data-stu-id="5ee63-391">General rules</span></span>  
 <span data-ttu-id="5ee63-392">Kontrakt danych może dziedziczyć z innego kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-392">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="5ee63-393">Takie kontraktów danych mapy podstawowy i są uzyskiwane przez typy rozszerzeń przy użyciu `<xs:extension>` konstrukcji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="5ee63-393">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>  
  
 <span data-ttu-id="5ee63-394">Kontrakt danych nie może dziedziczyć z kontraktu danych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5ee63-394">A data contract cannot inherit from a collection data contract.</span></span>  
  
 <span data-ttu-id="5ee63-395">Na przykład poniższy kod jest kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-395">For example, the following code is a data contract.</span></span>  
  
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
  
 <span data-ttu-id="5ee63-396">Ten kontrakt danych mapuje następującą deklarację typu schematu XML.</span><span class="sxs-lookup"><span data-stu-id="5ee63-396">This data contract maps to the following XML Schema type declaration.</span></span>  
  
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
  
### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="5ee63-397">\<xs:complexContent>: attributes</span><span class="sxs-lookup"><span data-stu-id="5ee63-397">\<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="5ee63-398">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ee63-398">Attribute</span></span>|<span data-ttu-id="5ee63-399">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-399">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="5ee63-400">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-400">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="5ee63-401">Musi mieć wartość false.</span><span class="sxs-lookup"><span data-stu-id="5ee63-401">Must be false.</span></span>|  
  
### <a name="xscomplexcontent-contents"></a><span data-ttu-id="5ee63-402">\<xs:complexContent>: contents</span><span class="sxs-lookup"><span data-stu-id="5ee63-402">\<xs:complexContent>: contents</span></span>  
  
|<span data-ttu-id="5ee63-403">Spis treści</span><span class="sxs-lookup"><span data-stu-id="5ee63-403">Contents</span></span>|<span data-ttu-id="5ee63-404">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-404">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="5ee63-405">Dostęp zabroniony, z wyjątkiem sytuacji, podstawowy = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="5ee63-405">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="5ee63-406">Jest odpowiednikiem umieszczenie zawartość `xs:restriction` bezpośrednio w kontenerze `xs:complexContent`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-406">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|  
|`extension`|<span data-ttu-id="5ee63-407">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-407">Supported.</span></span> <span data-ttu-id="5ee63-408">Mapy i dziedziczenie kontraktów danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-408">Maps to data contract inheritance.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="5ee63-409">\<xs:Extension > w \<xs:complexContent >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="5ee63-409">\<xs:extension> in \<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="5ee63-410">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ee63-410">Attribute</span></span>|<span data-ttu-id="5ee63-411">Schemat</span><span class="sxs-lookup"><span data-stu-id="5ee63-411">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="5ee63-412">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-412">Ignored.</span></span>|  
|`base`|<span data-ttu-id="5ee63-413">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-413">Supported.</span></span> <span data-ttu-id="5ee63-414">Mapuje do kontraktu danych podstawowych typu, że ten typ dziedziczy z.</span><span class="sxs-lookup"><span data-stu-id="5ee63-414">Maps to the base data contract type that this type inherits from.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="5ee63-415">\<xs:Extension > w \<xs:complexContent >: zawartość</span><span class="sxs-lookup"><span data-stu-id="5ee63-415">\<xs:extension> in \<xs:complexContent>: contents</span></span>  
 <span data-ttu-id="5ee63-416">Zasady są takie same jak w przypadku `<xs:complexType>` zawartość.</span><span class="sxs-lookup"><span data-stu-id="5ee63-416">The rules are the same as for `<xs:complexType>` contents.</span></span>  
  
 <span data-ttu-id="5ee63-417">Jeśli `<xs:sequence>` podano członków elementy mapy członkom dodatkowe dane, które znajdują się w kontrakcie pochodnego danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-417">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>  
  
 <span data-ttu-id="5ee63-418">Jeśli typ pochodny zawiera element o takiej samej nazwie jako element w typie podstawowym, deklaracja zduplikowany element mapuje element członkowski danych o nazwie, który jest generowany, aby była unikatowa.</span><span class="sxs-lookup"><span data-stu-id="5ee63-418">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="5ee63-419">Dodatnia liczba całkowita liczby są dodawane do nazwy elementu członkowskiego danych ("Członek1", "członek2" itd.) aż do znalezienia unikatową nazwę.</span><span class="sxs-lookup"><span data-stu-id="5ee63-419">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="5ee63-420">Z drugiej strony:</span><span class="sxs-lookup"><span data-stu-id="5ee63-420">Conversely:</span></span>  
  
- <span data-ttu-id="5ee63-421">Gdy kontrakt danych pochodnych ma element członkowski danych o tej samej nazwie i typie jako element członkowski danych w kontrakt danych podstawowych `DataContractSerializer` generuje ten odpowiadający mu element w typie pochodnym.</span><span class="sxs-lookup"><span data-stu-id="5ee63-421">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>  
  
- <span data-ttu-id="5ee63-422">Jeśli element członkowski danych o takiej samej nazwie jak element członkowski danych w kontraktu danych podstawowych, ale jest innego typu kontraktu danych pochodnych `DataContractSerializer` Importuje schemat z elementem typu `xs:anyType` zarówno w typie podstawowym, jak i w deklaracji typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="5ee63-422">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="5ee63-423">Oryginalna nazwa typu jest zachowywana w `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span><span class="sxs-lookup"><span data-stu-id="5ee63-423">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>  
  
 <span data-ttu-id="5ee63-424">Obu wariantów może prowadzić do schematu o niejednoznaczne modelu zawartości, który zależy od kolejności elementów członkowskich odpowiednich danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-424">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>  
  
## <a name="typeprimitive-mapping"></a><span data-ttu-id="5ee63-425">Mapowania typ/element</span><span class="sxs-lookup"><span data-stu-id="5ee63-425">Type/primitive mapping</span></span>  
 <span data-ttu-id="5ee63-426">`DataContractSerializer` Używa następującego mapowania dla typów pierwotnych schematu XML.</span><span class="sxs-lookup"><span data-stu-id="5ee63-426">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>  
  
|<span data-ttu-id="5ee63-427">Typ XSD</span><span class="sxs-lookup"><span data-stu-id="5ee63-427">XSD type</span></span>|<span data-ttu-id="5ee63-428">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="5ee63-428">.NET type</span></span>|  
|--------------|---------------|  
|`anyType`|<span data-ttu-id="5ee63-429"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-429"><xref:System.Object>.</span></span>|  
|`anySimpleType`|<span data-ttu-id="5ee63-430"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-430"><xref:System.String>.</span></span>|  
|`duration`|<span data-ttu-id="5ee63-431"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-431"><xref:System.TimeSpan>.</span></span>|  
|`dateTime`|<span data-ttu-id="5ee63-432"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-432"><xref:System.DateTime>.</span></span>|  
|`dateTimeOffset`|<span data-ttu-id="5ee63-433"><xref:System.DateTime> i <xref:System.TimeSpan> przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="5ee63-433"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="5ee63-434">Zobacz poniższe serializacji DateTimeOffset.</span><span class="sxs-lookup"><span data-stu-id="5ee63-434">See DateTimeOffset Serialization below.</span></span>|  
|`time`|<span data-ttu-id="5ee63-435"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-435"><xref:System.String>.</span></span>|  
|`date`|<span data-ttu-id="5ee63-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-436"><xref:System.String>.</span></span>|  
|`gYearMonth`|<span data-ttu-id="5ee63-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-437"><xref:System.String>.</span></span>|  
|`gYear`|<span data-ttu-id="5ee63-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-438"><xref:System.String>.</span></span>|  
|`gMonthDay`|<span data-ttu-id="5ee63-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-439"><xref:System.String>.</span></span>|  
|`gDay`|<span data-ttu-id="5ee63-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-440"><xref:System.String>.</span></span>|  
|`gMonth`|<span data-ttu-id="5ee63-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-441"><xref:System.String>.</span></span>|  
|`boolean`|<xref:System.Boolean>|  
|`base64Binary`|<span data-ttu-id="5ee63-442"><xref:System.Byte> Tablica.</span><span class="sxs-lookup"><span data-stu-id="5ee63-442"><xref:System.Byte> array.</span></span>|  
|`hexBinary`|<span data-ttu-id="5ee63-443"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-443"><xref:System.String>.</span></span>|  
|`float`|<span data-ttu-id="5ee63-444"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-444"><xref:System.Single>.</span></span>|  
|`double`|<span data-ttu-id="5ee63-445"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-445"><xref:System.Double>.</span></span>|  
|`anyURI`|<span data-ttu-id="5ee63-446"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-446"><xref:System.Uri>.</span></span>|  
|`QName`|<span data-ttu-id="5ee63-447"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-447"><xref:System.Xml.XmlQualifiedName>.</span></span>|  
|`string`|<span data-ttu-id="5ee63-448"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-448"><xref:System.String>.</span></span>|  
|`normalizedString`|<span data-ttu-id="5ee63-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-449"><xref:System.String>.</span></span>|  
|`token`|<span data-ttu-id="5ee63-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-450"><xref:System.String>.</span></span>|  
|`language`|<span data-ttu-id="5ee63-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-451"><xref:System.String>.</span></span>|  
|`Name`|<span data-ttu-id="5ee63-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-452"><xref:System.String>.</span></span>|  
|`NCName`|<span data-ttu-id="5ee63-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-453"><xref:System.String>.</span></span>|  
|`ID`|<span data-ttu-id="5ee63-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-454"><xref:System.String>.</span></span>|  
|`IDREF`|<span data-ttu-id="5ee63-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-455"><xref:System.String>.</span></span>|  
|`IDREFS`|<span data-ttu-id="5ee63-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-456"><xref:System.String>.</span></span>|  
|`ENTITY`|<span data-ttu-id="5ee63-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-457"><xref:System.String>.</span></span>|  
|`ENTITIES`|<span data-ttu-id="5ee63-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-458"><xref:System.String>.</span></span>|  
|`NMTOKEN`|<span data-ttu-id="5ee63-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-459"><xref:System.String>.</span></span>|  
|`NMTOKENS`|<span data-ttu-id="5ee63-460"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-460"><xref:System.String>.</span></span>|  
|`decimal`|<span data-ttu-id="5ee63-461"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-461"><xref:System.Decimal>.</span></span>|  
|`integer`|<span data-ttu-id="5ee63-462"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-462"><xref:System.Int64>.</span></span>|  
|`nonPositiveInteger`|<span data-ttu-id="5ee63-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-463"><xref:System.Int64>.</span></span>|  
|`negativeInteger`|<span data-ttu-id="5ee63-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-464"><xref:System.Int64>.</span></span>|  
|`long`|<span data-ttu-id="5ee63-465"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-465"><xref:System.Int64>.</span></span>|  
|`int`|<span data-ttu-id="5ee63-466"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-466"><xref:System.Int32>.</span></span>|  
|`short`|<span data-ttu-id="5ee63-467"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-467"><xref:System.Int16>.</span></span>|  
|`Byte`|<span data-ttu-id="5ee63-468"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-468"><xref:System.SByte>.</span></span>|  
|`nonNegativeInteger`|<span data-ttu-id="5ee63-469"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-469"><xref:System.Int64>.</span></span>|  
|`unsignedLong`|<span data-ttu-id="5ee63-470"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-470"><xref:System.UInt64>.</span></span>|  
|`unsignedInt`|<span data-ttu-id="5ee63-471"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-471"><xref:System.UInt32>.</span></span>|  
|`unsignedShort`|<span data-ttu-id="5ee63-472"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-472"><xref:System.UInt16>.</span></span>|  
|`unsignedByte`|<span data-ttu-id="5ee63-473"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-473"><xref:System.Byte>.</span></span>|  
|`positiveInteger`|<span data-ttu-id="5ee63-474"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-474"><xref:System.Int64>.</span></span>|  
  
## <a name="iserializable-types-mapping"></a><span data-ttu-id="5ee63-475">Mapowanie typów iSerializable</span><span class="sxs-lookup"><span data-stu-id="5ee63-475">ISerializable types mapping</span></span>  
 <span data-ttu-id="5ee63-476">W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0 <xref:System.Runtime.Serialization.ISerializable> została wprowadzona jako mechanizm ogólnego do wykonywania serializacji obiektów dla trwałości lub transfer danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-476">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0, <xref:System.Runtime.Serialization.ISerializable> was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="5ee63-477">Istnieje wiele [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typami, które implementują `ISerializable` i mogą być przekazywane między aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="5ee63-477">There are many [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="5ee63-478"><xref:System.Runtime.Serialization.DataContractSerializer> naturalnie zapewnia obsługę `ISerializable` klasy.</span><span class="sxs-lookup"><span data-stu-id="5ee63-478"><xref:System.Runtime.Serialization.DataContractSerializer> naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="5ee63-479">`DataContractSerializer` Mapuje `ISerializable` typów schematu implementacji różnią się jedynie QName (kwalifikowana nazwa) tego typu, które są faktycznymi kolekcji właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ee63-479">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="5ee63-480">Na przykład `DataContractSerializer` mapuje <xref:System.Exception> następujący typ XSD w `http://schemas.datacontract.org/2004/07/System` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5ee63-480">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 <span data-ttu-id="5ee63-481">Opcjonalny atrybut `ser:FactoryType` zadeklarowanych w danych serializacji umowy schematu odwołuje się do klasy fabryki, które może wykonywać deserializację typu.</span><span class="sxs-lookup"><span data-stu-id="5ee63-481">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="5ee63-482">Klasa fabryki musi należeć do kolekcji znanych typów `DataContractSerializer` wystąpienia używane.</span><span class="sxs-lookup"><span data-stu-id="5ee63-482">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="5ee63-483">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="5ee63-483">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="datacontract-serialization-schema"></a><span data-ttu-id="5ee63-484">DataContract schematu serializacji</span><span class="sxs-lookup"><span data-stu-id="5ee63-484">DataContract Serialization Schema</span></span>  
 <span data-ttu-id="5ee63-485">Liczba schematów wyeksportowany przez `DataContractSerializer` typy, elementy i atrybuty z przestrzeni nazw specjalnych serializacji kontrakt danych:</span><span class="sxs-lookup"><span data-stu-id="5ee63-485">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>  
  
 `http://schemas.microsoft.com/2003/10/Serialization`
  
 <span data-ttu-id="5ee63-486">Poniżej przedstawiono pełną deklarację schematu serializacji kontrakt danych.</span><span class="sxs-lookup"><span data-stu-id="5ee63-486">The following is a complete Data Contract Serialization schema declaration.</span></span>  
  
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
  
 <span data-ttu-id="5ee63-487">Należy można zauważyć następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5ee63-487">The following should be noted:</span></span>  
  
- <span data-ttu-id="5ee63-488">`ser:char` został wprowadzony do reprezentowania znaków Unicode typu <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-488">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>  
  
- <span data-ttu-id="5ee63-489">`valuespace` z `xs:duration` jest ograniczona do uporządkowany zestaw, dzięki czemu mogą być mapowane na <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-489">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>  
  
- <span data-ttu-id="5ee63-490">`FactoryType` jest używany w schematach wyeksportowane z typów, które są uzyskiwane z <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="5ee63-490">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="5ee63-491">Importowanie schematów innych niż typ</span><span class="sxs-lookup"><span data-stu-id="5ee63-491">Importing non-DataContract schemas</span></span>  
 <span data-ttu-id="5ee63-492">`DataContractSerializer` ma `ImportXmlTypes` opcję, aby umożliwić Importowanie schematów, które nie są zgodne z `DataContractSerializer` profilu XSD (zobacz <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> właściwości).</span><span class="sxs-lookup"><span data-stu-id="5ee63-492">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="5ee63-493">Ustawienie tej opcji na `true` umożliwia przyjmowanie niezgodnych typów schematu i mapowania ich na następującą implementacją <xref:System.Xml.Serialization.IXmlSerializable> zawijania tablicę <xref:System.Xml.XmlNode> (różni się tylko nazwę klasy).</span><span class="sxs-lookup"><span data-stu-id="5ee63-493">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>  
  
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
  
## <a name="datetimeoffset-serialization"></a><span data-ttu-id="5ee63-494">Serializacja DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="5ee63-494">DateTimeOffset Serialization</span></span>  
 <span data-ttu-id="5ee63-495"><xref:System.DateTimeOffset> Nie jest traktowana jako typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="5ee63-495">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="5ee63-496">Zamiast tego jest serializowana jako element złożonych z dwóch części.</span><span class="sxs-lookup"><span data-stu-id="5ee63-496">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="5ee63-497">Pierwsza część reprezentuje daty, godziny, a druga sekcja przedstawia przesunięcie od czasu daty.</span><span class="sxs-lookup"><span data-stu-id="5ee63-497">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="5ee63-498">W poniższym kodzie przedstawiono przykładowy serializowanej wartości DateTimeOffset.</span><span class="sxs-lookup"><span data-stu-id="5ee63-498">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="5ee63-499">Schemat jest w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="5ee63-499">The schema is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ee63-500">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ee63-500">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [<span data-ttu-id="5ee63-501">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="5ee63-501">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
