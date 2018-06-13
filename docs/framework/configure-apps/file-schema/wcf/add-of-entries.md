---
title: '&lt;add&gt; w &lt;entries&gt;'
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: a6960c16c84c13d905f0993ee3cfc1cf67df07fc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744983"
---
# <a name="ltaddgt-of-ltentriesgt"></a><span data-ttu-id="53739-102">&lt;add&gt; w &lt;entries&gt;</span><span class="sxs-lookup"><span data-stu-id="53739-102">&lt;add&gt; of &lt;entries&gt;</span></span>
<span data-ttu-id="53739-103">Reprezentuje pozycji routingu mapowanego klienta punktu końcowego, który został uprzednio zdefiniowany filtr.</span><span class="sxs-lookup"><span data-stu-id="53739-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="53739-104">Komunikatów spełniające warunki tego filtru będą wysyłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="53739-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="53739-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="53739-105">\<system.serviceModel></span></span>  
<span data-ttu-id="53739-106">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="53739-106">\<routing></span></span>  
<span data-ttu-id="53739-107">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="53739-107">\<routingTables></span></span>  
<span data-ttu-id="53739-108">\<Tabela ></span><span class="sxs-lookup"><span data-stu-id="53739-108">\<table></span></span>  
<span data-ttu-id="53739-109">\<wpisy ></span><span class="sxs-lookup"><span data-stu-id="53739-109">\<entries></span></span>  
<span data-ttu-id="53739-110">\<add></span><span class="sxs-lookup"><span data-stu-id="53739-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53739-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="53739-111">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53739-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="53739-112">Attributes and Elements</span></span>  
 <span data-ttu-id="53739-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="53739-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53739-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="53739-114">Attributes</span></span>  
  
|<span data-ttu-id="53739-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="53739-115">Attribute</span></span>|<span data-ttu-id="53739-116">Opis</span><span class="sxs-lookup"><span data-stu-id="53739-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53739-117">backupList</span><span class="sxs-lookup"><span data-stu-id="53739-117">backupList</span></span>|<span data-ttu-id="53739-118">Ciąg, który określa odwołania do tworzenia kopii zapasowej listy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="53739-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="53739-119">endpoint</span><span class="sxs-lookup"><span data-stu-id="53739-119">endpoint</span></span>|<span data-ttu-id="53739-120">Ciąg określający odwołanie do punktu końcowego klienta, które będą otrzymywać wiadomości, zgodne z filtrem określonym przez `filterName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="53739-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="53739-121">filterName</span><span class="sxs-lookup"><span data-stu-id="53739-121">filterName</span></span>|<span data-ttu-id="53739-122">Ciąg określający odwołanie do elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="53739-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="53739-123">priorytet</span><span class="sxs-lookup"><span data-stu-id="53739-123">priority</span></span>|<span data-ttu-id="53739-124">Liczba całkowita określająca priorytet tego wpisu.</span><span class="sxs-lookup"><span data-stu-id="53739-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="53739-125">Wpisy w tabeli routingu będą oceniane na podstawie priorytetu, używając 0 oznacza najniższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="53739-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="53739-126">Wszystkie wpisy dla priorytetu są oceniane jednocześnie, jeśli brak zgodności można odnaleźć wpisu dla Bieżący priorytet ocenia się na następny poziom priorytetu.</span><span class="sxs-lookup"><span data-stu-id="53739-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="53739-127">Ta wartość jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="53739-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53739-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="53739-128">Child Elements</span></span>  
 <span data-ttu-id="53739-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="53739-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53739-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="53739-130">Parent Elements</span></span>  
  
|<span data-ttu-id="53739-131">Element</span><span class="sxs-lookup"><span data-stu-id="53739-131">Element</span></span>|<span data-ttu-id="53739-132">Opis</span><span class="sxs-lookup"><span data-stu-id="53739-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53739-133">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="53739-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="53739-134">Sekcja konfiguracyjna, zawierającą pozycje mapowania routingu.</span><span class="sxs-lookup"><span data-stu-id="53739-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53739-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53739-135">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
