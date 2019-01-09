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
# <a name="ltbackuplistgt"></a>&lt;backupList&gt;
Reprezentuje sekcję konfiguracji dla definiowania listy kopii zapasowych, która wylicza zestaw punktów końcowych, które chcesz, aby usługa routingu do użycia w przypadku, gdy nie można nawiązać połączenia z podstawowego punktu końcowego. Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu będzie automatycznie przełączać się kolejny na liście.  Dzięki temu możesz szybko dodać niezawodność do Twojej aplikacji bez konieczności nauki aplikacji klienckiej sposobu obsługi złożonych wzorów lub wszystkich usług wdrożonym.  
  
 \<system.serviceModel>  
\<Routing >  
\<backupLists >  
\<backupList >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Ciąg określający nazwę użytą do identyfikacji listy punktów końcowych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Routing >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Lista punktów końcowych kopii zapasowej.|  
  
## <a name="remarks"></a>Uwagi  
 Ta sekcja zawiera uporządkowaną kolekcję punktów końcowych, które wiadomości zostaną przekazane w przypadku wyjątku komunikacji podczas wysyłania do podstawowego punktu końcowego.  
  
 Jeżeli wysłanie do podstawowego punktu końcowego na liście `endpointName` atrybutu [ \<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) kończy się niepowodzeniem z wyjątkiem komunikacji, usługa routingu będzie próbował wysłać wiadomość do pierwszego punktu końcowego, w tym Sekcja konfiguracji. Jeśli to nie powiedzie się także z wyjątkiem komunikacji, usługa routingu będzie próbował wysłać wiadomość do następnej wiadomości, które są zawarte w tej sekcji, dopóki próba wysłania zakończy się powodzeniem, zwraca błąd inny niż wyjątku komunikacji lub wszystkie punkty końcowe w Kolekcja ma zwróciła błąd.  
  
 W poniższym przykładzie Jeśli wysłanie do podstawowego punktu końcowego o nazwie "Miejsce docelowe" zwraca wyjątek komunikacji, usługa spróbuje wysłać wiadomość do "alternateServiceQueue". Jeśli ta próba również zwraca wyjątek komunikacji, usługa routingu spróbuje wysłać wiadomość do następnego punktu końcowego w kolekcji.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
