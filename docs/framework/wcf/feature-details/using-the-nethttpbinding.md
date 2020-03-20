---
title: Używanie elementu NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 82222dbfa3f35ed00d0173f2bc927c32e9e98470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184232"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="69239-102">Używanie elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="69239-102">Using the NetHttpBinding</span></span>
<span data-ttu-id="69239-103"><xref:System.ServiceModel.NetHttpBinding>jest wiązaniem przeznaczonym do korzystania z usług HTTP lub WebSocket i domyślnie używa kodowania binarnego.</span><span class="sxs-lookup"><span data-stu-id="69239-103"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="69239-104"><xref:System.ServiceModel.NetHttpBinding>wykryje, czy jest używany z umową żądanie odpowiedź lub dupleksu i zmienić jego zachowanie, aby dopasować - użyje HTTP dla umów żądanie odpowiedzi i WebSockets dla kontraktów dupleksu.</span><span class="sxs-lookup"><span data-stu-id="69239-104"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="69239-105">To zachowanie można zastąpić za <xref:System.ServiceModel.Channels.WebSocketTransportUsage> pomocą ustawienia:</span><span class="sxs-lookup"><span data-stu-id="69239-105">This behavior can be overridden using the <xref:System.ServiceModel.Channels.WebSocketTransportUsage> setting:</span></span>  
  
1. <span data-ttu-id="69239-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always>- Zmusza to WebSockets do wykorzystania nawet dla umowy żądanie odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="69239-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2. <span data-ttu-id="69239-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never>- Zapobiega to użyciu WebSockets.</span><span class="sxs-lookup"><span data-stu-id="69239-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> - This prevents WebSockets from being used.</span></span> <span data-ttu-id="69239-108">Próba użycia umowy dupleksu z tym ustawieniem spowoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="69239-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3. <span data-ttu-id="69239-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex>- Jest to wartość domyślna i zachowuje się tak, jak opisano powyżej.</span><span class="sxs-lookup"><span data-stu-id="69239-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="69239-110"><xref:System.ServiceModel.NetHttpBinding>obsługuje niezawodne sesje zarówno w trybie HTTP, jak i WebSocket.</span><span class="sxs-lookup"><span data-stu-id="69239-110"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="69239-111">W trybie WebSocket sesje są dostarczane przez transport.</span><span class="sxs-lookup"><span data-stu-id="69239-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="69239-112">Podczas korzystania <xref:System.ServiceModel.NetHttpBinding> z i powiązania TransferMode jest ustawiona na TransferMode.Streamed, duże strumienie mogą powodować zakleszczenie i wywołanie będzie limit czasu.</span><span class="sxs-lookup"><span data-stu-id="69239-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="69239-113">Aby obejść ten problem, wyślij mniejsze wiadomości lub użyj Pliku TransferMode.Buffered.</span><span class="sxs-lookup"><span data-stu-id="69239-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="69239-114">Konfigurowanie usługi do używania funkcji NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="69239-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="69239-115"><xref:System.ServiceModel.NetHttpBinding> Można skonfigurować tak samo jak inne powiązanie.</span><span class="sxs-lookup"><span data-stu-id="69239-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="69239-116">Poniższy fragment kodu konfiguracji ilustruje sposób konfigurowania usługi <xref:System.ServiceModel.NetHttpBinding>WCF za pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="69239-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
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
  
 <span data-ttu-id="69239-117">Poniższy fragment kodu pokazuje, jak <xref:System.ServiceModel.NetHttpBinding> dodać w kodzie.</span><span class="sxs-lookup"><span data-stu-id="69239-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="69239-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69239-118">See also</span></span>

- [<span data-ttu-id="69239-119">Konfigurowanie powiązań dla usług</span><span class="sxs-lookup"><span data-stu-id="69239-119">Configuring Bindings for Services</span></span>](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="69239-120">Powiązania</span><span class="sxs-lookup"><span data-stu-id="69239-120">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)
- [<span data-ttu-id="69239-121">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="69239-121">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="69239-122">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="69239-122">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
