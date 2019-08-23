---
title: <cancelRequestedQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 0f04fc928358c96ca3112422f1a6ccd039269e47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926247"
---
# <a name="cancelrequestedqueries-of-wcf"></a>\<cancelRequestedQueries > WCF
Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne. Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.  
  
Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<Śledzenie >  
\<profiles> \<trackingProfile>  
\<przepływ pracy >  
\<cancelRequestedQueries>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty

Brak.
  
### <a name="child-elements"></a>Elementy podrzędne
  
|Element|Opis|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery-of-wcf.md)|Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<przepływ pracy >](../windows-workflow-foundation/workflow.md)|Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> właściwości.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [Kontrola i śledzenie przepływu pracy](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Profile śledzenia](../../../windows-workflow-foundation/tracking-profiles.md)
