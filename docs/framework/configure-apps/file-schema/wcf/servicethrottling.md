---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 995ff9979096757225c9241e977f86f755955945
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758109"
---
# <a name="servicethrottling"></a>\<serviceThrottling>
Określa mechanizm ograniczania przepustowości usługi Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceThrottling>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|maxConcurrentCalls|Dodatnia liczba całkowita, która ogranicza liczbę wiadomości, które aktualnie przetworzyć w <xref:System.ServiceModel.ServiceHost>. Wywołania poza limitem zostaną umieszczone w kolejce. Ustawienie tej wartości na 0 jest równoważna z ustawieniem dla niego wartości Int32.MaxValue. Wartość domyślna to 16 * liczba procesorów.|  
|maxConcurrentInstances|Dodatnia liczba całkowita, która ogranicza liczbę <xref:System.ServiceModel.InstanceContext> obiekty, które są wykonywane w tym samym czasie między <xref:System.ServiceModel.ServiceHost>. Żądania utworzenia dodatkowych wystąpień są umieszczane w kolejce i ukończone, gdy miejsce poniżej limitu staje się dostępna. Wartość domyślna to suma maxConcurrentSessions i MaxConcurrentCalls|  
|maxConcurrentSessions|Dodatnia liczba całkowita, która ogranicza liczbę sesji <xref:System.ServiceModel.ServiceHost> akceptowanych przez obiekt.<br /><br /> Usługa będzie akceptować połączeń poza limitem, ale tylko kanały poniżej limitu są aktywne (komunikaty są odczytywane z kanału). Ustawienie tej wartości na 0 jest równoważna z ustawieniem dla niego wartości Int32.MaxValue. Wartość domyślna to 100 * Liczba procesorów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Formanty ograniczania przepływności ogranicza liczbę równoczesnych wywołań, wystąpienia lub sesji, aby uniknąć nadmiernego zużycia zasobów.  
  
 Śledzenia są zapisywane, za każdym razem, gdy zostanie osiągnięty wartości atrybutów. Pierwszy śledzenia są zapisywane jako ostrzeżenie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie konfiguracja Określa, że usługa ogranicza maksymalny współbieżnych wywołań 2 i maksymalnej liczby równoczesnych wystąpień do 10. Aby uzyskać szczegółowy przykład uruchomieniem tego przykładu, zobacz [ograniczania](../../../../../docs/framework/wcf/samples/throttling.md).  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
