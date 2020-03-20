---
title: Aktywacja UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: c0b351adb0b45f42404e94c74bdcff7785c2d0ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143723"
---
# <a name="udp-activation"></a><span data-ttu-id="61165-102">Aktywacja UDP</span><span class="sxs-lookup"><span data-stu-id="61165-102">UDP Activation</span></span>
<span data-ttu-id="61165-103">Ten przykład jest oparty na [transport: próbka UDP.](../../../../docs/framework/wcf/samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="61165-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="61165-104">Rozszerza [transport: przykład UDP](../../../../docs/framework/wcf/samples/transport-udp.md) do obsługi aktywacji procesu przy użyciu usługi aktywacji procesu systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="61165-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="61165-105">Próbka składa się z trzech głównych elementów:</span><span class="sxs-lookup"><span data-stu-id="61165-105">The sample consists of three major pieces:</span></span>  
  
- <span data-ttu-id="61165-106">A UDP Protocol Activator, autonomiczny proces, który odbiera wiadomości UDP w imieniu aplikacji, które mają być aktywowane.</span><span class="sxs-lookup"><span data-stu-id="61165-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
- <span data-ttu-id="61165-107">Klient, który używa transportu niestandardowego UDP do wysyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="61165-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
- <span data-ttu-id="61165-108">Usługa (hostowana w procesie roboczym aktywowanym przez was), która odbiera wiadomości za pomocą transportu niestandardowego UDP.</span><span class="sxs-lookup"><span data-stu-id="61165-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="61165-109">Aktywator protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="61165-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="61165-110">Aktywator protokołu UDP jest pomostem między klientem WCF a usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="61165-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="61165-111">Zapewnia komunikację danych za pośrednictwem protokołu UDP w warstwie transportu.</span><span class="sxs-lookup"><span data-stu-id="61165-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="61165-112">Posiada dwie główne funkcje:</span><span class="sxs-lookup"><span data-stu-id="61165-112">It has two major functions:</span></span>  
  
- <span data-ttu-id="61165-113">Was Listener Adapter (LA), który współpracuje z WAS, aby aktywować procesy w odpowiedzi na przychodzące wiadomości.</span><span class="sxs-lookup"><span data-stu-id="61165-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
- <span data-ttu-id="61165-114">Odbiornik protokołu UDP, który akceptuje komunikaty UDP w imieniu aplikacji, które mają być aktywowane.</span><span class="sxs-lookup"><span data-stu-id="61165-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="61165-115">Aktywator musi być uruchomiony jako program autonomiczny na komputerze serwera.</span><span class="sxs-lookup"><span data-stu-id="61165-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="61165-116">Zwykle karty odbiornika WAS (takie jak NetTcpActivator i NetPipeActivator) są implementowane w długotrwałych usługach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="61165-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="61165-117">Jednak dla uproszczenia i przejrzystości w tym przykładzie implementuje aktywator protokołu jako autonomiczną aplikację.</span><span class="sxs-lookup"><span data-stu-id="61165-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="61165-118">Adapter odbiornika WAS</span><span class="sxs-lookup"><span data-stu-id="61165-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="61165-119">Adapter odbiornika WAS dla UDP jest `UdpListenerAdapter` zaimplementowana w klasie.</span><span class="sxs-lookup"><span data-stu-id="61165-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="61165-120">Jest to moduł, który współdziała z was do wykonywania aktywacji aplikacji dla protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="61165-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="61165-121">Osiąga się to poprzez wywołanie następujących interfejsów API usługi Webhost:</span><span class="sxs-lookup"><span data-stu-id="61165-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="61165-122">Po początkowym wywołaniu `WebhostRegisterProtocol`karta odbiornika `ApplicationCreated` odbiera wywołanie zwrotne z usługi WAS dla wszystkich aplikacji zarejestrowanych w aplikacjiHost.config (znajdującej się w %windir%\system32\inetsrv).</span><span class="sxs-lookup"><span data-stu-id="61165-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="61165-123">W tym przykładzie obsługujemy tylko aplikacje z protokołem UDP (z identyfikatorem protokołu jako "net.udp") włączoną.</span><span class="sxs-lookup"><span data-stu-id="61165-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="61165-124">Inne implementacje mogą obsługiwać to inaczej, jeśli takie implementacje reagują na dynamiczne zmiany konfiguracji aplikacji (na przykład przejście aplikacji z wyłączone do włączone).</span><span class="sxs-lookup"><span data-stu-id="61165-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="61165-125">Po odebraniu wywołania zwrotnego `ConfigManagerInitializationCompleted` oznacza, że usługa WAS zakończyła wszystkie powiadomienia dotyczące inicjowania protokołu.</span><span class="sxs-lookup"><span data-stu-id="61165-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="61165-126">W tej chwili karta odbiornika jest gotowa do przetwarzania żądań aktywacji.</span><span class="sxs-lookup"><span data-stu-id="61165-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="61165-127">Gdy nowe żądanie pojawia się po raz pierwszy dla `WebhostOpenListenerChannelInstance` aplikacji, karta odbiornika wywołuje do usługi WAS, która uruchamia proces roboczy, jeśli nie jest jeszcze uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="61165-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="61165-128">Następnie są ładowane programy obsługi protokołu i można uruchomić komunikację między kartą odbiornika a aplikacją wirtualną.</span><span class="sxs-lookup"><span data-stu-id="61165-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="61165-129">Karta odbiornika jest zarejestrowana w sekcji %SystemRoot%\System32\inetsrv\ApplicationHost.config `listenerAdapters` w sekcji <> w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="61165-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="61165-130">Odbiornik protokołu</span><span class="sxs-lookup"><span data-stu-id="61165-130">Protocol Listener</span></span>  
 <span data-ttu-id="61165-131">Odbiornik protokołu UDP jest modułem wewnątrz aktywatora protokołu, który nasłuchuje w punkcie końcowym UDP w imieniu aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="61165-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="61165-132">Jest on realizowany w `UdpSocketListener`klasie .</span><span class="sxs-lookup"><span data-stu-id="61165-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="61165-133">Punkt końcowy jest reprezentowany jako `IPEndpoint` dla których numer portu jest wyodrębniany z powiązania protokołu dla lokacji.</span><span class="sxs-lookup"><span data-stu-id="61165-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="61165-134">Usługa sterowania</span><span class="sxs-lookup"><span data-stu-id="61165-134">Control Service</span></span>  
 <span data-ttu-id="61165-135">W tym przykładzie używamy WCF do komunikowania się między aktywatorem a procesem roboczym WAS.</span><span class="sxs-lookup"><span data-stu-id="61165-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="61165-136">Usługa, która znajduje się w aktywatorze jest nazywany Control Service.</span><span class="sxs-lookup"><span data-stu-id="61165-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="61165-137">Programy obsługi protokołów</span><span class="sxs-lookup"><span data-stu-id="61165-137">Protocol Handlers</span></span>  
 <span data-ttu-id="61165-138">Po wywołaniu `WebhostOpenListenerChannelInstance`karty odbiornika menedżer procesów WAS uruchamia proces roboczy, jeśli nie został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="61165-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="61165-139">Menedżer aplikacji wewnątrz procesu roboczego następnie ładuje program obsługi protokołu procesu UDP (PPH) z żądaniem tego `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="61165-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="61165-140">PPH z kolei `IAdphManager`wywołuje .`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="61165-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="61165-141">, aby uruchomić program obsługi protokołu UDP AppDomain Protocol (ADPH).</span><span class="sxs-lookup"><span data-stu-id="61165-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="61165-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="61165-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="61165-143">Informacje są rejestrowane w witrynie Web.config w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="61165-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="61165-144">Specjalna konfiguracja dla tego przykładu</span><span class="sxs-lookup"><span data-stu-id="61165-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="61165-145">Ten przykład można zbudować i uruchomić tylko w systemach Windows Vista, Windows Server 2008 lub Windows 7.</span><span class="sxs-lookup"><span data-stu-id="61165-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="61165-146">Aby uruchomić próbkę, należy najpierw poprawnie skonfigurować wszystkie składniki.</span><span class="sxs-lookup"><span data-stu-id="61165-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="61165-147">Aby zainstalować próbkę, należy wykonać następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="61165-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="61165-148">Aby skonfigurować tę próbkę</span><span class="sxs-lookup"><span data-stu-id="61165-148">To set up this sample</span></span>  
  
1. <span data-ttu-id="61165-149">Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="61165-149">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="61165-150">Tworzenie projektu w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="61165-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="61165-151">Po kompilacji wykonuje również następujące operacje w fazie po kompilacji:</span><span class="sxs-lookup"><span data-stu-id="61165-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    - <span data-ttu-id="61165-152">Instaluje powiązanie UDP z witryną "Domyślna witryna sieci Web".</span><span class="sxs-lookup"><span data-stu-id="61165-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    - <span data-ttu-id="61165-153">Tworzy aplikację wirtualną "ServiceModelSamples", aby wskazać ścieżkę fizyczną: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="61165-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    - <span data-ttu-id="61165-154">Umożliwia również protokół "net.udp" dla tej wirtualnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="61165-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3. <span data-ttu-id="61165-155">Uruchom aplikację interfejsu użytkownika "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="61165-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="61165-156">Kliknij kartę **Ustawienia,** zaznacz następujące pola wyboru, a następnie kliknij pozycję **Zainstaluj,** aby je zainstalować:</span><span class="sxs-lookup"><span data-stu-id="61165-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    - <span data-ttu-id="61165-157">Adapter odbiornika UDP</span><span class="sxs-lookup"><span data-stu-id="61165-157">UDP Listener Adapter</span></span>  
  
    - <span data-ttu-id="61165-158">Programy obsługi protokołów UDP</span><span class="sxs-lookup"><span data-stu-id="61165-158">UDP Protocol Handlers</span></span>  
  
4. <span data-ttu-id="61165-159">Kliknij kartę **Aktywacja** aplikacji interfejsu użytkownika "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="61165-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="61165-160">Kliknij przycisk **Start,** aby uruchomić kartę odbiornika.</span><span class="sxs-lookup"><span data-stu-id="61165-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="61165-161">Teraz możesz przystąpić do uruchomienia programu.</span><span class="sxs-lookup"><span data-stu-id="61165-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="61165-162">Po zakończeniu pracy z tym przykładem należy uruchomić plik Cleanup.bat, aby usunąć powiązanie net.udp z "Domyślnej witryny sieci Web".</span><span class="sxs-lookup"><span data-stu-id="61165-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="61165-163">Przykładowe użycie</span><span class="sxs-lookup"><span data-stu-id="61165-163">Sample Usage</span></span>  
 <span data-ttu-id="61165-164">Po kompilacji, istnieją cztery różne pliki binarne generowane:</span><span class="sxs-lookup"><span data-stu-id="61165-164">After compilation, there are four different binaries generated:</span></span>  
  
- <span data-ttu-id="61165-165">Client.exe: Kod klienta.</span><span class="sxs-lookup"><span data-stu-id="61165-165">Client.exe: The client code.</span></span> <span data-ttu-id="61165-166">Plik App.config jest kompilowany do pliku konfiguracyjnego klienta Client.exe.config.</span><span class="sxs-lookup"><span data-stu-id="61165-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
- <span data-ttu-id="61165-167">UDPActivation.dll: biblioteka, która zawiera wszystkie główne implementacje UDP.</span><span class="sxs-lookup"><span data-stu-id="61165-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
- <span data-ttu-id="61165-168">Service.dll: Kod usługi.</span><span class="sxs-lookup"><span data-stu-id="61165-168">Service.dll: The service code.</span></span> <span data-ttu-id="61165-169">Jest to kopiowane do katalogu \bin wirtualnej aplikacji ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="61165-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="61165-170">Plik usługi to Service.svc, a plik konfiguracyjny to Web.config. Po kompilacji są one kopiowane do następującej lokalizacji: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="61165-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
- <span data-ttu-id="61165-171">WasNetActivator: program aktywatora UDP.</span><span class="sxs-lookup"><span data-stu-id="61165-171">WasNetActivator: The UDP activator program.</span></span>  
  
- <span data-ttu-id="61165-172">Upewnij się, że wszystkie wymagane elementy są prawidłowo zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="61165-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="61165-173">Poniższe kroki pokazują, jak uruchomić przykład:</span><span class="sxs-lookup"><span data-stu-id="61165-173">The following steps show how to run the sample:</span></span>  
  
1. <span data-ttu-id="61165-174">Upewnij się, że uruchomiono następujące usługi systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="61165-174">Ensure that the following Windows services have been started:</span></span>  
  
    - <span data-ttu-id="61165-175">Usługa aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="61165-175">Windows Process Activation Service (WAS).</span></span>  
  
    - <span data-ttu-id="61165-176">Internetowe usługi informacyjne (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="61165-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2. <span data-ttu-id="61165-177">Następnie uruchom aktywator, WasNetActivator.exe.</span><span class="sxs-lookup"><span data-stu-id="61165-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="61165-178">Na karcie **Aktywacja** na liście rozwijanej wybrano jedyny protokół **UDP.**</span><span class="sxs-lookup"><span data-stu-id="61165-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="61165-179">Kliknij przycisk **Start,** aby uruchomić aktywator.</span><span class="sxs-lookup"><span data-stu-id="61165-179">Click the **Start** button to start the activator.</span></span>  
  
3. <span data-ttu-id="61165-180">Po uruchomieniu aktywatora można uruchomić kod klienta, uruchamiając client.exe z okna polecenia.</span><span class="sxs-lookup"><span data-stu-id="61165-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="61165-181">Poniżej przedstawiono dane wyjściowe próbki:</span><span class="sxs-lookup"><span data-stu-id="61165-181">The following is the sample output:</span></span>  
  
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
> <span data-ttu-id="61165-182">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="61165-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="61165-183">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="61165-183">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="61165-184">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="61165-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="61165-185">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="61165-185">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
