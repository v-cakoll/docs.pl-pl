---
title: Używanie powiązania niestandardowego z kanałem klienta odnajdywania
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 49983c3ab303d3839350af72b1aa4821c071fe99
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595040"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Używanie powiązania niestandardowego z kanałem klienta odnajdywania
W przypadku używania niestandardowego powiązania z <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> , należy zdefiniować, <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> które tworzy <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpienia.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Tworzenie DiscoveryEndpointProvider  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>Jest odpowiedzialny za tworzenie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpień na żądanie. Aby zdefiniować dostawcę punktu końcowego odnajdywania, należy utworzyć klasę z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> i zastąpić <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> metodę i zwrócić nowy punkt końcowy odnajdywania. Poniższy przykład pokazuje, jak utworzyć dostawcę punktu końcowego odnajdywania.  
  
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
  
 Po zdefiniowaniu dostawcy punktu końcowego odnajdywania można utworzyć niestandardowe powiązanie i dodać obiekt <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> , który odwołuje się do dostawcy punktu końcowego odnajdywania, jak pokazano w poniższym przykładzie.  
  
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
  
 Aby uzyskać więcej informacji o korzystaniu z kanału klienta odnajdywania, zobacz [Korzystanie z kanału klienta odnajdywania](using-the-discovery-client-channel.md).
  
## <a name="see-also"></a>Zobacz też

- [Omówienie odnajdywania WCF](wcf-discovery-overview.md)
- [Używanie kanału klienta odnajdywania](using-the-discovery-client-channel.md)
