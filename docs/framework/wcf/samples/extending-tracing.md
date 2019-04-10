---
title: Rozszerzanie śledzenia
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: c56f886857e8d391a243e3af4a13353f14116247
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329716"
---
# <a name="extending-tracing"></a><span data-ttu-id="5dc6b-102">Rozszerzanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="5dc6b-102">Extending Tracing</span></span>
<span data-ttu-id="5dc6b-103">Niniejszy przykład pokazuje, jak rozszerzyć funkcję śledzenia usług Windows Communication Foundation (WCF), pisząc dane śledzenia działań użytkownika w kodzie klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="5dc6b-104">Dzięki temu użytkownikowi na tworzenie śledzenia działań i grupować dane śledzenia w logiczne jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="5dc6b-105">Istnieje również możliwość skorelowania działania za pośrednictwem transfery (w obrębie tego samego punktu końcowego) i propagację (za pośrednictwem punktów końcowych).</span><span class="sxs-lookup"><span data-stu-id="5dc6b-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="5dc6b-106">W tym przykładzie jest włączone śledzenie zarówno klient, jak i usługi.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="5dc6b-107">Aby uzyskać więcej informacji o tym, jak włączyć śledzenie w plikach konfiguracji klienta i usługi, zobacz [śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="5dc6b-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="5dc6b-108">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5dc6b-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5dc6b-109">Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5dc6b-110">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5dc6b-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5dc6b-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5dc6b-112">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5dc6b-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="5dc6b-114">Śledzenie i propagowania działań.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="5dc6b-115">Śledzenie aktywności użytkownika zezwala użytkownikowi na tworzenie własnych śledzenia działań w ramach grupy danych śledzenia w logiczne jednostki pracy, korelować działania za pośrednictwem transferu i propagację i zmniejszyć koszty wydajności śledzenia WCF (na przykład miejsca na dysku, koszt pliku dziennika).</span><span class="sxs-lookup"><span data-stu-id="5dc6b-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="5dc6b-116">Dodawanie źródła niestandardowego</span><span class="sxs-lookup"><span data-stu-id="5dc6b-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="5dc6b-117">Ślady zdefiniowanych przez użytkownika można dodać do kodu zarówno klient, jak i usługi.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="5dc6b-118">Dodawanie źródła śledzenia do plików konfiguracji klienta lub usługę umożliwiają ślady te niestandardowe rejestrowane i wyświetlane w [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5dc6b-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="5dc6b-119">Poniższy kod przedstawia sposób dodawania źródła śledzenia zdefiniowanych przez użytkownika o nazwie `ServerCalculatorTraceSource` do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
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
  
### <a name="correlating-activities"></a><span data-ttu-id="5dc6b-120">Korelowanie działań</span><span class="sxs-lookup"><span data-stu-id="5dc6b-120">Correlating Activities</span></span>  
 <span data-ttu-id="5dc6b-121">Aby skorelować działania bezpośrednio w obrębie punktów końcowych, `propagateActivity` atrybutu musi być równa `true` w `System.ServiceModel` źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="5dc6b-122">Ponadto do propagowania ślady bez pośrednictwa usługi WCF działań, śledzenie aktywności ServiceModel musi być wyłączony.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="5dc6b-123">Można to zaobserwować w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5dc6b-124">Wyłączenie śledzenia działań ServiceModel nie jest taka sama jak o poziomie śledzenia, wskazywane przez `switchValue` właściwość ustawiona na wartość off.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="5dc6b-125">Zmniejszenie spadek wydajności</span><span class="sxs-lookup"><span data-stu-id="5dc6b-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="5dc6b-126">Ustawienie `ActivityTracing` na wyłączone w `System.ServiceModel` źródła śledzenia generuje plik śledzenia, który zawiera tylko działania użytkownika ślady, bez jakichkolwiek ślady działania elementu ServiceModel uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="5dc6b-127">Skutkuje to znacznie mniejszy rozmiar pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="5dc6b-128">Jednak możliwość korelacji WCF przetwarzania śladów zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="5dc6b-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5dc6b-129">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="5dc6b-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5dc6b-130">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5dc6b-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5dc6b-131">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5dc6b-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5dc6b-132">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5dc6b-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dc6b-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5dc6b-133">See also</span></span>

- [<span data-ttu-id="5dc6b-134">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="5dc6b-134">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
