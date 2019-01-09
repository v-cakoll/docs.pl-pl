---
title: '&lt;endpointExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: 3883a23c679abc83d7cfe9011b7cdb7e4154adfe
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146449"
---
# <a name="ltendpointextensionsgt"></a>&lt;endpointExtensions&gt;
Ta sekcja rejestruje nowy standardowy punkt końcowy w sekcji rozszerzenia na maszynie lub pliku konfiguracji aplikacji. Standardowy punkt końcowy może dodać do tej kolekcji, używając `add` — słowo kluczowe i ustawienie `type` atrybut elementu do typu punktu końcowego, jak również `name` atrybutu na nazwę standardowego punktu końcowego.  
  
 W poniższym przykładzie użyto `add` elementu, jak również `name` atrybutu, aby dodać standardowy punkt końcowy do `<endpointExtensions>` sekcję pliku konfiguracji.  
  
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
  
 Po zarejestrowaniu się standardowy punkt końcowy, można użyć jak pokazano w poniższym przykładzie. W [ \<punktu końcowego >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu `kind` atrybut określa typ Standardowy punkt końcowy, który został zarejestrowany w `<endpointExtensions>` sekcji. `endpointConfiguration` Atrybut będzie taka sama jak `name` atrybutu elementu Konfiguracja standardowego punktu końcowego w `<standardEndpoints>` sekcji.  
  
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
  
