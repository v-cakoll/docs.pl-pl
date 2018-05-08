---
title: Używanie powiązania niestandardowego z kanałem klienta odnajdywania
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 4ef85b4c52c1f27b333413e2b6178452142d313f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Używanie powiązania niestandardowego z kanałem klienta odnajdywania
Podczas korzystania z niestandardowego powiązania <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, należy zdefiniować <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> tworzącą <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpień.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Tworzenie DiscoveryEndpointProvider  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Odpowiedzialną za tworzenie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpienia na żądanie. Aby zdefiniować dostawcy punktu końcowego odnajdywania, klasa wyprowadzona z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> i zastąpić <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> — metoda i przywracać nowy punkt końcowy odnajdowania. Poniższy przykład przedstawia sposób tworzenia dostawcy punktu końcowego odnajdywania.  
  
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
  
 Po zdefiniowaniu dostawcy punktu końcowego odnajdywania można utworzyć niestandardowego powiązania i dodać <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, który odwołuje się do odnajdywania dostawcy punktu końcowego jak pokazano w poniższym przykładzie.  
  
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
  
 Aby uzyskać więcej informacji o korzystaniu z kanałem klienta odnajdywania, zobacz [przy użyciu kanału klienta odnajdowania](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md). Na przykład kompletny kod, zobacz [przykład elementu wiązania odnajdywania](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Używanie kanału klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [Przykład elementu powiązania odnajdywania](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)
