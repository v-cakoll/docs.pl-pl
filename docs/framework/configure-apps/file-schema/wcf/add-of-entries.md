---
title: '&lt;add&gt; w &lt;entries&gt;'
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 5a61aefd92390eefb95d1f3e39236e53fa264990
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151507"
---
# <a name="ltaddgt-of-ltentriesgt"></a><span data-ttu-id="04cce-102">&lt;add&gt; w &lt;entries&gt;</span><span class="sxs-lookup"><span data-stu-id="04cce-102">&lt;add&gt; of &lt;entries&gt;</span></span>
<span data-ttu-id="04cce-103">Reprezentuje pozycji routingu, który jest mapowany punkt końcowy klienta, który został uprzednio zdefiniowany filtr.</span><span class="sxs-lookup"><span data-stu-id="04cce-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="04cce-104">Komunikaty pasujących do tego filtru będą wysyłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="04cce-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="04cce-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="04cce-105">\<system.serviceModel></span></span>  
<span data-ttu-id="04cce-106">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="04cce-106">\<routing></span></span>  
<span data-ttu-id="04cce-107">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="04cce-107">\<filterTables></span></span>  
<span data-ttu-id="04cce-108">\<filterTable ></span><span class="sxs-lookup"><span data-stu-id="04cce-108">\<filterTable></span></span>  
<span data-ttu-id="04cce-109">\<wpisy ></span><span class="sxs-lookup"><span data-stu-id="04cce-109">\<entries></span></span>  
<span data-ttu-id="04cce-110">\<add></span><span class="sxs-lookup"><span data-stu-id="04cce-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04cce-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="04cce-111">Syntax</span></span>  
  
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
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04cce-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="04cce-112">Attributes and Elements</span></span>  
 <span data-ttu-id="04cce-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="04cce-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04cce-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="04cce-114">Attributes</span></span>  
  
|<span data-ttu-id="04cce-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="04cce-115">Attribute</span></span>|<span data-ttu-id="04cce-116">Opis</span><span class="sxs-lookup"><span data-stu-id="04cce-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04cce-117">backupList</span><span class="sxs-lookup"><span data-stu-id="04cce-117">backupList</span></span>|<span data-ttu-id="04cce-118">Ciąg, który określa odwołanie do tworzenia kopii zapasowej listy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="04cce-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="04cce-119">endpoint</span><span class="sxs-lookup"><span data-stu-id="04cce-119">endpoint</span></span>|<span data-ttu-id="04cce-120">Ciąg określający odniesienie do klienta punkt końcowy, który będą wysyłane wiadomości, które są zgodne z filtrem określonym przez `filterName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="04cce-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="04cce-121">filterName</span><span class="sxs-lookup"><span data-stu-id="04cce-121">filterName</span></span>|<span data-ttu-id="04cce-122">Ciąg, który określa odwołanie do elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="04cce-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="04cce-123">priority</span><span class="sxs-lookup"><span data-stu-id="04cce-123">priority</span></span>|<span data-ttu-id="04cce-124">Liczba całkowita, która określa priorytet tego wpisu.</span><span class="sxs-lookup"><span data-stu-id="04cce-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="04cce-125">Wpisy w tabeli routingu będą oceniane na podstawie priorytetu, używając najniższy priorytet 0.</span><span class="sxs-lookup"><span data-stu-id="04cce-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="04cce-126">Wszystkie wpisy dla określonego priorytetu są obliczane jednocześnie, jeśli brak zgodności można odnaleźć wpisu dla Bieżący priorytet zostaną ocenione na następny poziom priorytetu.</span><span class="sxs-lookup"><span data-stu-id="04cce-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="04cce-127">Ta wartość jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="04cce-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04cce-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="04cce-128">Child Elements</span></span>  
 <span data-ttu-id="04cce-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="04cce-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04cce-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="04cce-130">Parent Elements</span></span>  
  
|<span data-ttu-id="04cce-131">Element</span><span class="sxs-lookup"><span data-stu-id="04cce-131">Element</span></span>|<span data-ttu-id="04cce-132">Opis</span><span class="sxs-lookup"><span data-stu-id="04cce-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04cce-133">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="04cce-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="04cce-134">Sekcja konfiguracji, który zawiera pozycje mapowania routingu.</span><span class="sxs-lookup"><span data-stu-id="04cce-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04cce-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04cce-135">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
