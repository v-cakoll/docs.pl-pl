---
title: Konfigurowanie zachowań klienta
description: 'Dowiedz się więcej na temat dwóch sposobów konfigurowania zachowań przez funkcję WCF: w pliku konfiguracyjnym aplikacji lub programowo przy użyciu aplikacji wywołującej.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 4b83862221cf249455478c3ade159a3101062f3e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245443"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="22923-103">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="22923-103">Configuring Client Behaviors</span></span>
<span data-ttu-id="22923-104">Windows Communication Foundation (WCF) konfiguruje zachowania na dwa sposoby: w odniesieniu do konfiguracji zachowania — które są zdefiniowane w `<behavior>` sekcji pliku konfiguracyjnego aplikacji klienckiej — lub programowo w aplikacji wywołującej.</span><span class="sxs-lookup"><span data-stu-id="22923-104">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="22923-105">W tym temacie opisano oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="22923-105">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="22923-106">W przypadku korzystania z pliku konfiguracji, konfiguracja zachowania jest nazwaną kolekcją ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="22923-106">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="22923-107">Nazwa każdej konfiguracji zachowania musi być unikatowa.</span><span class="sxs-lookup"><span data-stu-id="22923-107">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="22923-108">Ten ciąg jest używany w `behaviorConfiguration` atrybucie konfiguracji punktu końcowego w celu połączenia punktu końcowego z zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="22923-108">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22923-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="22923-109">Example</span></span>  
 <span data-ttu-id="22923-110">Poniższy kod konfiguracji definiuje zachowanie o nazwie `myBehavior` .</span><span class="sxs-lookup"><span data-stu-id="22923-110">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="22923-111">Punkt końcowy klienta odwołuje się do tego zachowania w `behaviorConfiguration` atrybucie.</span><span class="sxs-lookup"><span data-stu-id="22923-111">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="22923-112">Programistyczne używanie zachowań</span><span class="sxs-lookup"><span data-stu-id="22923-112">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="22923-113">Można również programowo skonfigurować lub wstawić zachowania, lokalizując odpowiednią `Behaviors` Właściwość w obiekcie klienta Windows Communication Foundation (WCF) lub w obiekcie fabryki kanału klienta przed otwarciem klienta.</span><span class="sxs-lookup"><span data-stu-id="22923-113">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22923-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="22923-114">Example</span></span>  
 <span data-ttu-id="22923-115">Poniższy przykład kodu pokazuje, jak programowo wstawić zachowanie, uzyskując dostęp do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> właściwości <xref:System.ServiceModel.Description.ServiceEndpoint> zwracanej z <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> Właściwości przed utworzeniem obiektu kanału.</span><span class="sxs-lookup"><span data-stu-id="22923-115">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="22923-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22923-116">See also</span></span>

- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
