---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 8814a48df8933cf08db78e397c24d42f2da26026
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919229"
---
# <a name="datacontractserializer"></a><span data-ttu-id="43dca-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="43dca-102">dataContractSerializer</span></span>
<span data-ttu-id="43dca-103">Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="43dca-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="43dca-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="43dca-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="43dca-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="43dca-105">\<behaviors></span></span>  
<span data-ttu-id="43dca-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="43dca-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="43dca-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="43dca-107">\<behavior></span></span>  
<span data-ttu-id="43dca-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="43dca-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43dca-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="43dca-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43dca-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="43dca-110">Attributes and Elements</span></span>  
 <span data-ttu-id="43dca-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="43dca-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43dca-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="43dca-112">Attributes</span></span>  
  
|<span data-ttu-id="43dca-113">Element</span><span class="sxs-lookup"><span data-stu-id="43dca-113">Element</span></span>|<span data-ttu-id="43dca-114">Opis</span><span class="sxs-lookup"><span data-stu-id="43dca-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43dca-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="43dca-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="43dca-116">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jest on serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="43dca-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="43dca-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="43dca-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="43dca-118">Liczba całkowita, która określa maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="43dca-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43dca-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="43dca-119">Child Elements</span></span>  
 <span data-ttu-id="43dca-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="43dca-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43dca-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="43dca-121">Parent Elements</span></span>  
  
|<span data-ttu-id="43dca-122">Element</span><span class="sxs-lookup"><span data-stu-id="43dca-122">Element</span></span>|<span data-ttu-id="43dca-123">Opis</span><span class="sxs-lookup"><span data-stu-id="43dca-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43dca-124">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="43dca-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="43dca-125">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="43dca-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43dca-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43dca-126">Remarks</span></span>  
 <span data-ttu-id="43dca-127">Zapoznaj <xref:System.Runtime.Serialization.DataContractSerializer> się z dokumentacją, aby uzyskać więcej informacji na temat znanych typów.</span><span class="sxs-lookup"><span data-stu-id="43dca-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="43dca-128">Element Behavior (jeśli istnieje) powinien zawsze występować `<enableWebScript>` przed elementem Behavior w pliku konfiguracji. `<dataContractSerializer>`</span><span class="sxs-lookup"><span data-stu-id="43dca-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="43dca-129">W przeciwnym razie zachowanie nie jest zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="43dca-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43dca-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43dca-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="43dca-131">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="43dca-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="43dca-132">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="43dca-132">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
