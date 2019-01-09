---
title: '&lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 1a6a7ac42b379dd8fb2ba80cf6a3a38998c26a59
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146553"
---
# <a name="ltbackuplistgt"></a><span data-ttu-id="adcc7-102">&lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="adcc7-102">&lt;backupList&gt;</span></span>
<span data-ttu-id="adcc7-103">Reprezentuje sekcję konfiguracji dla definiowania listy kopii zapasowych, która wylicza zestaw punktów końcowych, które chcesz, aby usługa routingu do użycia w przypadku, gdy nie można nawiązać połączenia z podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="adcc7-103">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="adcc7-104">Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu będzie automatycznie przełączać się kolejny na liście.</span><span class="sxs-lookup"><span data-stu-id="adcc7-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="adcc7-105">Dzięki temu możesz szybko dodać niezawodność do Twojej aplikacji bez konieczności nauki aplikacji klienckiej sposobu obsługi złożonych wzorów lub wszystkich usług wdrożonym.</span><span class="sxs-lookup"><span data-stu-id="adcc7-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="adcc7-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="adcc7-106">\<system.serviceModel></span></span>  
<span data-ttu-id="adcc7-107">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="adcc7-107">\<routing></span></span>  
<span data-ttu-id="adcc7-108">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="adcc7-108">\<backupLists></span></span>  
<span data-ttu-id="adcc7-109">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="adcc7-109">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adcc7-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="adcc7-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adcc7-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="adcc7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="adcc7-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="adcc7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adcc7-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="adcc7-113">Attributes</span></span>  
  
|<span data-ttu-id="adcc7-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="adcc7-114">Attribute</span></span>|<span data-ttu-id="adcc7-115">Opis</span><span class="sxs-lookup"><span data-stu-id="adcc7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="adcc7-116">nazwa</span><span class="sxs-lookup"><span data-stu-id="adcc7-116">name</span></span>|<span data-ttu-id="adcc7-117">Ciąg określający nazwę użytą do identyfikacji listy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="adcc7-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adcc7-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="adcc7-118">Child Elements</span></span>  
  
|<span data-ttu-id="adcc7-119">Element</span><span class="sxs-lookup"><span data-stu-id="adcc7-119">Element</span></span>|<span data-ttu-id="adcc7-120">Opis</span><span class="sxs-lookup"><span data-stu-id="adcc7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adcc7-121">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="adcc7-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="adcc7-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="adcc7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="adcc7-123">Element</span><span class="sxs-lookup"><span data-stu-id="adcc7-123">Element</span></span>|<span data-ttu-id="adcc7-124">Opis</span><span class="sxs-lookup"><span data-stu-id="adcc7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adcc7-125">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="adcc7-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="adcc7-126">Lista punktów końcowych kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="adcc7-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adcc7-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="adcc7-127">Remarks</span></span>  
 <span data-ttu-id="adcc7-128">Ta sekcja zawiera uporządkowaną kolekcję punktów końcowych, które wiadomości zostaną przekazane w przypadku wyjątku komunikacji podczas wysyłania do podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="adcc7-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="adcc7-129">Jeżeli wysłanie do podstawowego punktu końcowego na liście `endpointName` atrybutu [ \<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) kończy się niepowodzeniem z wyjątkiem komunikacji, usługa routingu będzie próbował wysłać wiadomość do pierwszego punktu końcowego, w tym Sekcja konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="adcc7-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="adcc7-130">Jeśli to nie powiedzie się także z wyjątkiem komunikacji, usługa routingu będzie próbował wysłać wiadomość do następnej wiadomości, które są zawarte w tej sekcji, dopóki próba wysłania zakończy się powodzeniem, zwraca błąd inny niż wyjątku komunikacji lub wszystkie punkty końcowe w Kolekcja ma zwróciła błąd.</span><span class="sxs-lookup"><span data-stu-id="adcc7-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="adcc7-131">W poniższym przykładzie Jeśli wysłanie do podstawowego punktu końcowego o nazwie "Miejsce docelowe" zwraca wyjątek komunikacji, usługa spróbuje wysłać wiadomość do "alternateServiceQueue".</span><span class="sxs-lookup"><span data-stu-id="adcc7-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="adcc7-132">Jeśli ta próba również zwraca wyjątek komunikacji, usługa routingu spróbuje wysłać wiadomość do następnego punktu końcowego w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="adcc7-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="adcc7-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adcc7-133">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
