---
title: Śledzenie cykliczne
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: 1f6c5287e6a53ed26ee5c9ed477e08dafc512e3f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868290"
---
# <a name="circular-tracing"></a><span data-ttu-id="b263e-102">Śledzenie cykliczne</span><span class="sxs-lookup"><span data-stu-id="b263e-102">Circular Tracing</span></span>
<span data-ttu-id="b263e-103">Niniejszy przykład pokazuje implementację odbiornik śledzenia cyklicznego buforu.</span><span class="sxs-lookup"><span data-stu-id="b263e-103">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="b263e-104">Typowy scenariusz dla usług produkcyjnych jest usług, które są dostępne przez długi czas i mieć włączone na niskim poziomie rejestrowanie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b263e-104">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="b263e-105">Te usługi to zajmować dużo miejsca na dysku.</span><span class="sxs-lookup"><span data-stu-id="b263e-105">These services consume a lot of disk space.</span></span> <span data-ttu-id="b263e-106">Podczas rozwiązywania problemów z usługą, najnowsze dane w dzienniku śledzenia dotyczy rozwiązywanie problemów.</span><span class="sxs-lookup"><span data-stu-id="b263e-106">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="b263e-107">Niniejszy przykład pokazuje implementację odbiornik śledzenia cyklicznego buforu, w którym tylko najbardziej aktualne dane śledzenia są przechowywane na dysku do skonfigurowanej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="b263e-107">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="b263e-108">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i zawiera odbiornik śledzenia niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="b263e-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes a custom tracing listener.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b263e-109">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b263e-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b263e-110">W tym przykładzie przyjęto założenie, że czytelnik zna [śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) przykładowe i po ich przeczytaniu w dokumentacji dostarczonej [śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="b263e-110">This sample assumes that you are familiar with the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="b263e-111">Odbiornik śledzenia cyklicznego buforu</span><span class="sxs-lookup"><span data-stu-id="b263e-111">Circular Buffer Trace Listener</span></span>  
 <span data-ttu-id="b263e-112">Koncepcja za wdrożenia okrągły odbiornik śledzenia bufora ma dwa pliki, które każdy przechowywać do połowy dane dziennika całkowita żądanego śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b263e-112">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="b263e-113">Odbiornik tworzy jeden plik i zapisuje do tego pliku, dopóki nie zostanie osiągnięty limit połowę rozmiaru danych, w tym momencie przełączenie do drugiego pliku.</span><span class="sxs-lookup"><span data-stu-id="b263e-113">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="b263e-114">Gdy odbiornik osiągnie limit dla drugiego pliku — zastępuje pierwszego pliku przy użyciu nowych danych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b263e-114">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>  
  
 <span data-ttu-id="b263e-115">Tego odbiornika jest pochodną `XmlWriteTraceListener` i umożliwia dzienniki aby je przeglądać za pomocą [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b263e-115">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="b263e-116">Podczas próby wyświetlić dzienniki, dwa pliki dziennika można łatwo odtwarzane, otwierając oba pliki dziennika w tym samym czasie w narzędziu przeglądarki danych śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="b263e-116">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="b263e-117">Narzędzie przeglądarki danych śledzenia usługi automatycznie zajmie się sortowanie śladów, aby były wyświetlane w odpowiedniej kolejności.</span><span class="sxs-lookup"><span data-stu-id="b263e-117">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b263e-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="b263e-118">Configuration</span></span>  
 <span data-ttu-id="b263e-119">Usługę można skonfigurować do użycia odbiornik śledzenia cyklicznego buforu, dodając następujący kod dla elementów źródła i odbiornika.</span><span class="sxs-lookup"><span data-stu-id="b263e-119">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="b263e-120">Maksymalny rozmiar pliku jest określany przez ustawienie `maxFileSizeKB` atrybut w konfiguracji odbiornika śledzenia cykliczne.</span><span class="sxs-lookup"><span data-stu-id="b263e-120">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="b263e-121">Jest to zaprezentowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b263e-121">This is demonstrated in the following code.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b263e-122">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="b263e-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b263e-123">Pamiętaj, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b263e-123">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b263e-124">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b263e-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b263e-125">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b263e-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b263e-126">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b263e-126">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b263e-127">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b263e-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b263e-128">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="b263e-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b263e-129">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b263e-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a><span data-ttu-id="b263e-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b263e-130">See Also</span></span>  
 [<span data-ttu-id="b263e-131">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="b263e-131">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
