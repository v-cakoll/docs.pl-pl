---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 7952e6cc4d2fe7eaa77e297a650f7ffbd7aec785
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040927"
---
# <a name="datacontractserializer"></a><span data-ttu-id="f3d63-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="f3d63-102">dataContractSerializer</span></span>
<span data-ttu-id="f3d63-103">Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f3d63-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="f3d63-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f3d63-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f3d63-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="f3d63-105">\<behaviors></span></span>  
<span data-ttu-id="f3d63-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f3d63-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="f3d63-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="f3d63-107">\<behavior></span></span>  
<span data-ttu-id="f3d63-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="f3d63-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3d63-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3d63-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3d63-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f3d63-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f3d63-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f3d63-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3d63-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f3d63-112">Attributes</span></span>  
  
|<span data-ttu-id="f3d63-113">Element</span><span class="sxs-lookup"><span data-stu-id="f3d63-113">Element</span></span>|<span data-ttu-id="f3d63-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f3d63-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3d63-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="f3d63-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="f3d63-116">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jest on serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="f3d63-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="f3d63-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="f3d63-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="f3d63-118">Liczba całkowita, która określa maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="f3d63-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3d63-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f3d63-119">Child Elements</span></span>  
 <span data-ttu-id="f3d63-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="f3d63-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3d63-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f3d63-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f3d63-122">Element</span><span class="sxs-lookup"><span data-stu-id="f3d63-122">Element</span></span>|<span data-ttu-id="f3d63-123">Opis</span><span class="sxs-lookup"><span data-stu-id="f3d63-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3d63-124">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="f3d63-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f3d63-125">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f3d63-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3d63-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3d63-126">Remarks</span></span>  
 <span data-ttu-id="f3d63-127">Zapoznaj <xref:System.Runtime.Serialization.DataContractSerializer> się z dokumentacją, aby uzyskać więcej informacji na temat znanych typów.</span><span class="sxs-lookup"><span data-stu-id="f3d63-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f3d63-128">Element Behavior (jeśli istnieje) powinien zawsze występować `<enableWebScript>` przed elementem Behavior w pliku konfiguracji. `<dataContractSerializer>`</span><span class="sxs-lookup"><span data-stu-id="f3d63-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="f3d63-129">W przeciwnym razie zachowanie nie jest zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="f3d63-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d63-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3d63-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="f3d63-131">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="f3d63-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="f3d63-132">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="f3d63-132">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
