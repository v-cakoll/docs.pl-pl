---
title: '&lt;dataContractSerializer&gt; w &lt;system.runtime.serialization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 39d24f03bde729e99b629162aee86efe4b60fdd1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltdatacontractserializergt-of-ltsystemruntimeserializationgt"></a><span data-ttu-id="51ea4-102">&lt;dataContractSerializer&gt; w &lt;system.runtime.serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="51ea4-102">&lt;dataContractSerializer&gt; of &lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="51ea4-103">Zawiera dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="51ea4-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="51ea4-104">\<System.Runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="51ea4-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="51ea4-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="51ea4-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51ea4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="51ea4-106">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
            maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String">  
          <knownType type="String">  
             <parameter index="Integer"  
                        type="String" />  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51ea4-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="51ea4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="51ea4-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="51ea4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51ea4-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="51ea4-109">Attributes</span></span>  
  
|<span data-ttu-id="51ea4-110">Element</span><span class="sxs-lookup"><span data-stu-id="51ea4-110">Element</span></span>|<span data-ttu-id="51ea4-111">Opis</span><span class="sxs-lookup"><span data-stu-id="51ea4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51ea4-112">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="51ea4-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="51ea4-113">Wartość logiczna określająca, czy można zignorować dane dostarczone przez punkt końcowy, gdy jest on serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="51ea4-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="51ea4-114">Ten atrybut nie można ustawić tylko na `<dataContractSerializer>` w obszarze `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="51ea4-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="51ea4-115">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="51ea4-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="51ea4-116">Liczba całkowita określająca maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="51ea4-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="51ea4-117">Ten atrybut jest 65536.</span><span class="sxs-lookup"><span data-stu-id="51ea4-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51ea4-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="51ea4-118">Child Elements</span></span>  
  
|<span data-ttu-id="51ea4-119">Element</span><span class="sxs-lookup"><span data-stu-id="51ea4-119">Element</span></span>|<span data-ttu-id="51ea4-120">Opis</span><span class="sxs-lookup"><span data-stu-id="51ea4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51ea4-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="51ea4-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="51ea4-122">Zawiera znane typy, które <xref:System.Runtime.Serialization.DataContractSerializer> używa podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="51ea4-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="51ea4-123">Aby uzyskać więcej informacji na temat kontraktów danych i znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="51ea4-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="51ea4-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="51ea4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="51ea4-125">Element</span><span class="sxs-lookup"><span data-stu-id="51ea4-125">Element</span></span>|<span data-ttu-id="51ea4-126">Opis</span><span class="sxs-lookup"><span data-stu-id="51ea4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51ea4-127">\<System.Runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="51ea4-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="51ea4-128">Reprezentuje element główny <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="51ea4-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51ea4-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51ea4-129">Remarks</span></span>  
 <span data-ttu-id="51ea4-130">Aby uzyskać więcej informacji na temat znanych typów, zobacz <xref:System.Runtime.Serialization.DataContractSerializer> i [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="51ea4-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ea4-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51ea4-131">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 [<span data-ttu-id="51ea4-132">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="51ea4-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
