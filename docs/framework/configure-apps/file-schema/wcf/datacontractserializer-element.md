---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: b635f03d1e4a6628a76d678f7366482717276376
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116392"
---
# <a name="datacontractserializer"></a><span data-ttu-id="b5068-101">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="b5068-101">\<dataContractSerializer></span></span>
<span data-ttu-id="b5068-102">Zawierająca dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b5068-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="b5068-103">Ten element występuje w dwóch różnych hierarchii.</span><span class="sxs-lookup"><span data-stu-id="b5068-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="b5068-104">Jeden jest wymieniony w poniższej sekcji hierarchia schematu, a druga znajduje się w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="b5068-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="b5068-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b5068-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b5068-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="b5068-106">\<behaviors></span></span>  
<span data-ttu-id="b5068-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b5068-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="b5068-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b5068-108">\<behavior></span></span>  
<span data-ttu-id="b5068-109">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="b5068-109">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5068-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5068-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5068-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b5068-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b5068-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b5068-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5068-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b5068-113">Attributes</span></span>  
  
|<span data-ttu-id="b5068-114">Element</span><span class="sxs-lookup"><span data-stu-id="b5068-114">Element</span></span>|<span data-ttu-id="b5068-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b5068-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5068-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="b5068-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="b5068-117">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jego serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="b5068-117">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="b5068-118">Ten atrybut jest można ustawić tylko na `<dataContractSerializer>` w obszarze `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b5068-118">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="b5068-119">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="b5068-119">maxItemsInObjectGraph</span></span>|<span data-ttu-id="b5068-120">Liczba całkowita określająca maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="b5068-120">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="b5068-121">Ten atrybut jest 65536.</span><span class="sxs-lookup"><span data-stu-id="b5068-121">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5068-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b5068-122">Child Elements</span></span>  
 <span data-ttu-id="b5068-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="b5068-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5068-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b5068-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b5068-125">Element</span><span class="sxs-lookup"><span data-stu-id="b5068-125">Element</span></span>|<span data-ttu-id="b5068-126">Opis</span><span class="sxs-lookup"><span data-stu-id="b5068-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5068-127">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b5068-127">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="b5068-128">Kolekcję ustawień zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="b5068-128">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="b5068-129">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="b5068-129">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="b5068-130">Reprezentuje element root dla sekcji <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b5068-130">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5068-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5068-131">Remarks</span></span>  
 <span data-ttu-id="b5068-132">Jak wspomniano we wprowadzeniu do tego tematu, jest to druga hierarchia, w którym \<X509Extension > element występuje.</span><span class="sxs-lookup"><span data-stu-id="b5068-132">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="b5068-133">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="b5068-133">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="b5068-134">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="b5068-134">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="b5068-135">Aby uzyskać więcej informacji na temat znanych typów, zobacz <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b5068-135">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5068-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5068-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="b5068-137">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="b5068-137">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="b5068-138">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="b5068-138">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
