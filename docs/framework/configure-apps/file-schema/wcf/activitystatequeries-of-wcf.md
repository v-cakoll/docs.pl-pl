---
title: '&lt;activityStateQueries&gt; w WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5261e0769e63513720cc2df185920d424fa1a8f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a>&lt;activityStateQueries&gt; w WCF
Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy. Na przykład może być do śledzenia każdorazowo po ukończeniu działania "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy. To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania. Stany do subskrybowania są wyszczególnione w ActivityStates.  
  
 Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
 \<system.serviceModel >  
\<Śledzenie >  
\<trackingProfile >  
\<przepływ pracy >  
\<activityStateQueries >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|Kwerenda, która służy do śledzenia Obsługa błędów występujących w ramach działania.  To zdarzenie występuje zawsze FaultHandler przetwarza błąd.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<przepływ pracy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>    
 <xref:System.Activities.Tracking.ActivityStateQuery>    
 [Kontrola i śledzenie przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
