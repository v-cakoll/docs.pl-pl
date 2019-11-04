---
title: Aktywacja UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 6e8d2f4428e85c71571021e2735f90e2e0a9d35a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424187"
---
# <a name="udp-activation"></a><span data-ttu-id="c73b2-102">Aktywacja UDP</span><span class="sxs-lookup"><span data-stu-id="c73b2-102">UDP Activation</span></span>
<span data-ttu-id="c73b2-103">Ten przykład jest oparty na [transportie: przykład UDP](../../../../docs/framework/wcf/samples/transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="c73b2-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="c73b2-104">Rozszerza [transport: przykład UDP](../../../../docs/framework/wcf/samples/transport-udp.md) w celu obsługi aktywacji procesu przy użyciu usługi aktywacji procesów systemu Windows (was).</span><span class="sxs-lookup"><span data-stu-id="c73b2-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="c73b2-105">Przykład składa się z trzech głównych elementów:</span><span class="sxs-lookup"><span data-stu-id="c73b2-105">The sample consists of three major pieces:</span></span>  
  
- <span data-ttu-id="c73b2-106">Aktywator protokołu UDP, autonomiczny proces odbierający komunikaty UDP w imieniu aplikacji, które mają zostać aktywowane.</span><span class="sxs-lookup"><span data-stu-id="c73b2-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
- <span data-ttu-id="c73b2-107">Klient korzystający z transportu niestandardowego UDP do wysyłania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c73b2-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
- <span data-ttu-id="c73b2-108">Usługa (hostowana w procesie roboczym aktywowana przez usługę WAS), która odbiera komunikaty za pośrednictwem transportu niestandardowego protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="c73b2-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="c73b2-109">Aktywator protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="c73b2-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="c73b2-110">Aktywator protokołu UDP jest mostkiem między klientem programu WCF a usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="c73b2-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="c73b2-111">Zapewnia ona komunikację z danymi za pomocą protokołu UDP w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="c73b2-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="c73b2-112">Ma dwie główne funkcje:</span><span class="sxs-lookup"><span data-stu-id="c73b2-112">It has two major functions:</span></span>  
  
- <span data-ttu-id="c73b2-113">Adapter odbiornika (LA), który współpracuje z programem, można aktywować procesy w odpowiedzi na komunikaty przychodzące.</span><span class="sxs-lookup"><span data-stu-id="c73b2-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
- <span data-ttu-id="c73b2-114">Odbiornik protokołu UDP, który akceptuje komunikaty UDP w imieniu aplikacji, które mają zostać aktywowane.</span><span class="sxs-lookup"><span data-stu-id="c73b2-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="c73b2-115">Aktywator musi być uruchomiony jako program autonomiczny na komputerze serwera.</span><span class="sxs-lookup"><span data-stu-id="c73b2-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="c73b2-116">Zazwyczaj były to karty odbiornika (takie jak NetTcpActivator i NetPipeActivator), które są implementowane w długotrwałych usługach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c73b2-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="c73b2-117">Jednak w przypadku uproszczenia i przejrzystości ten przykład implementuje aktywatora protokołu jako autonomiczną aplikację.</span><span class="sxs-lookup"><span data-stu-id="c73b2-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="c73b2-118">Adapter odbiornika</span><span class="sxs-lookup"><span data-stu-id="c73b2-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="c73b2-119">Adapter odbiornika dla UDP został zaimplementowany w klasie `UdpListenerAdapter`.</span><span class="sxs-lookup"><span data-stu-id="c73b2-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="c73b2-120">Jest to moduł, który współdziała z programem, aby przeprowadzić aktywację aplikacji dla protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="c73b2-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="c73b2-121">Jest to osiągane przez wywołanie następujących interfejsów API webhost:</span><span class="sxs-lookup"><span data-stu-id="c73b2-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="c73b2-122">Po pierwszym wywołaniu `WebhostRegisterProtocol`Adapter odbiornika odbiera wywołanie zwrotne `ApplicationCreated` od były przeznaczone dla wszystkich aplikacji zarejestrowanych w pliku applicationHost. config (znajdującym się w%windir%\system32\inetsrv).</span><span class="sxs-lookup"><span data-stu-id="c73b2-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="c73b2-123">W tym przykładzie obsługujemy tylko aplikacje z protokołem UDP (z identyfikatorem protokołu "net. UDP").</span><span class="sxs-lookup"><span data-stu-id="c73b2-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="c73b2-124">Inne implementacje mogą być obsługiwane inaczej, jeśli takie implementacje odpowiadają na dynamiczne zmiany konfiguracji aplikacji (np. przejście aplikacji z wyłączone na włączone).</span><span class="sxs-lookup"><span data-stu-id="c73b2-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="c73b2-125">Po odebraniu `ConfigManagerInitializationCompleted` wywołania zwrotnego wskazuje, że został zakończony wszystkie powiadomienia dotyczące inicjowania protokołu.</span><span class="sxs-lookup"><span data-stu-id="c73b2-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="c73b2-126">W tej chwili Adapter odbiornika jest gotowy do przetwarzania żądań aktywacji.</span><span class="sxs-lookup"><span data-stu-id="c73b2-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="c73b2-127">Gdy nowe żądanie jest uruchamiane po raz pierwszy dla aplikacji, Adapter odbiornika wywołuje `WebhostOpenListenerChannelInstance`, co uruchamia proces roboczy, jeśli nie został jeszcze uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="c73b2-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="c73b2-128">Następnie programy obsługi protokołów są ładowane, a komunikacja między kartą odbiornika i aplikacją wirtualną może zostać uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="c73b2-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="c73b2-129">Karta odbiornika jest zarejestrowana w%SystemRoot%\System32\inetsrv\ApplicationHost.config w sekcji <`listenerAdapters`> w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c73b2-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="c73b2-130">Odbiornik protokołu</span><span class="sxs-lookup"><span data-stu-id="c73b2-130">Protocol Listener</span></span>  
 <span data-ttu-id="c73b2-131">Odbiornik protokołu UDP jest modułem w ramach aktywatora protokołu, który nasłuchuje w punkcie końcowym UDP w imieniu aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="c73b2-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="c73b2-132">Jest zaimplementowana w klasie `UdpSocketListener`.</span><span class="sxs-lookup"><span data-stu-id="c73b2-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="c73b2-133">Punkt końcowy jest reprezentowany jako `IPEndpoint`, dla którego jest wyodrębniany numer portu z powiązania protokołu dla lokacji.</span><span class="sxs-lookup"><span data-stu-id="c73b2-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="c73b2-134">Usługa sterowania</span><span class="sxs-lookup"><span data-stu-id="c73b2-134">Control Service</span></span>  
 <span data-ttu-id="c73b2-135">W tym przykładzie używamy funkcji WCF do komunikacji między aktywatorem a procesem roboczym.</span><span class="sxs-lookup"><span data-stu-id="c73b2-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="c73b2-136">Usługa, która znajduje się w aktywatora, nazywa się usługą kontroli.</span><span class="sxs-lookup"><span data-stu-id="c73b2-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="c73b2-137">Programy obsługi protokołów</span><span class="sxs-lookup"><span data-stu-id="c73b2-137">Protocol Handlers</span></span>  
 <span data-ttu-id="c73b2-138">Gdy Adapter odbiornika wywoła `WebhostOpenListenerChannelInstance`, Menedżer przetworzenia przetwarza proces roboczy, jeśli nie został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="c73b2-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="c73b2-139">Menedżer aplikacji wewnątrz procesu roboczego ładuje program obsługi protokołu UDP (PPH) żądania dla tego `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="c73b2-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="c73b2-140">PPH w programie włącza wywołania `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="c73b2-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="c73b2-141">Aby uruchomić procedurę obsługi protokołu UDP AppDomain (ADPH).</span><span class="sxs-lookup"><span data-stu-id="c73b2-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="c73b2-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="c73b2-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="c73b2-143">Informacje są rejestrowane w pliku Web. config w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c73b2-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="c73b2-144">Specjalna instalacja dla tego przykładu</span><span class="sxs-lookup"><span data-stu-id="c73b2-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="c73b2-145">Ten przykład może być zbudowany i uruchamiany tylko w systemie Windows Vista, Windows Server 2008 lub Windows 7.</span><span class="sxs-lookup"><span data-stu-id="c73b2-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="c73b2-146">Aby uruchomić przykład, należy najpierw pobrać wszystkie składniki skonfigurowane prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="c73b2-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="c73b2-147">Wykonaj poniższe kroki, aby zainstalować przykład.</span><span class="sxs-lookup"><span data-stu-id="c73b2-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="c73b2-148">Aby skonfigurować ten przykład</span><span class="sxs-lookup"><span data-stu-id="c73b2-148">To set up this sample</span></span>  
  
1. <span data-ttu-id="c73b2-149">Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="c73b2-149">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="c73b2-150">Skompiluj projekt w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="c73b2-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="c73b2-151">Po kompilacji wykonuje także następujące operacje w fazie po kompilacji:</span><span class="sxs-lookup"><span data-stu-id="c73b2-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    - <span data-ttu-id="c73b2-152">Instaluje powiązanie UDP z witryną "Default Web Site".</span><span class="sxs-lookup"><span data-stu-id="c73b2-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    - <span data-ttu-id="c73b2-153">Tworzy aplikację wirtualną "ServiceModelSamples" w celu wskazywania ścieżki fizycznej: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="c73b2-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    - <span data-ttu-id="c73b2-154">Włącza również protokół "net. UDP" dla tej aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="c73b2-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3. <span data-ttu-id="c73b2-155">Uruchom aplikację interfejsu użytkownika "WasNetActivator. exe".</span><span class="sxs-lookup"><span data-stu-id="c73b2-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="c73b2-156">Kliknij kartę **Instalator** , zaznacz następujące pola wyboru, a następnie kliknij przycisk **Instaluj** , aby je zainstalować:</span><span class="sxs-lookup"><span data-stu-id="c73b2-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    - <span data-ttu-id="c73b2-157">Adapter odbiornika UDP</span><span class="sxs-lookup"><span data-stu-id="c73b2-157">UDP Listener Adapter</span></span>  
  
    - <span data-ttu-id="c73b2-158">Procedury obsługi protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="c73b2-158">UDP Protocol Handlers</span></span>  
  
4. <span data-ttu-id="c73b2-159">Kliknij kartę **Aktywacja** aplikacji interfejsu użytkownika "WasNetActivator. exe".</span><span class="sxs-lookup"><span data-stu-id="c73b2-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="c73b2-160">Kliknij przycisk **Uruchom** , aby uruchomić Adapter odbiornika.</span><span class="sxs-lookup"><span data-stu-id="c73b2-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="c73b2-161">Teraz można przystąpić do uruchamiania programu.</span><span class="sxs-lookup"><span data-stu-id="c73b2-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c73b2-162">Po zakończeniu pracy z tym przykładem należy uruchomić polecenie Oczyść. bat, aby usunąć powiązanie net. UDP z "domyślnej witryny sieci Web".</span><span class="sxs-lookup"><span data-stu-id="c73b2-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="c73b2-163">Przykładowe użycie</span><span class="sxs-lookup"><span data-stu-id="c73b2-163">Sample Usage</span></span>  
 <span data-ttu-id="c73b2-164">Po kompilacji są generowane cztery różne pliki binarne:</span><span class="sxs-lookup"><span data-stu-id="c73b2-164">After compilation, there are four different binaries generated:</span></span>  
  
- <span data-ttu-id="c73b2-165">Client. exe: kod klienta.</span><span class="sxs-lookup"><span data-stu-id="c73b2-165">Client.exe: The client code.</span></span> <span data-ttu-id="c73b2-166">Plik App. config jest kompilowany do pliku konfiguracji klienta Client. exe. config.</span><span class="sxs-lookup"><span data-stu-id="c73b2-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
- <span data-ttu-id="c73b2-167">UDPActivation. dll: Biblioteka, która zawiera wszystkie główne implementacje protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="c73b2-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
- <span data-ttu-id="c73b2-168">Service. dll: kod usługi.</span><span class="sxs-lookup"><span data-stu-id="c73b2-168">Service.dll: The service code.</span></span> <span data-ttu-id="c73b2-169">Jest on kopiowany do katalogu \Bin aplikacji wirtualnej ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="c73b2-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="c73b2-170">Plik usługi to Service. svc, a plik konfiguracji to Web. config. Po kompilacji są one kopiowane do następującej lokalizacji:%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="c73b2-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
- <span data-ttu-id="c73b2-171">WasNetActivator: program aktywatora UDP.</span><span class="sxs-lookup"><span data-stu-id="c73b2-171">WasNetActivator: The UDP activator program.</span></span>  
  
- <span data-ttu-id="c73b2-172">Upewnij się, że wszystkie wymagane elementy są poprawnie zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="c73b2-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="c73b2-173">Poniższe kroki pokazują, jak uruchomić przykład:</span><span class="sxs-lookup"><span data-stu-id="c73b2-173">The following steps show how to run the sample:</span></span>  
  
1. <span data-ttu-id="c73b2-174">Upewnij się, że następujące usługi systemu Windows zostały uruchomione:</span><span class="sxs-lookup"><span data-stu-id="c73b2-174">Ensure that the following Windows services have been started:</span></span>  
  
    - <span data-ttu-id="c73b2-175">Usługa aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="c73b2-175">Windows Process Activation Service (WAS).</span></span>  
  
    - <span data-ttu-id="c73b2-176">Internet Information Services (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="c73b2-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2. <span data-ttu-id="c73b2-177">Następnie uruchom aktywatora, WasNetActivator. exe.</span><span class="sxs-lookup"><span data-stu-id="c73b2-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="c73b2-178">Na karcie **Aktywacja** na liście rozwijanej jest wybierany tylko protokół **UDP**.</span><span class="sxs-lookup"><span data-stu-id="c73b2-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="c73b2-179">Kliknij przycisk **Uruchom** , aby uruchomić aktywatora.</span><span class="sxs-lookup"><span data-stu-id="c73b2-179">Click the **Start** button to start the activator.</span></span>  
  
3. <span data-ttu-id="c73b2-180">Po uruchomieniu aktywatora można uruchomić kod klienta, uruchamiając program Client. exe z okna polecenia.</span><span class="sxs-lookup"><span data-stu-id="c73b2-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="c73b2-181">Oto przykładowe dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="c73b2-181">The following is the sample output:</span></span>  
  
    ```console  
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
> <span data-ttu-id="c73b2-182">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c73b2-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c73b2-183">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="c73b2-183">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="c73b2-184">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c73b2-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c73b2-185">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c73b2-185">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
