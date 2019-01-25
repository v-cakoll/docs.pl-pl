---
title: '&lt;system.runtime.serialization&gt;'
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 6321ab192161468142a4cd4d2155d3f787bb0165
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600264"
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="65cf5-102">&lt;system.runtime.serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="65cf5-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="65cf5-103">Reprezentuje element root dla sekcji <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="65cf5-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="65cf5-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="65cf5-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65cf5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="65cf5-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65cf5-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="65cf5-106">Attributes and Elements</span></span>  
 <span data-ttu-id="65cf5-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="65cf5-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65cf5-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="65cf5-108">Attributes</span></span>  
 <span data-ttu-id="65cf5-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="65cf5-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="65cf5-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="65cf5-110">Child Elements</span></span>  
  
|<span data-ttu-id="65cf5-111">Element</span><span class="sxs-lookup"><span data-stu-id="65cf5-111">Element</span></span>|<span data-ttu-id="65cf5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="65cf5-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65cf5-113">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="65cf5-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="65cf5-114">Umożliwia dodanie znane typy, które ma być używany podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="65cf5-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65cf5-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="65cf5-115">Parent Elements</span></span>  
  
|<span data-ttu-id="65cf5-116">Element</span><span class="sxs-lookup"><span data-stu-id="65cf5-116">Element</span></span>|<span data-ttu-id="65cf5-117">Opis</span><span class="sxs-lookup"><span data-stu-id="65cf5-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65cf5-118">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="65cf5-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="65cf5-119">Element najwyższego poziomu dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="65cf5-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65cf5-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65cf5-120">See also</span></span>
- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="65cf5-121">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="65cf5-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="65cf5-122">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="65cf5-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
