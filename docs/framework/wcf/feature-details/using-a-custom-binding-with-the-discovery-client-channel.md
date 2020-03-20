---
title: Używanie powiązania niestandardowego z kanałem klienta odnajdywania
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 5f3f5fe24d1f19ce503b793d9aad870d882c7971
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184289"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Używanie powiązania niestandardowego z kanałem klienta odnajdywania
Podczas korzystania z niestandardowego powiązania <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> , <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> należy zdefiniować, który tworzy wystąpienia.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Tworzenie programu DiscoveryEndpointProvider  
 Jest <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> odpowiedzialny za <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> tworzenie wystąpień na żądanie. Aby zdefiniować dostawcę punktu końcowego <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> odnajdywania, należy wyprowadzić klasę z i zastąpić <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> metodę i zwrócić nowy punkt końcowy odnajdywania. W poniższym przykładzie pokazano, jak utworzyć dostawcę punktu końcowego odnajdywania.  
  
```csharp
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
// to the DiscoveryClientBindingElement. The Discovery ClientChannel
// uses this endpoint to send Probe message.  
public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
{  
   public override DiscoveryEndpoint GetDiscoveryEndpoint()  
   {  
      return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
   }  
}  
```  
  
 Po zdefiniowaniu dostawcy punktu końcowego odnajdywania <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>można utworzyć niestandardowe powiązanie i dodać , który odwołuje się do dostawcy punktu końcowego odnajdywania, jak pokazano w poniższym przykładzie.  
  
```csharp
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 Aby uzyskać więcej informacji na temat korzystania z kanału klienta odnajdywania, zobacz [Korzystanie z kanału klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).
  
## <a name="see-also"></a>Zobacz też

- [Omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Używanie kanału klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
