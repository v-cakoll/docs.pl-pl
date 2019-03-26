---
title: Używanie elementu NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 47a4da6dd709c300b62a7380e6e0754e31782dd8
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411073"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="35ea8-102">Używanie elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="35ea8-102">Using the NetHttpBinding</span></span>
<span data-ttu-id="35ea8-103"><xref:System.ServiceModel.NetHttpBinding> jest przeznaczony dla korzystanie z usług HTTP i WebSocket powiązanie i używa kodowania binarnego domyślnie.</span><span class="sxs-lookup"><span data-stu-id="35ea8-103"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="35ea8-104"><xref:System.ServiceModel.NetHttpBinding> wykryje, czy jest używana za pomocą kontraktu dwukierunkowego lub kontraktu "żądanie odpowiedź" i zmianę jej zachowania, aby dopasować — go będzie używany protokół HTTP dla kontraktów "żądanie odpowiedź" i technologia WebSockets kontrakty dwukierunkowe.</span><span class="sxs-lookup"><span data-stu-id="35ea8-104"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="35ea8-105">To zachowanie można przesłonić przy użyciu <xref:System.ServiceModel.Channels.WebSocketTransportUsage> ustawienia:</span><span class="sxs-lookup"><span data-stu-id="35ea8-105">This behavior can be overridden using the <xref:System.ServiceModel.Channels.WebSocketTransportUsage> setting:</span></span>  
  
1. <span data-ttu-id="35ea8-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> -Wymusza WebSockets ma być używany, nawet w przypadku kontraktów "żądanie odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="35ea8-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2. <span data-ttu-id="35ea8-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> Zapobiega — używana przez protokół WebSockets.</span><span class="sxs-lookup"><span data-stu-id="35ea8-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> - This prevents WebSockets from being used.</span></span> <span data-ttu-id="35ea8-108">Podjęto próbę użycia kontrakt dupleksowy, to ustawienie powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="35ea8-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3. <span data-ttu-id="35ea8-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> -Jest wartością domyślną i zachowuje się zgodnie z powyższym opisem.</span><span class="sxs-lookup"><span data-stu-id="35ea8-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="35ea8-110"><xref:System.ServiceModel.NetHttpBinding> niezawodne sesje obsługuje zarówno w trybie HTTP, jak i w trybie protokołu WebSocket.</span><span class="sxs-lookup"><span data-stu-id="35ea8-110"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="35ea8-111">W WebSocket trybu sesji są dostarczane przez transportu.</span><span class="sxs-lookup"><span data-stu-id="35ea8-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="35ea8-112">Korzystając z <xref:System.ServiceModel.NetHttpBinding> i powiązania tryb transferu jest równa TransferMode.Streamed, dużych strumieni może spowodować, że zakleszczenie i limit czasu spowoduje wywołanie.</span><span class="sxs-lookup"><span data-stu-id="35ea8-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="35ea8-113">Aby obejść ten problem wysyłać mniejszych wiadomości, lub użyj elementy TransferMode.Buffered.</span><span class="sxs-lookup"><span data-stu-id="35ea8-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="35ea8-114">Konfigurowanie usługi do użycia NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="35ea8-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="35ea8-115"><xref:System.ServiceModel.NetHttpBinding> Może być skonfigurowane tak samo jak wszystkie inne powiązanie.</span><span class="sxs-lookup"><span data-stu-id="35ea8-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="35ea8-116">Poniższy fragment kodu konfiguracji przedstawia sposób konfigurowania usługi WCF, za pomocą <xref:System.ServiceModel.NetHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="35ea8-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
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
  
 <span data-ttu-id="35ea8-117">Poniższy fragment kodu przedstawia sposób dodawania <xref:System.ServiceModel.NetHttpBinding> w kodzie.</span><span class="sxs-lookup"><span data-stu-id="35ea8-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="35ea8-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35ea8-118">See also</span></span>
- [<span data-ttu-id="35ea8-119">Konfigurowanie powiązań dla usług</span><span class="sxs-lookup"><span data-stu-id="35ea8-119">Configuring Bindings for Services</span></span>](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="35ea8-120">Powiązania</span><span class="sxs-lookup"><span data-stu-id="35ea8-120">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)
- [<span data-ttu-id="35ea8-121">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="35ea8-121">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="35ea8-122">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="35ea8-122">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
