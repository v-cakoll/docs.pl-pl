---
title: Śledzenie i rejestrowanie komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 13d23c0f69c65dd3bd6b2714dd710eb7f97a1c07
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="ad512-102">Śledzenie i rejestrowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="ad512-102">Tracing and Message Logging</span></span>
<span data-ttu-id="ad512-103">W tym przykładzie pokazano, jak włączyć śledzenie i rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ad512-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="ad512-104">Wynikowa śladów i dzienników komunikatów wyświetlane przy użyciu [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ad512-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="ad512-105">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ad512-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad512-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ad512-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="ad512-107">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="ad512-107">Tracing</span></span>  
 <span data-ttu-id="ad512-108">Windows Communication Foundation (WCF) używa mechanizmu śledzenia zdefiniowanych w <xref:System.Diagnostics> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ad512-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="ad512-109">W tym modelu śledzenie danych śledzenia jest generowany przez źródła śledzenia, które implementują aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ad512-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="ad512-110">Każde źródło jest identyfikowane przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="ad512-110">Each source is identified by a name.</span></span> <span data-ttu-id="ad512-111">Śledzenia konsumenci tworzą obiekty nasłuchujące śledzenia dla źródła śledzenia, dla których chcesz pobrać informacji.</span><span class="sxs-lookup"><span data-stu-id="ad512-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="ad512-112">Aby odbierać dane śledzenia, należy utworzyć odbiornik źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ad512-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="ad512-113">W programie WCF, można to zrobić, dodając następujący kod do pliku konfiguracji usługi lub klienta przez ustawienie źródło śladu modelu usługi `switchValue`:</span><span class="sxs-lookup"><span data-stu-id="ad512-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 <span data-ttu-id="ad512-114">Aby uzyskać więcej informacji na temat źródeł śledzenia, zobacz sekcję źródła śledzenia w [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="ad512-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="ad512-115">Śledzenie działania i propagacji</span><span class="sxs-lookup"><span data-stu-id="ad512-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="ad512-116">O `ActivityTracing` włączone i `propagateActivity` ustawioną `true` w `system.ServiceModel` źródła śledzenia dla klienta i usługi dostarczać korelacji śladów w ramach przetwarzania (działania), jednostki logiczne działań wykonywanych w ciągu (punkty końcowe za pomocą działania przesyłania) i działań wykonywanych obejmujących wiele punktów końcowych (za pośrednictwem Propagacja Identyfikatora działania).</span><span class="sxs-lookup"><span data-stu-id="ad512-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="ad512-117">Mechanizmy te trzy (działania, przesyłania i propagacji) może pomóc więcej szybko przy użyciu narzędzia podglądu śledzenia usługi Znajdź przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="ad512-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="ad512-118">Aby uzyskać więcej informacji, zobacz [przy użyciu przeglądarki śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="ad512-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="ad512-119">Istnieje możliwość rozszerzenia śledzenie zapewnianej przez ServiceModel przez utworzenie śladów działania zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ad512-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="ad512-120">Śledzenie działania zdefiniowane przez użytkownika umożliwia użytkownikom tworzenie śledzenia działań do:</span><span class="sxs-lookup"><span data-stu-id="ad512-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
-   <span data-ttu-id="ad512-121">Grupa śledzenia w logiczne jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="ad512-121">Group traces into logical units of work.</span></span>  
  
-   <span data-ttu-id="ad512-122">Korelowanie działania za pośrednictwem przesyłania i propagacji.</span><span class="sxs-lookup"><span data-stu-id="ad512-122">Correlate activities through transfers and propagation.</span></span>  
  
-   <span data-ttu-id="ad512-123">Ogranicza koszty wydajności śledzenia WCF (na przykład kosztu miejsca na dysku w pliku dziennika).</span><span class="sxs-lookup"><span data-stu-id="ad512-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="ad512-124">Aby uzyskać więcej informacji dotyczących śledzenia zdefiniowanych przez użytkownika działań, zobacz [rozszerzanie śledzenia](../../../../docs/framework/wcf/samples/extending-tracing.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="ad512-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="ad512-125">Rejestrowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="ad512-125">Message Logging</span></span>  
 <span data-ttu-id="ad512-126">Zarówno na kliencie i usługi WCF dowolnej aplikacji, można włączyć rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ad512-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="ad512-127">Aby włączyć rejestrowanie komunikatów, musi Dodaj następujący kod do klienta lub usługi:</span><span class="sxs-lookup"><span data-stu-id="ad512-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ad512-128">Gdy komunikat jest rejestrowany, śledzenia zależy od tego, czy jest są śledzone na klienta lub serwera.</span><span class="sxs-lookup"><span data-stu-id="ad512-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="ad512-129">Na przykład komunikat "Dodaj", który jest wysyłany do klienta jest śledzone w kategorii "TransportWrite" po stronie klienta, podczas gdy ten sam komunikat śledzonego w kategorii "TransportRead" w punkcie usług.</span><span class="sxs-lookup"><span data-stu-id="ad512-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="ad512-130">Skonfiguruj odbiornik śledzenia, dodając następujący kod do <xref:System.Diagnostics> sekcji w pliku App.config klienta lub usługi w pliku Web.config:</span><span class="sxs-lookup"><span data-stu-id="ad512-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 <span data-ttu-id="ad512-131">Komunikaty są rejestrowane w formacie XML w katalog docelowy określony w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ad512-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad512-132">Pliki śledzenia nie są tworzone bez początkowo tworzenia katalogu dziennika.</span><span class="sxs-lookup"><span data-stu-id="ad512-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="ad512-133">Upewnij się, że istnieje katalog C:\logs\, lub określ katalog rejestrowania alternatywny w konfiguracji odbiornika.</span><span class="sxs-lookup"><span data-stu-id="ad512-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="ad512-134">Zapoznaj się z instrukcjami instalacji początkowej na końcu tego dokumentu, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="ad512-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="ad512-135">Aby uzyskać więcej informacji na temat rejestrowania komunikatów, zobacz [Konfigurowanie rejestrowania komunikatów](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="ad512-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ad512-136">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="ad512-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ad512-137">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ad512-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ad512-138">Przed uruchomieniem przykładowe śledzenie i rejestrowanie komunikatów, należy utworzyć katalog C:\logs\ usługi do zapisania plików .svclog do.</span><span class="sxs-lookup"><span data-stu-id="ad512-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="ad512-139">Nazwa tego katalogu jest zdefiniowana w pliku konfiguracyjnym jako ścieżkę do śledzenia i komunikaty, które mają być rejestrowane i może być zmieniona.</span><span class="sxs-lookup"><span data-stu-id="ad512-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="ad512-140">W katalogu dzienników, należy przyznać użytkownikowi dostęp do zapisu usługi sieciowej.</span><span class="sxs-lookup"><span data-stu-id="ad512-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3.  <span data-ttu-id="ad512-141">Tworzenie wersji języka C#, C++ lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ad512-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="ad512-142">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ad512-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ad512-143">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ad512-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ad512-144">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ad512-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ad512-145">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="ad512-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ad512-146">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ad512-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="ad512-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad512-147">See Also</span></span>  
 [<span data-ttu-id="ad512-148">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="ad512-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ad512-149">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="ad512-149">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
