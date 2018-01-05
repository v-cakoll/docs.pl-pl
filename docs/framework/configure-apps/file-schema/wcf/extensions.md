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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13d79a52690f8262b08c8510e1f78b7efbf3adab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltextensionsgt"></a><span data-ttu-id="02068-102">&lt;rozszerzenia&gt;</span><span class="sxs-lookup"><span data-stu-id="02068-102">&lt;extensions&gt;</span></span>
<span data-ttu-id="02068-103">Ten element konfiguracji zawiera kolekcję elementów XML, które zawierają niestandardowych metadanych do opublikowania oraz standardowe metadane wykrywalny (EPR, ContractTypeName, BindingName, zakresu i ListenUri o wartości).</span><span class="sxs-lookup"><span data-stu-id="02068-103">This configuration element contains a collection of XML elements that contain custom metadata to be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span> <span data-ttu-id="02068-104">Oto przykład za pomocą tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="02068-104">The following is an example of using this configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="02068-105">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02068-105">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
