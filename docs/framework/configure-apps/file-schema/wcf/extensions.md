---
title: <extensions>
ms.date: 03/30/2017
ms.assetid: bcfe5c44-04ef-4a20-96a5-90bfadf39623
ms.openlocfilehash: bb0df4535560a509d6e3511815196c126a95d0c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700777"
---
# <a name="extensions"></a><span data-ttu-id="bccb7-101">\<extensions></span><span class="sxs-lookup"><span data-stu-id="bccb7-101">\<extensions></span></span>
<span data-ttu-id="bccb7-102">Ten element konfiguracji zawiera kolekcję elementów XML, które zawierają niestandardowych metadanych do opublikowania oraz standardowe wykrywalny metadanych (EPR, ContractTypeName, BindingName, zakresu i identyfikatorze ListenURI).</span><span class="sxs-lookup"><span data-stu-id="bccb7-102">This configuration element contains a collection of XML elements that contain custom metadata to be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span> <span data-ttu-id="bccb7-103">Oto przykład użycia tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bccb7-103">The following is an example of using this configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bccb7-104">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bccb7-104">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
