---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: e24dae47171f741af064ca2eaa822928690acf6e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400448"
---
# <a name="datacontractserializer"></a><span data-ttu-id="00a06-101">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="00a06-101">\<dataContractSerializer></span></span>
<span data-ttu-id="00a06-102">Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="00a06-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="00a06-103">Ten element występuje w dwóch różnych hierarchiach.</span><span class="sxs-lookup"><span data-stu-id="00a06-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="00a06-104">Jeden z nich znajduje się w poniższej sekcji hierarchii schematu, a drugi jest wymieniony w sekcji uwagi.</span><span class="sxs-lookup"><span data-stu-id="00a06-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
<span data-ttu-id="00a06-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="00a06-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="00a06-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="00a06-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="00a06-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="00a06-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="00a06-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="00a06-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="00a06-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="00a06-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="00a06-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> dataContractSerializer**</span><span class="sxs-lookup"><span data-stu-id="00a06-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00a06-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="00a06-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00a06-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="00a06-112">Attributes and Elements</span></span>  
 <span data-ttu-id="00a06-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="00a06-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00a06-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="00a06-114">Attributes</span></span>  
  
|<span data-ttu-id="00a06-115">Element</span><span class="sxs-lookup"><span data-stu-id="00a06-115">Element</span></span>|<span data-ttu-id="00a06-116">Opis</span><span class="sxs-lookup"><span data-stu-id="00a06-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00a06-117">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="00a06-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="00a06-118">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jest on serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="00a06-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="00a06-119">Ten atrybut jest tylko do settable dla `<dataContractSerializer>` `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="00a06-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="00a06-120">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="00a06-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="00a06-121">Liczba całkowita, która określa maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="00a06-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="00a06-122">Ten atrybut to 65536.</span><span class="sxs-lookup"><span data-stu-id="00a06-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00a06-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="00a06-123">Child Elements</span></span>  
 <span data-ttu-id="00a06-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="00a06-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00a06-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="00a06-125">Parent Elements</span></span>  
  
|<span data-ttu-id="00a06-126">Element</span><span class="sxs-lookup"><span data-stu-id="00a06-126">Element</span></span>|<span data-ttu-id="00a06-127">Opis</span><span class="sxs-lookup"><span data-stu-id="00a06-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00a06-128">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="00a06-128">\<behavior></span></span>](behavior-of-servicebehaviors.md)|<span data-ttu-id="00a06-129">Kolekcja ustawień zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="00a06-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="00a06-130">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="00a06-130">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="00a06-131">Reprezentuje element główny dla <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji <xref:System.Runtime.Serialization.DataContractSerializer>ustawień.</span><span class="sxs-lookup"><span data-stu-id="00a06-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00a06-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00a06-132">Remarks</span></span>  
 <span data-ttu-id="00a06-133">Jak określono we wprowadzeniu tego tematu, jest to druga hierarchia, w której \<występuje element X509Extension >.</span><span class="sxs-lookup"><span data-stu-id="00a06-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="00a06-134">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="00a06-134">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)  
  
 [<span data-ttu-id="00a06-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="00a06-135">\<dataContractSerializer></span></span>](datacontractserializer-element.md)  
  
 <span data-ttu-id="00a06-136">Aby uzyskać więcej informacji na temat znanych typów <xref:System.Runtime.Serialization.DataContractSerializer>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="00a06-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a06-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00a06-137">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="00a06-138">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="00a06-138">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="00a06-139">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="00a06-139">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
