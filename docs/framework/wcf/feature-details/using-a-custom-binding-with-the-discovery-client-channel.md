---
title: Używanie powiązania niestandardowego z kanałem klienta odnajdywania
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 406a53dece6370fbb56daa5a30b52621ca1dcd6d
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975979"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="c2e46-102">Używanie powiązania niestandardowego z kanałem klienta odnajdywania</span><span class="sxs-lookup"><span data-stu-id="c2e46-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="c2e46-103">W przypadku używania niestandardowego powiązania z <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>należy zdefiniować <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>, które tworzą wystąpienia <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="c2e46-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="c2e46-104">Tworzenie DiscoveryEndpointProvider</span><span class="sxs-lookup"><span data-stu-id="c2e46-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="c2e46-105"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> jest odpowiedzialny za tworzenie wystąpień <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> na żądanie.</span><span class="sxs-lookup"><span data-stu-id="c2e46-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="c2e46-106">Aby zdefiniować dostawcę punktu końcowego odnajdywania, należy utworzyć klasę z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> i zastąpić metodę <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> i zwrócić nowy punkt końcowy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="c2e46-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="c2e46-107">Poniższy przykład pokazuje, jak utworzyć dostawcę punktu końcowego odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="c2e46-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="c2e46-108">Po zdefiniowaniu dostawcy punktu końcowego odnajdywania można utworzyć niestandardowe powiązanie i dodać <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, który odwołuje się do dostawcy punktu końcowego odnajdywania, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c2e46-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="c2e46-109">Aby uzyskać więcej informacji o korzystaniu z kanału klienta odnajdywania, zobacz [Korzystanie z kanału klienta odnajdywania](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="c2e46-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="c2e46-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2e46-110">See also</span></span>

- [<span data-ttu-id="c2e46-111">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="c2e46-111">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="c2e46-112">Używanie kanału klienta odnajdywania</span><span class="sxs-lookup"><span data-stu-id="c2e46-112">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
