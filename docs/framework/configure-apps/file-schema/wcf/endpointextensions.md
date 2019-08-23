---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: fe57cb84cfa70b1f6b92abf1dbac89ddad9d4dc8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925711"
---
# <a name="endpointextensions"></a>\<endpointExtensions >
Ta sekcja rejestruje nowy standardowy punkt końcowy w sekcji rozszerzeń w pliku konfiguracyjnym komputera lub aplikacji. Można dodać standardowy punkt końcowy do tej kolekcji przy użyciu `add` słowa kluczowego i `type` ustawić atrybut elementu na typ punktu końcowego `name` , a także atrybut na nazwę standardowego punktu końcowego.  
  
 W poniższym przykładzie użyto `add` elementu, a także `name` atrybutu, aby dodać standardowy punkt końcowy do `<endpointExtensions>` sekcji pliku konfiguracji.  
  
```xml  
<system.serviceModel>
  <extensions>
    <endpointExtensions>
      <add name="udpDiscoveryEndpoint"
           type="System.Discovery.UdpEndpointCollectionElement, System.Discovery.dll, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Po zarejestrowaniu standardowego punktu końcowego można go użyć, jak pokazano w poniższym przykładzie. W elemencie`kind` `<endpointExtensions>` [ >punktukońcowegoatrybutokreślastandardowytyppunktukońcowego,któryzostał\<](endpoint-element.md) zarejestrowany w sekcji. Ten `endpointConfiguration` atrybut będzie taki sam jak `name` atrybut elementu konfiguracji standardowego punktu końcowego w `<standardEndpoints>` sekcji.  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Service1">
      <endpoint kind="udpDiscoveryEndpoint"
                endpointConfiguration="udpConfig" />
    </service>
  </services>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="udpConfig"
                        multicastAddress="soap.udp://239.255.255.250:3703"
                        ... />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
