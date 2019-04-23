---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 5561cf61cef2258ec61bd32770538add1c69f5c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201796"
---
# <a name="entries"></a><span data-ttu-id="c6a61-101">\<entries></span><span class="sxs-lookup"><span data-stu-id="c6a61-101">\<entries></span></span>
<span data-ttu-id="c6a61-102">Wpis routingu, który zawiera mapowania między filtrami i docelowymi punktami końcowymi, aby wysyłać komunikaty do kiedy filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="c6a61-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="c6a61-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c6a61-103">\<system.serviceModel></span></span>  
<span data-ttu-id="c6a61-104">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="c6a61-104">\<routing></span></span>  
<span data-ttu-id="c6a61-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="c6a61-105">\<routingTables></span></span>  
<span data-ttu-id="c6a61-106">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="c6a61-106">\<table></span></span>  
<span data-ttu-id="c6a61-107">\<entries></span><span class="sxs-lookup"><span data-stu-id="c6a61-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6a61-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6a61-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6a61-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c6a61-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c6a61-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c6a61-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6a61-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c6a61-111">Attributes</span></span>  
 <span data-ttu-id="c6a61-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="c6a61-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c6a61-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c6a61-113">Child Elements</span></span>  
  
|<span data-ttu-id="c6a61-114">Element</span><span class="sxs-lookup"><span data-stu-id="c6a61-114">Element</span></span>|<span data-ttu-id="c6a61-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c6a61-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6a61-116">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="c6a61-116">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="c6a61-117">Mapuje punkt końcowy klienta, który został uprzednio zdefiniowany filtr.</span><span class="sxs-lookup"><span data-stu-id="c6a61-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="c6a61-118">Komunikaty pasujących do tego filtru będą wysyłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="c6a61-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6a61-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c6a61-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c6a61-120">Element</span><span class="sxs-lookup"><span data-stu-id="c6a61-120">Element</span></span>|<span data-ttu-id="c6a61-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c6a61-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6a61-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="c6a61-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="c6a61-123">Sekcja konfiguracji, który zawiera tabelę routingu.</span><span class="sxs-lookup"><span data-stu-id="c6a61-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6a61-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6a61-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
