---
title: Śledzenie i rejestrowanie komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 7f729e845fe552d523a46a1783404baf4e0bbfca
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227444"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="bf297-102">Śledzenie i rejestrowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="bf297-102">Tracing and Message Logging</span></span>
<span data-ttu-id="bf297-103">Niniejszy przykład pokazuje, jak włączyć śledzenie i rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="bf297-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="bf297-104">Wynikowy ślady i dzienniki komunikatów są wyświetlane przy użyciu [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bf297-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="bf297-105">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="bf297-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf297-106">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="bf297-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="bf297-107">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="bf297-107">Tracing</span></span>  
 <span data-ttu-id="bf297-108">Windows Communication Foundation (WCF) używa mechanizmu śledzenia, zdefiniowane w <xref:System.Diagnostics> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bf297-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="bf297-109">W tym modelu śledzenia danych śledzenia jest produkowanych przez źródła śledzenia, które implementują aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf297-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="bf297-110">Każde źródło jest identyfikowane przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="bf297-110">Each source is identified by a name.</span></span> <span data-ttu-id="bf297-111">Śledzenie konsumenci tworzą obiekty nasłuchujące śledzenia dla źródła śledzenia, dla których chcesz pobrać informacji.</span><span class="sxs-lookup"><span data-stu-id="bf297-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="bf297-112">Aby odbierać dane śledzenia, należy utworzyć odbiornik dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bf297-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="bf297-113">W programie WCF, można to zrobić, dodając następujący kod do pliku konfiguracji usługi lub klienta przez ustawienie źródło śladu modelu usługi `switchValue`:</span><span class="sxs-lookup"><span data-stu-id="bf297-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
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
  
 <span data-ttu-id="bf297-114">Aby uzyskać więcej informacji na temat źródła śledzenia, zobacz sekcję źródła śledzenia w [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="bf297-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="bf297-115">Śledzenie działania i propagację</span><span class="sxs-lookup"><span data-stu-id="bf297-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="bf297-116">Posiadanie `ActivityTracing` włączone i `propagateActivity` równa `true` w `system.ServiceModel` źródła śledzenia dla klienta i usługi zapewnienia działania w ramach punktów końcowych (korelacja ślady w ramach przetwarzania (działalności), jednostki logiczne za pośrednictwem przesyłania działania) i na różnych działań, obejmujące wiele punktów końcowych (za pośrednictwem Propagacja Identyfikatora działania).</span><span class="sxs-lookup"><span data-stu-id="bf297-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="bf297-117">Te trzy mechanizmy (działań transferu i propagację) pomóc Ci znaleźć przyczynę błędu, więcej szybko przy użyciu narzędzia przeglądarki danych śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="bf297-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="bf297-118">Aby uzyskać więcej informacji, zobacz [za pomocą przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów z](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="bf297-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="bf297-119">Istnieje możliwość rozszerzyć śledzenia, dostarczone przez ServiceModel, tworząc śledzenia działań użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bf297-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="bf297-120">Śledzenie aktywności użytkownika umożliwia użytkownikowi utworzenie śledzenia działań:</span><span class="sxs-lookup"><span data-stu-id="bf297-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
-   <span data-ttu-id="bf297-121">Grupa śledzenia w logiczne jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="bf297-121">Group traces into logical units of work.</span></span>  
  
-   <span data-ttu-id="bf297-122">Korelowanie działań przy użyciu transferu i propagacji.</span><span class="sxs-lookup"><span data-stu-id="bf297-122">Correlate activities through transfers and propagation.</span></span>  
  
-   <span data-ttu-id="bf297-123">Ogranicza koszty wydajności śledzenia WCF (na przykład koszt miejsca na dysku w pliku dziennika).</span><span class="sxs-lookup"><span data-stu-id="bf297-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="bf297-124">Aby uzyskać więcej informacji na temat śledzenia działań użytkownika, zobacz [rozszerzanie śledzenia](../../../../docs/framework/wcf/samples/extending-tracing.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="bf297-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="bf297-125">Rejestrowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="bf297-125">Message Logging</span></span>  
 <span data-ttu-id="bf297-126">Można ją włączyć rejestrowanie komunikatów, zarówno na kliencie i usługi aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="bf297-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="bf297-127">Aby włączyć rejestrowanie komunikatów, należy dodać następujący kod do klienta lub usługi:</span><span class="sxs-lookup"><span data-stu-id="bf297-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
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
  
 <span data-ttu-id="bf297-128">Gdy komunikat jest rejestrowany, typ śledzenia jest zależna od tego, czy jest on śledzone na klienta lub serwera.</span><span class="sxs-lookup"><span data-stu-id="bf297-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="bf297-129">Na przykład "Dodaj". komunikat o błędzie jest wysyłany do klienta śledzonego w kategorii "TransportWrite" po stronie klienta, natomiast śledzona jest ten sam komunikat w kategorii "TransportRead" na usługę.</span><span class="sxs-lookup"><span data-stu-id="bf297-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="bf297-130">Konfigurowanie odbiornika śledzenia, dodając następujący kod do <xref:System.Diagnostics> sekcji w pliku App.config klienta lub plik Web.config usługi:</span><span class="sxs-lookup"><span data-stu-id="bf297-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
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
  
 <span data-ttu-id="bf297-131">Komunikaty są rejestrowane w formacie XML w katalogu docelowym, określone w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bf297-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf297-132">Pliki śledzenia nie są tworzone bez początkowo tworzenia katalogu dziennika.</span><span class="sxs-lookup"><span data-stu-id="bf297-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="bf297-133">Upewnij się, że katalog C:\logs\ istnieje, lub określ katalog rejestrowania alternatywne w konfiguracji odbiornika.</span><span class="sxs-lookup"><span data-stu-id="bf297-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="bf297-134">Zapoznaj się z instrukcjami instalacji początkowej na końcu tego dokumentu, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="bf297-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="bf297-135">Aby uzyskać więcej informacji na temat rejestrowania komunikatów, zobacz [Konfigurowanie rejestrowania komunikatów](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="bf297-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bf297-136">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="bf297-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bf297-137">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf297-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bf297-138">Przed uruchomieniem przykładu śledzenia i rejestrowania komunikatów, należy utworzyć katalog C:\logs\ usługi do zapisania plików .svclog do.</span><span class="sxs-lookup"><span data-stu-id="bf297-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="bf297-139">Nazwa tego katalogu jest zdefiniowana w pliku konfiguracyjnym jako ścieżki dla danych śledzenia i komunikaty, które mają być rejestrowane i można je zmienić.</span><span class="sxs-lookup"><span data-stu-id="bf297-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="bf297-140">Przyznaj użytkownikowi dostęp do zapisu usługi sieciowej do katalogu logs.</span><span class="sxs-lookup"><span data-stu-id="bf297-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3.  <span data-ttu-id="bf297-141">Aby kompilować rozwiązania w wersji języka C#, C++ lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf297-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="bf297-142">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf297-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bf297-143">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bf297-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bf297-144">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="bf297-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bf297-145">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="bf297-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bf297-146">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="bf297-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="bf297-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf297-147">See Also</span></span>  
 [<span data-ttu-id="bf297-148">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="bf297-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="bf297-149">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="bf297-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
