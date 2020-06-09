---
title: Rozszerzanie śledzenia
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 59bdfeea41bac812840ffe166895050a6cd1ad2d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600519"
---
# <a name="extend-tracing"></a><span data-ttu-id="a6085-102">Rozwiń śledzenie</span><span class="sxs-lookup"><span data-stu-id="a6085-102">Extend tracing</span></span>

<span data-ttu-id="a6085-103">Ten przykład pokazuje, jak zwiększyć funkcję śledzenia Windows Communication Foundation (WCF), pisząc ślady aktywności zdefiniowane przez użytkownika w kodzie klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="a6085-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="a6085-104">Pisanie śladów aktywności zdefiniowanej przez użytkownika umożliwia użytkownikowi tworzenie działań śledzenia i grupowanie śladów w logiczne jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="a6085-104">Writing user-defined activity traces allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="a6085-105">Istnieje również możliwość skorelowania działań przez transfery (w tym samym punkcie końcowym) i propagacji (między punktami końcowymi).</span><span class="sxs-lookup"><span data-stu-id="a6085-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="a6085-106">W tym przykładzie śledzenie jest włączone zarówno dla klienta, jak i dla usługi.</span><span class="sxs-lookup"><span data-stu-id="a6085-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="a6085-107">Aby uzyskać więcej informacji na temat włączania śledzenia w plikach konfiguracji klienta i usługi, zobacz [śledzenie i rejestrowanie komunikatów](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="a6085-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="a6085-108">Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a6085-108">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6085-109">Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a6085-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a6085-110">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a6085-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a6085-111">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="a6085-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a6085-112">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="a6085-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a6085-113">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a6085-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="a6085-114">Śledzenie i Propagacja działań</span><span class="sxs-lookup"><span data-stu-id="a6085-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="a6085-115">Śledzenie aktywności zdefiniowane przez użytkownika umożliwia użytkownikowi tworzenie własnych działań śledzenia w celu grupowania śladów w logiczne jednostki pracy, skorelowanie działań przez transfery i propagację oraz zmniejszanie kosztów wydajności śledzenia WCF (na przykład koszt miejsca na dysku w pliku dziennika).</span><span class="sxs-lookup"><span data-stu-id="a6085-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="add-custom-sources"></a><span data-ttu-id="a6085-116">Dodawanie niestandardowych źródeł</span><span class="sxs-lookup"><span data-stu-id="a6085-116">Add custom sources</span></span>  
 <span data-ttu-id="a6085-117">Ślady zdefiniowane przez użytkownika mogą być dodawane do kodu klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="a6085-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="a6085-118">Dodawanie źródeł śledzenia do plików konfiguracji klienta lub usługi pozwala na rejestrowanie tych niestandardowych śladów i wyświetlanie ich w [narzędziu Podgląd śledzenia usługi (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a6085-118">Adding trace sources to the client or service configuration files allows for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="a6085-119">Poniższy kod przedstawia sposób dodawania zdefiniowanego przez użytkownika źródła śledzenia o nazwie `ServerCalculatorTraceSource` do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a6085-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>
....
```  
  
### <a name="correlate-activities"></a><span data-ttu-id="a6085-120">Skorelowanie działań</span><span class="sxs-lookup"><span data-stu-id="a6085-120">Correlate activities</span></span>  
 <span data-ttu-id="a6085-121">Aby skorelować działania bezpośrednio między punktami końcowymi, `propagateActivity` atrybut musi być ustawiony na `true` w `System.ServiceModel` źródle śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a6085-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="a6085-122">Ponadto w celu propagowania śladów bez przechodzenia przez działania programu WCF należy wyłączyć śledzenie działań elementu ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="a6085-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="a6085-123">Może to być widoczne w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="a6085-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6085-124">Wyłączenie śledzenia aktywności zestawu elementów nie jest takie samo jak w przypadku poziomu śledzenia, oznaczonego przez właściwość jako `switchValue` off.</span><span class="sxs-lookup"><span data-stu-id="a6085-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessen-performance-cost"></a><span data-ttu-id="a6085-125">Zmniejszanie kosztów wydajności</span><span class="sxs-lookup"><span data-stu-id="a6085-125">Lessen performance cost</span></span>  
 <span data-ttu-id="a6085-126">Ustawienie `ActivityTracing` wyłączone w `System.ServiceModel` źródle śledzenia generuje plik śledzenia, który zawiera tylko ślady aktywności zdefiniowane przez użytkownika, bez dołączania żadnych śladów działania programu ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="a6085-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="a6085-127">Wykluczenie wyników śledzenia działania programu ServiceModel skutkuje znacznie mniejszym plikiem dziennika.</span><span class="sxs-lookup"><span data-stu-id="a6085-127">Excluding ServiceModel activity traces results in a much smaller log file.</span></span> <span data-ttu-id="a6085-128">Jednak możliwość skorelowania śladów przetwarzania danych WCF zostanie utracona.</span><span class="sxs-lookup"><span data-stu-id="a6085-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="a6085-129">Konfigurowanie, kompilowanie i uruchamianie przykładu</span><span class="sxs-lookup"><span data-stu-id="a6085-129">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a6085-130">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a6085-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a6085-131">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a6085-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a6085-132">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a6085-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6085-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6085-133">See also</span></span>

- <span data-ttu-id="a6085-134">[Przykłady monitorowania oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a6085-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
