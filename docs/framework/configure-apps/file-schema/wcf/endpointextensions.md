---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: 12ac8d9a7b0ed584fb1308e56d197a03b1c53e51
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769349"
---
# <a name="endpointextensions"></a><span data-ttu-id="62894-101">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="62894-101">\<endpointExtensions></span></span>
<span data-ttu-id="62894-102">Ta sekcja rejestruje nowy standardowy punkt końcowy w sekcji rozszerzenia na maszynie lub pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="62894-102">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="62894-103">Standardowy punkt końcowy może dodać do tej kolekcji, używając `add` — słowo kluczowe i ustawienie `type` atrybut elementu do typu punktu końcowego, jak również `name` atrybutu na nazwę standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="62894-103">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="62894-104">W poniższym przykładzie użyto `add` elementu, jak również `name` atrybutu, aby dodać standardowy punkt końcowy do `<endpointExtensions>` sekcję pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="62894-104">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="62894-105">Po zarejestrowaniu się standardowy punkt końcowy, można użyć jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="62894-105">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="62894-106">W [ \<punktu końcowego >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu `kind` atrybut określa typ Standardowy punkt końcowy, który został zarejestrowany w `<endpointExtensions>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="62894-106">In the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="62894-107">`endpointConfiguration` Atrybut będzie taka sama jak `name` atrybutu elementu Konfiguracja standardowego punktu końcowego w `<standardEndpoints>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="62894-107">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
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
