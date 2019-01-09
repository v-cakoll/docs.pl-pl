---
title: '&lt;Parametr&gt;'
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 82a2f5c46c698508695fe5f13f67059860a50713
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148295"
---
# <a name="ltparametergt"></a><span data-ttu-id="fe85c-102">&lt;Parametr&gt;</span><span class="sxs-lookup"><span data-stu-id="fe85c-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="fe85c-103">Określa parametr generyczny, gdy deklarowany typ jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="fe85c-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="fe85c-104">\<System.Runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="fe85c-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="fe85c-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="fe85c-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="fe85c-106">\<declaredTypes > Element</span><span class="sxs-lookup"><span data-stu-id="fe85c-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="fe85c-107">\<Dodaj >, element dla \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="fe85c-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="fe85c-108">\<Element knownType > Element</span><span class="sxs-lookup"><span data-stu-id="fe85c-108">\<knownType> Element</span></span>  
<span data-ttu-id="fe85c-109">\<Parametr > Element</span><span class="sxs-lookup"><span data-stu-id="fe85c-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe85c-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe85c-110">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe85c-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fe85c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fe85c-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fe85c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe85c-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fe85c-113">Attributes</span></span>  
  
|<span data-ttu-id="fe85c-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fe85c-114">Attribute</span></span>|<span data-ttu-id="fe85c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="fe85c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe85c-116">indeks</span><span class="sxs-lookup"><span data-stu-id="fe85c-116">index</span></span>|<span data-ttu-id="fe85c-117">Gdy deklarowany typ jest typem ogólnym, określa parametr generyczny, który zwróci typ znany.</span><span class="sxs-lookup"><span data-stu-id="fe85c-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="fe85c-118">— typ</span><span class="sxs-lookup"><span data-stu-id="fe85c-118">type</span></span>|<span data-ttu-id="fe85c-119">Ciąg opisujący znany typ używany do serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="fe85c-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="fe85c-120">Indeks atrybut</span><span class="sxs-lookup"><span data-stu-id="fe85c-120">index Attribute</span></span>  
  
|<span data-ttu-id="fe85c-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="fe85c-121">Value</span></span>|<span data-ttu-id="fe85c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="fe85c-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fe85c-123">„0”</span><span class="sxs-lookup"><span data-stu-id="fe85c-123">"0"</span></span>|<span data-ttu-id="fe85c-124">Pierwszy parametr w typie ogólnym.</span><span class="sxs-lookup"><span data-stu-id="fe85c-124">The first parameter in the generic type.</span></span> <span data-ttu-id="fe85c-125">Na przykład <xref:System.Collections.Generic.List%601> ma tylko jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="fe85c-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="fe85c-126">Jeśli jest używany jako typ zadeklarowany, indeksem będzie miał ustawienie "0".</span><span class="sxs-lookup"><span data-stu-id="fe85c-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="fe85c-127">"1"</span><span class="sxs-lookup"><span data-stu-id="fe85c-127">"1"</span></span>|<span data-ttu-id="fe85c-128">Drugi parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="fe85c-128">The second parameter in a generic type.</span></span> <span data-ttu-id="fe85c-129">Na przykład <xref:System.Collections.Generic.Dictionary%602> zawiera dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="fe85c-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="fe85c-130">Jeśli znany typ zwracany przez drugi parametr, należy ustawić atrybutu indeksu "1".</span><span class="sxs-lookup"><span data-stu-id="fe85c-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe85c-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fe85c-131">Child Elements</span></span>  
 <span data-ttu-id="fe85c-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="fe85c-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe85c-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fe85c-133">Parent Elements</span></span>  
  
|<span data-ttu-id="fe85c-134">Element</span><span class="sxs-lookup"><span data-stu-id="fe85c-134">Element</span></span>|<span data-ttu-id="fe85c-135">Opis</span><span class="sxs-lookup"><span data-stu-id="fe85c-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe85c-136">\<Element knownType ></span><span class="sxs-lookup"><span data-stu-id="fe85c-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="fe85c-137">Określa znany typ, który może zostać zwrócony przez pole lub właściwość zadeklarowanym typem.</span><span class="sxs-lookup"><span data-stu-id="fe85c-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe85c-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe85c-138">Remarks</span></span>  
 <span data-ttu-id="fe85c-139">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fe85c-139">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="fe85c-140">Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) na przykład przy użyciu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="fe85c-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="fe85c-141">Ten element konfiguracji nie może mieć obu atrybutów, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="fe85c-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="fe85c-142">Jeśli oba atrybuty są ustawione, <xref:System.Configuration.ConfigurationErrorsException> występuje.</span><span class="sxs-lookup"><span data-stu-id="fe85c-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe85c-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe85c-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="fe85c-144">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="fe85c-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="fe85c-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="fe85c-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="fe85c-146">\<add></span><span class="sxs-lookup"><span data-stu-id="fe85c-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
