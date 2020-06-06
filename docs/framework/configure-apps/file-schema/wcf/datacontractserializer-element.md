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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400448"
---
# \<dataContractSerializer>
<span data-ttu-id="0cdc0-101">Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="0cdc0-101">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="0cdc0-102">Ten element występuje w dwóch różnych hierarchiach.</span><span class="sxs-lookup"><span data-stu-id="0cdc0-102">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="0cdc0-103">Jeden z nich znajduje się w poniższej sekcji hierarchii schematu, a drugi jest wymieniony w sekcji uwagi.</span><span class="sxs-lookup"><span data-stu-id="0cdc0-103">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="0cdc0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0cdc0-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0cdc0-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0cdc0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0cdc0-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0cdc0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0cdc0-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0cdc0-107">Attributes</span></span>  
  
|<span data-ttu-id="0cdc0-108">Element</span><span class="sxs-lookup"><span data-stu-id="0cdc0-108">Element</span></span>|<span data-ttu-id="0cdc0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0cdc0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0cdc0-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="0cdc0-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="0cdc0-111">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jest on serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="0cdc0-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="0cdc0-112">Ten atrybut jest tylko do settable dla `<dataContractSerializer>` `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="0cdc0-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="0cdc0-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="0cdc0-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="0cdc0-114">Liczba całkowita, która określa maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="0cdc0-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="0cdc0-115">Ten atrybut to 65536.</span><span class="sxs-lookup"><span data-stu-id="0cdc0-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0cdc0-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0cdc0-116">Child Elements</span></span>  
 <span data-ttu-id="0cdc0-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="0cdc0-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0cdc0-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0cdc0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0cdc0-119">Element</span><span class="sxs-lookup"><span data-stu-id="0cdc0-119">Element</span></span>|<span data-ttu-id="0cdc0-120">Opis</span><span class="sxs-lookup"><span data-stu-id="0cdc0-120">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|<span data-ttu-id="0cdc0-121">Kolekcja ustawień zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="0cdc0-121">A collection of settings for the behavior of a service.</span></span>|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="0cdc0-122">Reprezentuje element główny dla <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawień <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="0cdc0-122">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cdc0-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0cdc0-123">Remarks</span></span>  
 <span data-ttu-id="0cdc0-124">Zgodnie z wprowadzeniem tego tematu jest to druga hierarchia, w której \<X509Extension> występuje element.</span><span class="sxs-lookup"><span data-stu-id="0cdc0-124">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 <span data-ttu-id="0cdc0-125">Aby uzyskać więcej informacji na temat znanych typów, zobacz <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="0cdc0-125">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cdc0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0cdc0-126">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="0cdc0-127">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="0cdc0-127">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="0cdc0-128">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="0cdc0-128">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
