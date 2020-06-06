---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 07fa410109a7bd2fa315132c4737301698bb3a93
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400111"
---
# \<parameter>
<span data-ttu-id="fd0f8-101">Określa parametr generyczny, gdy zadeklarowany typ jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="fd0f8-101">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
## <a name="syntax"></a><span data-ttu-id="fd0f8-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd0f8-102">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd0f8-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fd0f8-103">Attributes and Elements</span></span>  
 <span data-ttu-id="fd0f8-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fd0f8-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd0f8-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fd0f8-105">Attributes</span></span>  
  
|<span data-ttu-id="fd0f8-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fd0f8-106">Attribute</span></span>|<span data-ttu-id="fd0f8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fd0f8-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd0f8-108">indeks</span><span class="sxs-lookup"><span data-stu-id="fd0f8-108">index</span></span>|<span data-ttu-id="fd0f8-109">Gdy zadeklarowany typ jest typem ogólnym, określa parametr generyczny, który zwróci znany typ.</span><span class="sxs-lookup"><span data-stu-id="fd0f8-109">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="fd0f8-110">typ</span><span class="sxs-lookup"><span data-stu-id="fd0f8-110">type</span></span>|<span data-ttu-id="fd0f8-111">Ciąg opisujący znany typ używany do serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="fd0f8-111">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="fd0f8-112">Atrybut indeksu</span><span class="sxs-lookup"><span data-stu-id="fd0f8-112">index Attribute</span></span>  
  
|<span data-ttu-id="fd0f8-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="fd0f8-113">Value</span></span>|<span data-ttu-id="fd0f8-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fd0f8-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd0f8-115">„0”</span><span class="sxs-lookup"><span data-stu-id="fd0f8-115">"0"</span></span>|<span data-ttu-id="fd0f8-116">Pierwszy parametr w typie ogólnym.</span><span class="sxs-lookup"><span data-stu-id="fd0f8-116">The first parameter in the generic type.</span></span> <span data-ttu-id="fd0f8-117">Na przykład <xref:System.Collections.Generic.List%601> ma tylko jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="fd0f8-117">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="fd0f8-118">Jeśli jest używany jako zadeklarowany typ, indeks zostanie ustawiony na wartość "0".</span><span class="sxs-lookup"><span data-stu-id="fd0f8-118">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="fd0f8-119">„1”</span><span class="sxs-lookup"><span data-stu-id="fd0f8-119">"1"</span></span>|<span data-ttu-id="fd0f8-120">Drugi parametr w typie ogólnym.</span><span class="sxs-lookup"><span data-stu-id="fd0f8-120">The second parameter in a generic type.</span></span> <span data-ttu-id="fd0f8-121">Na przykład <xref:System.Collections.Generic.Dictionary%602> ma dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="fd0f8-121">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="fd0f8-122">Jeśli znany typ jest zwracany przez drugi parametr, ustaw atrybut index na wartość "1".</span><span class="sxs-lookup"><span data-stu-id="fd0f8-122">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd0f8-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fd0f8-123">Child Elements</span></span>  
 <span data-ttu-id="fd0f8-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="fd0f8-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd0f8-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fd0f8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="fd0f8-126">Element</span><span class="sxs-lookup"><span data-stu-id="fd0f8-126">Element</span></span>|<span data-ttu-id="fd0f8-127">Opis</span><span class="sxs-lookup"><span data-stu-id="fd0f8-127">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="fd0f8-128">Określa znany typ, który może być zwracany przez pole lub właściwość zadeklarowanego typu.</span><span class="sxs-lookup"><span data-stu-id="fd0f8-128">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd0f8-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd0f8-129">Remarks</span></span>  
 <span data-ttu-id="fd0f8-130">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="fd0f8-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="fd0f8-131">Zobacz, [\<dataContractSerializer>](datacontractserializer-element.md) Aby zapoznać się z przykładem użycia tego elementu.</span><span class="sxs-lookup"><span data-stu-id="fd0f8-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="fd0f8-132">Ten element konfiguracji nie może jednocześnie mieć obu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="fd0f8-132">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="fd0f8-133">Jeśli oba atrybuty są ustawione, <xref:System.Configuration.ConfigurationErrorsException> występuje.</span><span class="sxs-lookup"><span data-stu-id="fd0f8-133">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd0f8-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd0f8-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="fd0f8-135">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="fd0f8-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
