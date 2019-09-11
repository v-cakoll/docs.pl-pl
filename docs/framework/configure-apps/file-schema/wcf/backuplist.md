---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 478211755b9131c03b72777ee95ff7223b9092c9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850272"
---
# <a name="backuplist"></a><span data-ttu-id="570b6-101">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="570b6-101">\<backupList></span></span>
<span data-ttu-id="570b6-102">Reprezentuje sekcję konfiguracji służącą do definiowania listy kopii zapasowych, która wylicza zestaw punktów końcowych, które mają być używane przez usługę routingu w przypadku, gdy podstawowy punkt końcowy nie zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="570b6-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="570b6-103">Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu automatycznie przejdzie w tryb failover do kolejnej listy.</span><span class="sxs-lookup"><span data-stu-id="570b6-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="570b6-104">Dzięki temu można szybko dodać niezawodność do aplikacji bez konieczności uczenia się aplikacji klienckiej, jak obsługiwać złożone wzorce lub wszystkie usługi są wdrażane.</span><span class="sxs-lookup"><span data-stu-id="570b6-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
<span data-ttu-id="570b6-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="570b6-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="570b6-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="570b6-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="570b6-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> routingu**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="570b6-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="570b6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupLists >** ](backuplists.md)</span><span class="sxs-lookup"><span data-stu-id="570b6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)</span></span>\
<span data-ttu-id="570b6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<backupList >**</span><span class="sxs-lookup"><span data-stu-id="570b6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="570b6-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="570b6-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="570b6-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="570b6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="570b6-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="570b6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="570b6-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="570b6-113">Attributes</span></span>  
  
|<span data-ttu-id="570b6-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="570b6-114">Attribute</span></span>|<span data-ttu-id="570b6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="570b6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="570b6-116">nazwa</span><span class="sxs-lookup"><span data-stu-id="570b6-116">name</span></span>|<span data-ttu-id="570b6-117">Ciąg określający nazwę używaną do identyfikowania tej listy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="570b6-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="570b6-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="570b6-118">Child Elements</span></span>  
  
|<span data-ttu-id="570b6-119">Element</span><span class="sxs-lookup"><span data-stu-id="570b6-119">Element</span></span>|<span data-ttu-id="570b6-120">Opis</span><span class="sxs-lookup"><span data-stu-id="570b6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="570b6-121">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="570b6-121">\<filter></span></span>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="570b6-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="570b6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="570b6-123">Element</span><span class="sxs-lookup"><span data-stu-id="570b6-123">Element</span></span>|<span data-ttu-id="570b6-124">Opis</span><span class="sxs-lookup"><span data-stu-id="570b6-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="570b6-125">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="570b6-125">\<routing></span></span>](routing.md)|<span data-ttu-id="570b6-126">Lista punktów końcowych kopii zapasowych.</span><span class="sxs-lookup"><span data-stu-id="570b6-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="570b6-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="570b6-127">Remarks</span></span>  
 <span data-ttu-id="570b6-128">Ta sekcja zawiera uporządkowaną kolekcję punktów końcowych, do której zostanie wysłany komunikat w przypadku wyjątku komunikacji podczas wysyłania do podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="570b6-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="570b6-129">Jeśli wysyłanie do podstawowego punktu końcowego wymienione w `endpointName` [ \<atrybucie Dodawanie >](add-of-entries.md) zakończy się niepowodzeniem z wyjątkiem komunikacji, usługa routingu podejmie próbę wysłania komunikatu do pierwszego punktu końcowego w tej sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="570b6-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="570b6-130">Jeśli to również się nie powiedzie z wyjątkiem komunikacji, usługa routingu podejmie próbę wysłania komunikatu do następnego komunikatu zawartego w tej sekcji do momentu pomyślnej próby wysłania, zwracając błąd inny niż wyjątek komunikacji lub wszystkie punkty końcowe w Kolekcja zwróciła błąd.</span><span class="sxs-lookup"><span data-stu-id="570b6-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="570b6-131">W poniższym przykładzie, jeśli Wyślij do podstawowego punktu końcowego o nazwie "Destination" zwróci wyjątek komunikacji, usługa podejmie próbę wysłania komunikatu do "alternateServiceQueue".</span><span class="sxs-lookup"><span data-stu-id="570b6-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="570b6-132">Jeśli ta próba zwróci również wyjątek komunikacji, usługa routingu podejmie próbę wysłania komunikatu do następnego punktu końcowego w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="570b6-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="570b6-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="570b6-133">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
