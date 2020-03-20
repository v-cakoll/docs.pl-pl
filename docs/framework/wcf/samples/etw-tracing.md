---
title: Śledzenie za pomocą funkcji ETW
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 07379a464e6635a3de10c08647dbc769a5885e4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183704"
---
# <a name="etw-tracing"></a><span data-ttu-id="e4b0f-102">Śledzenie za pomocą funkcji ETW</span><span class="sxs-lookup"><span data-stu-id="e4b0f-102">ETW Tracing</span></span>
<span data-ttu-id="e4b0f-103">W tym przykładzie pokazano, jak zaimplementować end-to-end (E2E) śledzenia `ETWTraceListener` przy użyciu śledzenia zdarzeń dla systemu Windows (ETW) i który jest dostarczany z tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-103">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="e4b0f-104">Próbka jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i zawiera śledzenie ETW.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4b0f-105">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e4b0f-106">W tym przykładzie przyjęto założenie, że użytkownik jest zaznajomiony z [śledzeniem i rejestrowaniem wiadomości.](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)</span><span class="sxs-lookup"><span data-stu-id="e4b0f-106">This sample assumes that you are familiar with [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="e4b0f-107">Każde źródło śledzenia <xref:System.Diagnostics> w modelu śledzenia może mieć wiele odbiorników śledzenia, które określają, gdzie i jak dane są śledzone.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-107">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="e4b0f-108">Typ odbiornika definiuje format, w którym rejestrowane są dane śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-108">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="e4b0f-109">Poniższy przykład kodu pokazuje, jak dodać odbiornika do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-109">The following code sample shows how to add the listener to configuration.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel"
             switchValue="Verbose,ActivityTracing"  
             propagateActivity="true">  
            <listeners>  
                <add type=  
                   "System.Diagnostics.DefaultTraceListener"  
                   name="Default">  
                   <filter type="" />  
                </add>  
                <add name="ETW">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
        <add type=  
            "Microsoft.ServiceModel.Samples.EtwTraceListener, ETWTraceListener"  
            name="ETW" traceOutputOptions="Timestamp">  
            <filter type="" />  
       </add>  
    </sharedListeners>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="e4b0f-110">Przed użyciem tego odbiornika należy uruchomić sesję śledzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-110">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="e4b0f-111">Tę sesję można uruchomić przy użyciu pliku Logman.exe lub Tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-111">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="e4b0f-112">Plik SetupETW.bat jest dołączony do tego przykładu, dzięki czemu można skonfigurować etw śledzenia sesji wraz z plikiem CleanupETW.bat do zamknięcia sesji i ukończenia pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-112">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4b0f-113">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="e4b0f-114">Aby uzyskać więcej informacji na temat tych narzędzi, zobacz<https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="e4b0f-114">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="e4b0f-115">Podczas korzystania z ETWTraceListener, ślady są rejestrowane w binarnych plikach .etl.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-115">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="e4b0f-116">Po włączeniu śledzenia ServiceModel wszystkie wygenerowane ślady są wyświetlane w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-116">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="e4b0f-117">Narzędzie [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) umożliwia przeglądanie plików dziennika .etl i .svclog.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-117">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="e4b0f-118">Przeglądarka tworzy widok end-to-end systemu, który umożliwia śledzenie wiadomości ze źródła do miejsca docelowego i punktu zużycia.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-118">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="e4b0f-119">Odbiornik śledzenia ETW obsługuje rejestrowanie cykliczne.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-119">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="e4b0f-120">Aby włączyć tę funkcję, przejdź do `cmd` ekranu **Start**, **Uruchom** i wpisz, aby uruchomić konsolę poleceń.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-120">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="e4b0f-121">W poniższym poleceniu zastąp `<logfilename>` parametr nazwą pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-121">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="e4b0f-122">`-f` Przełączniki `-max` i są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-122">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="e4b0f-123">Określają one binarny format kołowy i maksymalny rozmiar dziennika odpowiednio 1000MB.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-123">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="e4b0f-124">Przełącznik `-p` jest używany do określenia dostawcy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-124">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="e4b0f-125">W naszym `"{411a0819-c24b-428c-83e2-26b41091702e}"` przykładzie jest identyfikator GUID dla "XML ETW sample provider".</span><span class="sxs-lookup"><span data-stu-id="e4b0f-125">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="e4b0f-126">Aby rozpocząć sesję, wpisz następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-126">To start the session, type in the following command.</span></span>  
  
```console  
logman start Wcf  
```  
  
 <span data-ttu-id="e4b0f-127">Po zakończeniu rejestrowania można zatrzymać sesję za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-127">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```console  
logman stop Wcf  
```  
  
 <span data-ttu-id="e4b0f-128">Ten proces generuje binarne dzienniki cykliczne, które można przetwarzać za pomocą wybranego narzędzia, w tym [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) lub Tracerpt.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-128">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="e4b0f-129">Można również przejrzeć próbkę [śledzenia kołowego, aby](../../../../docs/framework/wcf/samples/circular-tracing.md) uzyskać więcej informacji na temat alternatywnego odbiornika do wykonywania rejestrowania cyklicznego.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-129">You can also review the [Circular Tracing](../../../../docs/framework/wcf/samples/circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e4b0f-130">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="e4b0f-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e4b0f-131">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e4b0f-131">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e4b0f-132">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e4b0f-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e4b0f-133">Aby użyć poleceń RegisterProvider.bat, SetupETW.bat i CleanupETW.bat, należy uruchomić je pod lokalnym kontem administratora.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-133">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="e4b0f-134">Jeśli używasz systemu Windows Vista lub nowszego, należy również uruchomić wiersz polecenia z podwyższonymi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-134">If you are using Windows Vista or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="e4b0f-135">W tym celu kliknij prawym przyciskiem myszy ikonę wiersza polecenia, a następnie kliknij polecenie **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-135">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="e4b0f-136">Przed uruchomieniem próbki uruchom registerprovider.bat na kliencie i serwerze.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-136">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="e4b0f-137">Spowoduje to skonfigurowanie wynikowego pliku ETWTracingSampleLog.etl w celu wygenerowania śladów, które mogą być odczytywane przez przeglądarkę śledzenia usług.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-137">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="e4b0f-138">Ten plik można znaleźć w folderze C:\logs.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-138">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="e4b0f-139">Jeśli ten folder nie istnieje, musi zostać utworzony lub nie są generowane żadne ślady.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-139">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="e4b0f-140">Następnie uruchom plik SetupETW.bat na komputerach klienckich i serwerowych, aby rozpocząć sesję śledzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-140">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="e4b0f-141">Plik SetupETW.bat można znaleźć w folderze CS\Client.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-141">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="e4b0f-142">Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e4b0f-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="e4b0f-143">Po zakończeniu próbkowania uruchom cleanupetw.bat, aby zakończyć tworzenie pliku ETWTracingSampleLog.etl.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-143">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="e4b0f-144">Otwórz plik ETWTracingSampleLog.etl z poziomu przeglądarki śledzenia usług.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-144">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="e4b0f-145">Zostanie wyświetlony monit o zapisanie pliku w formacie binarnym jako pliku .svclog.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-145">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="e4b0f-146">Otwórz nowo utworzony plik .svclog z poziomu przeglądarki śledzenia usług, aby wyświetlić ślady ETW i ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-146">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e4b0f-147">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-147">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e4b0f-148">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-148">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e4b0f-149">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e4b0f-150">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e4b0f-150">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="e4b0f-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4b0f-151">See also</span></span>

- <span data-ttu-id="e4b0f-152">[Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e4b0f-152">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
