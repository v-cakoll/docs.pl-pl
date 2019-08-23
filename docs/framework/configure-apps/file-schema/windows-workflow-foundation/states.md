---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: fd0b57d7d08cf77ba7792e079b7abd2ff8f2839e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947407"
---
# <a name="states"></a>\<Stany >
Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.  
  
 Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<Śledzenie >  
\<trackingProfile>  
\<przepływ pracy >  
\<workflowInstanceQueries>  
\<workflowInstanceQuery>  
\<Stany >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> stanu](states.md)|Stan subskrybowanego z wystąpienia elementu śledzonych przepływu pracy podczas rekordem śledzenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|Zapytanie, które śledzi zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.|  
  
## <a name="remarks"></a>Uwagi  
 Zwracane rekordy są filtrowane według stanów w tej kolekcji.  
  
 Stan możliwe wartości są opisane w poniższej tabeli.  
  
|Stan|Opis|  
|-----------|-----------------|  
|Zostało przerwane|Wystąpienie przepływu pracy zostało przerwane.|  
|Zakończone|Wystąpienie przepływu pracy zostało zakończone.|  
|Usunięte|Wystąpienie przepływu pracy, został usunięty.|  
|Bezczynności (%)|Wystąpienie przepływu pracy jest bezczynny.|  
|Trwały|Wystąpienie przepływu pracy jest trwały.|  
|Wznowione|Wystąpienie przepływu pracy zostanie wznowione.|  
|Rozpoczęto|Wystąpienie przepływu pracy zostało rozpoczęte.|  
|UnhandledException|Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.|  
|Zwolniono|Wystąpienie przepływu pracy nie jest załadowany.|  
|Anulowane|Wystąpienie przepływu pracy zostało anulowane.|  
|Suspended|Wystąpienie przepływu pracy jest zawieszone.|  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [Kontrola i śledzenie przepływu pracy](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Profile śledzenia](../../../windows-workflow-foundation/tracking-profiles.md)
