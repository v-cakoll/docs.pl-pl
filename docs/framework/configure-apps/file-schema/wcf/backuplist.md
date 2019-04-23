---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: b0a6c604b5741c1355c35fca510cd10544dab9f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135736"
---
# <a name="backuplist"></a><span data-ttu-id="ce0a2-101">\<backupList></span><span class="sxs-lookup"><span data-stu-id="ce0a2-101">\<backupList></span></span>
<span data-ttu-id="ce0a2-102">Reprezentuje sekcję konfiguracji dla definiowania listy kopii zapasowych, która wylicza zestaw punktów końcowych, które chcesz, aby usługa routingu do użycia w przypadku, gdy nie można nawiązać połączenia z podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ce0a2-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="ce0a2-103">Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu będzie automatycznie przełączać się kolejny na liście.</span><span class="sxs-lookup"><span data-stu-id="ce0a2-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="ce0a2-104">Dzięki temu możesz szybko dodać niezawodność do Twojej aplikacji bez konieczności nauki aplikacji klienckiej sposobu obsługi złożonych wzorów lub wszystkich usług wdrożonym.</span><span class="sxs-lookup"><span data-stu-id="ce0a2-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="ce0a2-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ce0a2-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ce0a2-106">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="ce0a2-106">\<routing></span></span>  
<span data-ttu-id="ce0a2-107">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="ce0a2-107">\<backupLists></span></span>  
<span data-ttu-id="ce0a2-108">\<backupList></span><span class="sxs-lookup"><span data-stu-id="ce0a2-108">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce0a2-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce0a2-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce0a2-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ce0a2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ce0a2-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ce0a2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce0a2-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ce0a2-112">Attributes</span></span>  
  
|<span data-ttu-id="ce0a2-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ce0a2-113">Attribute</span></span>|<span data-ttu-id="ce0a2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ce0a2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce0a2-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="ce0a2-115">name</span></span>|<span data-ttu-id="ce0a2-116">Ciąg określający nazwę użytą do identyfikacji listy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ce0a2-116">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce0a2-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ce0a2-117">Child Elements</span></span>  
  
|<span data-ttu-id="ce0a2-118">Element</span><span class="sxs-lookup"><span data-stu-id="ce0a2-118">Element</span></span>|<span data-ttu-id="ce0a2-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ce0a2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce0a2-120">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="ce0a2-120">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="ce0a2-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ce0a2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ce0a2-122">Element</span><span class="sxs-lookup"><span data-stu-id="ce0a2-122">Element</span></span>|<span data-ttu-id="ce0a2-123">Opis</span><span class="sxs-lookup"><span data-stu-id="ce0a2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce0a2-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="ce0a2-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="ce0a2-125">Lista punktów końcowych kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="ce0a2-125">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce0a2-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce0a2-126">Remarks</span></span>  
 <span data-ttu-id="ce0a2-127">Ta sekcja zawiera uporządkowaną kolekcję punktów końcowych, które wiadomości zostaną przekazane w przypadku wyjątku komunikacji podczas wysyłania do podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ce0a2-127">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="ce0a2-128">Jeżeli wysłanie do podstawowego punktu końcowego na liście `endpointName` atrybutu [ \<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) kończy się niepowodzeniem z wyjątkiem komunikacji, usługa routingu będzie próbował wysłać wiadomość do pierwszego punktu końcowego, w tym Sekcja konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ce0a2-128">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="ce0a2-129">Jeśli to nie powiedzie się także z wyjątkiem komunikacji, usługa routingu będzie próbował wysłać wiadomość do następnej wiadomości, które są zawarte w tej sekcji, dopóki próba wysłania zakończy się powodzeniem, zwraca błąd inny niż wyjątku komunikacji lub wszystkie punkty końcowe w Kolekcja ma zwróciła błąd.</span><span class="sxs-lookup"><span data-stu-id="ce0a2-129">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="ce0a2-130">W poniższym przykładzie Jeśli wysłanie do podstawowego punktu końcowego o nazwie "Miejsce docelowe" zwraca wyjątek komunikacji, usługa spróbuje wysłać wiadomość do "alternateServiceQueue".</span><span class="sxs-lookup"><span data-stu-id="ce0a2-130">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="ce0a2-131">Jeśli ta próba również zwraca wyjątek komunikacji, usługa routingu spróbuje wysłać wiadomość do następnego punktu końcowego w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ce0a2-131">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a><span data-ttu-id="ce0a2-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce0a2-132">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
