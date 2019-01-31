---
title: <dataContractSerializer> z < system.runtime.serialization >
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: 488b0754194c1fa7896a168daac0a3a497076e56
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265938"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="5e906-102">\<dataContractSerializer> of \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="5e906-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="5e906-103">Zawierająca dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5e906-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="5e906-104">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="5e906-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="5e906-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="5e906-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e906-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e906-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e906-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5e906-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5e906-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5e906-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e906-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5e906-109">Attributes</span></span>  
  
|<span data-ttu-id="5e906-110">Element</span><span class="sxs-lookup"><span data-stu-id="5e906-110">Element</span></span>|<span data-ttu-id="5e906-111">Opis</span><span class="sxs-lookup"><span data-stu-id="5e906-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e906-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="5e906-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="5e906-113">Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jego serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="5e906-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="5e906-114">Ten atrybut jest można ustawić tylko na `<dataContractSerializer>` w obszarze `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="5e906-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="5e906-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="5e906-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="5e906-116">Liczba całkowita określająca maksymalną liczbę elementów do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="5e906-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="5e906-117">Ten atrybut jest 65536.</span><span class="sxs-lookup"><span data-stu-id="5e906-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e906-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5e906-118">Child Elements</span></span>  
  
|<span data-ttu-id="5e906-119">Element</span><span class="sxs-lookup"><span data-stu-id="5e906-119">Element</span></span>|<span data-ttu-id="5e906-120">Opis</span><span class="sxs-lookup"><span data-stu-id="5e906-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e906-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="5e906-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="5e906-122">Zawiera znane typy, które <xref:System.Runtime.Serialization.DataContractSerializer> używa podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="5e906-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="5e906-123">Aby uzyskać więcej informacji na temat kontraktów danych i znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="5e906-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e906-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5e906-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5e906-125">Element</span><span class="sxs-lookup"><span data-stu-id="5e906-125">Element</span></span>|<span data-ttu-id="5e906-126">Opis</span><span class="sxs-lookup"><span data-stu-id="5e906-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e906-127">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="5e906-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="5e906-128">Reprezentuje element root dla sekcji <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5e906-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e906-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e906-129">Remarks</span></span>  
 <span data-ttu-id="5e906-130">Aby uzyskać więcej informacji na temat znanych typów, zobacz <xref:System.Runtime.Serialization.DataContractSerializer> i [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="5e906-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e906-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e906-131">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="5e906-132">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="5e906-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
