---
title: Konfigurowanie zachowań klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 83fdc77bd17115f9952f2ca6c494ed0eb873cd9c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193658"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="3be0e-102">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="3be0e-102">Configuring Client Behaviors</span></span>
<span data-ttu-id="3be0e-103">Windows Communication Foundation (WCF) umożliwia skonfigurowanie zachowania na dwa sposoby: przy odwoływaniu się do konfiguracji zachowanie — które są zdefiniowane w `<behavior>` sekcję pliku konfiguracji aplikacji klienta — lub programowo w wywołania aplikacja.</span><span class="sxs-lookup"><span data-stu-id="3be0e-103">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="3be0e-104">W tym temacie opisano oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="3be0e-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="3be0e-105">Korzystając z pliku konfiguracji, konfiguracji zachowanie jest nazwany zestaw ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3be0e-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="3be0e-106">Nazwa każdej konfiguracji zachowanie musi być unikatowa.</span><span class="sxs-lookup"><span data-stu-id="3be0e-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="3be0e-107">Ten ciąg jest używany podczas `behaviorConfiguration` atrybutu konfiguracji punktu końcowego do łączenia punktu końcowego do zachowania.</span><span class="sxs-lookup"><span data-stu-id="3be0e-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3be0e-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="3be0e-108">Example</span></span>  
 <span data-ttu-id="3be0e-109">Poniższy kod konfiguracji definiuje zachowanie nazywane `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="3be0e-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="3be0e-110">Punkt końcowy klienta odwołuje się do zachowania w `behaviorConfiguration` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3be0e-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="3be0e-111">Programowo za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="3be0e-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="3be0e-112">Można również skonfigurować lub programowe Wstawianie zachowania, znajdując odpowiednie `Behaviors` właściwości w obiekcie klienta usługi Windows Communication Foundation (WCF) lub na obiekt fabryki kanału klienta przed otwarciem klienta.</span><span class="sxs-lookup"><span data-stu-id="3be0e-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3be0e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="3be0e-113">Example</span></span>  
 <span data-ttu-id="3be0e-114">Poniższy przykład kodu pokazuje, jak programowe Wstawianie zachowania, uzyskując dostęp do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> właściwość <xref:System.ServiceModel.Description.ServiceEndpoint> zwróciło <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> właściwości przed utworzenia obiektu kanału.</span><span class="sxs-lookup"><span data-stu-id="3be0e-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="3be0e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3be0e-115">See also</span></span>

- [<span data-ttu-id="3be0e-116">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="3be0e-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
