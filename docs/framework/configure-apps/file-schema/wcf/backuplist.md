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
# <a name="backuplist"></a>\<backupList >
Reprezentuje sekcję konfiguracji służącą do definiowania listy kopii zapasowych, która wylicza zestaw punktów końcowych, które mają być używane przez usługę routingu w przypadku, gdy podstawowy punkt końcowy nie zostanie osiągnięty. Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu automatycznie przejdzie w tryb failover do kolejnej listy.  Dzięki temu można szybko dodać niezawodność do aplikacji bez konieczności uczenia się aplikacji klienckiej, jak obsługiwać złożone wzorce lub wszystkie usługi są wdrażane.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> routingu**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupLists >** ](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<backupList >**  
  
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
