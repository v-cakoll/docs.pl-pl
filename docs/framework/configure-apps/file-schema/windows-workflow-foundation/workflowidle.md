---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: d9eb182ef9c35d2e4c6f5d434e6b200ae2e7ca26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151848"
---
# <a name="workflowidle"></a>\<> przepływu pracy
Zachowanie usługi sterująca po zwolnione wystąpienia bezczynności przepływu pracy i utrwalone.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<zachowania>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<usługiZachowady>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>zachowania**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>przepływu pracyIdle**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan"
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|timeToPersist|Wartość Timespan, która określa czas trwania między czasem przepływu pracy staje się bezczynny i jest utrwalony. Wartością domyślną jest TimeSpan.MaxValue.<br /><br /> Czas trwania rozpoczyna upłynąć, gdy wystąpienie przepływu pracy staje się nieaktywna. Ten atrybut jest przydatne, jeśli chcesz utrwalić wystąpienie przepływu pracy bardziej agresywnie, zachowując wystąpienie w pamięci tak długo, jak to możliwe. Ten atrybut jest prawidłowy tylko wtedy, gdy jego wartość jest mniejsza niż **timeToUnload** atrybut. Jeśli jest większa, jest ignorowana. Jeśli ten atrybut upłynie przed wartością określoną przez **timeToUnload** atrybut, trwałość musi zakończyć się przed wyładowania przepływu pracy. Oznacza to, że operacja zwalniania może być opóźniona, dopóki przepływ pracy nie zostanie utrwalony. Warstwa trwałości jest odpowiedzialny za obsługę dowolnego powtórzeń przejściowy błędów i tylko na błędy bez nieodwracalny zgłasza wyjątek wyjątków. Dlatego wyjątki zgłaszane w trwałości są traktowane jako krytyczny, a wystąpienie przepływu pracy zostało przerwane.|  
|timeToUnload|Zakres czasu wartość, która określa czas trwania między czas przepływu pracy staje się bezczynności i jest zwalniana. Wartość domyślna to 1 minutę.<br /><br /> Zwalnianie przepływu pracy oznacza, że jest również utrwalony. Jeśli ten atrybut jest ustawiony na zero, wystąpienie przepływu pracy jest utrwalone i zwalniane natychmiast po tym, jak przepływ pracy stanie się bezczynny. Ustawienie tego atrybutu na TimeSpan.MaxValue skutecznie wyłącza operację zwalniania. Wystąpienia przepływu pracy bezczynności nigdy nie są usuwane.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie> \<usługZachod>](behavior-of-servicebehaviors-of-workflow.md)|Określa zachowanie elementu.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
