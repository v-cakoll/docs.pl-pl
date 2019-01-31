---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 5aa5d75e12852fe6a0e4e9a2eb4ae57d25d1022c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272697"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="8c8f4-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="8c8f4-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="8c8f4-103">Reprezentuje element root dla sekcji <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8c8f4-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="8c8f4-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="8c8f4-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c8f4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c8f4-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c8f4-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8c8f4-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8c8f4-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8c8f4-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c8f4-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8c8f4-108">Attributes</span></span>  
 <span data-ttu-id="8c8f4-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="8c8f4-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8c8f4-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8c8f4-110">Child Elements</span></span>  
  
|<span data-ttu-id="8c8f4-111">Element</span><span class="sxs-lookup"><span data-stu-id="8c8f4-111">Element</span></span>|<span data-ttu-id="8c8f4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8c8f4-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c8f4-113">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="8c8f4-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="8c8f4-114">Umożliwia dodanie znane typy, które ma być używany podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="8c8f4-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8c8f4-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8c8f4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="8c8f4-116">Element</span><span class="sxs-lookup"><span data-stu-id="8c8f4-116">Element</span></span>|<span data-ttu-id="8c8f4-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8c8f4-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c8f4-118">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="8c8f4-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="8c8f4-119">Element najwyższego poziomu dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8c8f4-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c8f4-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c8f4-120">See also</span></span>
- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="8c8f4-121">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="8c8f4-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="8c8f4-122">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="8c8f4-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
