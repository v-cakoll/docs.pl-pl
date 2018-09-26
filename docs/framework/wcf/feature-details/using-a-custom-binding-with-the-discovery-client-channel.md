---
title: Używanie powiązania niestandardowego z kanałem klienta odnajdywania
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 7473262ec52adfd917b8ec5cd7ec1f4935a3646d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195228"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Używanie powiązania niestandardowego z kanałem klienta odnajdywania
Korzystając z niestandardowego powiązania za pomocą <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, należy zdefiniować <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> tworząca <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpień.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Tworzenie DiscoveryEndpointProvider  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Jest odpowiedzialny za tworzenie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpień na żądanie. Aby zdefiniować dostawcy punktu końcowego odnajdywania, należy wyprowadzić klasę z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> i zastąpić <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> metody i wróć do nowego punktu końcowego wykrywania. Poniższy przykład pokazuje, jak utworzyć dostawcy punktu końcowego odnajdywania.  
  
```  
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
  
 Po zdefiniowaniu dostawcy punktu końcowego odnajdywania, można utworzyć powiązania niestandardowego i dodać <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, które odwołują się do dostawcy punktu końcowego odnajdywania jak pokazano w poniższym przykładzie.  
  
```  
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 Aby uzyskać więcej informacji o korzystaniu z kanałem klienta odnajdywania, zobacz [używanie kanału klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md). 
  
## <a name="see-also"></a>Zobacz też  

- [Omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
- [Używanie kanału klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  