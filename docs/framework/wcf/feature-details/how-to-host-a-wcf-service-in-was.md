---
title: 'Instrukcje: hostowanie usługi WCF w usłudze WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: b6d3ace054260de1ca649fbf4bd54156bbea24ce
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972204"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="4d3e0-102">Instrukcje: hostowanie usługi WCF w usłudze WAS</span><span class="sxs-lookup"><span data-stu-id="4d3e0-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="4d3e0-103">W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia usług aktywacji procesów systemu Windows (znanych także jako usługa Windows Communication Foundation hostowanej usługi WCF).</span><span class="sxs-lookup"><span data-stu-id="4d3e0-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="4d3e0-104">BYŁA to nowa usługa aktywacji procesów, która jest generalizacją funkcji Internet Information Services (IIS), które działają z protokołami transportu innym niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="4d3e0-105">Funkcja WCF używa interfejsu adaptera odbiornika do przekazywania żądań aktywacji odbieranych za pośrednictwem protokołów innych niż HTTP obsługiwanych przez program WCF, takich jak TCP, nazwane potoki i kolejkowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="4d3e0-106">Ta opcja hostingu wymaga, aby składniki aktywacji zostały prawidłowo zainstalowane i skonfigurowane, ale nie wymagają zapisywania kodu hostingu jako części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="4d3e0-107">Aby uzyskać więcej informacji na temat instalowania i konfigurowania programu [, zobacz How to: Zainstaluj i Skonfiguruj składniki](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)aktywacji WCF.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="4d3e0-108">Aktywacja nie jest obsługiwana, jeśli potok przetwarzania żądań serwera sieci Web jest ustawiony na tryb klasyczny.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="4d3e0-109">Jeśli aktywacja ma być używana, potok przetwarzania żądań serwera sieci Web musi być ustawiony na tryb zintegrowany.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="4d3e0-110">Gdy usługa WCF jest hostowana w programie, standardowe powiązania są używane w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="4d3e0-111">Jednak w przypadku korzystania z <xref:System.ServiceModel.NetTcpBinding> <xref:System.ServiceModel.NetNamedPipeBinding> i w celu skonfigurowania usługi hostowanej należy spełnić ograniczenie.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="4d3e0-112">Gdy różne punkty końcowe używają tego samego transportu, ustawienia powiązania muszą być zgodne z następującymi siedem właściwości:</span><span class="sxs-lookup"><span data-stu-id="4d3e0-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="4d3e0-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="4d3e0-113">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="4d3e0-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="4d3e0-114">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="4d3e0-115">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="4d3e0-115">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="4d3e0-116">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="4d3e0-116">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="4d3e0-117">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="4d3e0-117">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="4d3e0-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="4d3e0-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="4d3e0-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="4d3e0-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="4d3e0-120">W przeciwnym razie punkt końcowy, który jest inicjowany najpierw zawsze określa wartości tych właściwości, i punkty końcowe dodane później <xref:System.ServiceModel.ServiceActivationException> throw, jeśli nie są zgodne z tymi ustawieniami.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="4d3e0-121">Aby uzyskać kopię źródła tego przykładu, zobacz [Aktywacja protokołu TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="4d3e0-121">For the source copy of this example, see [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="4d3e0-122">Aby utworzyć podstawową usługę hostowaną przez program:</span><span class="sxs-lookup"><span data-stu-id="4d3e0-122">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="4d3e0-123">Zdefiniuj kontrakt usługi dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="4d3e0-124">Zaimplementuj kontrakt usługi w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="4d3e0-125">Należy zauważyć, że informacje o adresie lub powiązaniu nie są określone w implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="4d3e0-126">Ponadto kod nie musi być zapisany, aby można było pobrać te informacje z pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="4d3e0-127">Utwórz plik Web. config, <xref:System.ServiceModel.NetTcpBinding> aby zdefiniować powiązanie, które ma być używane `CalculatorService` przez punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="4d3e0-128">Utwórz plik Service. svc zawierający poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-128">Create a Service.svc file that contains the following code.</span></span>  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="4d3e0-129">Umieść plik Service. svc w katalogu wirtualnym usług IIS.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="4d3e0-130">Aby utworzyć klienta do korzystania z usługi</span><span class="sxs-lookup"><span data-stu-id="4d3e0-130">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="4d3e0-131">Użyj [Narzędzia do obsługi metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z wiersza polecenia, aby wygenerować kod na podstawie metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="4d3e0-132">Wygenerowany klient zawiera `ICalculator` interfejs, który definiuje kontrakt usługi, który musi spełniać implementacja klienta.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="4d3e0-133">Wygenerowana aplikacja kliencka zawiera również implementację `ClientCalculator`programu.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="4d3e0-134">Należy zauważyć, że informacje o adresie i powiązaniu nie są określone w dowolnym miejscu w implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="4d3e0-135">Ponadto kod nie musi być zapisany, aby można było pobrać te informacje z pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="4d3e0-136">Konfiguracja klienta korzystającego z programu <xref:System.ServiceModel.NetTcpBinding> jest również generowana przez Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="4d3e0-137">Ten plik powinien mieć nazwę w pliku App. config w przypadku korzystania z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5. <span data-ttu-id="4d3e0-138">Utwórz wystąpienie `ClientCalculator` elementu w aplikacji, a następnie Wywołaj operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="4d3e0-139">Kompiluj i uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="4d3e0-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d3e0-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d3e0-140">See also</span></span>

- [<span data-ttu-id="4d3e0-141">Aktywacja TCP</span><span class="sxs-lookup"><span data-stu-id="4d3e0-141">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [<span data-ttu-id="4d3e0-142">Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server</span><span class="sxs-lookup"><span data-stu-id="4d3e0-142">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
