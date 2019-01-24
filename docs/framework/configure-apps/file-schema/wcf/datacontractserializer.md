---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 933d49092c392fa293468d546e521bf7ed858376
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539847"
---
# <a name="datacontractserializer"></a><span data-ttu-id="c13d8-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="c13d8-102">dataContractSerializer</span></span>
<span data-ttu-id="c13d8-103">Zawierająca dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c13d8-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="c13d8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c13d8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c13d8-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="c13d8-105">\<behaviors></span></span>  
<span data-ttu-id="c13d8-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="c13d8-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="c13d8-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="c13d8-107">\<behavior></span></span>  
<span data-ttu-id="c13d8-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="c13d8-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c13d8-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c13d8-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c13d8-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c13d8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c13d8-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c13d8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c13d8-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c13d8-112">Attributes</span></span>  
  
|<span data-ttu-id="c13d8-113">Element</span><span class="sxs-lookup"><span data-stu-id="c13d8-113">Element</span></span>|<span data-ttu-id="c13d8-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c13d8-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c13d8-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="c13d8-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="c13d8-116">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, po jego serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="c13d8-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="c13d8-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="c13d8-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="c13d8-118">Liczba całkowita określająca maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="c13d8-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c13d8-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c13d8-119">Child Elements</span></span>  
 <span data-ttu-id="c13d8-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="c13d8-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c13d8-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c13d8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c13d8-122">Element</span><span class="sxs-lookup"><span data-stu-id="c13d8-122">Element</span></span>|<span data-ttu-id="c13d8-123">Opis</span><span class="sxs-lookup"><span data-stu-id="c13d8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c13d8-124">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="c13d8-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="c13d8-125">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c13d8-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c13d8-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c13d8-126">Remarks</span></span>  
 <span data-ttu-id="c13d8-127">Zobacz <xref:System.Runtime.Serialization.DataContractSerializer> dokumentacji, aby uzyskać więcej informacji na temat znanych typów.</span><span class="sxs-lookup"><span data-stu-id="c13d8-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c13d8-128">`<dataContractSerializer>` Zachowanie elementu (jeśli istnieje) zawsze powinna być wyświetlana przed `<enableWebScript>` zachowania elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c13d8-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="c13d8-129">W przeciwnym razie wynikowe zachowanie jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="c13d8-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c13d8-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c13d8-130">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="c13d8-131">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="c13d8-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="c13d8-132">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="c13d8-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
