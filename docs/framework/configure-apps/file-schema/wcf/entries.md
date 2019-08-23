---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 610ba29ec98f4b1f2a9b1db3542bcb3aefb46457
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925650"
---
# <a name="entries"></a><span data-ttu-id="db1a5-101">\<> wpisów</span><span class="sxs-lookup"><span data-stu-id="db1a5-101">\<entries></span></span>
<span data-ttu-id="db1a5-102">Wpis routingu zawierający mapowania między filtrami routingu i docelowymi punktami końcowymi, do których mają być wysyłane komunikaty, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="db1a5-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="db1a5-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="db1a5-103">\<system.serviceModel></span></span>  
<span data-ttu-id="db1a5-104">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="db1a5-104">\<routing></span></span>  
<span data-ttu-id="db1a5-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="db1a5-105">\<routingTables></span></span>  
<span data-ttu-id="db1a5-106">\<> tabeli</span><span class="sxs-lookup"><span data-stu-id="db1a5-106">\<table></span></span>  
<span data-ttu-id="db1a5-107">\<> wpisów</span><span class="sxs-lookup"><span data-stu-id="db1a5-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db1a5-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="db1a5-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db1a5-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="db1a5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="db1a5-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="db1a5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db1a5-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="db1a5-111">Attributes</span></span>  
 <span data-ttu-id="db1a5-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="db1a5-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="db1a5-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="db1a5-113">Child Elements</span></span>  
  
|<span data-ttu-id="db1a5-114">Element</span><span class="sxs-lookup"><span data-stu-id="db1a5-114">Element</span></span>|<span data-ttu-id="db1a5-115">Opis</span><span class="sxs-lookup"><span data-stu-id="db1a5-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db1a5-116">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="db1a5-116">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="db1a5-117">Mapuje filtr do punktu końcowego klienta, który został wcześniej zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="db1a5-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="db1a5-118">Komunikaty pasujące do tego filtru zostaną wysłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="db1a5-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="db1a5-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="db1a5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="db1a5-120">Element</span><span class="sxs-lookup"><span data-stu-id="db1a5-120">Element</span></span>|<span data-ttu-id="db1a5-121">Opis</span><span class="sxs-lookup"><span data-stu-id="db1a5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db1a5-122">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="db1a5-122">\<routing></span></span>](routing.md)|<span data-ttu-id="db1a5-123">Sekcja konfiguracji, która zawiera tabelę routingu.</span><span class="sxs-lookup"><span data-stu-id="db1a5-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="db1a5-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db1a5-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
