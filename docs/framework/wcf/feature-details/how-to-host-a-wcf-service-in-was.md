---
title: 'Instrukcje: hostowanie usługi WCF w usłudze WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 1ebce4f0182b68e0e3c10d3d04e07560130c0245
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635292"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="db473-102">Instrukcje: hostowanie usługi WCF w usłudze WAS</span><span class="sxs-lookup"><span data-stu-id="db473-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="db473-103">W tym temacie wymieniono podstawowe kroki wymagane do utworzenia usługi aktywacji procesów Windows (znany także jako WAS) hostowanych usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="db473-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="db473-104">ZOSTAŁA nowa usługa aktywacji procesów, która jest uogólnienie funkcji Internet Information Services (IIS), które działają z protokołami protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="db473-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="db473-105">Usługi WCF używa interfejsu karty odbiornika do komunikowania się żądania aktywacji, które są odbierane za pośrednictwem protokołów innych niż HTTP obsługiwane przez architekturę WCF, takich jak TCP, nazwanych potoków i usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="db473-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="db473-106">Ta opcja hostingu wymaga składników aktywacji WAS są prawidłowo zainstalowane i skonfigurowane, ale nie wymaga hostowania kodu do zapisania jako część aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db473-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="db473-107">Aby uzyskać więcej informacji o instalowaniu i konfigurowaniu WAS, zobacz [jak: Instalowanie i konfigurowanie składników aktywacji programu WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="db473-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="db473-108">BYŁA aktywacja nie jest obsługiwana, jeśli potok przetwarzania żądania serwer sieci web jest ustawiany w trybie klasycznym.</span><span class="sxs-lookup"><span data-stu-id="db473-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="db473-109">Potok przetwarzania żądania serwer sieci web musi być równa w trybie zintegrowanym, w przypadku aktywacji WAS do użycia.</span><span class="sxs-lookup"><span data-stu-id="db473-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="db473-110">Gdy usługa WCF jest hostowana w WAS, standardowe powiązania są używane w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="db473-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="db473-111">Jednak przy użyciu <xref:System.ServiceModel.NetTcpBinding> i <xref:System.ServiceModel.NetNamedPipeBinding> do skonfigurowania usługi hostowanej WAS, muszą być spełnione ograniczenie.</span><span class="sxs-lookup"><span data-stu-id="db473-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="db473-112">Korzystając z różnych punktów końcowych tego samego transportu, ustawienia powiązania muszą odpowiadać na następujące siedem właściwości:</span><span class="sxs-lookup"><span data-stu-id="db473-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="db473-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="db473-113">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="db473-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="db473-114">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="db473-115">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="db473-115">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="db473-116">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="db473-116">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="db473-117">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="db473-117">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="db473-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="db473-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="db473-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="db473-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="db473-120">W przeciwnym razie punkt końcowy, który jest inicjowany najpierw zawsze określi wartości tych właściwości i punktów końcowych, dodane później throw <xref:System.ServiceModel.ServiceActivationException> Jeśli te ustawienia są niezgodne.</span><span class="sxs-lookup"><span data-stu-id="db473-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="db473-121">Źródło kopię w tym przykładzie można zobaczyć [Aktywacja TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="db473-121">For the source copy of this example, see [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="db473-122">Aby utworzyć podstawowej usługi hostowane przez WAS</span><span class="sxs-lookup"><span data-stu-id="db473-122">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="db473-123">Definiowanie kontraktu usługi dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="db473-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="db473-124">Implementowanie kontraktu usługi, w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="db473-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="db473-125">Należy pamiętać, że wewnątrz implementacji usługi nie określono adresu lub powiązania informacji.</span><span class="sxs-lookup"><span data-stu-id="db473-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="db473-126">Ponadto kod nie ma do zapisania, aby pobrać te informacje z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="db473-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="db473-127">Utwórz plik Web.config w celu zdefiniowania <xref:System.ServiceModel.NetTcpBinding> powiązania, który będzie używany przez `CalculatorService` punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="db473-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
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
  
4. <span data-ttu-id="db473-128">Utwórz plik Service.svc, który zawiera następujący kod.</span><span class="sxs-lookup"><span data-stu-id="db473-128">Create a Service.svc file that contains the following code.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5. <span data-ttu-id="db473-129">Umieść plik Service.svc w wirtualny katalog IIS.</span><span class="sxs-lookup"><span data-stu-id="db473-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="db473-130">Można utworzyć klienta do korzystania z usługi</span><span class="sxs-lookup"><span data-stu-id="db473-130">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="db473-131">Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z poziomu wiersza polecenia, aby wygenerować kod z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="db473-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="db473-132">Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacji klienta.</span><span class="sxs-lookup"><span data-stu-id="db473-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="db473-133">Aplikacja wygenerowanego klienta zawiera również implementację `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="db473-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="db473-134">Należy pamiętać, informacje dotyczące adresów i powiązania nie dowolnym określona wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="db473-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="db473-135">Ponadto kod nie ma do zapisania, aby pobrać te informacje z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="db473-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="db473-136">Konfiguracja klienta, który używa <xref:System.ServiceModel.NetTcpBinding> również jest generowany przez Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="db473-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="db473-137">Ten plik powinien zostać nazwany w pliku App.config, korzystając z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="db473-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5. <span data-ttu-id="db473-138">Utwórz wystąpienie obiektu `ClientCalculator` w aplikacji, a następnie wywołać operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="db473-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="db473-139">Kompilowanie i uruchamianie klienta.</span><span class="sxs-lookup"><span data-stu-id="db473-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db473-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db473-140">See also</span></span>

- [<span data-ttu-id="db473-141">Aktywacja TCP</span><span class="sxs-lookup"><span data-stu-id="db473-141">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [<span data-ttu-id="db473-142">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="db473-142">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
