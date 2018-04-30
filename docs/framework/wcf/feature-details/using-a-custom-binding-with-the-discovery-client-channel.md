---
title: Używanie powiązania niestandardowego z kanałem klienta odnajdywania
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a5c80a257efb5f6006a0cf6394a1079cf92d2471
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="4765f-102">Używanie powiązania niestandardowego z kanałem klienta odnajdywania</span><span class="sxs-lookup"><span data-stu-id="4765f-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="4765f-103">Podczas korzystania z niestandardowego powiązania <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, należy zdefiniować <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> tworzącą <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="4765f-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="4765f-104">Tworzenie DiscoveryEndpointProvider</span><span class="sxs-lookup"><span data-stu-id="4765f-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="4765f-105"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Odpowiedzialną za tworzenie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpienia na żądanie.</span><span class="sxs-lookup"><span data-stu-id="4765f-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="4765f-106">Aby zdefiniować dostawcy punktu końcowego odnajdywania, klasa wyprowadzona z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> i zastąpić <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> — metoda i przywracać nowy punkt końcowy odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="4765f-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="4765f-107">Poniższy przykład przedstawia sposób tworzenia dostawcy punktu końcowego odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="4765f-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="4765f-108">Po zdefiniowaniu dostawcy punktu końcowego odnajdywania można utworzyć niestandardowego powiązania i dodać <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, który odwołuje się do odnajdywania dostawcy punktu końcowego jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4765f-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="4765f-109">Aby uzyskać więcej informacji o korzystaniu z kanałem klienta odnajdywania, zobacz [przy użyciu kanału klienta odnajdowania](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="4765f-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span> <span data-ttu-id="4765f-110">Na przykład kompletny kod, zobacz [przykład elementu wiązania odnajdywania](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)</span><span class="sxs-lookup"><span data-stu-id="4765f-110">For a complete code example, see [Discovery Binding Element Sample](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4765f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4765f-111">See Also</span></span>  
 [<span data-ttu-id="4765f-112">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="4765f-112">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="4765f-113">Używanie kanału klienta odnajdywania</span><span class="sxs-lookup"><span data-stu-id="4765f-113">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [<span data-ttu-id="4765f-114">Przykład elementu powiązania odnajdywania</span><span class="sxs-lookup"><span data-stu-id="4765f-114">Discovery Binding Element Sample</span></span>](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)
