---
title: '&lt;serviceThrottling&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6ba0f3a442e3598322f223be63b64a811c8f785a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicethrottlinggt"></a>&lt;serviceThrottling&gt;
Określa mechanizm ograniczania przepustowości usługi Windows Communication Foundation (WCF).  
  
 \<System. ServiceModel >  
\<zachowania >  
\<serviceBehaviors >  
\<zachowanie >  
\<serviceThrottling >  
  
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
|MaxConcurrentInstances|Dodatnia liczba całkowita, która ogranicza liczbę <xref:System.ServiceModel.InstanceContext> obiektów, które są wykonywane jednocześnie przez <xref:System.ServiceModel.ServiceHost>. Żądania utworzenia dodatkowe wystąpienia są umieszczane w kolejce i ukończyć po udostępnieniu miejsca poniżej limitu. Wartość domyślna to suma maxConcurrentSessions i MaxConcurrentCalls|  
|MaxConcurrentSessions|Dodatnia liczba całkowita, która ogranicza liczbę sesji <xref:System.ServiceModel.ServiceHost> akceptowanych przez obiekt.<br /><br /> Usługa będzie akceptować połączenia poza limitem, ale są aktywne tylko kanały poniżej limitu (wiadomości są odczytywane z kanału). Ustawienie tej wartości na 0 jest równoznaczne z ustawieniem jego wartości Int32.MaxValue. Wartość domyślna to 100 * Liczba procesorów.|  
  
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
 [Używanie elementu ServiceThrottlingBehavior do kontrolowania wydajności usługi WCF](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
