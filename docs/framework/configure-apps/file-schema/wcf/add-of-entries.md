---
title: <add> z <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 7267b8719987ecd25bcca78a7897a0d4172a42ef
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264573"
---
# <a name="add-of-entries"></a><span data-ttu-id="30374-102">\<Dodaj > z \<wpisów ></span><span class="sxs-lookup"><span data-stu-id="30374-102">\<add> of \<entries></span></span>
<span data-ttu-id="30374-103">Reprezentuje pozycji routingu, który jest mapowany punkt końcowy klienta, który został uprzednio zdefiniowany filtr.</span><span class="sxs-lookup"><span data-stu-id="30374-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="30374-104">Komunikaty pasujących do tego filtru będą wysyłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="30374-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="30374-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="30374-105">\<system.serviceModel></span></span>  
<span data-ttu-id="30374-106">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="30374-106">\<routing></span></span>  
<span data-ttu-id="30374-107">\<filterTables></span><span class="sxs-lookup"><span data-stu-id="30374-107">\<filterTables></span></span>  
<span data-ttu-id="30374-108">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="30374-108">\<filterTable></span></span>  
<span data-ttu-id="30374-109">\<entries></span><span class="sxs-lookup"><span data-stu-id="30374-109">\<entries></span></span>  
<span data-ttu-id="30374-110">\<add></span><span class="sxs-lookup"><span data-stu-id="30374-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30374-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="30374-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30374-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="30374-112">Attributes and Elements</span></span>  
 <span data-ttu-id="30374-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="30374-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30374-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="30374-114">Attributes</span></span>  
  
|<span data-ttu-id="30374-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="30374-115">Attribute</span></span>|<span data-ttu-id="30374-116">Opis</span><span class="sxs-lookup"><span data-stu-id="30374-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30374-117">backupList</span><span class="sxs-lookup"><span data-stu-id="30374-117">backupList</span></span>|<span data-ttu-id="30374-118">Ciąg, który określa odwołanie do tworzenia kopii zapasowej listy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="30374-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="30374-119">endpoint</span><span class="sxs-lookup"><span data-stu-id="30374-119">endpoint</span></span>|<span data-ttu-id="30374-120">Ciąg określający odniesienie do klienta punkt końcowy, który będą wysyłane wiadomości, które są zgodne z filtrem określonym przez `filterName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="30374-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="30374-121">filterName</span><span class="sxs-lookup"><span data-stu-id="30374-121">filterName</span></span>|<span data-ttu-id="30374-122">Ciąg, który określa odwołanie do elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="30374-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="30374-123">priority</span><span class="sxs-lookup"><span data-stu-id="30374-123">priority</span></span>|<span data-ttu-id="30374-124">Liczba całkowita, która określa priorytet tego wpisu.</span><span class="sxs-lookup"><span data-stu-id="30374-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="30374-125">Wpisy w tabeli routingu będą oceniane na podstawie priorytetu, używając najniższy priorytet 0.</span><span class="sxs-lookup"><span data-stu-id="30374-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="30374-126">Wszystkie wpisy dla określonego priorytetu są obliczane jednocześnie, jeśli brak zgodności można odnaleźć wpisu dla Bieżący priorytet zostaną ocenione na następny poziom priorytetu.</span><span class="sxs-lookup"><span data-stu-id="30374-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="30374-127">Ta wartość jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="30374-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30374-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="30374-128">Child Elements</span></span>  
 <span data-ttu-id="30374-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="30374-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30374-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="30374-130">Parent Elements</span></span>  
  
|<span data-ttu-id="30374-131">Element</span><span class="sxs-lookup"><span data-stu-id="30374-131">Element</span></span>|<span data-ttu-id="30374-132">Opis</span><span class="sxs-lookup"><span data-stu-id="30374-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30374-133">\<routing></span><span class="sxs-lookup"><span data-stu-id="30374-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="30374-134">Sekcja konfiguracji, który zawiera pozycje mapowania routingu.</span><span class="sxs-lookup"><span data-stu-id="30374-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30374-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30374-135">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
