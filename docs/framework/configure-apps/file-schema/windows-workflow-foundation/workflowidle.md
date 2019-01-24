---
title: '&lt;workflowIdle&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 9d9eb45090367fb2cc18fc357c219e74d63fb667
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628104"
---
# <a name="ltworkflowidlegt"></a>&lt;workflowIdle&gt;
Zachowanie usługi sterująca po zwolnione wystąpienia bezczynności przepływu pracy i utrwalone.  
  
\<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<workflowIdle>  
  
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
|timeToPersist|Wartość przedziału czasu, który określa czas trwania między czas przepływu pracy staje się bezczynności i jest trwały. Wartość domyślna to TimeSpan.MaxValue.<br /><br /> Czas trwania rozpoczyna upłynąć, gdy wystąpienie przepływu pracy staje się nieaktywna. Ten atrybut jest przydatna, jeśli chcesz utrwalić wystąpienia przepływu pracy agresywniej jednocześnie zachowując wystąpienie w pamięci tak długo, jak to możliwe. Ten atrybut jest tylko wtedy, gdy jej wartość jest mniejsza niż **timeToUnload** atrybutu. Jeśli jest większa, jest ignorowana. Jeśli ten atrybut upłynie przed wartość określoną przez **timeToUnload** atrybutu, trwałości przed należy ukończyć przepływ pracy zostanie zwolniony. Oznacza to, że operacja zwolnienia może być opóźniony, dopóki nie jest trwały przepływu pracy. Warstwa trwałości jest odpowiedzialny za obsługę dowolnego powtórzeń przejściowy błędów i tylko na błędy bez nieodwracalny zgłasza wyjątek wyjątków. Dlatego wyjątki zgłaszane w trwałości są traktowane jako krytyczny, a wystąpienie przepływu pracy zostało przerwane.|  
|timeToUnload|Zakres czasu wartość, która określa czas trwania między czas przepływu pracy staje się bezczynności i jest zwalniana. Wartość domyślna to 1 minutę.<br /><br /> Zwalnianie przepływu pracy oznacza również utrwalone. Jeśli ten atrybut jest równa zero wystąpienie przepływu pracy jest trwały i zwolnione natychmiast po przepływ pracy staje się nieaktywna. Ustawienie tego atrybutu na TimeSpan.MaxValue skutecznie wyłącza operacja zwolnienia. Wystąpienia przepływu pracy bezczynności nigdy nie są usuwane.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie > z \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Określa zachowanie elementu.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
