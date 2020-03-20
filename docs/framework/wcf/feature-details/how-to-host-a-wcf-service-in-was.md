---
title: 'Instrukcje: Hostowanie usługi WCF w usłudze WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 823c3b8452a3fd1c95758d2d09a9effdf02075c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184914"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="f86b0-102">Instrukcje: Hostowanie usługi WCF w usłudze WAS</span><span class="sxs-lookup"><span data-stu-id="f86b0-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="f86b0-103">W tym temacie opisano podstawowe kroki wymagane do utworzenia usługi aktywacji procesów systemu Windows (znanej również jako WAS) hostowanej w usłudze Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f86b0-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="f86b0-104">WAS to nowa usługa aktywacji procesu, która jest uogólnienie funkcji internetowych usług informacyjnych (IIS), które działają z protokołami transportu innych niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="f86b0-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="f86b0-105">WCF używa interfejsu karty odbiornika do przekazywania żądań aktywacji, które są odbierane za pośrednictwem protokołów innych niż HTTP obsługiwanych przez WCF, takich jak TCP, nazwane potoki i Usługi kolejkowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f86b0-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="f86b0-106">Ta opcja hostingu wymaga, aby składniki aktywacji WAS były poprawnie zainstalowane i skonfigurowane, ale nie wymaga żadnego kodu hostingu do zapisania jako część aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f86b0-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="f86b0-107">Aby uzyskać więcej informacji na temat instalowania i konfigurowania usługi WAS, zobacz [Jak: Instalowanie i konfigurowanie składników aktywacji WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="f86b0-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f86b0-108">Aktywacja usługi WAS nie jest obsługiwana, jeśli potok przetwarzania żądań serwera sieci web jest ustawiony na tryb klasyczny.</span><span class="sxs-lookup"><span data-stu-id="f86b0-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="f86b0-109">Potok przetwarzania żądań serwera sieci web musi być ustawiony na tryb zintegrowany, jeśli ma być używana aktywacja WAS.</span><span class="sxs-lookup"><span data-stu-id="f86b0-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="f86b0-110">Gdy usługa WCF jest hostowana wsłudze WAS, standardowe powiązania są używane w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="f86b0-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="f86b0-111">Jednak podczas korzystania <xref:System.ServiceModel.NetTcpBinding> z <xref:System.ServiceModel.NetNamedPipeBinding> i do konfigurowania usługi hostowane przez USŁUGI, musi być spełnione ograniczenie.</span><span class="sxs-lookup"><span data-stu-id="f86b0-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="f86b0-112">Gdy różne punkty końcowe używają tego samego transportu, ustawienia powiązania muszą być zgodne z następującymi siedmioma właściwościami:</span><span class="sxs-lookup"><span data-stu-id="f86b0-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="f86b0-113">Rozmiar bufora połączenia</span><span class="sxs-lookup"><span data-stu-id="f86b0-113">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="f86b0-114">Limit czasu na kanały</span><span class="sxs-lookup"><span data-stu-id="f86b0-114">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="f86b0-115">Maxpendingconnections</span><span class="sxs-lookup"><span data-stu-id="f86b0-115">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="f86b0-116">MaxOutputDelay (MaxOutputDelay)</span><span class="sxs-lookup"><span data-stu-id="f86b0-116">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="f86b0-117">Maxpendingaccepts</span><span class="sxs-lookup"><span data-stu-id="f86b0-117">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="f86b0-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="f86b0-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="f86b0-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="f86b0-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="f86b0-120">W przeciwnym razie punkt końcowy, który jest inicjowany najpierw zawsze określa wartości <xref:System.ServiceModel.ServiceActivationException> tych właściwości, a punkty końcowe dodane później zgłosić, jeśli nie pasują do tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="f86b0-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="f86b0-121">Aby zapoznać się z kopią źródłową tego przykładu, zobacz [Aktywacja TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="f86b0-121">For the source copy of this example, see [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="f86b0-122">Aby utworzyć podstawową usługę obsługiwaną przez usługę WAS</span><span class="sxs-lookup"><span data-stu-id="f86b0-122">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="f86b0-123">Zdefiniuj umowę serwisową dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="f86b0-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="f86b0-124">Zaimplementuj umowę serwisową w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="f86b0-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="f86b0-125">Należy zauważyć, że adres lub powiązanie informacje nie jest określony wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f86b0-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="f86b0-126">Ponadto kod nie musi być zapisywany, aby pobrać te informacje z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f86b0-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="f86b0-127">Utwórz plik Web.config, <xref:System.ServiceModel.NetTcpBinding> aby zdefiniować `CalculatorService` powiązanie, które ma być używane przez punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="f86b0-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
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
  
4. <span data-ttu-id="f86b0-128">Utwórz plik Service.svc zawierający następujący kod.</span><span class="sxs-lookup"><span data-stu-id="f86b0-128">Create a Service.svc file that contains the following code.</span></span>  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="f86b0-129">Umieść plik Service.svc w katalogu wirtualnym usług IIS.</span><span class="sxs-lookup"><span data-stu-id="f86b0-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="f86b0-130">Aby utworzyć klienta do korzystania z usługi</span><span class="sxs-lookup"><span data-stu-id="f86b0-130">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="f86b0-131">Użyj [narzędzia narzędzia metadanych ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z wiersza polecenia, aby wygenerować kod z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="f86b0-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="f86b0-132">Klient, który jest `ICalculator` generowany zawiera interfejs, który definiuje umowy serwisowej, że implementacja klienta musi spełniać.</span><span class="sxs-lookup"><span data-stu-id="f86b0-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="f86b0-133">Wygenerowana aplikacja kliencka zawiera `ClientCalculator`również implementację pliku .</span><span class="sxs-lookup"><span data-stu-id="f86b0-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="f86b0-134">Należy zauważyć, że adres i informacje o powiązaniach nie jest określony w dowolnym miejscu wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f86b0-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="f86b0-135">Ponadto kod nie musi być zapisywany, aby pobrać te informacje z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f86b0-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="f86b0-136">Konfiguracja dla klienta, który <xref:System.ServiceModel.NetTcpBinding> używa jest również generowany przez Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="f86b0-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="f86b0-137">Ten plik powinien być nazwany w pliku App.config podczas korzystania z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f86b0-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. <span data-ttu-id="f86b0-138">Utwórz wystąpienie `ClientCalculator` w aplikacji, a następnie wywołaj operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="f86b0-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="f86b0-139">Skompiluj i uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="f86b0-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f86b0-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f86b0-140">See also</span></span>

- [<span data-ttu-id="f86b0-141">Aktywacja TCP</span><span class="sxs-lookup"><span data-stu-id="f86b0-141">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- <span data-ttu-id="f86b0-142">[Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f86b0-142">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
