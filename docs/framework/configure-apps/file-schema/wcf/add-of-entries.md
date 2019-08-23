---
title: <add> dla <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 690fd07159e07b7e037f7330b31fdcba423e80f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920129"
---
# <a name="add-of-entries"></a><span data-ttu-id="20092-102">\<Dodaj > \<wpisów ></span><span class="sxs-lookup"><span data-stu-id="20092-102">\<add> of \<entries></span></span>
<span data-ttu-id="20092-103">Reprezentuje wpis routingu, który mapuje filtr do punktu końcowego klienta, który został wcześniej zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="20092-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="20092-104">Komunikaty pasujące do tego filtru zostaną wysłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="20092-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="20092-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="20092-105">\<system.serviceModel></span></span>  
<span data-ttu-id="20092-106">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="20092-106">\<routing></span></span>  
<span data-ttu-id="20092-107">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="20092-107">\<filterTables></span></span>  
<span data-ttu-id="20092-108">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="20092-108">\<filterTable></span></span>  
<span data-ttu-id="20092-109">\<> wpisów</span><span class="sxs-lookup"><span data-stu-id="20092-109">\<entries></span></span>  
<span data-ttu-id="20092-110">\<add></span><span class="sxs-lookup"><span data-stu-id="20092-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20092-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="20092-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20092-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="20092-112">Attributes and Elements</span></span>  
 <span data-ttu-id="20092-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="20092-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20092-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="20092-114">Attributes</span></span>  
  
|<span data-ttu-id="20092-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="20092-115">Attribute</span></span>|<span data-ttu-id="20092-116">Opis</span><span class="sxs-lookup"><span data-stu-id="20092-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20092-117">backupList</span><span class="sxs-lookup"><span data-stu-id="20092-117">backupList</span></span>|<span data-ttu-id="20092-118">Ciąg określający odwołanie do listy kopii zapasowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="20092-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="20092-119">endpoint</span><span class="sxs-lookup"><span data-stu-id="20092-119">endpoint</span></span>|<span data-ttu-id="20092-120">Ciąg określający odwołanie do punktu końcowego klienta, który będzie odbierać komunikaty zgodne z filtrem określonym przez `filterName` atrybut.</span><span class="sxs-lookup"><span data-stu-id="20092-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="20092-121">filterName</span><span class="sxs-lookup"><span data-stu-id="20092-121">filterName</span></span>|<span data-ttu-id="20092-122">Ciąg określający odwołanie do elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="20092-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="20092-123">priority</span><span class="sxs-lookup"><span data-stu-id="20092-123">priority</span></span>|<span data-ttu-id="20092-124">Liczba całkowita, która określa priorytet tego wpisu.</span><span class="sxs-lookup"><span data-stu-id="20092-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="20092-125">Wpisy w tabeli routingu będą oceniane na podstawie priorytetu, a wartość 0 to najniższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="20092-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="20092-126">Wszystkie wpisy o określonym priorytecie są oceniane jednocześnie, jeśli nie zostanie znaleziony pasujący wpis dla bieżącego priorytetu, zostanie obliczony następny poziom priorytetu.</span><span class="sxs-lookup"><span data-stu-id="20092-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="20092-127">Ta wartość jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="20092-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20092-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="20092-128">Child Elements</span></span>  
 <span data-ttu-id="20092-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="20092-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20092-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="20092-130">Parent Elements</span></span>  
  
|<span data-ttu-id="20092-131">Element</span><span class="sxs-lookup"><span data-stu-id="20092-131">Element</span></span>|<span data-ttu-id="20092-132">Opis</span><span class="sxs-lookup"><span data-stu-id="20092-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20092-133">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="20092-133">\<routing></span></span>](routing.md)|<span data-ttu-id="20092-134">Sekcja konfiguracji, która zawiera wpisy mapowania routingu.</span><span class="sxs-lookup"><span data-stu-id="20092-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20092-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20092-135">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
