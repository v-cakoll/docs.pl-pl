---
title: Śledzenie cykliczne
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: 0b1d62177828b52b21a3e43cc083f79c27878804
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741974"
---
# <a name="circular-tracing"></a><span data-ttu-id="d226e-102">Śledzenie cykliczne</span><span class="sxs-lookup"><span data-stu-id="d226e-102">Circular Tracing</span></span>

<span data-ttu-id="d226e-103">Ten przykład pokazuje implementację odbiornika cyklicznego śledzenia buforów.</span><span class="sxs-lookup"><span data-stu-id="d226e-103">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="d226e-104">Typowym scenariuszem dla usług produkcyjnych jest posiadanie usług dostępnych przez długi czas i włączenie rejestrowania śledzenia na niskim poziomie.</span><span class="sxs-lookup"><span data-stu-id="d226e-104">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="d226e-105">Te usługi zużywają dużo miejsca na dysku.</span><span class="sxs-lookup"><span data-stu-id="d226e-105">These services consume a lot of disk space.</span></span> <span data-ttu-id="d226e-106">W przypadku rozwiązywania problemów z usługą najnowsze dane w dzienniku śledzenia są istotne do rozwiązywania problemu.</span><span class="sxs-lookup"><span data-stu-id="d226e-106">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="d226e-107">Ten przykład pokazuje implementację detektora cyklicznego śledzenia bufora, w którym tylko najnowsze ślady są przechowywane na dysku do konfigurowalnej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="d226e-107">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="d226e-108">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i zawiera odbiornik niestandardowego śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d226e-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes a custom tracing listener.</span></span>

> [!NOTE]
> <span data-ttu-id="d226e-109">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d226e-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="d226e-110">W tym przykładzie założono, że znasz przykład [śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) oraz Przeczytaj dokumentację dotyczącą śledzenia i przykładowego [rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) .</span><span class="sxs-lookup"><span data-stu-id="d226e-110">This sample assumes that you are familiar with the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>

## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="d226e-111">Odbiornik cyklicznego śledzenia buforu</span><span class="sxs-lookup"><span data-stu-id="d226e-111">Circular Buffer Trace Listener</span></span>

<span data-ttu-id="d226e-112">Koncepcja w odróżnieniu od implementacji detektora śledzenia cyklicznego buforu ma dwa pliki, które mogą przechowywać do połowy łącznej liczby żądanych danych dziennika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d226e-112">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="d226e-113">Odbiornik tworzy jeden plik i zapisuje je do tego pliku do momentu, aż osiągnie limit o połowie rozmiaru danych, w którym wskazuje na drugi plik.</span><span class="sxs-lookup"><span data-stu-id="d226e-113">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="d226e-114">Gdy odbiornik osiągnie limit dla drugiego pliku — zastępuje pierwszy plik nowym śladem.</span><span class="sxs-lookup"><span data-stu-id="d226e-114">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>

<span data-ttu-id="d226e-115">Ten odbiornik pochodzi z `XmlWriteTraceListener` i umożliwia wyświetlanie dzienników za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d226e-115">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="d226e-116">Podczas próby wyświetlenia dzienników te dwa pliki dziennika można łatwo połączyć przez otwarcie obu plików dziennika w tym samym czasie w narzędziu Podgląd śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="d226e-116">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="d226e-117">Narzędzie Podgląd śledzenia usług automatycznie zajmuje się sortowaniem śladów, tak aby były wyświetlane w odpowiedniej kolejności.</span><span class="sxs-lookup"><span data-stu-id="d226e-117">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>

## <a name="configuration"></a><span data-ttu-id="d226e-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d226e-118">Configuration</span></span>

<span data-ttu-id="d226e-119">Usługę można skonfigurować tak, aby korzystała z detektora śledzenia cyklicznego buforu przez dodanie następującego kodu dla odbiornika i elementów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="d226e-119">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="d226e-120">Maksymalny rozmiar pliku jest określony przez ustawienie atrybutu `maxFileSizeKB` w konfiguracji detektora cyklicznego śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d226e-120">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="d226e-121">Przedstawiono to w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d226e-121">This is demonstrated in the following code.</span></span>

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

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d226e-122">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="d226e-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d226e-123">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d226e-123">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d226e-124">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d226e-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="d226e-125">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d226e-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d226e-126">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d226e-126">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d226e-127">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="d226e-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d226e-128">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d226e-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d226e-129">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d226e-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`

## <a name="see-also"></a><span data-ttu-id="d226e-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d226e-130">See also</span></span>

- <span data-ttu-id="d226e-131">[Przykłady monitorowania oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d226e-131">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
