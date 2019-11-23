---
title: Konfigurowanie zachowań klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: ca466af71f62ef72e021753b132afdc847f75d76
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320695"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="5a6a2-102">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="5a6a2-102">Configuring Client Behaviors</span></span>
<span data-ttu-id="5a6a2-103">Windows Communication Foundation (WCF) konfiguruje zachowania na dwa sposoby: w odniesieniu do konfiguracji zachowania — które są zdefiniowane w sekcji `<behavior>` pliku konfiguracyjnego aplikacji klienckiej — lub programowo w aplikacji wywołującej.</span><span class="sxs-lookup"><span data-stu-id="5a6a2-103">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="5a6a2-104">W tym temacie opisano oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="5a6a2-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="5a6a2-105">W przypadku korzystania z pliku konfiguracji, konfiguracja zachowania jest nazwaną kolekcją ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5a6a2-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="5a6a2-106">Nazwa każdej konfiguracji zachowania musi być unikatowa.</span><span class="sxs-lookup"><span data-stu-id="5a6a2-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="5a6a2-107">Ten ciąg jest używany w atrybucie `behaviorConfiguration` konfiguracji punktu końcowego w celu połączenia punktu końcowego z zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="5a6a2-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a6a2-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a6a2-108">Example</span></span>  
 <span data-ttu-id="5a6a2-109">Poniższy kod konfiguracji definiuje zachowanie o nazwie `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="5a6a2-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="5a6a2-110">Punkt końcowy klienta odwołuje się do tego zachowania w atrybucie `behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="5a6a2-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="5a6a2-111">Programistyczne używanie zachowań</span><span class="sxs-lookup"><span data-stu-id="5a6a2-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="5a6a2-112">Można również programowo skonfigurować lub wstawić zachowania, lokalizując odpowiednią właściwość `Behaviors` w obiekcie klienta Windows Communication Foundation (WCF) lub w obiekcie fabryki kanału klienta przed otwarciem klienta.</span><span class="sxs-lookup"><span data-stu-id="5a6a2-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a6a2-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a6a2-113">Example</span></span>  
 <span data-ttu-id="5a6a2-114">Poniższy przykład kodu pokazuje, jak programowo wstawić zachowanie, uzyskując dostęp do właściwości <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> na <xref:System.ServiceModel.Description.ServiceEndpoint> zwróconej przez właściwość <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> przed utworzeniem obiektu kanału.</span><span class="sxs-lookup"><span data-stu-id="5a6a2-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="5a6a2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a6a2-115">See also</span></span>

- [<span data-ttu-id="5a6a2-116">zachowania \<></span><span class="sxs-lookup"><span data-stu-id="5a6a2-116">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)
