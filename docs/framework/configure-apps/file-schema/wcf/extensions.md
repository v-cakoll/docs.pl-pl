---
title: '&lt;rozszerzenia&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcfe5c44-04ef-4a20-96a5-90bfadf39623
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5bdfd491cdc39accb396664500eef7c66142ef9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltextensionsgt"></a><span data-ttu-id="801e9-102">&lt;rozszerzenia&gt;</span><span class="sxs-lookup"><span data-stu-id="801e9-102">&lt;extensions&gt;</span></span>
<span data-ttu-id="801e9-103">Ten element konfiguracji zawiera kolekcję elementów XML, które zawierają niestandardowych metadanych do opublikowania oraz standardowe metadane wykrywalny (EPR, ContractTypeName, BindingName, zakresu i ListenUri o wartości).</span><span class="sxs-lookup"><span data-stu-id="801e9-103">This configuration element contains a collection of XML elements that contain custom metadata to be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span> <span data-ttu-id="801e9-104">Oto przykład za pomocą tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="801e9-104">The following is an example of using this configuration element.</span></span>  
  
```xml  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
     <endpoint binding="basicHttpBinding"  
              address="calculator"  
              contract="ICalculatorService"  
              behaviorConfiguration="calculatorEndpointBehavior" />  
  </service>  
</services>  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery />  
    </behavior>  
  </serviceBehaviors>  
  <endpointBehaviors>  
    <behavior name="calculatorEndpointBehavior">  
      <endpointDiscovery enable="true">  
        <extensions>  
          <e:Publisher xmlns:e="http://example.org">  
            <e:Name>The Example Organization</e:Name>  
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>  
            <e:Contact>support@example.org</e:Contact>  
          </e:Publisher>  
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>  
        </extensions>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="801e9-105">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="801e9-105">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
