---
title: '&lt;Wpisy&gt;'
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 8c442990ee736c17b71b625e06d961230a8ceed2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146436"
---
# <a name="ltentriesgt"></a>&lt;Wpisy&gt;
Wpis routingu, który zawiera mapowania między filtrami i docelowymi punktami końcowymi, aby wysyłać komunikaty do kiedy filtr dopasowuje wartość.  
  
 \<system.serviceModel>  
\<Routing >  
\<routingTables >  
\<Tabela >  
\<wpisy >  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtry >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Mapuje punkt końcowy klienta, który został uprzednio zdefiniowany filtr. Komunikaty pasujących do tego filtru będą wysyłane do tego miejsca docelowego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Routing >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Sekcja konfiguracji, który zawiera tabelę routingu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
