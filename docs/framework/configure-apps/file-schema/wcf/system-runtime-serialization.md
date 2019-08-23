---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 4ec5cd19ccdc5c21a3caf426520d51442dc5ab3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938923"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="e9a55-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="e9a55-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="e9a55-103">Reprezentuje element główny dla <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji <xref:System.Runtime.Serialization.DataContractSerializer>ustawień.</span><span class="sxs-lookup"><span data-stu-id="e9a55-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="e9a55-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="e9a55-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9a55-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9a55-105">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9a55-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e9a55-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e9a55-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e9a55-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9a55-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e9a55-108">Attributes</span></span>  
 <span data-ttu-id="e9a55-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="e9a55-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e9a55-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e9a55-110">Child Elements</span></span>  
  
|<span data-ttu-id="e9a55-111">Element</span><span class="sxs-lookup"><span data-stu-id="e9a55-111">Element</span></span>|<span data-ttu-id="e9a55-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e9a55-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9a55-113">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="e9a55-113">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="e9a55-114">Umożliwia dodanie znanych typów, które mają być używane podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="e9a55-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9a55-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e9a55-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e9a55-116">Element</span><span class="sxs-lookup"><span data-stu-id="e9a55-116">Element</span></span>|<span data-ttu-id="e9a55-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e9a55-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9a55-118">\<> elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e9a55-118">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="e9a55-119">Element najwyższego poziomu dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e9a55-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9a55-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9a55-120">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="e9a55-121">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="e9a55-121">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="e9a55-122">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="e9a55-122">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
