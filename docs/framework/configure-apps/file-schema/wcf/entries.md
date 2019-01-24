---
title: '&lt;Wpisy&gt;'
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 33f98cb4b138307622a14463ce5a3008058b6e31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587063"
---
# <a name="ltentriesgt"></a><span data-ttu-id="1c29d-102">&lt;Wpisy&gt;</span><span class="sxs-lookup"><span data-stu-id="1c29d-102">&lt;entries&gt;</span></span>
<span data-ttu-id="1c29d-103">Wpis routingu, który zawiera mapowania między filtrami i docelowymi punktami końcowymi, aby wysyłać komunikaty do kiedy filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="1c29d-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="1c29d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1c29d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1c29d-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="1c29d-105">\<routing></span></span>  
<span data-ttu-id="1c29d-106">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="1c29d-106">\<routingTables></span></span>  
<span data-ttu-id="1c29d-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="1c29d-107">\<table></span></span>  
<span data-ttu-id="1c29d-108">\<entries></span><span class="sxs-lookup"><span data-stu-id="1c29d-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c29d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c29d-109">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c29d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1c29d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1c29d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1c29d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c29d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1c29d-112">Attributes</span></span>  
 <span data-ttu-id="1c29d-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="1c29d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1c29d-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1c29d-114">Child Elements</span></span>  
  
|<span data-ttu-id="1c29d-115">Element</span><span class="sxs-lookup"><span data-stu-id="1c29d-115">Element</span></span>|<span data-ttu-id="1c29d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="1c29d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c29d-117">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="1c29d-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="1c29d-118">Mapuje punkt końcowy klienta, który został uprzednio zdefiniowany filtr.</span><span class="sxs-lookup"><span data-stu-id="1c29d-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="1c29d-119">Komunikaty pasujących do tego filtru będą wysyłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="1c29d-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1c29d-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1c29d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1c29d-121">Element</span><span class="sxs-lookup"><span data-stu-id="1c29d-121">Element</span></span>|<span data-ttu-id="1c29d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="1c29d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c29d-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="1c29d-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="1c29d-124">Sekcja konfiguracji, który zawiera tabelę routingu.</span><span class="sxs-lookup"><span data-stu-id="1c29d-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c29d-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c29d-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
