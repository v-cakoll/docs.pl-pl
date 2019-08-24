---
title: Używanie elementu NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 0f908361c5f9152d333daaf5e3ee90de3b1b89e9
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988632"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="7c1dc-102">Używanie elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="7c1dc-102">Using the NetHttpBinding</span></span>
<span data-ttu-id="7c1dc-103"><xref:System.ServiceModel.NetHttpBinding>to powiązanie przeznaczone do konsumowania usług HTTP lub WebSocket i domyślnie używa kodowania binarnego.</span><span class="sxs-lookup"><span data-stu-id="7c1dc-103"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="7c1dc-104"><xref:System.ServiceModel.NetHttpBinding>Program wykrywa, czy jest używany z kontraktem typu żądanie-odpowiedź, czy z umową dupleksową, i zmienia jego zachowanie na zgodne — będzie używać protokołu HTTP dla kontraktów żądania i odpowiedzi oraz dla kontraktów dwukierunkowych.</span><span class="sxs-lookup"><span data-stu-id="7c1dc-104"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="7c1dc-105">To zachowanie można zastąpić przy użyciu <xref:System.ServiceModel.Channels.WebSocketTransportUsage> ustawienia:</span><span class="sxs-lookup"><span data-stu-id="7c1dc-105">This behavior can be overridden using the <xref:System.ServiceModel.Channels.WebSocketTransportUsage> setting:</span></span>  
  
1. <span data-ttu-id="7c1dc-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always>— Spowoduje to wymuszenie użycia obiektów WebSockets nawet w przypadku kontraktów żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="7c1dc-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2. <span data-ttu-id="7c1dc-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never>— Uniemożliwia korzystanie z obiektów WebSockets.</span><span class="sxs-lookup"><span data-stu-id="7c1dc-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> - This prevents WebSockets from being used.</span></span> <span data-ttu-id="7c1dc-108">Próba użycia kontraktu dupleksowego z tym ustawieniem spowoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7c1dc-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3. <span data-ttu-id="7c1dc-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex>— Jest to wartość domyślna i zachowuje się zgodnie z powyższym opisem.</span><span class="sxs-lookup"><span data-stu-id="7c1dc-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="7c1dc-110"><xref:System.ServiceModel.NetHttpBinding>obsługuje niezawodne sesje w trybie HTTP i w trybie WebSocket.</span><span class="sxs-lookup"><span data-stu-id="7c1dc-110"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="7c1dc-111">W przypadku sesji trybu WebSocket są udostępniane przez transport.</span><span class="sxs-lookup"><span data-stu-id="7c1dc-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="7c1dc-112">W przypadku korzystania <xref:System.ServiceModel.NetHttpBinding> z i elementu BindingMode ma ustawioną wartość TransferMode. streamd, duże strumienie mogą spowodować zakleszczenie i wywołanie zostanie przekroczenie limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="7c1dc-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="7c1dc-113">Aby obejść ten problem, Wyślij mniejsze wiadomości lub użyj przetransfermode. Buffered.</span><span class="sxs-lookup"><span data-stu-id="7c1dc-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="7c1dc-114">Konfigurowanie usługi do korzystania z protokołu HttpBinding</span><span class="sxs-lookup"><span data-stu-id="7c1dc-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="7c1dc-115"><xref:System.ServiceModel.NetHttpBinding> Można skonfigurować takie same jak inne powiązania.</span><span class="sxs-lookup"><span data-stu-id="7c1dc-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="7c1dc-116">Poniższy fragment konfiguracji ilustruje sposób konfigurowania usługi WCF w <xref:System.ServiceModel.NetHttpBinding>usłudze.</span><span class="sxs-lookup"><span data-stu-id="7c1dc-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    ...
  </system.serviceModel>  
```  
  
 <span data-ttu-id="7c1dc-117">Poniższy fragment kodu pokazuje, <xref:System.ServiceModel.NetHttpBinding> jak dodać kod w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7c1dc-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c1dc-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c1dc-118">See also</span></span>

- [<span data-ttu-id="7c1dc-119">Konfigurowanie powiązań dla usług</span><span class="sxs-lookup"><span data-stu-id="7c1dc-119">Configuring Bindings for Services</span></span>](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="7c1dc-120">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7c1dc-120">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)
- [<span data-ttu-id="7c1dc-121">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="7c1dc-121">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="7c1dc-122">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="7c1dc-122">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
