---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ad87a5876381a7224341babdb076c85edcd1dd87
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399564"
---
# \<serviceThrottling>
Określa mechanizm ograniczania przepustowości usługi Windows Communication Foundation (WCF).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**  
  
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
|maxConcurrentCalls|Dodatnia liczba całkowita, która ogranicza liczbę komunikatów przetwarzanych obecnie w ramach <xref:System.ServiceModel.ServiceHost> . Wywołania przekraczające limit są umieszczane w kolejce. Ustawienie tej wartości na 0 jest równoznaczne z ustawieniem wartość Int32. MaxValue. Wartość domyślna to 16 * liczba procesorów.|  
|maxConcurrentInstances|Dodatnia liczba całkowita, która ogranicza liczbę <xref:System.ServiceModel.InstanceContext> obiektów, które są wykonywane jednocześnie w czasie <xref:System.ServiceModel.ServiceHost> . Żądania utworzenia dodatkowych wystąpień są umieszczane w kolejce i uzupełniane, gdy zostanie udostępnione miejsce poniżej limitu. Wartość domyślna to suma wartości maxConcurrentSessions i MaxConcurrentCalls|  
|maxConcurrentSessions|Dodatnia liczba całkowita, która ogranicza liczbę sesji <xref:System.ServiceModel.ServiceHost> akceptowanych przez obiekt.<br /><br /> Usługa będzie akceptować połączenia o przekroczeniu limitu, ale tylko kanały poniżej limitu są aktywne (komunikaty są odczytywane z kanału). Ustawienie tej wartości na 0 jest równoznaczne z ustawieniem wartość Int32. MaxValue. Wartość domyślna to 100 * liczba procesorów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Kontrolki ograniczania nakładają limity liczby współbieżnych wywołań, wystąpień lub sesji, aby zapobiec nadmiernemu zużyciu zasobów.  
  
 Ślad jest zapisywana za każdym razem, gdy wartość atrybutu zostanie osiągnięta. Pierwszy ślad jest zapisywana jako ostrzeżenie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konfiguracji określa, że usługa ogranicza maksymalną liczbę współbieżnych wywołań do 2, a maksymalna liczba równoczesnych wystąpień do 10. Aby zapoznać się z szczegółowym przykładem uruchamiania tego przykładu, zobacz [ograniczanie przepustowości](../../../wcf/samples/throttling.md).  
  
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
- [Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
