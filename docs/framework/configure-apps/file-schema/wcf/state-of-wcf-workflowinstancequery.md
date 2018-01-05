---
title: "&lt;state&gt; w WCF — &lt;workflowInstanceQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edb6cc424be51e03b3c34182a2b456a9658e2bc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a>&lt;state&gt; w WCF — &lt;workflowInstanceQuery&gt;
Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.  
  
 Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
 \<system.serviceModel >  
\<Śledzenie >  
\<trackingProfile >  
\<przepływ pracy >  
\<workflowInstanceQueries >  
\<workflowInstanceQuery >  
\<Stany >  
\<Stan >  
  
## <a name="syntax"></a>Składnia  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Ciąg, który określa subskrybowanego stanu z wystąpienia śledzonych przepływu pracy podczas rekordem śledzenia.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Zwracane rekordy są filtrowane według stanów w tej kolekcji.  
  
 Stan możliwe wartości są opisane w poniższej tabeli.  
  
|Stan|Opis|  
|-----------|-----------------|  
|Zostało przerwane|Wystąpienie przepływu pracy zostało przerwane.|  
|Zakończone|Wystąpienie przepływu pracy jest zakończone.|  
|Usunięte|Wystąpienie przepływu pracy, został usunięty.|  
|Bezczynności (%)|Wystąpienie przepływu pracy jest bezczynny.|  
|Trwały|Wystąpienie przepływu pracy jest trwały.|  
|Wznowione|Wystąpienie przepływu pracy zostanie wznowione.|  
|Rozpoczęto|Wystąpienie przepływu pracy zostało rozpoczęte.|  
|UnhandledException|Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.|  
|Zwolniono|Wystąpienie przepływu pracy nie jest załadowany.|  
|Anulowane|Wystąpienie przepływu pracy zostało anulowane.|  
|Wstrzymane|Wystąpienie przepływu pracy jest zawieszone.|  
|Zakończone|Wystąpienie przepływu pracy jest zakończone.|  
|Anulowano|Anulowano to wystąpienie przepływu pracy.|  
  
## <a name="example"></a>Przykład  
 Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [Kontrola i śledzenie przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
