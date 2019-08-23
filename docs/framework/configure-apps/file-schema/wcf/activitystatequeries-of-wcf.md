---
title: <activityStateQueries>programu WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 415cd4a75ecab725f91bcd298f8a7966ea6079d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920298"
---
# <a name="activitystatequeries-of-wcf"></a>\<activityStateQueries > WCF

Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy. Na przykład możesz chcieć śledzić każde działanie "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy. To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania. Stany do subskrybowania są wyszczególnione w ActivityStates.

Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).

\<system.serviceModel>  
\<Śledzenie >  
\<> profilów  
\<trackingProfile>  
\<przepływ pracy >  
\<activityStateQueries>  

## <a name="syntax"></a>Składnia  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
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
|[\<activityStateQuery>](activitystatequery-of-wcf.md)|Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.  To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<przepływ pracy >](../windows-workflow-foundation/workflow.md)|Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.|

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [Kontrola i śledzenie przepływu pracy](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Profile śledzenia](../../../windows-workflow-foundation/tracking-profiles.md)
