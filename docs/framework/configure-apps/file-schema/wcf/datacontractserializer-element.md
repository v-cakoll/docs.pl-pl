---
title: '&lt;dataContractSerializer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d38e3786c595c3fe6cc9ea54b68784c927901731
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltdatacontractserializergt"></a><span data-ttu-id="2b49d-102">&lt;dataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="2b49d-102">&lt;dataContractSerializer&gt;</span></span>
<span data-ttu-id="2b49d-103">Zawiera dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2b49d-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="2b49d-104">Ten element występuje w dwóch różnych hierarchii.</span><span class="sxs-lookup"><span data-stu-id="2b49d-104">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="2b49d-105">Co znajduje się w poniższej sekcji hierarchii schematu, a druga jest wymieniony w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="2b49d-105">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="2b49d-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2b49d-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="2b49d-107">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="2b49d-107">\<behaviors></span></span>  
<span data-ttu-id="2b49d-108">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2b49d-108">\<serviceBehaviors></span></span>  
<span data-ttu-id="2b49d-109">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="2b49d-109">\<behavior></span></span>  
<span data-ttu-id="2b49d-110">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="2b49d-110">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b49d-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b49d-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
   maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b49d-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2b49d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2b49d-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2b49d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b49d-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2b49d-114">Attributes</span></span>  
  
|<span data-ttu-id="2b49d-115">Element</span><span class="sxs-lookup"><span data-stu-id="2b49d-115">Element</span></span>|<span data-ttu-id="2b49d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="2b49d-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b49d-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="2b49d-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="2b49d-118">Wartość logiczna określająca, czy można zignorować dane dostarczone przez punkt końcowy, gdy jest on serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="2b49d-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="2b49d-119">Ten atrybut nie można ustawić tylko na `<dataContractSerializer>` w obszarze `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="2b49d-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="2b49d-120">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="2b49d-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="2b49d-121">Liczba całkowita określająca maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="2b49d-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="2b49d-122">Ten atrybut jest 65536.</span><span class="sxs-lookup"><span data-stu-id="2b49d-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b49d-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2b49d-123">Child Elements</span></span>  
 <span data-ttu-id="2b49d-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="2b49d-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b49d-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2b49d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2b49d-126">Element</span><span class="sxs-lookup"><span data-stu-id="2b49d-126">Element</span></span>|<span data-ttu-id="2b49d-127">Opis</span><span class="sxs-lookup"><span data-stu-id="2b49d-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b49d-128">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="2b49d-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="2b49d-129">Kolekcję ustawień zachowania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="2b49d-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="2b49d-130">\<System.Runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="2b49d-130">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="2b49d-131">Reprezentuje element główny <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2b49d-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b49d-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b49d-132">Remarks</span></span>  
 <span data-ttu-id="2b49d-133">Jak już wspomniano w wprowadzenie tego tematu, to drugiej hierarchii, w którym \<X509Extension > element występuje.</span><span class="sxs-lookup"><span data-stu-id="2b49d-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="2b49d-134">\<System.Runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="2b49d-134">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="2b49d-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="2b49d-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="2b49d-136">Aby uzyskać więcej informacji na temat znanych typów, zobacz <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2b49d-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b49d-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b49d-137">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="2b49d-138">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="2b49d-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="2b49d-139">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="2b49d-139">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
