---
title: <add> z <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 1324803d7c0f127cfee9eadebff2672955780eda
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165415"
---
# <a name="add-of-entries"></a><span data-ttu-id="20ebf-102">\<Dodaj > z \<wpisów ></span><span class="sxs-lookup"><span data-stu-id="20ebf-102">\<add> of \<entries></span></span>
<span data-ttu-id="20ebf-103">Reprezentuje pozycji routingu, który jest mapowany punkt końcowy klienta, który został uprzednio zdefiniowany filtr.</span><span class="sxs-lookup"><span data-stu-id="20ebf-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="20ebf-104">Komunikaty pasujących do tego filtru będą wysyłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="20ebf-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="20ebf-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="20ebf-105">\<system.serviceModel></span></span>  
<span data-ttu-id="20ebf-106">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="20ebf-106">\<routing></span></span>  
<span data-ttu-id="20ebf-107">\<filterTables></span><span class="sxs-lookup"><span data-stu-id="20ebf-107">\<filterTables></span></span>  
<span data-ttu-id="20ebf-108">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="20ebf-108">\<filterTable></span></span>  
<span data-ttu-id="20ebf-109">\<entries></span><span class="sxs-lookup"><span data-stu-id="20ebf-109">\<entries></span></span>  
<span data-ttu-id="20ebf-110">\<add></span><span class="sxs-lookup"><span data-stu-id="20ebf-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20ebf-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="20ebf-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20ebf-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="20ebf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="20ebf-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="20ebf-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20ebf-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="20ebf-114">Attributes</span></span>  
  
|<span data-ttu-id="20ebf-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="20ebf-115">Attribute</span></span>|<span data-ttu-id="20ebf-116">Opis</span><span class="sxs-lookup"><span data-stu-id="20ebf-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20ebf-117">backupList</span><span class="sxs-lookup"><span data-stu-id="20ebf-117">backupList</span></span>|<span data-ttu-id="20ebf-118">Ciąg, który określa odwołanie do tworzenia kopii zapasowej listy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="20ebf-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="20ebf-119">endpoint</span><span class="sxs-lookup"><span data-stu-id="20ebf-119">endpoint</span></span>|<span data-ttu-id="20ebf-120">Ciąg określający odniesienie do klienta punkt końcowy, który będą wysyłane wiadomości, które są zgodne z filtrem określonym przez `filterName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="20ebf-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="20ebf-121">filterName</span><span class="sxs-lookup"><span data-stu-id="20ebf-121">filterName</span></span>|<span data-ttu-id="20ebf-122">Ciąg, który określa odwołanie do elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="20ebf-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="20ebf-123">priority</span><span class="sxs-lookup"><span data-stu-id="20ebf-123">priority</span></span>|<span data-ttu-id="20ebf-124">Liczba całkowita, która określa priorytet tego wpisu.</span><span class="sxs-lookup"><span data-stu-id="20ebf-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="20ebf-125">Wpisy w tabeli routingu będą oceniane na podstawie priorytetu, używając najniższy priorytet 0.</span><span class="sxs-lookup"><span data-stu-id="20ebf-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="20ebf-126">Wszystkie wpisy dla określonego priorytetu są obliczane jednocześnie, jeśli brak zgodności można odnaleźć wpisu dla Bieżący priorytet zostaną ocenione na następny poziom priorytetu.</span><span class="sxs-lookup"><span data-stu-id="20ebf-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="20ebf-127">Ta wartość jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="20ebf-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20ebf-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="20ebf-128">Child Elements</span></span>  
 <span data-ttu-id="20ebf-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="20ebf-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20ebf-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="20ebf-130">Parent Elements</span></span>  
  
|<span data-ttu-id="20ebf-131">Element</span><span class="sxs-lookup"><span data-stu-id="20ebf-131">Element</span></span>|<span data-ttu-id="20ebf-132">Opis</span><span class="sxs-lookup"><span data-stu-id="20ebf-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20ebf-133">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="20ebf-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="20ebf-134">Sekcja konfiguracji, który zawiera pozycje mapowania routingu.</span><span class="sxs-lookup"><span data-stu-id="20ebf-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20ebf-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20ebf-135">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
