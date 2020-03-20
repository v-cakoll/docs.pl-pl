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
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="596af-102">Używanie powiązania niestandardowego z kanałem klienta odnajdywania</span><span class="sxs-lookup"><span data-stu-id="596af-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="596af-103">Podczas korzystania z niestandardowego powiązania <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> , <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> należy zdefiniować, który tworzy wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="596af-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="596af-104">Tworzenie programu DiscoveryEndpointProvider</span><span class="sxs-lookup"><span data-stu-id="596af-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="596af-105">Jest <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> odpowiedzialny za <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> tworzenie wystąpień na żądanie.</span><span class="sxs-lookup"><span data-stu-id="596af-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="596af-106">Aby zdefiniować dostawcę punktu końcowego <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> odnajdywania, należy wyprowadzić klasę z i zastąpić <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> metodę i zwrócić nowy punkt końcowy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="596af-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="596af-107">W poniższym przykładzie pokazano, jak utworzyć dostawcę punktu końcowego odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="596af-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="596af-108">Po zdefiniowaniu dostawcy punktu końcowego odnajdywania <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>można utworzyć niestandardowe powiązanie i dodać , który odwołuje się do dostawcy punktu końcowego odnajdywania, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="596af-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="596af-109">Aby uzyskać więcej informacji na temat korzystania z kanału klienta odnajdywania, zobacz [Korzystanie z kanału klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="596af-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="596af-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="596af-110">See also</span></span>

- [<span data-ttu-id="596af-111">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="596af-111">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="596af-112">Używanie kanału klienta odnajdywania</span><span class="sxs-lookup"><span data-stu-id="596af-112">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
