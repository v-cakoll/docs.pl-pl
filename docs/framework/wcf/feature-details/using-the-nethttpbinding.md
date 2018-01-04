---
title: "Używanie elementu NetHttpBinding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca19446d286395a744496fa300ad1a72e504e738
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="d7f07-102">Używanie elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d7f07-102">Using the NetHttpBinding</span></span>
<span data-ttu-id="d7f07-103"><xref:System.ServiceModel.NetHttpBinding>jest przeznaczony do używania protokołu HTTP lub protokołu WebSocket usług powiązania i używa kodowanie binarne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d7f07-103"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="d7f07-104"><xref:System.ServiceModel.NetHttpBinding>wykryje, czy jest używana z kontraktu "żądanie-odpowiedź" lub kontraktu dwukierunkowego i zmianę jego zachowania, aby dopasować — zostanie użyty HTTP dla kontraktów "żądanie-odpowiedź" i technologia WebSockets dla kontraktów dupleksowych.</span><span class="sxs-lookup"><span data-stu-id="d7f07-104"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="d7f07-105">To zachowanie można przesłonić przy użyciu <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A> --> `WebSocketTransportUsage` ustawienia:</span><span class="sxs-lookup"><span data-stu-id="d7f07-105">This behavior can be overridden using the <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A> --> `WebSocketTransportUsage` setting:</span></span>  
  
1.  <span data-ttu-id="d7f07-106">Zawsze — wymusza Websocket do użycia nawet w przypadku kontraktów "żądanie-odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="d7f07-106">Always - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2.  <span data-ttu-id="d7f07-107">Nigdy nie - zapobiega to Websocket używana.</span><span class="sxs-lookup"><span data-stu-id="d7f07-107">Never - This prevents WebSockets from being used.</span></span> <span data-ttu-id="d7f07-108">Podjęto próbę użycia kontraktu dwukierunkowego tego ustawienia spowoduje Wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d7f07-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3.  <span data-ttu-id="d7f07-109">WhenDuplex — jest to wartość domyślna i działa zgodnie z powyższym opisem.</span><span class="sxs-lookup"><span data-stu-id="d7f07-109">WhenDuplex - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="d7f07-110"><xref:System.ServiceModel.NetHttpBinding>niezawodnej sesji obsługuje zarówno w trybie HTTP, jak i w trybie protokołu WebSocket.</span><span class="sxs-lookup"><span data-stu-id="d7f07-110"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="d7f07-111">W WebSocket tryb sesji są dostarczane przez transport.</span><span class="sxs-lookup"><span data-stu-id="d7f07-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="d7f07-112">Korzystając z <xref:System.ServiceModel.NetHttpBinding> i tryb transferu wiązania jest ustawiona na TransferMode.Streamed, dużych strumieni może spowodować zakleszczenie i zostanie limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d7f07-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="d7f07-113">Aby obejść ten problem wysyłać mniejszych wiadomości, lub użyj elementy TransferMode.Buffered.</span><span class="sxs-lookup"><span data-stu-id="d7f07-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="d7f07-114">Konfigurowanie usługi do użycia NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d7f07-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="d7f07-115"><xref:System.ServiceModel.NetHttpBinding> Może być skonfigurowane tak samo jak wszystkie inne powiązanie.</span><span class="sxs-lookup"><span data-stu-id="d7f07-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="d7f07-116">Poniższy fragment konfiguracji przedstawiono sposób konfigurowania usługi WCF za pomocą <xref:System.ServiceModel.NetHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d7f07-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
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
    <!- ... -->   
  </system.serviceModel>  
```  
  
 <span data-ttu-id="d7f07-117">Poniższy fragment kodu przedstawia sposób dodawania <xref:System.ServiceModel.NetHttpBinding> w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d7f07-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7f07-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7f07-118">See Also</span></span>  
 [<span data-ttu-id="d7f07-119">Konfigurowanie powiązań dla usług</span><span class="sxs-lookup"><span data-stu-id="d7f07-119">Configuring Bindings for Services</span></span>](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [<span data-ttu-id="d7f07-120">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d7f07-120">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="d7f07-121">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="d7f07-121">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="d7f07-122">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="d7f07-122">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
