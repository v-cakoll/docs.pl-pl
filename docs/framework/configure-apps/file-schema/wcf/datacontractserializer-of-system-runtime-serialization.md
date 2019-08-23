---
title: <dataContractSerializer>< System. Runtime. Serialization >
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: 380d9ba5b8407d78b5045fd34fcdf37c0818d6f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919349"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="3046a-102">\<> DataContractSerializer elementu \<system. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="3046a-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="3046a-103">Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3046a-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="3046a-104">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="3046a-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="3046a-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="3046a-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3046a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3046a-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3046a-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3046a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3046a-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3046a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3046a-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3046a-109">Attributes</span></span>  
  
|<span data-ttu-id="3046a-110">Element</span><span class="sxs-lookup"><span data-stu-id="3046a-110">Element</span></span>|<span data-ttu-id="3046a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="3046a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3046a-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="3046a-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="3046a-113">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jest on serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="3046a-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="3046a-114">Ten atrybut jest tylko do settable dla `<dataContractSerializer>` `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="3046a-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="3046a-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="3046a-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="3046a-116">Liczba całkowita, która określa maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="3046a-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="3046a-117">Ten atrybut to 65536.</span><span class="sxs-lookup"><span data-stu-id="3046a-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3046a-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3046a-118">Child Elements</span></span>  
  
|<span data-ttu-id="3046a-119">Element</span><span class="sxs-lookup"><span data-stu-id="3046a-119">Element</span></span>|<span data-ttu-id="3046a-120">Opis</span><span class="sxs-lookup"><span data-stu-id="3046a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3046a-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="3046a-121">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="3046a-122">Zawiera znane typy <xref:System.Runtime.Serialization.DataContractSerializer> używane podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="3046a-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="3046a-123">Aby uzyskać więcej informacji na temat kontraktów danych i znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="3046a-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3046a-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3046a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3046a-125">Element</span><span class="sxs-lookup"><span data-stu-id="3046a-125">Element</span></span>|<span data-ttu-id="3046a-126">Opis</span><span class="sxs-lookup"><span data-stu-id="3046a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3046a-127">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="3046a-127">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="3046a-128">Reprezentuje element główny dla <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji <xref:System.Runtime.Serialization.DataContractSerializer>ustawień.</span><span class="sxs-lookup"><span data-stu-id="3046a-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3046a-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3046a-129">Remarks</span></span>  
 <span data-ttu-id="3046a-130">Aby uzyskać więcej informacji na temat znanych typów <xref:System.Runtime.Serialization.DataContractSerializer> , zobacz i [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="3046a-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3046a-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3046a-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="3046a-132">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="3046a-132">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
