---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: d12656b77fa219080382603fd04a542d2fa9064a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399087"
---
# \<workflowRuntime>
Określa ustawienia dla wystąpienia programu <xref:System.Workflow.Runtime.WorkflowRuntime> do hostowania usług Windows Communication Foundation opartych na przepływie pracy (WCF).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**  
  
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
|cachedInstanceExpiration|Opcjonalna <xref:System.TimeSpan> wartość, która określa maksymalny czas trwania wystąpienia przepływu pracy w pamięci w stanie bezczynności, zanim zostanie wymuszone zwolnione lub przerwane. Jeśli element WorkflowRuntime ma `PersistenceService` unloadOnIdle, ten atrybut jest ignorowany.|  
|enablePerformanceCounters|Opcjonalna wartość logiczna określająca, czy liczniki wydajności są włączone. Liczniki wydajności dostarczają informacji na temat różnych statystyk związanych z przepływem pracy, ale powodują spadek wydajności, gdy uruchamiany jest aparat środowiska uruchomieniowego przepływu pracy i kiedy wystąpienia przepływu pracy są uruchomione. Wartość domyślna to `true`.|  
|name|Ciąg zawierający nazwę aparatu środowiska uruchomieniowego przepływu pracy. Nazwa jest używana w danych wyjściowych w celu odróżnienia tego środowiska uruchomieniowego od innych środowisk uruchomieniowych, które mogą być uruchomione w systemie, na przykład w licznikach wydajności.<br /><br /> Wartość domyślna to pusty ciąg.|  
|validateOnCreate|Opcjonalna wartość logiczna określająca, czy Walidacja definicji przepływu pracy nastąpi po otwarciu obiektu WorkflowServiceHost.  Gdy ten atrybut jest ustawiony na `true` , sprawdzanie poprawności przepływu pracy jest wykonywane za każdym razem, gdy `WorkflowServiceHost.Open` jest wywoływana. Jeśli zostaną znalezione błędy walidacji, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> zostanie zgłoszony błąd.<br /><br /> Gdy ta właściwość jest ustawiona na `false` , nie będzie wykonywane Walidacja definicji przepływu pracy.<br /><br /> Wartość domyślna tej właściwości to `true` .|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|commonParameters|Kolekcja typowych parametrów używanych przez usługi. Ta kolekcja zazwyczaj obejmuje parametry połączenia z bazą danych, które mogą być współużytkowane przez trwałe usługi.|  
|services|Kolekcja usług, które zostaną dodane do <xref:System.Workflow.Runtime.WorkflowRuntime> aparatu. Elementy są typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .  Usługi określone w kolekcji zostaną zainicjowane przez aparat środowiska uruchomieniowego przepływu pracy i dodawane do swoich usług, gdy <xref:System.Workflow.Runtime.WorkflowRuntime> zostanie wywołany odpowiedni Konstruktor. W związku z tym usługi określone w kolekcji muszą przestrzegać pewnych zasad dotyczących podpisów ich konstruktorów. Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat używania pliku konfiguracji do sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu Windows Workflow Foundation aplikacji hosta, zobacz [pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- [Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
