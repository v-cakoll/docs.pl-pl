---
title: Śledzenie za pomocą funkcji ETW
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 0bdbf6699a0cfa3dce58abda4c989fb25d764459
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600566"
---
# <a name="etw-tracing"></a><span data-ttu-id="d1367-102">Śledzenie za pomocą funkcji ETW</span><span class="sxs-lookup"><span data-stu-id="d1367-102">ETW Tracing</span></span>
<span data-ttu-id="d1367-103">W tym przykładzie pokazano, jak zaimplementować śledzenie kompleksowego (E2E) przy użyciu funkcji śledzenia zdarzeń systemu Windows (ETW) i `ETWTraceListener` dostarczonej z tym przykładem.</span><span class="sxs-lookup"><span data-stu-id="d1367-103">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="d1367-104">Przykład jest oparty na [wprowadzenie](getting-started-sample.md) i zawiera śledzenie ETW.</span><span class="sxs-lookup"><span data-stu-id="d1367-104">The sample is based on the [Getting Started](getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1367-105">Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d1367-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d1367-106">W tym przykładzie założono, że wiesz już, [jak śledzenie i rejestrowanie komunikatów](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="d1367-106">This sample assumes that you are familiar with [Tracing and Message Logging](tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="d1367-107">Każde źródło śledzenia w <xref:System.Diagnostics> modelu śledzenia może mieć wiele detektorów śledzenia, które określają miejsce i sposób, w jaki dane są śledzone.</span><span class="sxs-lookup"><span data-stu-id="d1367-107">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="d1367-108">Typ odbiornika definiuje format, w którym rejestrowane są dane śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d1367-108">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="d1367-109">Poniższy przykład kodu pokazuje, jak dodać odbiornik do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d1367-109">The following code sample shows how to add the listener to configuration.</span></span>  
  
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
  
 <span data-ttu-id="d1367-110">Przed użyciem tego odbiornika należy uruchomić sesję śledzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="d1367-110">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="d1367-111">Tę sesję można uruchomić przy użyciu narzędzia Logman. exe lub tracelog. exe.</span><span class="sxs-lookup"><span data-stu-id="d1367-111">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="d1367-112">Plik SetupETW. bat jest dołączony do tego przykładu, aby można było skonfigurować sesję śledzenia ETW wraz z plikiem CleanupETW. bat do zamykania sesji i wypełniania pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="d1367-112">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1367-113">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d1367-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="d1367-114">Aby uzyskać więcej informacji na temat tych narzędzi, zobacz.<https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="d1367-114">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="d1367-115">W przypadku korzystania z ETWTraceListener, ślady są rejestrowane w binarnych plikach. etl.</span><span class="sxs-lookup"><span data-stu-id="d1367-115">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="d1367-116">Śledzenie ServiceModel jest włączone, wszystkie wygenerowane ślady pojawiają się w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="d1367-116">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="d1367-117">Użyj [narzędzia Podgląd śledzenia usług (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) do wyświetlania plików dziennika. ETL i. svclog.</span><span class="sxs-lookup"><span data-stu-id="d1367-117">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="d1367-118">Przeglądarka tworzy kompleksowy widok systemu, który umożliwia śledzenie komunikatu z jego źródła do jego lokalizacji docelowej i punktu zużycia.</span><span class="sxs-lookup"><span data-stu-id="d1367-118">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="d1367-119">Odbiornik śledzenia ETW obsługuje rejestrowanie cykliczne.</span><span class="sxs-lookup"><span data-stu-id="d1367-119">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="d1367-120">Aby włączyć tę funkcję, przejdź do **menu Start**, **Uruchom** polecenie i wpisz, `cmd` Aby uruchomić konsolę poleceń.</span><span class="sxs-lookup"><span data-stu-id="d1367-120">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="d1367-121">W poniższym poleceniu Zastąp `<logfilename>` parametr nazwą pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="d1367-121">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="d1367-122">`-f`Przełączniki i `-max` są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d1367-122">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="d1367-123">Określają one odpowiednio binarny format cykliczny i maksymalny rozmiar dziennika 1000 MB.</span><span class="sxs-lookup"><span data-stu-id="d1367-123">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="d1367-124">`-p`Przełącznik służy do określania dostawcy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d1367-124">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="d1367-125">W naszym przykładzie `"{411a0819-c24b-428c-83e2-26b41091702e}"` jest identyfikator GUID dla "przykładowego dostawcy funkcji ETW języka XML".</span><span class="sxs-lookup"><span data-stu-id="d1367-125">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="d1367-126">Aby rozpocząć sesję, wpisz następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="d1367-126">To start the session, type in the following command.</span></span>  
  
```console  
logman start Wcf  
```  
  
 <span data-ttu-id="d1367-127">Po zakończeniu rejestrowania możesz zatrzymać sesję przy użyciu poniższego polecenia.</span><span class="sxs-lookup"><span data-stu-id="d1367-127">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```console  
logman stop Wcf  
```  
  
 <span data-ttu-id="d1367-128">Ten proces generuje binarne dzienniki cykliczne, które można przetwarzać za pomocą wybranego narzędzia, w tym [Narzędzia do przeglądania śledzenia usługi (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) lub tracerpt.</span><span class="sxs-lookup"><span data-stu-id="d1367-128">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="d1367-129">Możesz również przejrzeć przykład [cyklicznego śledzenia](circular-tracing.md) , aby uzyskać więcej informacji na temat alternatywnego odbiornika do wykonywania rejestrowania cyklicznego.</span><span class="sxs-lookup"><span data-stu-id="d1367-129">You can also review the [Circular Tracing](circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d1367-130">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="d1367-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d1367-131">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1367-131">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d1367-132">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1367-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d1367-133">Aby użyć poleceń RegisterProvider. bat, SetupETW. bat i CleanupETW. bat, należy uruchomić program przy użyciu konta administratora lokalnego.</span><span class="sxs-lookup"><span data-stu-id="d1367-133">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="d1367-134">W przypadku korzystania z systemu Windows Vista lub nowszego należy również uruchomić wiersz polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="d1367-134">If you are using Windows Vista or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="d1367-135">Aby to zrobić, kliknij prawym przyciskiem myszy ikonę wiersza polecenia, a następnie kliknij polecenie **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="d1367-135">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="d1367-136">Przed uruchomieniem przykładu należy uruchomić program RegisterProvider. bat na kliencie i serwerze.</span><span class="sxs-lookup"><span data-stu-id="d1367-136">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="d1367-137">Powoduje to skonfigurowanie wynikowego pliku ETWTracingSampleLog. etl w celu wygenerowania śladów, które mogą być odczytywane przez Podgląd śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="d1367-137">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="d1367-138">Ten plik znajduje się w folderze C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="d1367-138">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="d1367-139">Jeśli ten folder nie istnieje, należy go utworzyć lub nie są generowane żadne dane śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d1367-139">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="d1367-140">Następnie uruchom program SetupETW. bat na komputerach klienckich i serwerach, aby rozpocząć sesję śledzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="d1367-140">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="d1367-141">Plik SetupETW. bat można znaleźć w folderze CS\Client.</span><span class="sxs-lookup"><span data-stu-id="d1367-141">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="d1367-142">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1367-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="d1367-143">Po zakończeniu przykładu należy uruchomić CleanupETW. bat, aby zakończyć tworzenie pliku ETWTracingSampleLog. etl.</span><span class="sxs-lookup"><span data-stu-id="d1367-143">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="d1367-144">Otwórz plik ETWTracingSampleLog. etl z poziomu przeglądarki śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="d1367-144">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="d1367-145">Zostanie wyświetlony monit o zapisanie pliku binarnego w formacie pliku. svclog.</span><span class="sxs-lookup"><span data-stu-id="d1367-145">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="d1367-146">Otwórz nowo utworzony plik svclog z poziomu przeglądarki śledzenia usługi, aby wyświetlić dane śledzenia ETW i ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="d1367-146">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d1367-147">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d1367-147">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d1367-148">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="d1367-148">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d1367-149">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="d1367-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d1367-150">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d1367-150">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="d1367-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1367-151">See also</span></span>

- <span data-ttu-id="d1367-152">[Przykłady monitorowania oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d1367-152">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
