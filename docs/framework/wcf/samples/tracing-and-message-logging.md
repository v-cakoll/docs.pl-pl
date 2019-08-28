---
title: Śledzenie i rejestrowanie komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: a58541b7d50d83d1e39d7c9dd9c58be4111ec494
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038737"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="cb9f1-102">Śledzenie i rejestrowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="cb9f1-102">Tracing and Message Logging</span></span>
<span data-ttu-id="cb9f1-103">Ten przykład pokazuje, jak włączyć śledzenie i rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="cb9f1-104">Wynikowe ślady i dzienniki komunikatów są wyświetlane za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cb9f1-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="cb9f1-105">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="cb9f1-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb9f1-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="cb9f1-107">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="cb9f1-107">Tracing</span></span>  
 <span data-ttu-id="cb9f1-108">Windows Communication Foundation (WCF) używa mechanizmu śledzenia zdefiniowanego w <xref:System.Diagnostics> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="cb9f1-109">W tym modelu śledzenia dane śledzenia są tworzone przez źródła śledzenia wdrażane przez aplikacje.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="cb9f1-110">Każde źródło jest identyfikowane przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-110">Each source is identified by a name.</span></span> <span data-ttu-id="cb9f1-111">Użytkownicy śledzenia tworzą detektory śledzenia dla źródeł śledzenia, dla których chcą pobrać informacje.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="cb9f1-112">Aby odbierać dane śledzenia, należy utworzyć odbiornik dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="cb9f1-113">W programie WCF można to zrobić, dodając następujący kod do pliku konfiguracji usługi lub klienta, ustawiając źródło `switchValue`śledzenia modelu usługi:</span><span class="sxs-lookup"><span data-stu-id="cb9f1-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
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
  
 <span data-ttu-id="cb9f1-114">Więcej informacji o źródłach śledzenia znajduje się w sekcji Źródło śledzenia w temacie [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) .</span><span class="sxs-lookup"><span data-stu-id="cb9f1-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="cb9f1-115">Śledzenie działań i Propagacja</span><span class="sxs-lookup"><span data-stu-id="cb9f1-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="cb9f1-116">Włączenie i `propagateActivity` ustawienie`true` w`system.ServiceModel` źródła śledzenia dla klienta i usługi zapewnia korelację śladów w jednostkach logicznych przetwarzania (działania), między działaniami w punktach końcowych ( `ActivityTracing` za pośrednictwem transferów działań) i między działaniami obejmującymi wiele punktów końcowych (za pośrednictwem propagacji identyfikatora działania).</span><span class="sxs-lookup"><span data-stu-id="cb9f1-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="cb9f1-117">Te trzy mechanizmy (działania, transfery i propagacje) mogą pomóc w szybkim wyszukiwaniu głównej przyczyny błędu za pomocą narzędzia Podgląd śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="cb9f1-118">Aby uzyskać więcej informacji, zobacz [Korzystanie z przeglądarki śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="cb9f1-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="cb9f1-119">Można zwiększyć śledzenie dostarczone przez element ServiceModel, tworząc zdefiniowane przez użytkownika ślady aktywności.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="cb9f1-120">Śledzenie działań zdefiniowane przez użytkownika umożliwia użytkownikowi tworzenie działań śledzenia:</span><span class="sxs-lookup"><span data-stu-id="cb9f1-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
- <span data-ttu-id="cb9f1-121">Grupuj ślady na jednostki logiczne pracy.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-121">Group traces into logical units of work.</span></span>  
  
- <span data-ttu-id="cb9f1-122">Skorelowanie działań przy użyciu transferów i propagacji.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-122">Correlate activities through transfers and propagation.</span></span>  
  
- <span data-ttu-id="cb9f1-123">Obniżenie kosztu wydajności śledzenia WCF (na przykład koszt miejsca na dysku w pliku dziennika).</span><span class="sxs-lookup"><span data-stu-id="cb9f1-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="cb9f1-124">Aby uzyskać więcej informacji na temat śledzenia aktywności zdefiniowanej przez użytkownika, zobacz Rozszerzanie przykładu [śledzenia](../../../../docs/framework/wcf/samples/extending-tracing.md) .</span><span class="sxs-lookup"><span data-stu-id="cb9f1-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="cb9f1-125">Rejestrowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="cb9f1-125">Message Logging</span></span>  
 <span data-ttu-id="cb9f1-126">Rejestrowanie komunikatów można włączyć zarówno dla klienta, jak i usługi dowolnej aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="cb9f1-127">Aby włączyć rejestrowanie komunikatów, należy dodać następujący kod do klienta lub usługi:</span><span class="sxs-lookup"><span data-stu-id="cb9f1-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
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
  
 <span data-ttu-id="cb9f1-128">Po zarejestrowaniu komunikatu typ śledzenia zależy od tego, czy jest on śledzony na kliencie, czy na serwerze.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="cb9f1-129">Na przykład komunikat "Add", który jest wysyłany do klienta, jest śledzony w kategorii "TransportWrite" na kliencie, podczas gdy ten sam komunikat jest śledzony w kategorii "TransportRead" w usłudze.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="cb9f1-130">Skonfiguruj odbiornik śledzenia, dodając następujący kod do <xref:System.Diagnostics> sekcji pliku App. config klienta lub pliku Web. config usługi:</span><span class="sxs-lookup"><span data-stu-id="cb9f1-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
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
  
 <span data-ttu-id="cb9f1-131">Komunikaty są rejestrowane w formacie XML w katalogu docelowym określonym w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb9f1-132">Pliki śledzenia nie są tworzone bez wstępnego utworzenia katalogu dziennika.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="cb9f1-133">Upewnij się, że katalog C:\logs\ istnieje lub określ alternatywny katalog rejestrowania w konfiguracji odbiornika.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="cb9f1-134">Aby uzyskać więcej informacji, zobacz instrukcje wstępne Instalatora na końcu tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="cb9f1-135">Więcej informacji o rejestrowaniu komunikatów znajduje się w temacie [Konfigurowanie rejestrowania komunikatów](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) .</span><span class="sxs-lookup"><span data-stu-id="cb9f1-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cb9f1-136">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="cb9f1-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cb9f1-137">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb9f1-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cb9f1-138">Przed uruchomieniem przykładu śledzenia i rejestrowania komunikatów Utwórz katalog C:\logs\ dla usługi, aby napisać pliki. svclog do programu.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="cb9f1-139">Nazwa tego katalogu jest zdefiniowana w pliku konfiguracji jako ścieżka śledzenia i komunikatów, które mają być rejestrowane i można je zmienić.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="cb9f1-140">Przyznaj usłudze sieciowej dostępu zapis do katalogu dzienników.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3. <span data-ttu-id="cb9f1-141">Aby skompilować C# C++lub Visual Basic wersję .NET rozwiązania, należy postępować zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb9f1-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="cb9f1-142">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb9f1-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cb9f1-143">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cb9f1-144">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="cb9f1-144">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="cb9f1-145">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb9f1-146">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cb9f1-146">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="cb9f1-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb9f1-147">See also</span></span>

- [<span data-ttu-id="cb9f1-148">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="cb9f1-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="cb9f1-149">Przykłady monitorowania oprogramowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="cb9f1-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
