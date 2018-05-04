---
title: '&lt;faultPropagationQuery&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: fe3dd90a5c6b26537ab461b4bf4993df5be625a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a>&lt;faultPropagationQuery&gt; w WCF
Reprezentuje zapytanie, które jest używane do śledzenia Obsługa błędów występujących w ramach działania.  To zdarzenie występuje zawsze FaultHandler przetwarza błąd. Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania. Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.  
  
 Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
 \<system.serviceModel>  
\<Śledzenie >  
\<trackingProfile>  
\<przepływ pracy >  
\<faultPropagationQueries >  
\<faultPropagationQuery >  
  
## <a name="syntax"></a>Składnia  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|activityName|Ciąg, który określa nazwę propagowane błędu działanie obsługi błędów. Wartość domyślna to *, która wskazuje, że dla wszystkich działań zwracane są rekordy propagacji błędów.|  
|faultHandlerActivityName|Ciąg określający nazwę czynności, która została źródła błędu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<faultPropagationQueries>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|Reprezentuje listę elementów konfiguracji, które są używane do śledzenia Obsługa błędów występujących w ramach działania.  To zdarzenie występuje zawsze FaultHandler przetwarza błąd.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [Kontrola i śledzenie przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
