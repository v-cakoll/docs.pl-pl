---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: fe57cb84cfa70b1f6b92abf1dbac89ddad9d4dc8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "69925711"
---
# \<endpointExtensions>
<span data-ttu-id="0071d-101">Ta sekcja rejestruje nowy standardowy punkt końcowy w sekcji rozszerzeń w pliku konfiguracyjnym komputera lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0071d-101">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="0071d-102">Można dodać standardowy punkt końcowy do tej kolekcji przy użyciu `add` słowa kluczowego i ustawić `type` atrybut elementu na typ punktu końcowego, a także `name` atrybut na nazwę standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0071d-102">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="0071d-103">W poniższym przykładzie użyto `add` elementu, a także `name` atrybutu, aby dodać standardowy punkt końcowy do `<endpointExtensions>` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0071d-103">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="0071d-104">Po zarejestrowaniu standardowego punktu końcowego można go użyć, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0071d-104">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="0071d-105">W [\<endpoint>](endpoint-element.md) elemencie `kind` atrybut określa standardowy typ punktu końcowego, który został zarejestrowany w `<endpointExtensions>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="0071d-105">In the [\<endpoint>](endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="0071d-106">Ten `endpointConfiguration` atrybut będzie taki sam jak `name` atrybut elementu konfiguracji standardowego punktu końcowego w `<standardEndpoints>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="0071d-106">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
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
