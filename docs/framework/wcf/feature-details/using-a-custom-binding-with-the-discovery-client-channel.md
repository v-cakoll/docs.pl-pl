---
title: Używanie powiązania niestandardowego z kanałem klienta odnajdywania
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 6fe9370bb22ca424774fc8cb4566e0802bc06697
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918622"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="85c11-102">Używanie powiązania niestandardowego z kanałem klienta odnajdywania</span><span class="sxs-lookup"><span data-stu-id="85c11-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="85c11-103">Korzystając z niestandardowego powiązania za pomocą <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, należy zdefiniować <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> tworząca <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="85c11-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="85c11-104">Tworzenie DiscoveryEndpointProvider</span><span class="sxs-lookup"><span data-stu-id="85c11-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="85c11-105"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Jest odpowiedzialny za tworzenie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpień na żądanie.</span><span class="sxs-lookup"><span data-stu-id="85c11-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="85c11-106">Aby zdefiniować dostawcy punktu końcowego odnajdywania, należy wyprowadzić klasę z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> i zastąpić <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> metody i wróć do nowego punktu końcowego wykrywania.</span><span class="sxs-lookup"><span data-stu-id="85c11-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="85c11-107">Poniższy przykład pokazuje, jak utworzyć dostawcy punktu końcowego odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="85c11-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="85c11-108">Po zdefiniowaniu dostawcy punktu końcowego odnajdywania, można utworzyć powiązania niestandardowego i dodać <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, które odwołują się do dostawcy punktu końcowego odnajdywania jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="85c11-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="85c11-109">Aby uzyskać więcej informacji o korzystaniu z kanałem klienta odnajdywania, zobacz [używanie kanału klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="85c11-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="85c11-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85c11-110">See also</span></span>

- [<span data-ttu-id="85c11-111">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="85c11-111">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="85c11-112">Używanie kanału klienta odnajdywania</span><span class="sxs-lookup"><span data-stu-id="85c11-112">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
