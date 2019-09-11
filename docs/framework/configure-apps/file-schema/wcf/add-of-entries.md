---
title: <add> dla <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 23b0a825ea593f85ade870d5b93367571eaa3ec0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850508"
---
# <a name="add-of-entries"></a><span data-ttu-id="6cc1c-102">\<Dodaj > \<wpisów ></span><span class="sxs-lookup"><span data-stu-id="6cc1c-102">\<add> of \<entries></span></span>
<span data-ttu-id="6cc1c-103">Reprezentuje wpis routingu, który mapuje filtr do punktu końcowego klienta, który został wcześniej zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="6cc1c-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="6cc1c-104">Komunikaty pasujące do tego filtru zostaną wysłane do tego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="6cc1c-104">Messages matching this filter will be sent to this destination.</span></span>  
  
<span data-ttu-id="6cc1c-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6cc1c-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6cc1c-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6cc1c-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6cc1c-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> routingu**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="6cc1c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="6cc1c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="6cc1c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="6cc1c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> filtrowania**](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="6cc1c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)</span></span>\
<span data-ttu-id="6cc1c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> wpisów**](entries.md)</span><span class="sxs-lookup"><span data-stu-id="6cc1c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)</span></span>\
<span data-ttu-id="6cc1c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="6cc1c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cc1c-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="6cc1c-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cc1c-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6cc1c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6cc1c-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6cc1c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cc1c-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6cc1c-115">Attributes</span></span>  
  
|<span data-ttu-id="6cc1c-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6cc1c-116">Attribute</span></span>|<span data-ttu-id="6cc1c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6cc1c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6cc1c-118">backupList</span><span class="sxs-lookup"><span data-stu-id="6cc1c-118">backupList</span></span>|<span data-ttu-id="6cc1c-119">Ciąg określający odwołanie do listy kopii zapasowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="6cc1c-119">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="6cc1c-120">endpoint</span><span class="sxs-lookup"><span data-stu-id="6cc1c-120">endpoint</span></span>|<span data-ttu-id="6cc1c-121">Ciąg określający odwołanie do punktu końcowego klienta, który będzie odbierać komunikaty zgodne z filtrem określonym przez `filterName` atrybut.</span><span class="sxs-lookup"><span data-stu-id="6cc1c-121">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="6cc1c-122">filterName</span><span class="sxs-lookup"><span data-stu-id="6cc1c-122">filterName</span></span>|<span data-ttu-id="6cc1c-123">Ciąg określający odwołanie do elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="6cc1c-123">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="6cc1c-124">priority</span><span class="sxs-lookup"><span data-stu-id="6cc1c-124">priority</span></span>|<span data-ttu-id="6cc1c-125">Liczba całkowita, która określa priorytet tego wpisu.</span><span class="sxs-lookup"><span data-stu-id="6cc1c-125">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="6cc1c-126">Wpisy w tabeli routingu będą oceniane na podstawie priorytetu, a wartość 0 to najniższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="6cc1c-126">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="6cc1c-127">Wszystkie wpisy o określonym priorytecie są oceniane jednocześnie, jeśli nie zostanie znaleziony pasujący wpis dla bieżącego priorytetu, zostanie obliczony następny poziom priorytetu.</span><span class="sxs-lookup"><span data-stu-id="6cc1c-127">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="6cc1c-128">Ta wartość jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="6cc1c-128">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6cc1c-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6cc1c-129">Child Elements</span></span>  
 <span data-ttu-id="6cc1c-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="6cc1c-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6cc1c-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6cc1c-131">Parent Elements</span></span>  
  
|<span data-ttu-id="6cc1c-132">Element</span><span class="sxs-lookup"><span data-stu-id="6cc1c-132">Element</span></span>|<span data-ttu-id="6cc1c-133">Opis</span><span class="sxs-lookup"><span data-stu-id="6cc1c-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6cc1c-134">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="6cc1c-134">\<routing></span></span>](routing.md)|<span data-ttu-id="6cc1c-135">Sekcja konfiguracji, która zawiera wpisy mapowania routingu.</span><span class="sxs-lookup"><span data-stu-id="6cc1c-135">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6cc1c-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6cc1c-136">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
