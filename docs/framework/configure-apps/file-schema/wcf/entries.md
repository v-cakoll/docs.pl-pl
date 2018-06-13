---
title: '&lt;Wpisy&gt;'
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: b9cc7f7736ffefaca68a0f197bd064a99c4dca9a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746712"
---
# <a name="ltentriesgt"></a><span data-ttu-id="691d6-102">&lt;Wpisy&gt;</span><span class="sxs-lookup"><span data-stu-id="691d6-102">&lt;entries&gt;</span></span>
<span data-ttu-id="691d6-103">Wpis routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi do wysyłania komunikatów do gdy kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="691d6-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="691d6-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="691d6-104">\<system.serviceModel></span></span>  
<span data-ttu-id="691d6-105">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="691d6-105">\<routing></span></span>  
<span data-ttu-id="691d6-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="691d6-106">\<routingTables></span></span>  
<span data-ttu-id="691d6-107">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="691d6-107">\<table></span></span>  
<span data-ttu-id="691d6-108">\<wpisy ></span><span class="sxs-lookup"><span data-stu-id="691d6-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="691d6-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="691d6-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="691d6-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="691d6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="691d6-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="691d6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="691d6-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="691d6-112">Attributes</span></span>  
 <span data-ttu-id="691d6-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="691d6-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="691d6-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="691d6-114">Child Elements</span></span>  
  
|<span data-ttu-id="691d6-115">Element</span><span class="sxs-lookup"><span data-stu-id="691d6-115">Element</span></span>|<span data-ttu-id="691d6-116">Opis</span><span class="sxs-lookup"><span data-stu-id="691d6-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="691d6-117">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="691d6-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="691d6-118">Mapuje klienta punktu końcowego, który został uprzednio zdefiniowany filtr.</span><span class="sxs-lookup"><span data-stu-id="691d6-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="691d6-119">Komunikatów spełniające warunki tego filtru będą wysyłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="691d6-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="691d6-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="691d6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="691d6-121">Element</span><span class="sxs-lookup"><span data-stu-id="691d6-121">Element</span></span>|<span data-ttu-id="691d6-122">Opis</span><span class="sxs-lookup"><span data-stu-id="691d6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="691d6-123">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="691d6-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="691d6-124">Sekcja konfiguracyjna, który zawiera tabelę routingu.</span><span class="sxs-lookup"><span data-stu-id="691d6-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="691d6-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="691d6-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
