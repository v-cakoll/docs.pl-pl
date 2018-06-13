---
title: '&lt;Parametr&gt;'
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: b9cccfe37e7658afbf2e49555e6c505497598fbb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754057"
---
# <a name="ltparametergt"></a><span data-ttu-id="4e7df-102">&lt;Parametr&gt;</span><span class="sxs-lookup"><span data-stu-id="4e7df-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="4e7df-103">Określa parametr generyczny, gdy deklarowany typ jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="4e7df-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="4e7df-104">\<System.Runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="4e7df-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="4e7df-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="4e7df-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="4e7df-106">\<declaredTypes > — Element</span><span class="sxs-lookup"><span data-stu-id="4e7df-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="4e7df-107">\<Dodaj > elementu \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="4e7df-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="4e7df-108">\<Typ knownType > — Element</span><span class="sxs-lookup"><span data-stu-id="4e7df-108">\<knownType> Element</span></span>  
<span data-ttu-id="4e7df-109">\<Parametr > — Element</span><span class="sxs-lookup"><span data-stu-id="4e7df-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e7df-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e7df-110">Syntax</span></span>  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e7df-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4e7df-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4e7df-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4e7df-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e7df-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4e7df-113">Attributes</span></span>  
  
|<span data-ttu-id="4e7df-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4e7df-114">Attribute</span></span>|<span data-ttu-id="4e7df-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4e7df-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e7df-116">indeks</span><span class="sxs-lookup"><span data-stu-id="4e7df-116">index</span></span>|<span data-ttu-id="4e7df-117">Gdy deklarowany typ jest typem ogólnym, określa parametr generyczny, który zwróci typ znany.</span><span class="sxs-lookup"><span data-stu-id="4e7df-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="4e7df-118">— typ</span><span class="sxs-lookup"><span data-stu-id="4e7df-118">type</span></span>|<span data-ttu-id="4e7df-119">Ciąg opisujący znany typ używany do serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="4e7df-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="4e7df-120">Indeks atrybut</span><span class="sxs-lookup"><span data-stu-id="4e7df-120">index Attribute</span></span>  
  
|<span data-ttu-id="4e7df-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="4e7df-121">Value</span></span>|<span data-ttu-id="4e7df-122">Opis</span><span class="sxs-lookup"><span data-stu-id="4e7df-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4e7df-123">„0”</span><span class="sxs-lookup"><span data-stu-id="4e7df-123">"0"</span></span>|<span data-ttu-id="4e7df-124">Pierwszy parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="4e7df-124">The first parameter in the generic type.</span></span> <span data-ttu-id="4e7df-125">Na przykład <xref:System.Collections.Generic.List%601> ma tylko jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="4e7df-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="4e7df-126">Jeśli jest on używany jako deklarowanego typu, indeks ustawiał "0".</span><span class="sxs-lookup"><span data-stu-id="4e7df-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="4e7df-127">"1"</span><span class="sxs-lookup"><span data-stu-id="4e7df-127">"1"</span></span>|<span data-ttu-id="4e7df-128">Drugi parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="4e7df-128">The second parameter in a generic type.</span></span> <span data-ttu-id="4e7df-129">Na przykład <xref:System.Collections.Generic.Dictionary%602> zawiera dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="4e7df-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="4e7df-130">Jeśli drugi parametr zwracany jest znanym typem, ustaw dla atrybutu indeksu "1".</span><span class="sxs-lookup"><span data-stu-id="4e7df-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e7df-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4e7df-131">Child Elements</span></span>  
 <span data-ttu-id="4e7df-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="4e7df-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e7df-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4e7df-133">Parent Elements</span></span>  
  
|<span data-ttu-id="4e7df-134">Element</span><span class="sxs-lookup"><span data-stu-id="4e7df-134">Element</span></span>|<span data-ttu-id="4e7df-135">Opis</span><span class="sxs-lookup"><span data-stu-id="4e7df-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e7df-136">\<Typ knownType ></span><span class="sxs-lookup"><span data-stu-id="4e7df-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="4e7df-137">Określa znanym typem, który może być zwracany przez pole lub właściwość deklarowanego typu.</span><span class="sxs-lookup"><span data-stu-id="4e7df-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e7df-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e7df-138">Remarks</span></span>  
 <span data-ttu-id="4e7df-139">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="4e7df-139">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="4e7df-140">Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) przykład za pomocą tego elementu.</span><span class="sxs-lookup"><span data-stu-id="4e7df-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="4e7df-141">Ten element konfiguracji nie może mieć obu atrybutów, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="4e7df-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="4e7df-142">Jeśli oba atrybuty są ustawione, <xref:System.Configuration.ConfigurationErrorsException> występuje.</span><span class="sxs-lookup"><span data-stu-id="4e7df-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7df-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e7df-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="4e7df-144">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="4e7df-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="4e7df-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="4e7df-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="4e7df-146">\<add></span><span class="sxs-lookup"><span data-stu-id="4e7df-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
