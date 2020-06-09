---
title: Używanie elementu NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: ac6fc658731d032051f2dfd4058397f9b9a55828
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585639"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="52e74-102">Używanie elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="52e74-102">Using the NetHttpBinding</span></span>
<span data-ttu-id="52e74-103"><xref:System.ServiceModel.NetHttpBinding>to powiązanie przeznaczone do konsumowania usług HTTP lub WebSocket i domyślnie używa kodowania binarnego.</span><span class="sxs-lookup"><span data-stu-id="52e74-103"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="52e74-104"><xref:System.ServiceModel.NetHttpBinding>Program wykrywa, czy jest używany z kontraktem typu żądanie-odpowiedź, czy z umową dupleksową, i zmienia jego zachowanie na zgodne — będzie używać protokołu HTTP dla kontraktów żądania i odpowiedzi oraz dla kontraktów dwukierunkowych.</span><span class="sxs-lookup"><span data-stu-id="52e74-104"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="52e74-105">To zachowanie można zastąpić przy użyciu <xref:System.ServiceModel.Channels.WebSocketTransportUsage> Ustawienia:</span><span class="sxs-lookup"><span data-stu-id="52e74-105">This behavior can be overridden using the <xref:System.ServiceModel.Channels.WebSocketTransportUsage> setting:</span></span>  
  
1. <span data-ttu-id="52e74-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always>— Spowoduje to wymuszenie użycia obiektów WebSockets nawet w przypadku kontraktów żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="52e74-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2. <span data-ttu-id="52e74-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never>— Uniemożliwia korzystanie z obiektów WebSockets.</span><span class="sxs-lookup"><span data-stu-id="52e74-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> - This prevents WebSockets from being used.</span></span> <span data-ttu-id="52e74-108">Próba użycia kontraktu dupleksowego z tym ustawieniem spowoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="52e74-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3. <span data-ttu-id="52e74-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex>— Jest to wartość domyślna i zachowuje się zgodnie z powyższym opisem.</span><span class="sxs-lookup"><span data-stu-id="52e74-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="52e74-110"><xref:System.ServiceModel.NetHttpBinding>obsługuje niezawodne sesje w trybie HTTP i w trybie WebSocket.</span><span class="sxs-lookup"><span data-stu-id="52e74-110"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="52e74-111">W przypadku sesji trybu WebSocket są udostępniane przez transport.</span><span class="sxs-lookup"><span data-stu-id="52e74-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="52e74-112">W przypadku korzystania z <xref:System.ServiceModel.NetHttpBinding> i elementu BindingMode ma ustawioną wartość TransferMode. streamd, duże strumienie mogą spowodować zakleszczenie i wywołanie zostanie przekroczenie limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="52e74-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="52e74-113">Aby obejść ten problem, Wyślij mniejsze wiadomości lub użyj przetransfermode. Buffered.</span><span class="sxs-lookup"><span data-stu-id="52e74-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="52e74-114">Konfigurowanie usługi do korzystania z protokołu HttpBinding</span><span class="sxs-lookup"><span data-stu-id="52e74-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="52e74-115"><xref:System.ServiceModel.NetHttpBinding>Można skonfigurować takie same jak inne powiązania.</span><span class="sxs-lookup"><span data-stu-id="52e74-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="52e74-116">Poniższy fragment konfiguracji ilustruje sposób konfigurowania usługi WCF w usłudze <xref:System.ServiceModel.NetHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="52e74-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
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
  
 <span data-ttu-id="52e74-117">Poniższy fragment kodu pokazuje, jak dodać <xref:System.ServiceModel.NetHttpBinding> kod w kodzie.</span><span class="sxs-lookup"><span data-stu-id="52e74-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="52e74-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52e74-118">See also</span></span>

- [<span data-ttu-id="52e74-119">Konfigurowanie powiązań dla usług</span><span class="sxs-lookup"><span data-stu-id="52e74-119">Configuring Bindings for Services</span></span>](../configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="52e74-120">Powiązania</span><span class="sxs-lookup"><span data-stu-id="52e74-120">Bindings</span></span>](bindings.md)
- [<span data-ttu-id="52e74-121">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="52e74-121">System-Provided Bindings</span></span>](../system-provided-bindings.md)
- [<span data-ttu-id="52e74-122">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="52e74-122">Duplex Services</span></span>](duplex-services.md)
