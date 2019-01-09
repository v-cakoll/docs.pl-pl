---
title: '&lt;workflowRuntime&gt;'
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: ffc4bbeb44561cbe2d809b2fb2263068fef542d1
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150074"
---
# <a name="ltworkflowruntimegt"></a>&lt;workflowRuntime&gt;
Określa ustawienia dla wystąpienia <xref:System.Workflow.Runtime.WorkflowRuntime> do hostingu opartego o przepływ pracy usług Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<workflowRuntime>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
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
|cachedInstanceExpiration|Opcjonalny <xref:System.TimeSpan> wartość, która określa maksymalny czas pobytu wystąpienia przepływu pracy w pamięci w stanie bezczynności, zanim go jest wyładowania lub przerwania. Jeśli ma workflowruntime `PersistenceService` który wykonuje unloadOnIdle, ten atrybut zostanie zignorowany.|  
|enablePerformanceCounters|Opcjonalna wartość logiczna określająca, czy liczniki wydajności są włączone. Liczniki wydajności zawierają informacje na temat różne statystyki związane z przepływu pracy, ale powodują spadek wydajności podczas uruchamiania aparatu wykonawczego przepływów pracy i wystąpienia przepływu pracy są uruchomione. Wartość domyślna to `true`.|  
|nazwa|Ciąg zawierający nazwę aparatu wykonawczego przepływów pracy. Nazwa jest używana w danych wyjściowych, aby odróżnić to środowisko wykonawcze od innych środowisk wykonawczych, które mogą być uruchomione w systemie, na przykład liczniki wydajności.<br /><br /> Wartość domyślna to ciąg pusty.|  
|validateOnCreate|Opcjonalna wartość logiczna określająca, czy Walidacja definicji przepływu pracy nastąpi przy otwarciu WorkflowServiceHost.  Jeśli ten atrybut jest równa `true`, walidacji przepływu pracy jest wykonywana w każdym `WorkflowServiceHost.Open` jest wywoływana. Jeśli zostaną znalezione błędy sprawdzania poprawności, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> , zostanie zgłoszony błąd.<br /><br /> Jeśli ta właściwość jest równa `false`, nastąpi nie nastąpi sprawdzanie poprawności definicji przepływu pracy.<br /><br /> Wartość domyślna tej właściwości to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|commonParameters|Kolekcja wspólnych parametrów używane przez usługi. Ta kolekcja zwykle będzie zawierać parametry połączenia bazy danych, które mogą być współużytkowane przez trwałych usług.|  
|usługi|Kolekcja usług, które zostaną dodane do <xref:System.Workflow.Runtime.WorkflowRuntime> aparatu. Elementy są typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Usługi określone w kolekcji zostanie zainicjowany przez aparatu wykonawczego przepływów pracy i dodane do swoich usług przy odpowiednim <xref:System.Workflow.Runtime.WorkflowRuntime> wywoływany jest Konstruktor. W związku z tym usług określonych w kolekcji, należy wykonać niektóre zasady sposobu podpisy ich konstruktory. Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat korzystania z pliku konfiguracji w celu sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiekt aplikacji hosta Windows Workflow Foundation, zobacz [pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
## <a name="example"></a>Przykład  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
