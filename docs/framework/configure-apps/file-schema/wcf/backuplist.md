---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: d5feab6cb374f98e683cf15f797de4f478e23131
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919925"
---
# <a name="backuplist"></a>\<backupList >
Reprezentuje sekcję konfiguracji służącą do definiowania listy kopii zapasowych, która wylicza zestaw punktów końcowych, które mają być używane przez usługę routingu w przypadku, gdy podstawowy punkt końcowy nie zostanie osiągnięty. Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu automatycznie przejdzie w tryb failover do kolejnej listy.  Dzięki temu można szybko dodać niezawodność do aplikacji bez konieczności uczenia się aplikacji klienckiej, jak obsługiwać złożone wzorce lub wszystkie usługi są wdrażane.  
  
 \<system.serviceModel>  
\<> routingu  
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
|nazwa|Ciąg określający nazwę używaną do identyfikowania tej listy punktów końcowych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtr >](filter.md)||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> routingu](routing.md)|Lista punktów końcowych kopii zapasowych.|  
  
## <a name="remarks"></a>Uwagi  
 Ta sekcja zawiera uporządkowaną kolekcję punktów końcowych, do której zostanie wysłany komunikat w przypadku wyjątku komunikacji podczas wysyłania do podstawowego punktu końcowego.  
  
 Jeśli wysyłanie do podstawowego punktu końcowego wymienione w `endpointName` [ \<atrybucie Dodawanie >](add-of-entries.md) zakończy się niepowodzeniem z wyjątkiem komunikacji, usługa routingu podejmie próbę wysłania komunikatu do pierwszego punktu końcowego w tej sekcji konfiguracji. Jeśli to również się nie powiedzie z wyjątkiem komunikacji, usługa routingu podejmie próbę wysłania komunikatu do następnego komunikatu zawartego w tej sekcji do momentu pomyślnej próby wysłania, zwracając błąd inny niż wyjątek komunikacji lub wszystkie punkty końcowe w Kolekcja zwróciła błąd.  
  
 W poniższym przykładzie, jeśli Wyślij do podstawowego punktu końcowego o nazwie "Destination" zwróci wyjątek komunikacji, usługa podejmie próbę wysłania komunikatu do "alternateServiceQueue". Jeśli ta próba zwróci również wyjątek komunikacji, usługa routingu podejmie próbę wysłania komunikatu do następnego punktu końcowego w kolekcji.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
