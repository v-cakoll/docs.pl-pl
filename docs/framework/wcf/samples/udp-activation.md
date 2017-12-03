---
title: Aktywacja UDP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 32c452042ffee0a09143042900d24b7429234bec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="udp-activation"></a><span data-ttu-id="712c8-102">Aktywacja UDP</span><span class="sxs-lookup"><span data-stu-id="712c8-102">UDP Activation</span></span>
<span data-ttu-id="712c8-103">Ten przykład jest oparty na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="712c8-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="712c8-104">Rozszerza [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki do obsługi aktywacji procesu przy użyciu usługi aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="712c8-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="712c8-105">Przykład obejmuje trzy główne:</span><span class="sxs-lookup"><span data-stu-id="712c8-105">The sample consists of three major pieces:</span></span>  
  
-   <span data-ttu-id="712c8-106">UDP protokołu aktywatora, proces autonomiczny, który odbiera komunikaty UDP w imieniu aplikacji, które mają być aktywowany.</span><span class="sxs-lookup"><span data-stu-id="712c8-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
-   <span data-ttu-id="712c8-107">Klient, który używa niestandardowych transportu UDP do wysyłania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="712c8-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
-   <span data-ttu-id="712c8-108">Usługa (obsługiwanych przez proces roboczy aktywowany przez WAS), która odbiera komunikaty za pomocą niestandardowych transportu UDP.</span><span class="sxs-lookup"><span data-stu-id="712c8-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="712c8-109">Aktywator protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="712c8-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="712c8-110">Aktywator protokół UDP jest mostka między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="712c8-110">The UDP Protocol Activator is a bridge between the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="712c8-111">Zapewnia komunikację danych za pośrednictwem protokołu UDP w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="712c8-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="712c8-112">Składa się z dwóch głównych funkcji:</span><span class="sxs-lookup"><span data-stu-id="712c8-112">It has two major functions:</span></span>  
  
-   <span data-ttu-id="712c8-113">ZOSTAŁ odbiornika karty (LA), który współpracuje z WAS do aktywowania procesów w odpowiedzi na wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="712c8-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
-   <span data-ttu-id="712c8-114">Odbiornika protokołu UDP, który akceptuje wiadomości UDP w imieniu aplikacji, które mają być aktywowany.</span><span class="sxs-lookup"><span data-stu-id="712c8-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="712c8-115">Aktywator musi działać jako autonomiczny program na komputerze z serwerem.</span><span class="sxs-lookup"><span data-stu-id="712c8-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="712c8-116">Zwykle WAS odbiornika kart (takie jak usługi NetTcpActivator i NetPipeActivator) zostały wdrożone w długim usług systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="712c8-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="712c8-117">Jednak dla uproszczenia i przejrzystości, w tym przykładzie implementuje protokół aktywatora jako aplikacja autonomiczna.</span><span class="sxs-lookup"><span data-stu-id="712c8-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="712c8-118">Adapter odbiornika zostało</span><span class="sxs-lookup"><span data-stu-id="712c8-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="712c8-119">Adapter odbiornika zostało UDP jest zaimplementowana w `UdpListenerAdapter` klasy.</span><span class="sxs-lookup"><span data-stu-id="712c8-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="712c8-120">Jest moduł, który współdziała z WAS do wykonywania aktywacji aplikacji dla protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="712c8-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="712c8-121">Jest to osiągane przez wywołanie metody Webhost API:</span><span class="sxs-lookup"><span data-stu-id="712c8-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="712c8-122">Po wywołaniu metody początkowo `WebhostRegisterProtocol`, adapter odbiornika odbiera wywołania zwrotnego `ApplicationCreated` z WAS dla wszystkich aplikacji w zarejestrowany w pliku applicationHost.config (znajdujący się w % windir%\system32\inetsrv).</span><span class="sxs-lookup"><span data-stu-id="712c8-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="712c8-123">W tym przykładzie mamy tylko obsługi aplikacji przy użyciu protokołu UDP (o identyfikatorze protokołu jako "net.udp") włączone.</span><span class="sxs-lookup"><span data-stu-id="712c8-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="712c8-124">Implementacje mogą obsługiwać to inaczej, jeśli takie implementacje reagowania na zmiany konfiguracji dynamicznej dla aplikacji (na przykład aplikacji przejście wyłączonego na włączony).</span><span class="sxs-lookup"><span data-stu-id="712c8-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="712c8-125">Podczas wywołania zwrotnego `ConfigManagerInitializationCompleted` zostanie odebrana, oznacza to, że WAS zakończył wszystkie powiadomienia do inicjowania protokołu.</span><span class="sxs-lookup"><span data-stu-id="712c8-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="712c8-126">W tej chwili adapter odbiornika jest gotowy do przetwarzania żądań aktywacji.</span><span class="sxs-lookup"><span data-stu-id="712c8-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="712c8-127">Gdy nowe żądanie w aplikacji po raz pierwszy, wywołuje adapter odbiornika `WebhostOpenListenerChannelInstance` do WAS, który rozpoczyna się proces roboczy, jeśli nie jest jeszcze uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="712c8-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="712c8-128">Następnie obsług protokołu są ładowane i umożliwić komunikację między adapter odbiornika i aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="712c8-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="712c8-129">Adapter odbiornika jest zarejestrowany w %SystemRoot%\System32\inetsrv\ApplicationHost.config w <`listenerAdapters`> sekcji jako następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="712c8-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="712c8-130">Protokół odbiornika</span><span class="sxs-lookup"><span data-stu-id="712c8-130">Protocol Listener</span></span>  
 <span data-ttu-id="712c8-131">Protokół UDP odbiornika jest modułem wewnątrz aktywatora protokołu, która nasłuchuje na punkt końcowy protokołu UDP w imieniu aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="712c8-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="712c8-132">Jest zaimplementowana w klasie `UdpSocketListener`.</span><span class="sxs-lookup"><span data-stu-id="712c8-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="712c8-133">Punkt końcowy jest reprezentowany jako `IPEndpoint` dla którego numer portu jest wyodrębniana z powiązania protokołu dla tej lokacji.</span><span class="sxs-lookup"><span data-stu-id="712c8-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="712c8-134">Sterowanie</span><span class="sxs-lookup"><span data-stu-id="712c8-134">Control Service</span></span>  
 <span data-ttu-id="712c8-135">W tym przykładzie używamy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do komunikacji między aktywatora i proces roboczy WAS.</span><span class="sxs-lookup"><span data-stu-id="712c8-135">In this sample, we use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="712c8-136">Usługa, która znajduje się w aktywatora nosi nazwę usługi kontroli.</span><span class="sxs-lookup"><span data-stu-id="712c8-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="712c8-137">Programy obsługi protokołu</span><span class="sxs-lookup"><span data-stu-id="712c8-137">Protocol Handlers</span></span>  
 <span data-ttu-id="712c8-138">Po wywołania adapter odbiornika `WebhostOpenListenerChannelInstance`, Menedżer procesu WAS uruchamia proces roboczy, jeśli nie jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="712c8-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="712c8-139">Menedżer aplikacji wewnątrz proces roboczy ładuje obsługi protokołu procesu (PPH) UDP, z żądaniem w tym `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="712c8-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="712c8-140">PPH w wywołaniach włącza `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="712c8-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="712c8-141">Aby uruchomić program obsługi protokołu domeny aplikacji UDP (ADPH).</span><span class="sxs-lookup"><span data-stu-id="712c8-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="712c8-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="712c8-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="712c8-143">Informacje jest zarejestrowany w pliku Web.config:</span><span class="sxs-lookup"><span data-stu-id="712c8-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="712c8-144">Specjalnych ustawień dla tego przykładu</span><span class="sxs-lookup"><span data-stu-id="712c8-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="712c8-145">W tym przykładzie można tylko wbudowane i uruchomić w systemie Windows Vista, Windows Server 2008 lub Windows 7.</span><span class="sxs-lookup"><span data-stu-id="712c8-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="712c8-146">Aby uruchomić próbki, należy najpierw pobrać wszystkie składniki są nieprawidłowo skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="712c8-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="712c8-147">Wykonaj następujące kroki, aby zainstalować przykład.</span><span class="sxs-lookup"><span data-stu-id="712c8-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="712c8-148">Aby skonfigurować ten przykład</span><span class="sxs-lookup"><span data-stu-id="712c8-148">To set up this sample</span></span>  
  
1.  <span data-ttu-id="712c8-149">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="712c8-149">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="712c8-150">Skompiluj projekt w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="712c8-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="712c8-151">Po kompilacji również wykonuje następujące operacje w fazie mające miejsce po kompilacji:</span><span class="sxs-lookup"><span data-stu-id="712c8-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    -   <span data-ttu-id="712c8-152">Instaluje powiązania protokołu UDP do witryny "Default Web Site".</span><span class="sxs-lookup"><span data-stu-id="712c8-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    -   <span data-ttu-id="712c8-153">Tworzy aplikację wirtualną "ServiceModelSamples" wskaż ścieżkę fizyczną: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="712c8-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    -   <span data-ttu-id="712c8-154">Umożliwia również protokół "net.udp" dla tej aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="712c8-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3.  <span data-ttu-id="712c8-155">Uruchom aplikację interfejsu użytkownika "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="712c8-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="712c8-156">Kliknij przycisk **Instalator** karcie, sprawdź poniższe pola wyboru, a następnie kliknij przycisk **zainstalować** ich instalowania:</span><span class="sxs-lookup"><span data-stu-id="712c8-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    -   <span data-ttu-id="712c8-157">Adapter odbiornika protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="712c8-157">UDP Listener Adapter</span></span>  
  
    -   <span data-ttu-id="712c8-158">Programy obsługi protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="712c8-158">UDP Protocol Handlers</span></span>  
  
4.  <span data-ttu-id="712c8-159">Kliknij przycisk **aktywacji** na karcie aplikacja interfejsu użytkownika "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="712c8-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="712c8-160">Kliknij przycisk **Start** przycisk, aby uruchomić adapter odbiornika.</span><span class="sxs-lookup"><span data-stu-id="712c8-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="712c8-161">Teraz można przystąpić do uruchomienia programu.</span><span class="sxs-lookup"><span data-stu-id="712c8-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="712c8-162">Po zakończeniu tej próbki, należy uruchomić Cleanup.bat usunąć powiązania net.udp z "Default Web Site".</span><span class="sxs-lookup"><span data-stu-id="712c8-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="712c8-163">Przykładowe zastosowanie</span><span class="sxs-lookup"><span data-stu-id="712c8-163">Sample Usage</span></span>  
 <span data-ttu-id="712c8-164">Po kompilacji istnieją cztery różne pliki binarne wygenerowane:</span><span class="sxs-lookup"><span data-stu-id="712c8-164">After compilation, there are four different binaries generated:</span></span>  
  
-   <span data-ttu-id="712c8-165">Client.exe: Kod klienta.</span><span class="sxs-lookup"><span data-stu-id="712c8-165">Client.exe: The client code.</span></span> <span data-ttu-id="712c8-166">App.config jest skompilowany w pliku konfiguracji klienta Client.exe.config.</span><span class="sxs-lookup"><span data-stu-id="712c8-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
-   <span data-ttu-id="712c8-167">UDPActivation.dll: Biblioteka, która zawiera wszystkie główne implementacje protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="712c8-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
-   <span data-ttu-id="712c8-168">Service.dll: Kodzie usługi.</span><span class="sxs-lookup"><span data-stu-id="712c8-168">Service.dll: The service code.</span></span> <span data-ttu-id="712c8-169">To jest kopiowana do katalogu \bin ServiceModelSamples aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="712c8-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="712c8-170">Plik usługi jest Service.svc i plik konfiguracji jest pliku Web.config. Po kompilacji, są kopiowane do następującej lokalizacji: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="712c8-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
-   <span data-ttu-id="712c8-171">WasNetActivator: UDP aktywatora program.</span><span class="sxs-lookup"><span data-stu-id="712c8-171">WasNetActivator: The UDP activator program.</span></span>  
  
-   <span data-ttu-id="712c8-172">Upewnij się, że wszystkie wymagane elementy zostały zainstalowane poprawnie.</span><span class="sxs-lookup"><span data-stu-id="712c8-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="712c8-173">Poniższe kroki przedstawiają sposób uruchamiania próbki:</span><span class="sxs-lookup"><span data-stu-id="712c8-173">The following steps show how to run the sample:</span></span>  
  
1.  <span data-ttu-id="712c8-174">Upewnij się, że zostały uruchomione następujące usługi systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="712c8-174">Ensure that the following Windows services have been started:</span></span>  
  
    -   <span data-ttu-id="712c8-175">Usługa aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="712c8-175">Windows Process Activation Service (WAS).</span></span>  
  
    -   <span data-ttu-id="712c8-176">Internetowe usługi informacyjne (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="712c8-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2.  <span data-ttu-id="712c8-177">Następnie uruchom aktywatora WasNetActivator.exe.</span><span class="sxs-lookup"><span data-stu-id="712c8-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="712c8-178">W obszarze **aktywacji** kartę, jedynym protokołem **UDP**, jest zaznaczona na liście rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="712c8-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="712c8-179">Kliknij przycisk **Start** przycisk, aby uruchomić aktywatora.</span><span class="sxs-lookup"><span data-stu-id="712c8-179">Click the **Start** button to start the activator.</span></span>  
  
3.  <span data-ttu-id="712c8-180">Po rozpoczęciu aktywatora kod klienta można uruchomić, uruchamiając Client.exe z okna poleceń.</span><span class="sxs-lookup"><span data-stu-id="712c8-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="712c8-181">Oto przykładowe dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="712c8-181">The following is the sample output:</span></span>  
  
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
>  <span data-ttu-id="712c8-182">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="712c8-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="712c8-183">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="712c8-183">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="712c8-184">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="712c8-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="712c8-185">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="712c8-185">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
## <a name="see-also"></a><span data-ttu-id="712c8-186">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="712c8-186">See Also</span></span>
