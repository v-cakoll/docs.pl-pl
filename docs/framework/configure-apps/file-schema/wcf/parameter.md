---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: c3f2179835ad1232e115cad0decdd3d41bbdc160
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932848"
---
# <a name="parameter"></a><span data-ttu-id="80b5c-101">\<> parametru</span><span class="sxs-lookup"><span data-stu-id="80b5c-101">\<parameter></span></span>
<span data-ttu-id="80b5c-102">Określa parametr generyczny, gdy zadeklarowany typ jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="80b5c-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="80b5c-103">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="80b5c-103">\<system.runtime.serialization></span></span>  
<span data-ttu-id="80b5c-104">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="80b5c-104">\<dataContractSerializer></span></span>  
<span data-ttu-id="80b5c-105">\<declaredTypes, element ></span><span class="sxs-lookup"><span data-stu-id="80b5c-105">\<declaredTypes> Element</span></span>  
<span data-ttu-id="80b5c-106">\<Dodaj element > dla \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="80b5c-106">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="80b5c-107">\<Element > knownType</span><span class="sxs-lookup"><span data-stu-id="80b5c-107">\<knownType> Element</span></span>  
<span data-ttu-id="80b5c-108">\<Element > parametru</span><span class="sxs-lookup"><span data-stu-id="80b5c-108">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80b5c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="80b5c-109">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80b5c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="80b5c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="80b5c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="80b5c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80b5c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="80b5c-112">Attributes</span></span>  
  
|<span data-ttu-id="80b5c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="80b5c-113">Attribute</span></span>|<span data-ttu-id="80b5c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="80b5c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80b5c-115">indeks</span><span class="sxs-lookup"><span data-stu-id="80b5c-115">index</span></span>|<span data-ttu-id="80b5c-116">Gdy zadeklarowany typ jest typem ogólnym, określa parametr generyczny, który zwróci znany typ.</span><span class="sxs-lookup"><span data-stu-id="80b5c-116">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="80b5c-117">— typ</span><span class="sxs-lookup"><span data-stu-id="80b5c-117">type</span></span>|<span data-ttu-id="80b5c-118">Ciąg opisujący znany typ używany do serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="80b5c-118">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="80b5c-119">Atrybut indeksu</span><span class="sxs-lookup"><span data-stu-id="80b5c-119">index Attribute</span></span>  
  
|<span data-ttu-id="80b5c-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="80b5c-120">Value</span></span>|<span data-ttu-id="80b5c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="80b5c-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="80b5c-122">„0”</span><span class="sxs-lookup"><span data-stu-id="80b5c-122">"0"</span></span>|<span data-ttu-id="80b5c-123">Pierwszy parametr w typie ogólnym.</span><span class="sxs-lookup"><span data-stu-id="80b5c-123">The first parameter in the generic type.</span></span> <span data-ttu-id="80b5c-124">Na przykład <xref:System.Collections.Generic.List%601> ma tylko jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="80b5c-124">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="80b5c-125">Jeśli jest używany jako zadeklarowany typ, indeks zostanie ustawiony na wartość "0".</span><span class="sxs-lookup"><span data-stu-id="80b5c-125">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="80b5c-126">"1"</span><span class="sxs-lookup"><span data-stu-id="80b5c-126">"1"</span></span>|<span data-ttu-id="80b5c-127">Drugi parametr w typie ogólnym.</span><span class="sxs-lookup"><span data-stu-id="80b5c-127">The second parameter in a generic type.</span></span> <span data-ttu-id="80b5c-128">Na przykład <xref:System.Collections.Generic.Dictionary%602> ma dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="80b5c-128">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="80b5c-129">Jeśli znany typ jest zwracany przez drugi parametr, ustaw atrybut index na wartość "1".</span><span class="sxs-lookup"><span data-stu-id="80b5c-129">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80b5c-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="80b5c-130">Child Elements</span></span>  
 <span data-ttu-id="80b5c-131">Brak.</span><span class="sxs-lookup"><span data-stu-id="80b5c-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80b5c-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="80b5c-132">Parent Elements</span></span>  
  
|<span data-ttu-id="80b5c-133">Element</span><span class="sxs-lookup"><span data-stu-id="80b5c-133">Element</span></span>|<span data-ttu-id="80b5c-134">Opis</span><span class="sxs-lookup"><span data-stu-id="80b5c-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80b5c-135">\<> knownType</span><span class="sxs-lookup"><span data-stu-id="80b5c-135">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="80b5c-136">Określa znany typ, który może być zwracany przez pole lub właściwość zadeklarowanego typu.</span><span class="sxs-lookup"><span data-stu-id="80b5c-136">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80b5c-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80b5c-137">Remarks</span></span>  
 <span data-ttu-id="80b5c-138">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="80b5c-138">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="80b5c-139">Zobacz [ \<> DataContractSerializer](datacontractserializer-element.md) , aby zapoznać się z przykładem użycia tego elementu.</span><span class="sxs-lookup"><span data-stu-id="80b5c-139">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="80b5c-140">Ten element konfiguracji nie może jednocześnie mieć obu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="80b5c-140">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="80b5c-141">Jeśli oba atrybuty są ustawione, <xref:System.Configuration.ConfigurationErrorsException> występuje.</span><span class="sxs-lookup"><span data-stu-id="80b5c-141">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80b5c-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80b5c-142">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="80b5c-143">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="80b5c-143">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="80b5c-144">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="80b5c-144">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="80b5c-145">\<add></span><span class="sxs-lookup"><span data-stu-id="80b5c-145">\<add></span></span>](add-of-declaredtypes-element.md)
