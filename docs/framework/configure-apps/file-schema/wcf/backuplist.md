---
title: '&lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 6684dcc485ef1ee2c3e5501f2fbc43898e172958
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltbackuplistgt"></a>&lt;backupList&gt;
Reprezentuje sekcję konfiguracji dla definiowania listy kopii zapasowych, który wylicza zestaw punktów końcowych, które chcesz usługa routingu do użycia w przypadku, gdy podstawowy punkt końcowy jest nieosiągalny. Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu zostanie automatycznie awaryjnej do następnego w liście.  Dzięki temu można szybko dodać niezawodność do aplikacji bez konieczności nauki aplikacji klienckiej sposobu obsługi złożonych wzorów lub wszystkich usług wdrożonym.  
  
 \<system.serviceModel>  
\<Routing >  
\<backupLists >  
\<backupList >  
  
## <a name="syntax"></a>Składnia  
  
```xml 
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
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
 Ta sekcja zawiera uporządkowaną kolekcję punktów końcowych, które wiadomości zostaną przekazane w przypadku komunikacji wyjątek podczas wysyłania do podstawowego punktu końcowego.  
  
 Jeśli wysyłania do podstawowego punktu końcowego na liście `endpointName` atrybutu [ \<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) kończy się niepowodzeniem z wyjątkiem komunikacji, usługa routingu będzie podejmować próby wysłania wiadomości do pierwszego punktu końcowego, w tym Sekcja konfiguracji. Jeśli to nie powiedzie się także z wyjątkiem komunikacji, usługa routingu będzie podejmować próby wysłania wiadomości do następnej wiadomości, które są zawarte w tej sekcji, dopóki próby wysłania zakończy się powodzeniem, zwraca błąd niż wyjątek komunikacji lub wszystkie punkty końcowe w Kolekcja ma zwróciła błąd.  
  
 W poniższym przykładzie Jeśli wysyłania do podstawowego punktu końcowego o nazwie "Miejsce docelowe" zwraca wyjątek komunikacji, usługa będzie podejmować próby wysłać wiadomość do "alternateServiceQueue". Jeśli ta próba również zwraca wyjątek komunikacji, usługa routingu będzie podejmować próby wysłania wiadomości do następnego punktu końcowego w kolekcji.  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
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
