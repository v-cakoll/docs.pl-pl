---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 9c4c7fa4f778642d549deebce6e7476f4da13a0d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283689"
---
# <a name="entries"></a><span data-ttu-id="1a934-101">\<entries></span><span class="sxs-lookup"><span data-stu-id="1a934-101">\<entries></span></span>
<span data-ttu-id="1a934-102">Wpis routingu, który zawiera mapowania między filtrami i docelowymi punktami końcowymi, aby wysyłać komunikaty do kiedy filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="1a934-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="1a934-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1a934-103">\<system.serviceModel></span></span>  
<span data-ttu-id="1a934-104">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="1a934-104">\<routing></span></span>  
<span data-ttu-id="1a934-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="1a934-105">\<routingTables></span></span>  
<span data-ttu-id="1a934-106">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="1a934-106">\<table></span></span>  
<span data-ttu-id="1a934-107">\<entries></span><span class="sxs-lookup"><span data-stu-id="1a934-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a934-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a934-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a934-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1a934-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1a934-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1a934-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a934-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1a934-111">Attributes</span></span>  
 <span data-ttu-id="1a934-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="1a934-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1a934-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1a934-113">Child Elements</span></span>  
  
|<span data-ttu-id="1a934-114">Element</span><span class="sxs-lookup"><span data-stu-id="1a934-114">Element</span></span>|<span data-ttu-id="1a934-115">Opis</span><span class="sxs-lookup"><span data-stu-id="1a934-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a934-116">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="1a934-116">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="1a934-117">Mapuje punkt końcowy klienta, który został uprzednio zdefiniowany filtr.</span><span class="sxs-lookup"><span data-stu-id="1a934-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="1a934-118">Komunikaty pasujących do tego filtru będą wysyłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="1a934-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a934-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1a934-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1a934-120">Element</span><span class="sxs-lookup"><span data-stu-id="1a934-120">Element</span></span>|<span data-ttu-id="1a934-121">Opis</span><span class="sxs-lookup"><span data-stu-id="1a934-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a934-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="1a934-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="1a934-123">Sekcja konfiguracji, który zawiera tabelę routingu.</span><span class="sxs-lookup"><span data-stu-id="1a934-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a934-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a934-124">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
