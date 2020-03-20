---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c93a1f482882cc8cd9d229d82597efa64ba209bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152973"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="d0eb5-102">\<> system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="d0eb5-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="d0eb5-103">Reprezentuje element główny <xref:System.Runtime.Serialization> sekcji obszaru nazw i zawiera elementy <xref:System.Runtime.Serialization.DataContractSerializer>do ustawiania opcji programu .</span><span class="sxs-lookup"><span data-stu-id="d0eb5-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

<span data-ttu-id="d0eb5-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d0eb5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d0eb5-105">&nbsp;&nbsp;**\<>system.runtime.serialization**</span><span class="sxs-lookup"><span data-stu-id="d0eb5-105">&nbsp;&nbsp;**\<system.runtime.serialization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0eb5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0eb5-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0eb5-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d0eb5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d0eb5-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d0eb5-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0eb5-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0eb5-109">Attributes</span></span>  
 <span data-ttu-id="d0eb5-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="d0eb5-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d0eb5-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d0eb5-111">Child Elements</span></span>  
  
|<span data-ttu-id="d0eb5-112">Element</span><span class="sxs-lookup"><span data-stu-id="d0eb5-112">Element</span></span>|<span data-ttu-id="d0eb5-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d0eb5-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0eb5-114">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="d0eb5-114">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="d0eb5-115">Umożliwia dodawanie znanych typów, które mają być używane podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="d0eb5-115">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0eb5-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d0eb5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d0eb5-117">Element</span><span class="sxs-lookup"><span data-stu-id="d0eb5-117">Element</span></span>|<span data-ttu-id="d0eb5-118">Opis</span><span class="sxs-lookup"><span data-stu-id="d0eb5-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0eb5-119">\<element> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d0eb5-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="d0eb5-120">Element najwyższego poziomu dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d0eb5-120">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0eb5-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0eb5-121">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="d0eb5-122">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="d0eb5-122">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="d0eb5-123">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="d0eb5-123">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
