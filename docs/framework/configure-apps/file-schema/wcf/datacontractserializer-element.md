---
title: '&lt;DataContractSerializer&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: c79c8e8db2a4ea4526000bcbe336d1e664f9c4c2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150958"
---
# <a name="ltdatacontractserializergt"></a><span data-ttu-id="85454-102">&lt;DataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="85454-102">&lt;dataContractSerializer&gt;</span></span>
<span data-ttu-id="85454-103">Zawierająca dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="85454-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="85454-104">Ten element występuje w dwóch różnych hierarchii.</span><span class="sxs-lookup"><span data-stu-id="85454-104">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="85454-105">Jeden jest wymieniony w poniższej sekcji hierarchia schematu, a druga znajduje się w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="85454-105">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="85454-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="85454-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="85454-107">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="85454-107">\<behaviors></span></span>  
<span data-ttu-id="85454-108">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="85454-108">\<serviceBehaviors></span></span>  
<span data-ttu-id="85454-109">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="85454-109">\<behavior></span></span>  
<span data-ttu-id="85454-110">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="85454-110">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85454-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="85454-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85454-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="85454-112">Attributes and Elements</span></span>  
 <span data-ttu-id="85454-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="85454-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85454-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="85454-114">Attributes</span></span>  
  
|<span data-ttu-id="85454-115">Element</span><span class="sxs-lookup"><span data-stu-id="85454-115">Element</span></span>|<span data-ttu-id="85454-116">Opis</span><span class="sxs-lookup"><span data-stu-id="85454-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85454-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="85454-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="85454-118">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jego serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="85454-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="85454-119">Ten atrybut jest można ustawić tylko na `<dataContractSerializer>` w obszarze `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="85454-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="85454-120">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="85454-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="85454-121">Liczba całkowita określająca maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="85454-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="85454-122">Ten atrybut jest 65536.</span><span class="sxs-lookup"><span data-stu-id="85454-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85454-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="85454-123">Child Elements</span></span>  
 <span data-ttu-id="85454-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="85454-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85454-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="85454-125">Parent Elements</span></span>  
  
|<span data-ttu-id="85454-126">Element</span><span class="sxs-lookup"><span data-stu-id="85454-126">Element</span></span>|<span data-ttu-id="85454-127">Opis</span><span class="sxs-lookup"><span data-stu-id="85454-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85454-128">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="85454-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="85454-129">Kolekcję ustawień zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="85454-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="85454-130">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="85454-130">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="85454-131">Reprezentuje element root dla sekcji <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="85454-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85454-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85454-132">Remarks</span></span>  
 <span data-ttu-id="85454-133">Jak wspomniano we wprowadzeniu do tego tematu, jest to druga hierarchia, w którym \<X509Extension > element występuje.</span><span class="sxs-lookup"><span data-stu-id="85454-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="85454-134">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="85454-134">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="85454-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="85454-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="85454-136">Aby uzyskać więcej informacji na temat znanych typów, zobacz <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="85454-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85454-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85454-137">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="85454-138">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="85454-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="85454-139">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="85454-139">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
