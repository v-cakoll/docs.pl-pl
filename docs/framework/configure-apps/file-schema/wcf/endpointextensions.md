---
title: '&lt;endpointExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3c0d9dd167dbef4a641566e3d89abcdaf7c0302a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltendpointextensionsgt"></a><span data-ttu-id="2dadd-102">&lt;endpointExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="2dadd-102">&lt;endpointExtensions&gt;</span></span>
<span data-ttu-id="2dadd-103">Ta sekcja rejestruje nowy standardowy punkt końcowy w sekcji rozszerzenia na maszynie lub pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2dadd-103">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="2dadd-104">Standardowy punkt końcowy można dodać do tej kolekcji przy użyciu `add` — słowo kluczowe i ustawienie `type` atrybut element, aby typ punktu końcowego, jak również `name` atrybutu nazwę standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="2dadd-104">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="2dadd-105">W poniższym przykładzie użyto `add` elementu, jak również `name` atrybutu można dodać standardowy punkt końcowy do `<endpointExtensions>` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2dadd-105">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="2dadd-106">Po zarejestrowaniu standardowy punkt końcowy, można użyć jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2dadd-106">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="2dadd-107">W [ \<punktu końcowego >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu `kind` atrybut określa typ Standardowy punkt końcowy, który został zarejestrowany w `<endpointExtensions>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="2dadd-107">In the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="2dadd-108">`endpointConfiguration` Atrybut będzie taka sama jak `name` atrybut elementu Konfiguracja standardowego punktu końcowego w `<standardEndpoints>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="2dadd-108">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
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
        <standardEndpoint  
                  name="udpConfig"  
                  multicastAddress="soap.udp://239.255.255.250:3703"  
                  ... />  
      </udpDiscoveryEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```
