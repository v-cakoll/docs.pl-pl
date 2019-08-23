---
title: <add> dla <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 38dec132626b97accacea1b7007d914edcab0abc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926657"
---
# <a name="add-of-services"></a>\<Dodawanie > \<usług >
Określa ustawienia dla wystąpienia programu <xref:System.Workflow.Runtime.WorkflowRuntime> do hostowania usług Windows Communication Foundation opartych na przepływie pracy (WCF). Ten element jest typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
\<> usług  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|— typ|Ciąg określający nazwę typu kwalifikowanego zestawu usługi do zainicjowania. Określona usługa musi być zgodna z określonymi regułami dotyczącymi podpisów ich konstruktorów. Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> usług](services-of-workflowruntime.md)|Kolekcja usług, które zostaną dodane do <xref:System.Workflow.Runtime.WorkflowRuntime> aparatu. Elementy są typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Usługi określone w kolekcji zostaną zainicjowane przez aparat środowiska uruchomieniowego przepływu pracy i dodawane do swoich usług, gdy zostanie wywołany odpowiedni <xref:System.Workflow.Runtime.WorkflowRuntime> Konstruktor. W związku z tym usługi określone w kolekcji muszą przestrzegać pewnych zasad dotyczących podpisów ich konstruktorów. Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
## <a name="remarks"></a>Uwagi  
 Usługa określona w tym elemencie zostanie zainicjowana przez aparat środowiska uruchomieniowego przepływu pracy i dodana do jej usług, <xref:System.Workflow.Runtime.WorkflowRuntime> gdy zostanie wywołany odpowiedni Konstruktor. W związku z tym określona usługa musi być zgodna z określonymi regułami dotyczącymi podpisów ich konstruktorów. Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  
  
## <a name="example"></a>Przykład  
  
```xml  
<serviceBehaviors>
  <behavior name="ServiceBehavior">
    <workflowRuntime name="WorkflowServiceHostRuntime"
                     validateOnCreate="true"
                     enablePerformanceCounters="true">
      <services>
        <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common" />
      </services>
    </workflowRuntime>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- [Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
