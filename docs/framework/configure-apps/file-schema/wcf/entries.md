---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 5561cf61cef2258ec61bd32770538add1c69f5c1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201796"
---
# <a name="entries"></a><span data-ttu-id="6a4e8-101">\<entries></span><span class="sxs-lookup"><span data-stu-id="6a4e8-101">\<entries></span></span>
<span data-ttu-id="6a4e8-102">Wpis routingu, który zawiera mapowania między filtrami i docelowymi punktami końcowymi, aby wysyłać komunikaty do kiedy filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="6a4e8-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="6a4e8-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6a4e8-103">\<system.serviceModel></span></span>  
<span data-ttu-id="6a4e8-104">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="6a4e8-104">\<routing></span></span>  
<span data-ttu-id="6a4e8-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="6a4e8-105">\<routingTables></span></span>  
<span data-ttu-id="6a4e8-106">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="6a4e8-106">\<table></span></span>  
<span data-ttu-id="6a4e8-107">\<entries></span><span class="sxs-lookup"><span data-stu-id="6a4e8-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a4e8-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a4e8-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a4e8-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6a4e8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6a4e8-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6a4e8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a4e8-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6a4e8-111">Attributes</span></span>  
 <span data-ttu-id="6a4e8-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="6a4e8-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6a4e8-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6a4e8-113">Child Elements</span></span>  
  
|<span data-ttu-id="6a4e8-114">Element</span><span class="sxs-lookup"><span data-stu-id="6a4e8-114">Element</span></span>|<span data-ttu-id="6a4e8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6a4e8-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a4e8-116">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="6a4e8-116">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="6a4e8-117">Mapuje punkt końcowy klienta, który został uprzednio zdefiniowany filtr.</span><span class="sxs-lookup"><span data-stu-id="6a4e8-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="6a4e8-118">Komunikaty pasujących do tego filtru będą wysyłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="6a4e8-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6a4e8-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6a4e8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6a4e8-120">Element</span><span class="sxs-lookup"><span data-stu-id="6a4e8-120">Element</span></span>|<span data-ttu-id="6a4e8-121">Opis</span><span class="sxs-lookup"><span data-stu-id="6a4e8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a4e8-122">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="6a4e8-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="6a4e8-123">Sekcja konfiguracji, który zawiera tabelę routingu.</span><span class="sxs-lookup"><span data-stu-id="6a4e8-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a4e8-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a4e8-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
