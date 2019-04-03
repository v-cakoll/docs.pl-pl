---
title: Aktywacja UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: a61b7fce891ea1ab68f48f836ffaae2b96c8e25d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836327"
---
# <a name="udp-activation"></a><span data-ttu-id="0a924-102">Aktywacja UDP</span><span class="sxs-lookup"><span data-stu-id="0a924-102">UDP Activation</span></span>
<span data-ttu-id="0a924-103">Ten przykład jest oparty na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="0a924-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="0a924-104">Rozszerza [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki do obsługi aktywacji procesu przy użyciu Windows Process Activation Service (WAS).</span><span class="sxs-lookup"><span data-stu-id="0a924-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="0a924-105">Przykład składa się z trzech głównych części:</span><span class="sxs-lookup"><span data-stu-id="0a924-105">The sample consists of three major pieces:</span></span>  
  
-   <span data-ttu-id="0a924-106">UDP protokołu aktywator, procesem autonomicznym, która odbiera komunikaty protokołu UDP w imieniu aplikacji, które mają być aktywowany.</span><span class="sxs-lookup"><span data-stu-id="0a924-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
-   <span data-ttu-id="0a924-107">Klient, który używa niestandardowego transportu UDP do wysyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0a924-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
-   <span data-ttu-id="0a924-108">Usługa (hostowane w procesie roboczym aktywowany przez WAS), która odbiera komunikaty za pośrednictwem protokołu UDP transportu niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="0a924-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="0a924-109">Aktywator protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="0a924-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="0a924-110">Aktywator protokołu UDP jest mostem między klientem usługi WCF i usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="0a924-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="0a924-111">Umożliwia przesyłanie danych za pośrednictwem protokołu UDP w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="0a924-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="0a924-112">Ma dwie główne funkcje:</span><span class="sxs-lookup"><span data-stu-id="0a924-112">It has two major functions:</span></span>  
  
-   <span data-ttu-id="0a924-113">BYŁO odbiornika karty (LA), który współpracuje z WAS do aktywowania procesów w odpowiedzi na wiadomości przychodzące.</span><span class="sxs-lookup"><span data-stu-id="0a924-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
-   <span data-ttu-id="0a924-114">Odbiornik protokołu UDP, który akceptuje komunikaty protokołu UDP w imieniu aplikacji, które mają być aktywowany.</span><span class="sxs-lookup"><span data-stu-id="0a924-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="0a924-115">Aktywator musi działać jako autonomiczna programu na komputerze z serwerem.</span><span class="sxs-lookup"><span data-stu-id="0a924-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="0a924-116">Zazwyczaj karty listener WAS (na przykład NetTcpActivator i NetPipeActivator) są implementowane w usługach Windows długoterminowych.</span><span class="sxs-lookup"><span data-stu-id="0a924-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="0a924-117">Jednak dla prostoty i jasności ten przykład implementuje aktywatora protokołu jako oddzielną aplikację.</span><span class="sxs-lookup"><span data-stu-id="0a924-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="0a924-118">ZOSTAŁ Adapter odbiornika</span><span class="sxs-lookup"><span data-stu-id="0a924-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="0a924-119">Adapter odbiornika zostało protokołu UDP został zaimplementowany w `UdpListenerAdapter` klasy.</span><span class="sxs-lookup"><span data-stu-id="0a924-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="0a924-120">To jest moduł, który wchodzi w interakcję z WAS do wykonywania aktywacji aplikacji dla protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="0a924-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="0a924-121">Jest to osiągane przez wywołanie następujące interfejsy API hostem sieci Web:</span><span class="sxs-lookup"><span data-stu-id="0a924-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="0a924-122">Po wywołaniu początkowo `WebhostRegisterProtocol`, karta odbiornika odbiera wywołania zwrotnego `ApplicationCreated` z WAS dla wszystkich aplikacji zarejestrowanych w pliku applicationHost.config (znajdujący się w % windir%\system32\inetsrv).</span><span class="sxs-lookup"><span data-stu-id="0a924-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="0a924-123">W tym przykładzie będziemy obsługiwać aplikacje przy użyciu protokołu UDP (identyfikatorem protokołu jako "net.udp"), włączone.</span><span class="sxs-lookup"><span data-stu-id="0a924-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="0a924-124">Inne implementacje może obsługiwać to inaczej w przypadku takich implementacje odpowiadanie na dynamiczną konfigurację zmian w aplikacji (na przykład aplikacja przejście z wyłączonego na włączony).</span><span class="sxs-lookup"><span data-stu-id="0a924-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="0a924-125">Podczas wywołania zwrotnego `ConfigManagerInitializationCompleted` zostanie odebrana, oznacza to, tym WAS zakończy wszystkie powiadomienia dotyczące inicjowania protokołu.</span><span class="sxs-lookup"><span data-stu-id="0a924-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="0a924-126">W tej chwili adapter odbiornika jest gotowy do przetwarzania żądań aktywacji.</span><span class="sxs-lookup"><span data-stu-id="0a924-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="0a924-127">Gdy nowe żądanie jest dostępna w aplikacji po raz pierwszy, wywołuje adapter odbiornika `WebhostOpenListenerChannelInstance` do WAS, który rozpoczyna się proces roboczy, jeśli nie jest jeszcze uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="0a924-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="0a924-128">Następnie są ładowane obsługi protokołu i umożliwić komunikację między kartą odbiornik i aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="0a924-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="0a924-129">Adapter odbiornika jest zarejestrowany w %SystemRoot%\System32\inetsrv\ApplicationHost.config w <`listenerAdapters`> sekcji, jako pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="0a924-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="0a924-130">Odbiornik protokołu</span><span class="sxs-lookup"><span data-stu-id="0a924-130">Protocol Listener</span></span>  
 <span data-ttu-id="0a924-131">Odbiornik protokołu UDP jest modułem wewnątrz aktywatora protokołu, który nasłuchuje w punkcie końcowym protokołu UDP w imieniu aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="0a924-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="0a924-132">Jest zaimplementowana w klasie `UdpSocketListener`.</span><span class="sxs-lookup"><span data-stu-id="0a924-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="0a924-133">Punkt końcowy jest reprezentowany jako `IPEndpoint` dla której są wyodrębniane numer portu z powiązania protokołu dla witryny.</span><span class="sxs-lookup"><span data-stu-id="0a924-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="0a924-134">Usługa sterowania</span><span class="sxs-lookup"><span data-stu-id="0a924-134">Control Service</span></span>  
 <span data-ttu-id="0a924-135">W tym przykładzie używamy usługi WCF do komunikowania się między aktywator i proces roboczy WAS.</span><span class="sxs-lookup"><span data-stu-id="0a924-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="0a924-136">Usługa, która znajduje się w aktywator nosi nazwę usługi kontroli.</span><span class="sxs-lookup"><span data-stu-id="0a924-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="0a924-137">Programy obsługi protokołu</span><span class="sxs-lookup"><span data-stu-id="0a924-137">Protocol Handlers</span></span>  
 <span data-ttu-id="0a924-138">Po wywołania adapter odbiornika `WebhostOpenListenerChannelInstance`, menedżera procesów WAS rozpoczyna się proces roboczy, jeśli nie została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="0a924-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="0a924-139">Menedżer aplikacji wewnątrz procesu roboczego ładuje obsługi protokołu procesu (PPH) UDP, z tym żądaniem, w tym `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="0a924-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="0a924-140">PPH w wywołaniach włącza `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="0a924-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="0a924-141">Aby uruchomić UDP AppDomain protokołu obsługi (ADPH).</span><span class="sxs-lookup"><span data-stu-id="0a924-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="0a924-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="0a924-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="0a924-143">Informacje jest zarejestrowany w pliku Web.config w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0a924-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="0a924-144">Specjalnej konfiguracji dla tego przykładu</span><span class="sxs-lookup"><span data-stu-id="0a924-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="0a924-145">W tym przykładzie można tylko skompilować i uruchomić na Windows Vista, Windows Server 2008 lub Windows 7.</span><span class="sxs-lookup"><span data-stu-id="0a924-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="0a924-146">Do uruchomienia przykładu, należy najpierw uzyskać wszystkie składniki poprawnie skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="0a924-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="0a924-147">Wykonaj następujące kroki, aby zainstalować przykład.</span><span class="sxs-lookup"><span data-stu-id="0a924-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="0a924-148">Aby skonfigurować w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="0a924-148">To set up this sample</span></span>  
  
1.  <span data-ttu-id="0a924-149">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="0a924-149">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="0a924-150">Skompiluj projekt w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="0a924-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="0a924-151">Po kompilacji również wykonuje następujące operacje w fazie po kompilacji:</span><span class="sxs-lookup"><span data-stu-id="0a924-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    -   <span data-ttu-id="0a924-152">Instaluje powiązania protokołu UDP do lokacji "Domyślna witryna sieci Web".</span><span class="sxs-lookup"><span data-stu-id="0a924-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    -   <span data-ttu-id="0a924-153">Tworzy aplikację wirtualną "ServiceModelSamples" wskaż ścieżkę fizyczną: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="0a924-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    -   <span data-ttu-id="0a924-154">Umożliwia ona także protokół "net.udp" dla tej aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="0a924-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3.  <span data-ttu-id="0a924-155">Uruchom aplikację interfejsu użytkownika "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="0a924-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="0a924-156">Kliknij przycisk **instalacji** kartę, zaznacz następujące pola wyboru, a następnie kliknij przycisk **zainstalować** je zainstalować:</span><span class="sxs-lookup"><span data-stu-id="0a924-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    -   <span data-ttu-id="0a924-157">Adapter odbiornika protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="0a924-157">UDP Listener Adapter</span></span>  
  
    -   <span data-ttu-id="0a924-158">Programy obsługi protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="0a924-158">UDP Protocol Handlers</span></span>  
  
4.  <span data-ttu-id="0a924-159">Kliknij przycisk **aktywacji** kartę aplikacji interfejsu użytkownika "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="0a924-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="0a924-160">Kliknij przycisk **Start** przycisk, aby uruchomić odbiornik karty.</span><span class="sxs-lookup"><span data-stu-id="0a924-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="0a924-161">Teraz można przystąpić do uruchomienia programu.</span><span class="sxs-lookup"><span data-stu-id="0a924-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0a924-162">Po zakończeniu tego przykładu, należy uruchomić Cleanup.bat, aby usunąć powiązanie net.udp z "Domyślna witryna sieci Web".</span><span class="sxs-lookup"><span data-stu-id="0a924-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="0a924-163">Przykładowe zastosowanie</span><span class="sxs-lookup"><span data-stu-id="0a924-163">Sample Usage</span></span>  
 <span data-ttu-id="0a924-164">Po kompilacji dostępne są cztery różne pliki binarne wygenerowane:</span><span class="sxs-lookup"><span data-stu-id="0a924-164">After compilation, there are four different binaries generated:</span></span>  
  
-   <span data-ttu-id="0a924-165">Client.exe: Kod klienta.</span><span class="sxs-lookup"><span data-stu-id="0a924-165">Client.exe: The client code.</span></span> <span data-ttu-id="0a924-166">App.config jest kompilowany do pliku konfiguracji klienta Client.exe.config.</span><span class="sxs-lookup"><span data-stu-id="0a924-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
-   <span data-ttu-id="0a924-167">UDPActivation.dll: Biblioteka, która zawiera wszystkie główne implementacji protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="0a924-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
-   <span data-ttu-id="0a924-168">Service.dll: W kodzie usługi.</span><span class="sxs-lookup"><span data-stu-id="0a924-168">Service.dll: The service code.</span></span> <span data-ttu-id="0a924-169">To jest kopiowany do katalogu \bin zestawu ServiceModelSamples pakiecie aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="0a924-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="0a924-170">Plik usługi jest Service.svc i plik konfiguracji jest plik Web.config. Po kompilacji, są kopiowane do następującej lokalizacji: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="0a924-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
-   <span data-ttu-id="0a924-171">WasNetActivator: Program aktywatora UDP.</span><span class="sxs-lookup"><span data-stu-id="0a924-171">WasNetActivator: The UDP activator program.</span></span>  
  
-   <span data-ttu-id="0a924-172">Upewnij się, że wszystkie wymagane elementy zostały zainstalowane poprawnie.</span><span class="sxs-lookup"><span data-stu-id="0a924-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="0a924-173">Poniższe kroki pokazują jak do uruchomienia przykładu:</span><span class="sxs-lookup"><span data-stu-id="0a924-173">The following steps show how to run the sample:</span></span>  
  
1.  <span data-ttu-id="0a924-174">Upewnij się, że zostały uruchomione następujące usługi Windows:</span><span class="sxs-lookup"><span data-stu-id="0a924-174">Ensure that the following Windows services have been started:</span></span>  
  
    -   <span data-ttu-id="0a924-175">Usługi Windows Process Activation Service (WAS).</span><span class="sxs-lookup"><span data-stu-id="0a924-175">Windows Process Activation Service (WAS).</span></span>  
  
    -   <span data-ttu-id="0a924-176">Internetowe usługi informacyjne (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="0a924-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2.  <span data-ttu-id="0a924-177">Następnie uruchom aktywator WasNetActivator.exe.</span><span class="sxs-lookup"><span data-stu-id="0a924-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="0a924-178">W obszarze **aktywacji** karta, jedynym protokołem **UDP**, jest zaznaczony na liście rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="0a924-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="0a924-179">Kliknij przycisk **Start** przycisk, aby uruchomić aktywatora.</span><span class="sxs-lookup"><span data-stu-id="0a924-179">Click the **Start** button to start the activator.</span></span>  
  
3.  <span data-ttu-id="0a924-180">Po rozpoczęciu aktywator może uruchamiać kod klienta, uruchamiając Client.exe z okna poleceń.</span><span class="sxs-lookup"><span data-stu-id="0a924-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="0a924-181">Poniżej przedstawiono przykładowe dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0a924-181">The following is the sample output:</span></span>  
  
    ```  
    Testing Udp Activation.  
    Start the status service.  
    Sending UDP datagrams.  
    Type a word that you want to say to the server: Hello, world!  
        Sending datagram: Hello, world![0]  
        Sending datagram: Hello, world![1]  
        Sending datagram: Hello, world![2]  
        Sending datagram: Hello, world![3]  
        Sending datagram: Hello, world![4]  
    Calling UDP duplex contract (ICalculatorContract).  
        0 + 0 = 0  
        1 + 2 = 3  
        2 + 4 = 6  
        3 + 6 = 9  
        4 + 8 = 12  
    Getting status and dump server traces:  
        Operation 'Hello' is called: Hello, world![0]  
        Operation 'Hello' is called: Hello, world![1]  
        Operation 'Hello' is called: Hello, world![2]  
        Operation 'Hello' is called: Hello, world![3]  
        Operation 'Hello' is called: Hello, world![4]  
        Operation 'Add' is called: 0 + 0  
        Operation 'Add' is called: 1 + 2  
        Operation 'Add' is called: 2 + 4  
        Operation 'Add' is called: 3 + 6  
        Operation 'Add' is called: 4 + 8  
    Press <ENTER> to complete test.  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="0a924-182">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0a924-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0a924-183">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="0a924-183">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0a924-184">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="0a924-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0a924-185">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0a924-185">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
