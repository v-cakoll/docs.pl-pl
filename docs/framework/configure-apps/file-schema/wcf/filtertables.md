---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: a54386de369a11a1958e4d81ab01f053a0bc5b36
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55253980"
---
# <a name="filtertables"></a>\<filterTables>
Reprezentuje sekcję konfiguracji określającą tabele routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi do wysłania wiadomości, gdy filtr dopasowuje wartość.  
  
 \<system.serviceModel>  
\<Routing >  
\<routingTables>  
  
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
|[\<Filtry >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Tabele routingu, które zawierają mapowania między filtrami i docelowymi punktami końcowymi, aby wysyłać komunikaty do kiedy filtr dopasowuje wartość.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Sekcja konfiguracji, zawierający filtrów routingu i tabele routingu.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
