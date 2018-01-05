---
title: '&lt;wpisy&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1bd6fd679d3f6440ff685c8cd2646b1fa0a13e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltentriesgt"></a><span data-ttu-id="f2463-102">&lt;wpisy&gt;</span><span class="sxs-lookup"><span data-stu-id="f2463-102">&lt;entries&gt;</span></span>
<span data-ttu-id="f2463-103">Wpis routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi do wysyłania komunikatów do gdy kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="f2463-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="f2463-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f2463-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f2463-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="f2463-105">\<routing></span></span>  
<span data-ttu-id="f2463-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="f2463-106">\<routingTables></span></span>  
<span data-ttu-id="f2463-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="f2463-107">\<table></span></span>  
<span data-ttu-id="f2463-108">\<wpisy ></span><span class="sxs-lookup"><span data-stu-id="f2463-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2463-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2463-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2463-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f2463-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f2463-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f2463-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2463-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f2463-112">Attributes</span></span>  
 <span data-ttu-id="f2463-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="f2463-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f2463-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f2463-114">Child Elements</span></span>  
  
|<span data-ttu-id="f2463-115">Element</span><span class="sxs-lookup"><span data-stu-id="f2463-115">Element</span></span>|<span data-ttu-id="f2463-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f2463-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2463-117">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="f2463-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="f2463-118">Mapuje klienta punktu końcowego, który został uprzednio zdefiniowany filtr.</span><span class="sxs-lookup"><span data-stu-id="f2463-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="f2463-119">Komunikatów spełniające warunki tego filtru będą wysyłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="f2463-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2463-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f2463-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f2463-121">Element</span><span class="sxs-lookup"><span data-stu-id="f2463-121">Element</span></span>|<span data-ttu-id="f2463-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f2463-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2463-123">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="f2463-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="f2463-124">Sekcja konfiguracyjna, który zawiera tabelę routingu.</span><span class="sxs-lookup"><span data-stu-id="f2463-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2463-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2463-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
