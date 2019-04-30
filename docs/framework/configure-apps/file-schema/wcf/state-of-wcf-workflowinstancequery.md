---
title: <state> w WCF — <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 1615c83ffe0735d9e55e822f2651da41d02b1610
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757966"
---
# <a name="state-of-wcf-workflowinstancequery"></a>\<Stan > w WCF — \<workflowInstanceQuery >
Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.  
  
 Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<Śledzenie >  
\<profiles>  
\<trackingProfile>  
\<przepływ pracy >  
\<workflowInstanceQueries>  
\<workflowInstanceQuery>  
\<Stany >  
\<state>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name" />
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.
  
### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Ciąg, który określa subskrybowanego stanu z wystąpienia śledzonych przepływu pracy podczas rekordem śledzenia.|  
  
### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|  
|-------------|-----------------|  
|[\<Stany >](states-of-wcf-workflowinstancequery.md)|Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.|  
  
## <a name="remarks"></a>Uwagi  

Zwracane rekordy są filtrowane według stanów w tej kolekcji.  
  
Stan możliwe wartości są opisane w poniższej tabeli:
  
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
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [Kontrola i śledzenie przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
