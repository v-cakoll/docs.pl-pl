---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 7ac067e84f2a4d2724e3d8f2d0af9b220fd15538
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399644"
---
# \<serviceDiscovery>
Określa możliwość odnajdywania punktów końcowych usługi.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|Kolekcja punktów końcowych anonsów. Ta sekcja służy do określania punktów końcowych, które mają być używane do wysyłania komunikatów anonsu.|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|Kolekcja punktów końcowych odnajdywania. Użyj tej sekcji, aby określić punkty końcowe, w których mają być nasłuchiwani wiadomości odnajdowania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji udostępnia wszystkie punkty końcowe tej usługi. Można skonfigurować funkcje odnajdywania takich punktów końcowych przy użyciu [\<discoveryEndpoint>](discoveryendpoint.md) [\<announcementEndpoint>](announcementendpoint.md) elementów podrzędnych lub. Skorzystaj z [\<announcementEndpoint>](announcementendpoint.md) sekcji, aby skonfigurować Anonsy, określając konfigurację punktu końcowego, który ma być używany do wysyłania anonsów usługi (online/Hello i offline/bye). Użyj [\<discoveryEndpoint>](discoveryendpoint.md) sekcji, aby ręcznie określić punkt końcowy, w którym mają być nasłuchiwani wiadomości odnajdowania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konfiguracji określa, że CalculatorService ma być wykrywalny, i opcjonalnie określa punkt końcowy anonsu, który ma być używany.  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
