---
title: "Instrukcje: Hostowanie usługi WCF w usłudze WAS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
caps.latest.revision: "25"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3069dfbde9fedc0a0c89d8f55ba1adcc852d5c24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="8be6a-102">Instrukcje: Hostowanie usługi WCF w usłudze WAS</span><span class="sxs-lookup"><span data-stu-id="8be6a-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="8be6a-103">W tym temacie przedstawiono podstawowe czynności wymagane do tworzenia usług systemu Windows proces aktywacji (znanej także jako Usługa WAS) hostowanej [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="8be6a-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="8be6a-104">ZOSTAŁO to nowa usługa aktywacji procesów, która jest generalizacji funkcji Internet Information Services (IIS), które współpracują z protokołów innych niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="8be6a-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8be6a-105">używa interfejsu adapter odbiornika do komunikowania się żądania aktywacji, które są otrzymywane za pośrednictwem protokołów innych niż HTTP obsługiwane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], takich jak TCP, potoków nazwanych i usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8be6a-105"> uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="8be6a-106">Ta opcja hostingu wymaga składników aktywacji WAS są prawidłowo zainstalowane i skonfigurowane, ale nie wymaga żadnego kodu macierzystego do zapisania jako części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8be6a-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8be6a-107">Instalowanie i konfigurowanie usługi WAS, zobacz [porady: Instalowanie i konfigurowanie składników aktywacji programu WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="8be6a-107"> installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8be6a-108">BYŁA aktywacji nie jest obsługiwane, jeśli ustawiono potoku przetwarzania żądań serwera sieci web do trybu klasycznego.</span><span class="sxs-lookup"><span data-stu-id="8be6a-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="8be6a-109">Potoku przetwarzania żądań serwera sieci web musi mieć ustawioną trybu zintegrowanego, jeśli ma być używany przez aktywację usługi WAS.</span><span class="sxs-lookup"><span data-stu-id="8be6a-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="8be6a-110">Gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hostowanej usługi WAS, standardowe powiązania są używane w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="8be6a-110">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="8be6a-111">Jednak przy użyciu <xref:System.ServiceModel.NetTcpBinding> i <xref:System.ServiceModel.NetNamedPipeBinding> skonfigurowanie usługi hostowanej WAS, muszą być spełnione ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="8be6a-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="8be6a-112">Korzystając z różnych punktów końcowych tego samego transportu, ustawienia powiązania musi odpowiadać na siedem następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="8be6a-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
-   <span data-ttu-id="8be6a-113">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="8be6a-113">ConnectionBufferSize</span></span>  
  
-   <span data-ttu-id="8be6a-114">limitu czasu channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="8be6a-114">ChannelInitializationTimeout</span></span>  
  
-   <span data-ttu-id="8be6a-115">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="8be6a-115">MaxPendingConnections</span></span>  
  
-   <span data-ttu-id="8be6a-116">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="8be6a-116">MaxOutputDelay</span></span>  
  
-   <span data-ttu-id="8be6a-117">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="8be6a-117">MaxPendingAccepts</span></span>  
  
-   <span data-ttu-id="8be6a-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="8be6a-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
-   <span data-ttu-id="8be6a-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="8be6a-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="8be6a-120">W przeciwnym razie wartość punktu końcowego, który został zainicjowany najpierw zawsze określa wartości tych właściwości, a punkty końcowe można dodać później throw <xref:System.ServiceModel.ServiceActivationException> Jeśli nie spełniają tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="8be6a-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="8be6a-121">Dla źródła kopię w tym przykładzie [Aktywacja TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="8be6a-121">For the source copy of this example, see [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="8be6a-122">Aby utworzyć podstawowej usługi hostowanej przez usługę WAS</span><span class="sxs-lookup"><span data-stu-id="8be6a-122">To create a basic service hosted by WAS</span></span>  
  
1.  <span data-ttu-id="8be6a-123">Definiowanie kontraktu usługi dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="8be6a-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2.  <span data-ttu-id="8be6a-124">Implementowanie kontraktu usługi w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="8be6a-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="8be6a-125">Należy pamiętać, że wewnątrz implementacji usługi nie określono informacji o adresie lub powiązanie.</span><span class="sxs-lookup"><span data-stu-id="8be6a-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="8be6a-126">Ponadto kodu nie ma do zapisania do pobierania informacji z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8be6a-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3.  <span data-ttu-id="8be6a-127">Utwórz plik Web.config, aby zdefiniować <xref:System.ServiceModel.NetTcpBinding> powiązania, które mają być używane przez `CalculatorService` punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8be6a-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
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
  
4.  <span data-ttu-id="8be6a-128">Utwórz plik Service.svc zawierający następujący kod.</span><span class="sxs-lookup"><span data-stu-id="8be6a-128">Create a Service.svc file that contains the following code.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  <span data-ttu-id="8be6a-129">Umieść plik Service.svc w katalogu wirtualnego usług IIS.</span><span class="sxs-lookup"><span data-stu-id="8be6a-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="8be6a-130">Aby utworzyć klienta do korzystania z usługi</span><span class="sxs-lookup"><span data-stu-id="8be6a-130">To create a client to use the service</span></span>  
  
1.  <span data-ttu-id="8be6a-131">Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z poziomu wiersza polecenia, aby wygenerować kod na podstawie metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="8be6a-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="8be6a-132">Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacja klienta.</span><span class="sxs-lookup"><span data-stu-id="8be6a-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3.  <span data-ttu-id="8be6a-133">Aplikacja wygenerowanego klienta zawiera również implementacja `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="8be6a-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="8be6a-134">Należy pamiętać, że informacji adres i powiązanie nie określono dowolnym wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="8be6a-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="8be6a-135">Ponadto kodu nie ma do zapisania do pobierania informacji z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8be6a-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4.  <span data-ttu-id="8be6a-136">Konfiguracja klienta, który używa <xref:System.ServiceModel.NetTcpBinding> również jest generowany przez Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="8be6a-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="8be6a-137">Ten plik powinien być o nazwie w pliku App.config, przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8be6a-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5.  <span data-ttu-id="8be6a-138">Utwórz wystąpienie `ClientCalculator` w aplikacji, a następnie wywołać operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="8be6a-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6.  <span data-ttu-id="8be6a-139">Kompilowanie i uruchamianie klienta.</span><span class="sxs-lookup"><span data-stu-id="8be6a-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8be6a-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8be6a-140">See Also</span></span>  
 [<span data-ttu-id="8be6a-141">Aktywacja TCP</span><span class="sxs-lookup"><span data-stu-id="8be6a-141">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [<span data-ttu-id="8be6a-142">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="8be6a-142">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
