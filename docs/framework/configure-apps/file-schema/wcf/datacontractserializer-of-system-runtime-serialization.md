---
title: <dataContractSerializer> of <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: c81fdb040f2e0d6c9a3728d8ed3b917443ecb42e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115365"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="daffd-102">\<dataContractSerializer> of \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="daffd-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="daffd-103">Zawierająca dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="daffd-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="daffd-104">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="daffd-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="daffd-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="daffd-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daffd-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="daffd-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="daffd-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="daffd-107">Attributes and Elements</span></span>  
 <span data-ttu-id="daffd-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="daffd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="daffd-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="daffd-109">Attributes</span></span>  
  
|<span data-ttu-id="daffd-110">Element</span><span class="sxs-lookup"><span data-stu-id="daffd-110">Element</span></span>|<span data-ttu-id="daffd-111">Opis</span><span class="sxs-lookup"><span data-stu-id="daffd-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="daffd-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="daffd-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="daffd-113">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jego serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="daffd-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="daffd-114">Ten atrybut jest można ustawić tylko na `<dataContractSerializer>` w obszarze `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="daffd-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="daffd-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="daffd-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="daffd-116">Liczba całkowita określająca maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="daffd-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="daffd-117">Ten atrybut jest 65536.</span><span class="sxs-lookup"><span data-stu-id="daffd-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="daffd-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="daffd-118">Child Elements</span></span>  
  
|<span data-ttu-id="daffd-119">Element</span><span class="sxs-lookup"><span data-stu-id="daffd-119">Element</span></span>|<span data-ttu-id="daffd-120">Opis</span><span class="sxs-lookup"><span data-stu-id="daffd-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="daffd-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="daffd-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="daffd-122">Zawiera znane typy, które <xref:System.Runtime.Serialization.DataContractSerializer> używa podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="daffd-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="daffd-123">Aby uzyskać więcej informacji na temat kontraktów danych i znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="daffd-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="daffd-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="daffd-124">Parent Elements</span></span>  
  
|<span data-ttu-id="daffd-125">Element</span><span class="sxs-lookup"><span data-stu-id="daffd-125">Element</span></span>|<span data-ttu-id="daffd-126">Opis</span><span class="sxs-lookup"><span data-stu-id="daffd-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="daffd-127">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="daffd-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="daffd-128">Reprezentuje element root dla sekcji <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="daffd-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="daffd-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="daffd-129">Remarks</span></span>  
 <span data-ttu-id="daffd-130">Aby uzyskać więcej informacji na temat znanych typów, zobacz <xref:System.Runtime.Serialization.DataContractSerializer> i [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="daffd-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daffd-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="daffd-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="daffd-132">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="daffd-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
