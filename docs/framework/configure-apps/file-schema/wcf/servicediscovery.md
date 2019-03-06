---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 564410fdc4085cc3ed14c394006551cddb028910
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373754"
---
# <a name="servicediscovery"></a>\<serviceDiscovery>
Określa wykrywalność usługi punktów końcowych.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceDiscovery>  
  
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
|[\<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|Kolekcja punktów końcowych anonsu. Ta sekcja umożliwia określenie punktów końcowych, używany do wysyłania wiadomości anonsów.|  
|[\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|Kolekcja punktów końcowych odnajdywania. Ta sekcja umożliwia określenie punktów końcowych, na którym chcesz nasłuchiwać komunikatów odnajdywania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji sprawia, że wszystkie punkty końcowe usługi wykrywalne. Można dodatkowo skonfigurować funkcji odnajdywania tych punktów końcowych przy użyciu [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) lub [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) elementów podrzędnych. Użyj [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) sekcji, aby skonfigurować anonsów, określając konfiguracji punktu końcowego na potrzeby wysyłania zawiadomienia dotyczące usługi (online/Hello i offline/Bye). Użyj [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) sekcji, aby ręcznie określić punkt końcowy do nasłuchiwania wiadomości odnajdywania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie konfiguracja Określa, że CalculatorService być wykrywalny i opcjonalnie określa punkt końcowy anonsu do użycia.  
  
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
