---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: e6524c18780c062c3b5b7dfc2509449cb208e270
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400431"
---
# <a name="datacontractserializer"></a><span data-ttu-id="62e8b-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="62e8b-102">dataContractSerializer</span></span>
<span data-ttu-id="62e8b-103">Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="62e8b-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="62e8b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62e8b-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62e8b-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="62e8b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="62e8b-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="62e8b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62e8b-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="62e8b-107">Attributes</span></span>  
  
|<span data-ttu-id="62e8b-108">Element</span><span class="sxs-lookup"><span data-stu-id="62e8b-108">Element</span></span>|<span data-ttu-id="62e8b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="62e8b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62e8b-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="62e8b-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="62e8b-111">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jest on serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="62e8b-111">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="62e8b-112">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="62e8b-112">maxItemsInObjectGraph</span></span>|<span data-ttu-id="62e8b-113">Liczba całkowita, która określa maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="62e8b-113">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62e8b-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="62e8b-114">Child Elements</span></span>  
 <span data-ttu-id="62e8b-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="62e8b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62e8b-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="62e8b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="62e8b-117">Element</span><span class="sxs-lookup"><span data-stu-id="62e8b-117">Element</span></span>|<span data-ttu-id="62e8b-118">Opis</span><span class="sxs-lookup"><span data-stu-id="62e8b-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="62e8b-119">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="62e8b-119">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62e8b-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62e8b-120">Remarks</span></span>  
 <span data-ttu-id="62e8b-121">Zapoznaj się z <xref:System.Runtime.Serialization.DataContractSerializer> dokumentacją, aby uzyskać więcej informacji na temat znanych typów.</span><span class="sxs-lookup"><span data-stu-id="62e8b-121">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="62e8b-122">`<dataContractSerializer>`Element Behavior (jeśli istnieje) powinien zawsze występować przed `<enableWebScript>` elementem Behavior w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="62e8b-122">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="62e8b-123">W przeciwnym razie zachowanie nie jest zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="62e8b-123">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e8b-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62e8b-124">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="62e8b-125">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="62e8b-125">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="62e8b-126">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="62e8b-126">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
