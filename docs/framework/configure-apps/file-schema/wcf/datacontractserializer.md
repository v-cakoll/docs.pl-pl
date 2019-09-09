---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: e6524c18780c062c3b5b7dfc2509449cb208e270
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400431"
---
# <a name="datacontractserializer"></a><span data-ttu-id="e6cfa-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="e6cfa-102">dataContractSerializer</span></span>
<span data-ttu-id="e6cfa-103">Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e6cfa-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
<span data-ttu-id="e6cfa-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e6cfa-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e6cfa-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e6cfa-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e6cfa-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e6cfa-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="e6cfa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e6cfa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="e6cfa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e6cfa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="e6cfa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> dataContractSerializer**</span><span class="sxs-lookup"><span data-stu-id="e6cfa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6cfa-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6cfa-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6cfa-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e6cfa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e6cfa-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e6cfa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6cfa-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e6cfa-113">Attributes</span></span>  
  
|<span data-ttu-id="e6cfa-114">Element</span><span class="sxs-lookup"><span data-stu-id="e6cfa-114">Element</span></span>|<span data-ttu-id="e6cfa-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e6cfa-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6cfa-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="e6cfa-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="e6cfa-117">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jest on serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="e6cfa-117">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="e6cfa-118">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="e6cfa-118">maxItemsInObjectGraph</span></span>|<span data-ttu-id="e6cfa-119">Liczba całkowita, która określa maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="e6cfa-119">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6cfa-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e6cfa-120">Child Elements</span></span>  
 <span data-ttu-id="e6cfa-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="e6cfa-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6cfa-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e6cfa-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e6cfa-123">Element</span><span class="sxs-lookup"><span data-stu-id="e6cfa-123">Element</span></span>|<span data-ttu-id="e6cfa-124">Opis</span><span class="sxs-lookup"><span data-stu-id="e6cfa-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6cfa-125">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="e6cfa-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e6cfa-126">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e6cfa-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6cfa-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6cfa-127">Remarks</span></span>  
 <span data-ttu-id="e6cfa-128">Zapoznaj <xref:System.Runtime.Serialization.DataContractSerializer> się z dokumentacją, aby uzyskać więcej informacji na temat znanych typów.</span><span class="sxs-lookup"><span data-stu-id="e6cfa-128">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="e6cfa-129">Element Behavior (jeśli istnieje) powinien zawsze występować `<enableWebScript>` przed elementem Behavior w pliku konfiguracji. `<dataContractSerializer>`</span><span class="sxs-lookup"><span data-stu-id="e6cfa-129">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="e6cfa-130">W przeciwnym razie zachowanie nie jest zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="e6cfa-130">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6cfa-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6cfa-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="e6cfa-132">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="e6cfa-132">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="e6cfa-133">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="e6cfa-133">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
