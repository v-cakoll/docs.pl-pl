---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 22ef3c3c6d23d6c68c27d6b5d1ed35b7c9910d48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783438"
---
# <a name="parameter"></a><span data-ttu-id="cc463-101">\<parameter></span><span class="sxs-lookup"><span data-stu-id="cc463-101">\<parameter></span></span>
<span data-ttu-id="cc463-102">Określa parametr generyczny, gdy deklarowany typ jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="cc463-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="cc463-103">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="cc463-103">\<system.runtime.serialization></span></span>  
<span data-ttu-id="cc463-104">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="cc463-104">\<dataContractSerializer></span></span>  
<span data-ttu-id="cc463-105">\<declaredTypes > Element</span><span class="sxs-lookup"><span data-stu-id="cc463-105">\<declaredTypes> Element</span></span>  
<span data-ttu-id="cc463-106">\<Dodaj >, element dla \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="cc463-106">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="cc463-107">\<knownType> Element</span><span class="sxs-lookup"><span data-stu-id="cc463-107">\<knownType> Element</span></span>  
<span data-ttu-id="cc463-108">\<parameter> Element</span><span class="sxs-lookup"><span data-stu-id="cc463-108">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc463-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc463-109">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc463-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cc463-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cc463-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cc463-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc463-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cc463-112">Attributes</span></span>  
  
|<span data-ttu-id="cc463-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cc463-113">Attribute</span></span>|<span data-ttu-id="cc463-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cc463-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc463-115">indeks</span><span class="sxs-lookup"><span data-stu-id="cc463-115">index</span></span>|<span data-ttu-id="cc463-116">Gdy deklarowany typ jest typem ogólnym, określa parametr generyczny, który zwróci typ znany.</span><span class="sxs-lookup"><span data-stu-id="cc463-116">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="cc463-117">— typ</span><span class="sxs-lookup"><span data-stu-id="cc463-117">type</span></span>|<span data-ttu-id="cc463-118">Ciąg opisujący znany typ używany do serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="cc463-118">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="cc463-119">Indeks atrybut</span><span class="sxs-lookup"><span data-stu-id="cc463-119">index Attribute</span></span>  
  
|<span data-ttu-id="cc463-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="cc463-120">Value</span></span>|<span data-ttu-id="cc463-121">Opis</span><span class="sxs-lookup"><span data-stu-id="cc463-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cc463-122">„0”</span><span class="sxs-lookup"><span data-stu-id="cc463-122">"0"</span></span>|<span data-ttu-id="cc463-123">Pierwszy parametr w typie ogólnym.</span><span class="sxs-lookup"><span data-stu-id="cc463-123">The first parameter in the generic type.</span></span> <span data-ttu-id="cc463-124">Na przykład <xref:System.Collections.Generic.List%601> ma tylko jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="cc463-124">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="cc463-125">Jeśli jest używany jako typ zadeklarowany, indeksem będzie miał ustawienie "0".</span><span class="sxs-lookup"><span data-stu-id="cc463-125">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="cc463-126">"1"</span><span class="sxs-lookup"><span data-stu-id="cc463-126">"1"</span></span>|<span data-ttu-id="cc463-127">Drugi parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="cc463-127">The second parameter in a generic type.</span></span> <span data-ttu-id="cc463-128">Na przykład <xref:System.Collections.Generic.Dictionary%602> zawiera dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="cc463-128">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="cc463-129">Jeśli znany typ zwracany przez drugi parametr, należy ustawić atrybutu indeksu "1".</span><span class="sxs-lookup"><span data-stu-id="cc463-129">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc463-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cc463-130">Child Elements</span></span>  
 <span data-ttu-id="cc463-131">Brak.</span><span class="sxs-lookup"><span data-stu-id="cc463-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc463-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cc463-132">Parent Elements</span></span>  
  
|<span data-ttu-id="cc463-133">Element</span><span class="sxs-lookup"><span data-stu-id="cc463-133">Element</span></span>|<span data-ttu-id="cc463-134">Opis</span><span class="sxs-lookup"><span data-stu-id="cc463-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc463-135">\<Element knownType ></span><span class="sxs-lookup"><span data-stu-id="cc463-135">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="cc463-136">Określa znany typ, który może zostać zwrócony przez pole lub właściwość zadeklarowanym typem.</span><span class="sxs-lookup"><span data-stu-id="cc463-136">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc463-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc463-137">Remarks</span></span>  
 <span data-ttu-id="cc463-138">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="cc463-138">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="cc463-139">Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) na przykład przy użyciu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="cc463-139">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="cc463-140">Ten element konfiguracji nie może mieć obu atrybutów, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="cc463-140">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="cc463-141">Jeśli oba atrybuty są ustawione, <xref:System.Configuration.ConfigurationErrorsException> występuje.</span><span class="sxs-lookup"><span data-stu-id="cc463-141">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc463-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc463-142">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="cc463-143">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="cc463-143">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="cc463-144">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="cc463-144">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="cc463-145">\<add></span><span class="sxs-lookup"><span data-stu-id="cc463-145">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
