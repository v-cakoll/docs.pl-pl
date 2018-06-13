---
title: '&lt;serviceThrottling&gt;'
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: b0f5197bf4e9017007f29f86048756b43e3b15fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750170"
---
# <a name="ltservicethrottlinggt"></a>&lt;serviceThrottling&gt;
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
|maxConcurrentCalls|Dodatnia liczba całkowita, która ogranicza liczbę wiadomości, które obecnie procesu na <xref:System.ServiceModel.ServiceHost>. Wywołania poza limitem są umieszczane w kolejce. Ustawienie tej wartości na 0 jest równoznaczne z ustawieniem jego wartości Int32.MaxValue. Wartość domyślna to 16 * liczba procesorów.|  
|maxConcurrentInstances|Dodatnia liczba całkowita, która ogranicza liczbę <xref:System.ServiceModel.InstanceContext> obiektów, które są wykonywane jednocześnie przez <xref:System.ServiceModel.ServiceHost>. Żądania utworzenia dodatkowe wystąpienia są umieszczane w kolejce i ukończyć po udostępnieniu miejsca poniżej limitu. Wartość domyślna to suma maxConcurrentSessions i MaxConcurrentCalls|  
|maxConcurrentSessions|Dodatnia liczba całkowita, która ogranicza liczbę sesji <xref:System.ServiceModel.ServiceHost> akceptowanych przez obiekt.<br /><br /> Usługa będzie akceptować połączenia poza limitem, ale są aktywne tylko kanały poniżej limitu (wiadomości są odczytywane z kanału). Ustawienie tej wartości na 0 jest równoznaczne z ustawieniem jego wartości Int32.MaxValue. Wartość domyślna to 100 * Liczba procesorów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Formanty ograniczania przepustowości umieść limity liczby równoczesnych wywołań, obiektów lub sesji, aby uniknąć nadmiernego zużycia zasobów.  
  
 Śledzenia są zapisywane za każdym razem, gdy wartości atrybutów. Pierwszy śledzenia są zapisywane jako ostrzeżenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie konfiguracja Określa, że usługa ogranicza maksymalną równoczesnych wywołań 2 i maksymalnej liczby równoczesnych wystąpień do 10. Aby uzyskać szczegółowy przykład uruchomionych w tym przykładzie, zobacz [ograniczania](../../../../../docs/framework/wcf/samples/throttling.md).  
  
```xml  
<behaviors>   
  <serviceBehaviors>   
    <behavior name="CalculatorServiceBehavior">   
      <serviceDebug includeExceptionDetailInFaults="False" />   
      <serviceMetadata httpGetEnabled="True"/>   
      <!-- Specify throttling behavior -->  
      <serviceThrottling maxConcurrentCalls="2"   
           maxConcurrentInstances="10"/>   
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>  
 [Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności programu WCF](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
