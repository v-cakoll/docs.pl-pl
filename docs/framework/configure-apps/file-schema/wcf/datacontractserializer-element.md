---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 7e440810fee1dddb7025d1385b1edb4838d98a39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925910"
---
# <a name="datacontractserializer"></a><span data-ttu-id="03adf-101">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="03adf-101">\<dataContractSerializer></span></span>
<span data-ttu-id="03adf-102">Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="03adf-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="03adf-103">Ten element występuje w dwóch różnych hierarchiach.</span><span class="sxs-lookup"><span data-stu-id="03adf-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="03adf-104">Jeden z nich znajduje się w poniższej sekcji hierarchii schematu, a drugi jest wymieniony w sekcji uwagi.</span><span class="sxs-lookup"><span data-stu-id="03adf-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="03adf-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="03adf-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="03adf-106">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="03adf-106">\<behaviors></span></span>  
<span data-ttu-id="03adf-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="03adf-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="03adf-108">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="03adf-108">\<behavior></span></span>  
<span data-ttu-id="03adf-109">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="03adf-109">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03adf-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="03adf-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03adf-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="03adf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="03adf-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="03adf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03adf-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="03adf-113">Attributes</span></span>  
  
|<span data-ttu-id="03adf-114">Element</span><span class="sxs-lookup"><span data-stu-id="03adf-114">Element</span></span>|<span data-ttu-id="03adf-115">Opis</span><span class="sxs-lookup"><span data-stu-id="03adf-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03adf-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="03adf-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="03adf-117">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jest on serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="03adf-117">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="03adf-118">Ten atrybut jest tylko do settable dla `<dataContractSerializer>` `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="03adf-118">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="03adf-119">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="03adf-119">maxItemsInObjectGraph</span></span>|<span data-ttu-id="03adf-120">Liczba całkowita, która określa maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="03adf-120">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="03adf-121">Ten atrybut to 65536.</span><span class="sxs-lookup"><span data-stu-id="03adf-121">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03adf-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="03adf-122">Child Elements</span></span>  
 <span data-ttu-id="03adf-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="03adf-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03adf-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="03adf-124">Parent Elements</span></span>  
  
|<span data-ttu-id="03adf-125">Element</span><span class="sxs-lookup"><span data-stu-id="03adf-125">Element</span></span>|<span data-ttu-id="03adf-126">Opis</span><span class="sxs-lookup"><span data-stu-id="03adf-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03adf-127">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="03adf-127">\<behavior></span></span>](behavior-of-servicebehaviors.md)|<span data-ttu-id="03adf-128">Kolekcja ustawień zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="03adf-128">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="03adf-129">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="03adf-129">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="03adf-130">Reprezentuje element główny dla <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji <xref:System.Runtime.Serialization.DataContractSerializer>ustawień.</span><span class="sxs-lookup"><span data-stu-id="03adf-130">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03adf-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03adf-131">Remarks</span></span>  
 <span data-ttu-id="03adf-132">Jak określono we wprowadzeniu tego tematu, jest to druga hierarchia, w której \<występuje element X509Extension >.</span><span class="sxs-lookup"><span data-stu-id="03adf-132">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="03adf-133">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="03adf-133">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)  
  
 [<span data-ttu-id="03adf-134">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="03adf-134">\<dataContractSerializer></span></span>](datacontractserializer-element.md)  
  
 <span data-ttu-id="03adf-135">Aby uzyskać więcej informacji na temat znanych typów <xref:System.Runtime.Serialization.DataContractSerializer>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="03adf-135">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03adf-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03adf-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="03adf-137">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="03adf-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="03adf-138">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="03adf-138">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
