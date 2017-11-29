---
title: "Rozszerzanie śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 235b1a8454d573264f0bbe3cd5f9809d88d08209
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="extending-tracing"></a><span data-ttu-id="aaff5-102">Rozszerzanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="aaff5-102">Extending Tracing</span></span>
<span data-ttu-id="aaff5-103">W tym przykładzie pokazano, jak rozszerzyć [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkcja śledzenia pisząc śledzenia zdefiniowanych przez użytkownika działań w kod klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="aaff5-103">This sample demonstrates how to extend the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="aaff5-104">Dzięki temu użytkownikowi na tworzenie śledzenia działań i grupować dane śledzenia w logiczne jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="aaff5-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="aaff5-105">Istnieje również możliwość służące do skorelowania działań za pośrednictwem transferu (w ramach tego samego punktu końcowego) i propagacji (za pośrednictwem punktów końcowych).</span><span class="sxs-lookup"><span data-stu-id="aaff5-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="aaff5-106">W tym przykładzie śledzenie jest włączone dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="aaff5-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="aaff5-107">Aby uzyskać więcej informacji o sposobie włączania śledzenia w plikach konfiguracji klienta i usługi, zobacz [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="aaff5-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="aaff5-108">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="aaff5-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aaff5-109">Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="aaff5-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aaff5-110">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="aaff5-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="aaff5-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="aaff5-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="aaff5-112">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="aaff5-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aaff5-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="aaff5-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="aaff5-114">Śledzenie i propagowania działań.</span><span class="sxs-lookup"><span data-stu-id="aaff5-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="aaff5-115">Śledzenie działania użytkownika zezwala użytkownikowi na tworzenie własnych działań śledzenia do śledzenia grupy w logiczne jednostki pracy, korelowanie działań za pośrednictwem przesyłania i propagacji i zmniejszyć koszt wydajności [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] śledzenia (na przykład miejsce kosztu dysku dla pliku dziennika).</span><span class="sxs-lookup"><span data-stu-id="aaff5-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="aaff5-116">Dodawanie źródeł niestandardowych</span><span class="sxs-lookup"><span data-stu-id="aaff5-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="aaff5-117">Ślady zdefiniowane przez użytkownika można dodać do kodu klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="aaff5-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="aaff5-118">Dodawanie źródła śledzenia w plikach konfiguracji klienta lub usługę umożliwiają te niestandardowe śladów rejestrowane i wyświetlane w [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="aaff5-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="aaff5-119">Poniższy kod przedstawia sposób dodawania źródła śledzenia zdefiniowanych przez użytkownika o nazwie `ServerCalculatorTraceSource` do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="aaff5-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
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
  
### <a name="correlating-activities"></a><span data-ttu-id="aaff5-120">Korelowanie działań</span><span class="sxs-lookup"><span data-stu-id="aaff5-120">Correlating Activities</span></span>  
 <span data-ttu-id="aaff5-121">Aby skorelować działań bezpośrednio w obrębie punktów końcowych, `propagateActivity` atrybut musi być ustawiony na `true` w `System.ServiceModel` źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="aaff5-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="aaff5-122">Ponadto propagację śladów bez pośrednictwa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] działania ServiceModel działania śledzenia musi być wyłączona.</span><span class="sxs-lookup"><span data-stu-id="aaff5-122">Also, to propagate traces without going through [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="aaff5-123">Można to zaobserwować w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="aaff5-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aaff5-124">Wyłączenie śledzenia działania ServiceModel nie jest taka sama jak o poziomie śledzenia, wskazywane przez `switchValue` właściwość ustawiona na wartość off.</span><span class="sxs-lookup"><span data-stu-id="aaff5-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="aaff5-125">Zmniejszenie kosztów wydajności</span><span class="sxs-lookup"><span data-stu-id="aaff5-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="aaff5-126">Ustawienie `ActivityTracing` wyłączone w `System.ServiceModel` źródło śladu generuje plik śledzenia, który zawiera tylko ślady działania zdefiniowane przez użytkownika, bez żadnej śladów działania ServiceModel uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="aaff5-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="aaff5-127">Powoduje to znacznie mniejszy rozmiar pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="aaff5-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="aaff5-128">Jednak możliwość skorelowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przetwarzania śladów zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="aaff5-128">However, the opportunity to correlate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aaff5-129">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="aaff5-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="aaff5-130">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aaff5-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="aaff5-131">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aaff5-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="aaff5-132">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aaff5-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaff5-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aaff5-133">See Also</span></span>  
 [<span data-ttu-id="aaff5-134">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="aaff5-134">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
