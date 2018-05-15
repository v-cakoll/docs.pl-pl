---
title: '&lt;dataContractSerializer&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 5f2a05fdf2e38923205092b232995a70a87f7e87
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltdatacontractserializergt"></a><span data-ttu-id="2878b-102">&lt;dataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="2878b-102">&lt;dataContractSerializer&gt;</span></span>
<span data-ttu-id="2878b-103">Zawiera dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2878b-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="2878b-104">Ten element występuje w dwóch różnych hierarchii.</span><span class="sxs-lookup"><span data-stu-id="2878b-104">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="2878b-105">Co znajduje się w poniższej sekcji hierarchii schematu, a druga jest wymieniony w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="2878b-105">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="2878b-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2878b-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="2878b-107">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="2878b-107">\<behaviors></span></span>  
<span data-ttu-id="2878b-108">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2878b-108">\<serviceBehaviors></span></span>  
<span data-ttu-id="2878b-109">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="2878b-109">\<behavior></span></span>  
<span data-ttu-id="2878b-110">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="2878b-110">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2878b-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="2878b-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
   maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2878b-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2878b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2878b-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2878b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2878b-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2878b-114">Attributes</span></span>  
  
|<span data-ttu-id="2878b-115">Element</span><span class="sxs-lookup"><span data-stu-id="2878b-115">Element</span></span>|<span data-ttu-id="2878b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="2878b-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2878b-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="2878b-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="2878b-118">Wartość logiczna określająca, czy można zignorować dane dostarczone przez punkt końcowy, gdy jest on serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="2878b-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="2878b-119">Ten atrybut nie można ustawić tylko na `<dataContractSerializer>` w obszarze `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="2878b-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="2878b-120">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="2878b-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="2878b-121">Liczba całkowita określająca maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="2878b-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="2878b-122">Ten atrybut jest 65536.</span><span class="sxs-lookup"><span data-stu-id="2878b-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2878b-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2878b-123">Child Elements</span></span>  
 <span data-ttu-id="2878b-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="2878b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2878b-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2878b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2878b-126">Element</span><span class="sxs-lookup"><span data-stu-id="2878b-126">Element</span></span>|<span data-ttu-id="2878b-127">Opis</span><span class="sxs-lookup"><span data-stu-id="2878b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2878b-128">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="2878b-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="2878b-129">Kolekcję ustawień zachowania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="2878b-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="2878b-130">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="2878b-130">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="2878b-131">Reprezentuje element główny <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2878b-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2878b-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2878b-132">Remarks</span></span>  
 <span data-ttu-id="2878b-133">Jak już wspomniano w wprowadzenie tego tematu, to drugiej hierarchii, w którym \<X509Extension > element występuje.</span><span class="sxs-lookup"><span data-stu-id="2878b-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="2878b-134">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="2878b-134">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="2878b-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="2878b-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="2878b-136">Aby uzyskać więcej informacji na temat znanych typów, zobacz <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2878b-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2878b-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2878b-137">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="2878b-138">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="2878b-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="2878b-139">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="2878b-139">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
