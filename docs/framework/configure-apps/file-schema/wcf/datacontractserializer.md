---
title: dataContractSerializer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4044e81b7c33c7a755678e79586dd4f37cf54ed5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="datacontractserializer"></a><span data-ttu-id="7f617-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="7f617-102">dataContractSerializer</span></span>
<span data-ttu-id="7f617-103">Zawiera dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7f617-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="7f617-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7f617-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7f617-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="7f617-105">\<behaviors></span></span>  
<span data-ttu-id="7f617-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7f617-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7f617-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="7f617-107">\<behavior></span></span>  
<span data-ttu-id="7f617-108">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="7f617-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f617-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f617-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f617-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7f617-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7f617-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7f617-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f617-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7f617-112">Attributes</span></span>  
  
|<span data-ttu-id="7f617-113">Element</span><span class="sxs-lookup"><span data-stu-id="7f617-113">Element</span></span>|<span data-ttu-id="7f617-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7f617-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f617-115">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="7f617-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="7f617-116">Wartość logiczna określająca, czy można zignorować dane dostarczone przez punkt końcowy, gdy jest on serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="7f617-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="7f617-117">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="7f617-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="7f617-118">Liczba całkowita określająca maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="7f617-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f617-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7f617-119">Child Elements</span></span>  
 <span data-ttu-id="7f617-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="7f617-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f617-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7f617-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7f617-122">Element</span><span class="sxs-lookup"><span data-stu-id="7f617-122">Element</span></span>|<span data-ttu-id="7f617-123">Opis</span><span class="sxs-lookup"><span data-stu-id="7f617-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f617-124">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="7f617-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7f617-125">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7f617-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f617-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f617-126">Remarks</span></span>  
 <span data-ttu-id="7f617-127">Zobacz <xref:System.Runtime.Serialization.DataContractSerializer> dokumentację, aby uzyskać więcej informacji na temat znanych typów.</span><span class="sxs-lookup"><span data-stu-id="7f617-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="7f617-128">`<dataContractSerializer>` Zachowanie elementu (jeśli istnieje) zawsze powinna być wyświetlana przed `<enableWebScript>` zachowanie elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7f617-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="7f617-129">W przeciwnym razie efekty jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="7f617-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f617-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f617-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="7f617-131">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="7f617-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="7f617-132">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="7f617-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
