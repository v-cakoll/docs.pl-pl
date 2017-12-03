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
ms.openlocfilehash: ef9c58a9b4ecd6db8b4efe116f6fafba01c3f6f5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltentriesgt"></a><span data-ttu-id="3830c-102">&lt;wpisy&gt;</span><span class="sxs-lookup"><span data-stu-id="3830c-102">&lt;entries&gt;</span></span>
<span data-ttu-id="3830c-103">Wpis routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi do wysyłania komunikatów do gdy kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="3830c-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="3830c-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="3830c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3830c-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="3830c-105">\<routing></span></span>  
<span data-ttu-id="3830c-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="3830c-106">\<routingTables></span></span>  
<span data-ttu-id="3830c-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="3830c-107">\<table></span></span>  
<span data-ttu-id="3830c-108">\<wpisy ></span><span class="sxs-lookup"><span data-stu-id="3830c-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3830c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="3830c-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3830c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3830c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3830c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3830c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3830c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3830c-112">Attributes</span></span>  
 <span data-ttu-id="3830c-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="3830c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3830c-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3830c-114">Child Elements</span></span>  
  
|<span data-ttu-id="3830c-115">Element</span><span class="sxs-lookup"><span data-stu-id="3830c-115">Element</span></span>|<span data-ttu-id="3830c-116">Opis</span><span class="sxs-lookup"><span data-stu-id="3830c-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3830c-117">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="3830c-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="3830c-118">Mapuje klienta punktu końcowego, który został uprzednio zdefiniowany filtr.</span><span class="sxs-lookup"><span data-stu-id="3830c-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="3830c-119">Komunikatów spełniające warunki tego filtru będą wysyłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="3830c-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3830c-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3830c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3830c-121">Element</span><span class="sxs-lookup"><span data-stu-id="3830c-121">Element</span></span>|<span data-ttu-id="3830c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="3830c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3830c-123">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="3830c-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="3830c-124">Sekcja konfiguracyjna, który zawiera tabelę routingu.</span><span class="sxs-lookup"><span data-stu-id="3830c-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3830c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3830c-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
