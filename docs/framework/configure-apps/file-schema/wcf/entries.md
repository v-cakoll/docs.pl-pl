---
title: '&lt;Wpisy&gt;'
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 8c442990ee736c17b71b625e06d961230a8ceed2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146436"
---
# <a name="ltentriesgt"></a><span data-ttu-id="1ad7e-102">&lt;Wpisy&gt;</span><span class="sxs-lookup"><span data-stu-id="1ad7e-102">&lt;entries&gt;</span></span>
<span data-ttu-id="1ad7e-103">Wpis routingu, który zawiera mapowania między filtrami i docelowymi punktami końcowymi, aby wysyłać komunikaty do kiedy filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="1ad7e-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="1ad7e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1ad7e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1ad7e-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="1ad7e-105">\<routing></span></span>  
<span data-ttu-id="1ad7e-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="1ad7e-106">\<routingTables></span></span>  
<span data-ttu-id="1ad7e-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="1ad7e-107">\<table></span></span>  
<span data-ttu-id="1ad7e-108">\<wpisy ></span><span class="sxs-lookup"><span data-stu-id="1ad7e-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ad7e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ad7e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ad7e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1ad7e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1ad7e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1ad7e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ad7e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1ad7e-112">Attributes</span></span>  
 <span data-ttu-id="1ad7e-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="1ad7e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1ad7e-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1ad7e-114">Child Elements</span></span>  
  
|<span data-ttu-id="1ad7e-115">Element</span><span class="sxs-lookup"><span data-stu-id="1ad7e-115">Element</span></span>|<span data-ttu-id="1ad7e-116">Opis</span><span class="sxs-lookup"><span data-stu-id="1ad7e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ad7e-117">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="1ad7e-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="1ad7e-118">Mapuje punkt końcowy klienta, który został uprzednio zdefiniowany filtr.</span><span class="sxs-lookup"><span data-stu-id="1ad7e-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="1ad7e-119">Komunikaty pasujących do tego filtru będą wysyłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="1ad7e-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ad7e-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1ad7e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1ad7e-121">Element</span><span class="sxs-lookup"><span data-stu-id="1ad7e-121">Element</span></span>|<span data-ttu-id="1ad7e-122">Opis</span><span class="sxs-lookup"><span data-stu-id="1ad7e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ad7e-123">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="1ad7e-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="1ad7e-124">Sekcja konfiguracji, który zawiera tabelę routingu.</span><span class="sxs-lookup"><span data-stu-id="1ad7e-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ad7e-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ad7e-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
