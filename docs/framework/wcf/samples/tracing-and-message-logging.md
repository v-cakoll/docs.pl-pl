---
title: Śledzenie i rejestrowanie komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 9ffb7a99540b953fc93a22d2296caf86f294d25d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143827"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="c517f-102">Śledzenie i rejestrowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="c517f-102">Tracing and Message Logging</span></span>
<span data-ttu-id="c517f-103">W tym przykładzie pokazano, jak włączyć śledzenie i rejestrowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c517f-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="c517f-104">Wynikowe ślady i dzienniki komunikatów są wyświetlane za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer.exe).](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)</span><span class="sxs-lookup"><span data-stu-id="c517f-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="c517f-105">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c517f-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c517f-106">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c517f-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="c517f-107">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="c517f-107">Tracing</span></span>  
 <span data-ttu-id="c517f-108">Windows Communication Foundation (WCF) używa mechanizmu <xref:System.Diagnostics> śledzenia zdefiniowanego w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="c517f-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="c517f-109">W tym modelu śledzenia dane śledzenia są tworzone przez źródła śledzenia, które implementują aplikacje.</span><span class="sxs-lookup"><span data-stu-id="c517f-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="c517f-110">Każde źródło jest identyfikowane przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="c517f-110">Each source is identified by a name.</span></span> <span data-ttu-id="c517f-111">Śledź konsumentów utworzyć detektory śledzenia dla źródeł śledzenia, dla których chcą pobrać informacje.</span><span class="sxs-lookup"><span data-stu-id="c517f-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="c517f-112">Aby odbierać dane śledzenia, należy utworzyć odbiornik dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c517f-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="c517f-113">W WCF można to zrobić, dodając następujący kod do pliku konfiguracyjnego usługi lub klienta, `switchValue`ustawiając źródło śledzenia modelu usługi:</span><span class="sxs-lookup"><span data-stu-id="c517f-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
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
  
 <span data-ttu-id="c517f-114">Aby uzyskać więcej informacji na temat źródeł śledzenia, zobacz sekcję Źródło śledzenia w temacie [Konfigurowanie śledzenia.](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="c517f-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="c517f-115">Śledzenie i propagacja aktywności</span><span class="sxs-lookup"><span data-stu-id="c517f-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="c517f-116">Po `ActivityTracing` włączeniu `propagateActivity` i `true` ustawieniu w źródłach `system.ServiceModel` śledzenia dla klienta i usługi zapewniają korelację śladów w ramach jednostek logicznych przetwarzania (działania), między działaniami w punktach końcowych (za pośrednictwem transferów działań) i między działaniami obejmującymi wiele punktów końcowych (za pośrednictwem propagacji identyfikatora działania).</span><span class="sxs-lookup"><span data-stu-id="c517f-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="c517f-117">Te trzy mechanizmy (działania, transfery i propagacji) może pomóc zlokalizować główną przyczynę błędu szybciej za pomocą narzędzia Podgląd śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="c517f-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="c517f-118">Aby uzyskać więcej informacji, zobacz [Używanie przeglądarki śledzenia usług do wyświetlania skorelowanych śladów i rozwiązywania problemów](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="c517f-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="c517f-119">Istnieje możliwość rozszerzenia śledzenia, który jest dostarczany przez ServiceModel przez tworzenie śladów aktywności zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c517f-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="c517f-120">Śledzenie aktywności zdefiniowane przez użytkownika umożliwia użytkownikowi tworzenie działań śledzenia w celu:</span><span class="sxs-lookup"><span data-stu-id="c517f-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
- <span data-ttu-id="c517f-121">Grupuj ślady w logiczne jednostki pracy.</span><span class="sxs-lookup"><span data-stu-id="c517f-121">Group traces into logical units of work.</span></span>  
  
- <span data-ttu-id="c517f-122">Skorelować działania poprzez transfery i propagacji.</span><span class="sxs-lookup"><span data-stu-id="c517f-122">Correlate activities through transfers and propagation.</span></span>  
  
- <span data-ttu-id="c517f-123">Zmniejsz koszt wydajności śledzenia WCF (na przykład koszt miejsca na dysku pliku dziennika).</span><span class="sxs-lookup"><span data-stu-id="c517f-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="c517f-124">Aby uzyskać więcej informacji na temat śledzenia aktywności zdefiniowanej przez użytkownika, zobacz [rozszerzenie śledzenia](../../../../docs/framework/wcf/samples/extending-tracing.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="c517f-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="c517f-125">Rejestrowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="c517f-125">Message Logging</span></span>  
 <span data-ttu-id="c517f-126">Rejestrowanie wiadomości można włączyć zarówno na kliencie, jak i w usłudze dowolnej aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="c517f-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="c517f-127">Aby włączyć rejestrowanie wiadomości, należy dodać następujący kod do klienta lub usługi:</span><span class="sxs-lookup"><span data-stu-id="c517f-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
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
  
 <span data-ttu-id="c517f-128">Po zarejestrowaniu wiadomości typ śledzenia zależy od tego, czy jest śledzony na kliencie, czy na serwerze.</span><span class="sxs-lookup"><span data-stu-id="c517f-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="c517f-129">Na przykład komunikat "Dodaj", który jest wysyłany do klienta jest śledzony w kategorii "TransportWrite" na kliencie, podczas gdy ten sam komunikat jest śledzony w kategorii "TransportRead" w usłudze.</span><span class="sxs-lookup"><span data-stu-id="c517f-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="c517f-130">Skonfiguruj odbiornik śledzenia, dodając <xref:System.Diagnostics> następujący kod do sekcji pliku App.config klienta lub pliku Web.config usługi:</span><span class="sxs-lookup"><span data-stu-id="c517f-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
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
  
 <span data-ttu-id="c517f-131">Komunikaty są rejestrowane w formacie XML w katalogu docelowym określonym w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="c517f-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c517f-132">Pliki śledzenia nie są tworzone bez początkowego tworzenia katalogu dziennika.</span><span class="sxs-lookup"><span data-stu-id="c517f-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="c517f-133">Upewnij się, że katalog C:\logs\ istnieje lub określ alternatywny katalog rejestrowania w konfiguracji odbiornika.</span><span class="sxs-lookup"><span data-stu-id="c517f-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="c517f-134">Aby uzyskać więcej informacji, zobacz instrukcje konfiguracji początkowej na końcu tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c517f-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="c517f-135">Aby uzyskać więcej informacji na temat rejestrowania wiadomości, zobacz temat [Rejestrowanie wiadomości konfigurowania.](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)</span><span class="sxs-lookup"><span data-stu-id="c517f-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c517f-136">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="c517f-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c517f-137">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c517f-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c517f-138">Przed uruchomieniem próbki śledzenia i rejestrowania wiadomości utwórz katalog C:\logs\ dla usługi, do którą chcesz zapisać pliki .svclog.</span><span class="sxs-lookup"><span data-stu-id="c517f-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="c517f-139">Nazwa tego katalogu jest zdefiniowana w pliku konfiguracyjnym jako ścieżka śledzenia i komunikatów, które mają być rejestrowane i mogą być zmieniane.</span><span class="sxs-lookup"><span data-stu-id="c517f-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="c517f-140">Nadaj użytkownikowi usługę sieciową dostęp do zapisu do katalogu dzienników.</span><span class="sxs-lookup"><span data-stu-id="c517f-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3. <span data-ttu-id="c517f-141">Aby utworzyć wersję C#, C++ lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c517f-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="c517f-142">Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c517f-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c517f-143">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c517f-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c517f-144">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="c517f-144">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c517f-145">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="c517f-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c517f-146">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c517f-146">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="c517f-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c517f-147">See also</span></span>

- [<span data-ttu-id="c517f-148">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="c517f-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- <span data-ttu-id="c517f-149">[Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c517f-149">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
