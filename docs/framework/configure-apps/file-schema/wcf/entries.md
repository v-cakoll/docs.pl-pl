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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9b6d8d1c3797d60b26443e07cc527ea8b86f526e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltentriesgt"></a><span data-ttu-id="23971-102">&lt;wpisy&gt;</span><span class="sxs-lookup"><span data-stu-id="23971-102">&lt;entries&gt;</span></span>
<span data-ttu-id="23971-103">Wpis routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi do wysyłania komunikatów do gdy kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="23971-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="23971-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="23971-104">\<system.serviceModel></span></span>  
<span data-ttu-id="23971-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="23971-105">\<routing></span></span>  
<span data-ttu-id="23971-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="23971-106">\<routingTables></span></span>  
<span data-ttu-id="23971-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="23971-107">\<table></span></span>  
<span data-ttu-id="23971-108">\<wpisy ></span><span class="sxs-lookup"><span data-stu-id="23971-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23971-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="23971-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="23971-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="23971-110">Attributes and Elements</span></span>  
 <span data-ttu-id="23971-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="23971-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23971-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="23971-112">Attributes</span></span>  
 <span data-ttu-id="23971-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="23971-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="23971-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="23971-114">Child Elements</span></span>  
  
|<span data-ttu-id="23971-115">Element</span><span class="sxs-lookup"><span data-stu-id="23971-115">Element</span></span>|<span data-ttu-id="23971-116">Opis</span><span class="sxs-lookup"><span data-stu-id="23971-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23971-117">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="23971-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="23971-118">Mapuje klienta punktu końcowego, który został uprzednio zdefiniowany filtr.</span><span class="sxs-lookup"><span data-stu-id="23971-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="23971-119">Komunikatów spełniające warunki tego filtru będą wysyłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="23971-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23971-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="23971-120">Parent Elements</span></span>  
  
|<span data-ttu-id="23971-121">Element</span><span class="sxs-lookup"><span data-stu-id="23971-121">Element</span></span>|<span data-ttu-id="23971-122">Opis</span><span class="sxs-lookup"><span data-stu-id="23971-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23971-123">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="23971-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="23971-124">Sekcja konfiguracyjna, który zawiera tabelę routingu.</span><span class="sxs-lookup"><span data-stu-id="23971-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23971-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23971-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
