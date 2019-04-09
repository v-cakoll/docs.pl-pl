---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c34eba2614a354f1753d8da077f8653f2c260a97
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165896"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="f9aa2-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="f9aa2-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="f9aa2-103">Reprezentuje element root dla sekcji <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f9aa2-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="f9aa2-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="f9aa2-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9aa2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9aa2-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9aa2-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f9aa2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f9aa2-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f9aa2-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9aa2-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f9aa2-108">Attributes</span></span>  
 <span data-ttu-id="f9aa2-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="f9aa2-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f9aa2-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f9aa2-110">Child Elements</span></span>  
  
|<span data-ttu-id="f9aa2-111">Element</span><span class="sxs-lookup"><span data-stu-id="f9aa2-111">Element</span></span>|<span data-ttu-id="f9aa2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f9aa2-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9aa2-113">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="f9aa2-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="f9aa2-114">Umożliwia dodanie znane typy, które ma być używany podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="f9aa2-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9aa2-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f9aa2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f9aa2-116">Element</span><span class="sxs-lookup"><span data-stu-id="f9aa2-116">Element</span></span>|<span data-ttu-id="f9aa2-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f9aa2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9aa2-118">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="f9aa2-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="f9aa2-119">Element najwyższego poziomu dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f9aa2-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9aa2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9aa2-120">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="f9aa2-121">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="f9aa2-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="f9aa2-122">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="f9aa2-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
