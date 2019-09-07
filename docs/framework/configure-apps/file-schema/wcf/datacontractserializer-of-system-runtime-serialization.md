---
title: <dataContractSerializer>< System. Runtime. Serialization >
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: eb556f533af1f99049382e9a2e34465f88d563db
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398080"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="f4d59-102">\<> DataContractSerializer elementu \<system. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="f4d59-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="f4d59-103">Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f4d59-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
<span data-ttu-id="f4d59-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f4d59-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f4d59-105">&nbsp;&nbsp;[ **\<> System. Runtime. Serialization**](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="f4d59-105">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="f4d59-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> dataContractSerializer**</span><span class="sxs-lookup"><span data-stu-id="f4d59-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4d59-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4d59-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4d59-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f4d59-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f4d59-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f4d59-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4d59-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f4d59-110">Attributes</span></span>  
  
|<span data-ttu-id="f4d59-111">Element</span><span class="sxs-lookup"><span data-stu-id="f4d59-111">Element</span></span>|<span data-ttu-id="f4d59-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f4d59-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f4d59-113">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="f4d59-113">ignoreExtensionDataObject</span></span>|<span data-ttu-id="f4d59-114">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jest on serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="f4d59-114">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="f4d59-115">Ten atrybut jest tylko do settable dla `<dataContractSerializer>` `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f4d59-115">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="f4d59-116">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="f4d59-116">maxItemsInObjectGraph</span></span>|<span data-ttu-id="f4d59-117">Liczba całkowita, która określa maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="f4d59-117">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="f4d59-118">Ten atrybut to 65536.</span><span class="sxs-lookup"><span data-stu-id="f4d59-118">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4d59-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f4d59-119">Child Elements</span></span>  
  
|<span data-ttu-id="f4d59-120">Element</span><span class="sxs-lookup"><span data-stu-id="f4d59-120">Element</span></span>|<span data-ttu-id="f4d59-121">Opis</span><span class="sxs-lookup"><span data-stu-id="f4d59-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4d59-122">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="f4d59-122">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="f4d59-123">Zawiera znane typy <xref:System.Runtime.Serialization.DataContractSerializer> używane podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="f4d59-123">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="f4d59-124">Aby uzyskać więcej informacji na temat kontraktów danych i znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="f4d59-124">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4d59-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f4d59-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f4d59-126">Element</span><span class="sxs-lookup"><span data-stu-id="f4d59-126">Element</span></span>|<span data-ttu-id="f4d59-127">Opis</span><span class="sxs-lookup"><span data-stu-id="f4d59-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4d59-128">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="f4d59-128">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="f4d59-129">Reprezentuje element główny dla <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji <xref:System.Runtime.Serialization.DataContractSerializer>ustawień.</span><span class="sxs-lookup"><span data-stu-id="f4d59-129">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4d59-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f4d59-130">Remarks</span></span>  
 <span data-ttu-id="f4d59-131">Aby uzyskać więcej informacji na temat znanych typów <xref:System.Runtime.Serialization.DataContractSerializer> , zobacz i [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="f4d59-131">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d59-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4d59-132">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="f4d59-133">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="f4d59-133">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
