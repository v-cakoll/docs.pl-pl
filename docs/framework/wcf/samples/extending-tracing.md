---
title: Rozszerzanie śledzenia
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: a7231d340d2528a42c8cbb5294d812d52db92d54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183687"
---
# <a name="extending-tracing"></a><span data-ttu-id="955d5-102">Rozszerzanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="955d5-102">Extending Tracing</span></span>
<span data-ttu-id="955d5-103">W tym przykładzie pokazano, jak rozszerzyć funkcję śledzenia programu Windows Communication Foundation (WCF), zapisując ślady aktywności zdefiniowane przez użytkownika w kodzie klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="955d5-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="955d5-104">Dzięki temu użytkownik może tworzyć działania śledzenia i grupować ślady w logiczne jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="955d5-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="955d5-105">Możliwe jest również skorelowanie działań za pośrednictwem transferów (w ramach tego samego punktu końcowego) i propagacji (między punktami końcowymi).</span><span class="sxs-lookup"><span data-stu-id="955d5-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="955d5-106">W tym przykładzie śledzenie jest włączone dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="955d5-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="955d5-107">Aby uzyskać więcej informacji na temat włączania śledzenia w plikach konfiguracyjnych klienta i usługi, zobacz [Śledzenie i rejestrowanie wiadomości](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="955d5-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="955d5-108">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="955d5-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="955d5-109">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="955d5-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="955d5-110">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="955d5-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="955d5-111">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="955d5-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="955d5-112">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="955d5-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="955d5-113">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="955d5-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="955d5-114">Śledzenie i propagacja aktywności</span><span class="sxs-lookup"><span data-stu-id="955d5-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="955d5-115">Śledzenie aktywności zdefiniowane przez użytkownika umożliwia użytkownikowi tworzenie własnych działań śledzenia w celu grupowania śladów w logiczne jednostki pracy, skorelowanie działań poprzez transfery i propagację oraz zmniejszenie kosztów wydajności śledzenia WCF (na przykład koszt miejsca na dysku pliku dziennika).</span><span class="sxs-lookup"><span data-stu-id="955d5-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="955d5-116">Dodawanie źródeł niestandardowych</span><span class="sxs-lookup"><span data-stu-id="955d5-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="955d5-117">Ślady zdefiniowane przez użytkownika można dodać do kodu klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="955d5-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="955d5-118">Dodawanie źródeł śledzenia do plików konfiguracyjnych klienta lub usługi umożliwia rejestrowanie i wyświetlanie tych niestandardowych śladów w [narzędziu Service Trace Viewer Tool (SvcTraceViewer.exe).](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)</span><span class="sxs-lookup"><span data-stu-id="955d5-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="955d5-119">Poniższy kod pokazuje, jak dodać źródło `ServerCalculatorTraceSource` śledzenia zdefiniowane przez użytkownika o nazwie do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="955d5-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
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
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a><span data-ttu-id="955d5-120">Działania korelujące</span><span class="sxs-lookup"><span data-stu-id="955d5-120">Correlating Activities</span></span>  
 <span data-ttu-id="955d5-121">Aby skorelować działania bezpośrednio między punktami końcowymi, `propagateActivity` `true` atrybut `System.ServiceModel` musi być ustawiony w źródle śledzenia.</span><span class="sxs-lookup"><span data-stu-id="955d5-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="955d5-122">Ponadto do propagowania śladów bez przechodzenia przez WCF działań, ServiceModel śledzenia aktywności musi być wyłączony.</span><span class="sxs-lookup"><span data-stu-id="955d5-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="955d5-123">Można to zobaczyć w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="955d5-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="955d5-124">Wyłączenie śledzenia aktywności Usługi ServiceModel nie jest tym samym, co `switchValue` poziom śledzenia, oznaczony przez właściwość, ustawiony na wyłączony.</span><span class="sxs-lookup"><span data-stu-id="955d5-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="955d5-125">Zmniejszenie kosztów wydajności</span><span class="sxs-lookup"><span data-stu-id="955d5-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="955d5-126">Ustawienie `ActivityTracing` wyłączone w `System.ServiceModel` źródle śledzenia generuje plik śledzenia, który zawiera tylko ślady aktywności zdefiniowane przez użytkownika, bez żadnych servicemodel śledzenia aktywności zawarte.</span><span class="sxs-lookup"><span data-stu-id="955d5-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="955d5-127">Powoduje to plik dziennika o znacznie mniejszym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="955d5-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="955d5-128">Jednak możliwość skorelowania śladów przetwarzania WCF zostanie utracona.</span><span class="sxs-lookup"><span data-stu-id="955d5-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="955d5-129">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="955d5-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="955d5-130">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="955d5-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="955d5-131">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="955d5-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="955d5-132">Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="955d5-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="955d5-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="955d5-133">See also</span></span>

- <span data-ttu-id="955d5-134">[Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="955d5-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
