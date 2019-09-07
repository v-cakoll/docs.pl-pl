---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 07fa410109a7bd2fa315132c4737301698bb3a93
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400111"
---
# <a name="parameter"></a><span data-ttu-id="9926b-101">\<> parametru</span><span class="sxs-lookup"><span data-stu-id="9926b-101">\<parameter></span></span>
<span data-ttu-id="9926b-102">Określa parametr generyczny, gdy zadeklarowany typ jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="9926b-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
<span data-ttu-id="9926b-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9926b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9926b-104">&nbsp;&nbsp;[ **\<> System. Runtime. Serialization**](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="9926b-104">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="9926b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="9926b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="9926b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="9926b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="9926b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Dodaj >** ](add-of-declaredtypes-element.md)</span><span class="sxs-lookup"><span data-stu-id="9926b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)</span></span>\
<span data-ttu-id="9926b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> knownType**](knowntype.md)</span><span class="sxs-lookup"><span data-stu-id="9926b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)</span></span>\
<span data-ttu-id="9926b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> parametru**</span><span class="sxs-lookup"><span data-stu-id="9926b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9926b-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="9926b-110">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9926b-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9926b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9926b-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9926b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9926b-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9926b-113">Attributes</span></span>  
  
|<span data-ttu-id="9926b-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9926b-114">Attribute</span></span>|<span data-ttu-id="9926b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9926b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9926b-116">indeks</span><span class="sxs-lookup"><span data-stu-id="9926b-116">index</span></span>|<span data-ttu-id="9926b-117">Gdy zadeklarowany typ jest typem ogólnym, określa parametr generyczny, który zwróci znany typ.</span><span class="sxs-lookup"><span data-stu-id="9926b-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="9926b-118">— typ</span><span class="sxs-lookup"><span data-stu-id="9926b-118">type</span></span>|<span data-ttu-id="9926b-119">Ciąg opisujący znany typ używany do serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="9926b-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="9926b-120">Atrybut indeksu</span><span class="sxs-lookup"><span data-stu-id="9926b-120">index Attribute</span></span>  
  
|<span data-ttu-id="9926b-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="9926b-121">Value</span></span>|<span data-ttu-id="9926b-122">Opis</span><span class="sxs-lookup"><span data-stu-id="9926b-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9926b-123">„0”</span><span class="sxs-lookup"><span data-stu-id="9926b-123">"0"</span></span>|<span data-ttu-id="9926b-124">Pierwszy parametr w typie ogólnym.</span><span class="sxs-lookup"><span data-stu-id="9926b-124">The first parameter in the generic type.</span></span> <span data-ttu-id="9926b-125">Na przykład <xref:System.Collections.Generic.List%601> ma tylko jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="9926b-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="9926b-126">Jeśli jest używany jako zadeklarowany typ, indeks zostanie ustawiony na wartość "0".</span><span class="sxs-lookup"><span data-stu-id="9926b-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="9926b-127">"1"</span><span class="sxs-lookup"><span data-stu-id="9926b-127">"1"</span></span>|<span data-ttu-id="9926b-128">Drugi parametr w typie ogólnym.</span><span class="sxs-lookup"><span data-stu-id="9926b-128">The second parameter in a generic type.</span></span> <span data-ttu-id="9926b-129">Na przykład <xref:System.Collections.Generic.Dictionary%602> ma dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="9926b-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="9926b-130">Jeśli znany typ jest zwracany przez drugi parametr, ustaw atrybut index na wartość "1".</span><span class="sxs-lookup"><span data-stu-id="9926b-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9926b-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9926b-131">Child Elements</span></span>  
 <span data-ttu-id="9926b-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="9926b-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9926b-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9926b-133">Parent Elements</span></span>  
  
|<span data-ttu-id="9926b-134">Element</span><span class="sxs-lookup"><span data-stu-id="9926b-134">Element</span></span>|<span data-ttu-id="9926b-135">Opis</span><span class="sxs-lookup"><span data-stu-id="9926b-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9926b-136">\<> knownType</span><span class="sxs-lookup"><span data-stu-id="9926b-136">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="9926b-137">Określa znany typ, który może być zwracany przez pole lub właściwość zadeklarowanego typu.</span><span class="sxs-lookup"><span data-stu-id="9926b-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9926b-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9926b-138">Remarks</span></span>  
 <span data-ttu-id="9926b-139">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9926b-139">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="9926b-140">Zobacz [ \<> DataContractSerializer](datacontractserializer-element.md) , aby zapoznać się z przykładem użycia tego elementu.</span><span class="sxs-lookup"><span data-stu-id="9926b-140">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="9926b-141">Ten element konfiguracji nie może jednocześnie mieć obu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="9926b-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="9926b-142">Jeśli oba atrybuty są ustawione, <xref:System.Configuration.ConfigurationErrorsException> występuje.</span><span class="sxs-lookup"><span data-stu-id="9926b-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9926b-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9926b-143">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="9926b-144">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="9926b-144">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="9926b-145">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="9926b-145">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="9926b-146">\<add></span><span class="sxs-lookup"><span data-stu-id="9926b-146">\<add></span></span>](add-of-declaredtypes-element.md)
