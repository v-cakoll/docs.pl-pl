---
title: '&lt;workflowIdle&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 65bcc1ccd357fb7f331665aefbd975b11a2378cd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowidlegt"></a>&lt;workflowIdle&gt;
Zachowanie usługi sterująca po zwolnione wystąpienia bezczynności przepływu pracy i utrwalone.  
  
\<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<workflowIdle >  
  
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
|timeToPersist|Wartość Timespan określający okres czasu, między czasem przepływu pracy, staje się bezczynności i jest trwały. Wartość domyślna to wartość TimeSpan.MaxValue.<br /><br /> Czas trwania rozpoczyna upłynąć, gdy wystąpienie przepływu pracy staje się nieaktywna. Ten atrybut jest przydatne, jeśli chcesz bardziej agresywnie utrwalenie wystąpienia przepływu pracy, jednocześnie zachowując wystąpienia w pamięci tak długo, jak to możliwe. Ten atrybut jest tylko wtedy, gdy jego wartość jest mniejsza niż **timeToUnload** atrybutu. Jeśli jest większa, jest ignorowana. Jeśli ten atrybut, który musi upłynąć przed wartość określoną przez **timeToUnload** atrybutu trwałości należy wykonać przed przepływ pracy zostanie zwolniony. Oznacza to, że operacja zwolnienia mogą być opóźnione aż do przepływu pracy jest trwały. Warstwa trwałości jest odpowiedzialny za obsługę dowolnego powtórzeń przejściowy błędów i tylko na błędy bez nieodwracalny zgłasza wyjątek wyjątków. Dlatego wyjątki zgłaszane w trwałości są traktowane jako krytyczny, a wystąpienie przepływu pracy zostało przerwane.|  
|timeToUnload|Zakres czasu wartość, która określa czas trwania między czas przepływu pracy staje się bezczynności i jest zwalniana. Wartość domyślna to 1 minutę.<br /><br /> Zwalnianie przepływu pracy oznacza to również utrwalone. Ten atrybut jest ustawiony na zero, wystąpienie przepływu pracy jest utrwalona i zwalnianie natychmiast po przepływu pracy, staje się bezczynności. Ustawienie tego atrybutu na wartość TimeSpan.MaxValue skutecznie wyłącza operacja zwolnienia. Wystąpienia przepływu pracy bezczynności nigdy nie są usuwane.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie > z \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Określa zachowanie elementu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
