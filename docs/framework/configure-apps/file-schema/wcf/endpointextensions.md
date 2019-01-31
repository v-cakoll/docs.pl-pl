---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: 746f98b54285f95bb63e15136508909327c0d140
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264612"
---
# <a name="endpointextensions"></a>\<endpointExtensions>
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
  
