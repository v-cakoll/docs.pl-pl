---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: b67f51e634d1294830690dad8c8cffb1fc9a6cd2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399462"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="38959-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="38959-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="38959-103">Reprezentuje element główny dla <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji <xref:System.Runtime.Serialization.DataContractSerializer>ustawień.</span><span class="sxs-lookup"><span data-stu-id="38959-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

<span data-ttu-id="38959-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="38959-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="38959-105">&nbsp;&nbsp; **\<> System. Runtime. Serialization**</span><span class="sxs-lookup"><span data-stu-id="38959-105">&nbsp;&nbsp;**\<system.runtime.serialization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38959-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="38959-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38959-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="38959-107">Attributes and Elements</span></span>  
 <span data-ttu-id="38959-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="38959-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38959-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="38959-109">Attributes</span></span>  
 <span data-ttu-id="38959-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="38959-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="38959-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="38959-111">Child Elements</span></span>  
  
|<span data-ttu-id="38959-112">Element</span><span class="sxs-lookup"><span data-stu-id="38959-112">Element</span></span>|<span data-ttu-id="38959-113">Opis</span><span class="sxs-lookup"><span data-stu-id="38959-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38959-114">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="38959-114">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="38959-115">Umożliwia dodanie znanych typów, które mają być używane podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="38959-115">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="38959-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="38959-116">Parent Elements</span></span>  
  
|<span data-ttu-id="38959-117">Element</span><span class="sxs-lookup"><span data-stu-id="38959-117">Element</span></span>|<span data-ttu-id="38959-118">Opis</span><span class="sxs-lookup"><span data-stu-id="38959-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38959-119">\<> elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="38959-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="38959-120">Element najwyższego poziomu dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="38959-120">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38959-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38959-121">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="38959-122">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="38959-122">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="38959-123">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="38959-123">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
 