---
title: Korelacja rozwiązywania problemów
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: be48a55a87d199829de4038e7e2a7642c102acf2
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976017"
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="fb1e8-102">Korelacja rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="fb1e8-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="fb1e8-103">Korelacja jest używana do powiązania komunikatów usługi przepływu pracy ze sobą i do prawidłowego wystąpienia przepływu pracy, ale jeśli nie jest prawidłowo skonfigurowana, komunikaty nie będą odbierane, a aplikacje nie będą działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="fb1e8-104">Ten temat zawiera omówienie kilku metod rozwiązywania problemów z korelacją, a także listę typowych problemów, które mogą wystąpić w przypadku korzystania z korelacji.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>

## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="fb1e8-105">Obsługuj zdarzenie UnknownMessageReceived</span><span class="sxs-lookup"><span data-stu-id="fb1e8-105">Handle the UnknownMessageReceived Event</span></span>
 <span data-ttu-id="fb1e8-106">Zdarzenie <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> występuje po odebraniu przez usługę nieznanego komunikatu, w tym komunikatów, które nie mogą być skorelowane z istniejącym wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="fb1e8-107">W przypadku usług samoobsługowych to zdarzenie może być obsługiwane w aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-107">For self-hosted services, this event can be handled in the host application.</span></span>

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 <span data-ttu-id="fb1e8-108">W przypadku usług hostowanych w sieci Web to zdarzenie może być obsługiwane przez wyznaczanie klasy z <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> i zastępowanie <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>

```csharp
class CustomFactory : WorkflowServiceHostFactory
{
    protected override WorkflowServiceHost CreateWorkflowServiceHost(Activity activity, Uri[] baseAddresses)
    {
        // Create the WorkflowServiceHost.
        WorkflowServiceHost host = new WorkflowServiceHost(activity, baseAddresses);

        // Handle the UnknownMessageReceived event.
        host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
        {
            Console.WriteLine("Unknown Message Received:");
            Console.WriteLine(e.Message);
        };

        return host;
    }
}
```

 <span data-ttu-id="fb1e8-109">Ten niestandardowy <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> można następnie określić w pliku `svc` dla usługi.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>

`<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>`

 <span data-ttu-id="fb1e8-110">Po wywołaniu tej procedury obsługi wiadomości można pobrać przy użyciu właściwości <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>i będzie wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <To s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://localhost:8080/OrderService</To>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
  </s:Header>
  <s:Body>
    <AddItem xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItem>
  </s:Body>
</s:Envelope>
```

 <span data-ttu-id="fb1e8-111">Inspekcja komunikatów wysłanych do procedury obsługi <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> może przedstawiać wskazówki dotyczące przyczyny nieskorelowania komunikatu z wystąpieniem usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="fb1e8-112">Monitorowanie postępu przepływu pracy przy użyciu funkcji śledzenia</span><span class="sxs-lookup"><span data-stu-id="fb1e8-112">Use Tracking to Monitor the Progress of the Workflow</span></span>
 <span data-ttu-id="fb1e8-113">Śledzenie umożliwia monitorowanie postępu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="fb1e8-114">Domyślnie śledzenie rekordów jest emitowane w przypadku zdarzeń cyklu życia przepływu pracy, zdarzeń cyklu życia aktywności, propagacji błędów i wznowienia zakładki.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="fb1e8-115">Ponadto niestandardowe rekordy śledzenia mogą być emitowane przez działania niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="fb1e8-116">W przypadku rozwiązywania problemów z korelacją rekordy śledzenia działań, rekordy wznawiania z zakładkami i rekordy propagacji błędów są najbardziej przydatne.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="fb1e8-117">Rekordy śledzenia działań mogą służyć do określenia bieżącego postępu przepływu pracy i mogą ułatwić identyfikację działania komunikatów oczekujących na komunikaty.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="fb1e8-118">Rekordy wznawiania zakładki są przydatne, ponieważ wskazują, że komunikat został odebrany przez przepływ pracy, a rekordy propagacji błędów zawierają rekord błędów w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="fb1e8-119">Aby włączyć śledzenie, określ odpowiednie <xref:System.Activities.Tracking.TrackingParticipant> w <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="fb1e8-120">W poniższym przykładzie `ConsoleTrackingParticipant` (z niestandardowego przykładu [śledzenia](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) ) jest konfigurowany przy użyciu domyślnego profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 <span data-ttu-id="fb1e8-121">Uczestnik śledzenia, taki jak ConsoleTrackingParticipant, jest przydatny w przypadku samodzielnej usługi przepływu pracy, która ma okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="fb1e8-122">W przypadku usługi hostowanej przez sieć Web Uczestnik śledzenia, który rejestruje informacje o śledzeniu do magazynu trwałego, powinien być używany, taki jak wbudowana <xref:System.Activities.Tracking.EtwTrackingParticipant>lub uczestnik śledzenia niestandardowego, który rejestruje informacje w pliku.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file.</span></span>

 <span data-ttu-id="fb1e8-123">Aby uzyskać więcej informacji na temat śledzenia i konfigurowania śledzenia dla usługi przepływu pracy hostowanej w sieci Web, zobacz [śledzenie i śledzenie przepływów pracy](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Konfigurowanie śledzenia dla przepływu pracy](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)oraz próbkowanie próbek [ &#91;WF&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) .</span><span class="sxs-lookup"><span data-stu-id="fb1e8-123">For more information about tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>

## <a name="use-wcf-tracing"></a><span data-ttu-id="fb1e8-124">Korzystanie z funkcji śledzenia WCF</span><span class="sxs-lookup"><span data-stu-id="fb1e8-124">Use WCF Tracing</span></span>
 <span data-ttu-id="fb1e8-125">Śledzenie WCF umożliwia śledzenie przepływów komunikatów do i z usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="fb1e8-126">Te informacje śledzenia są przydatne podczas rozwiązywania problemów z korelacją, szczególnie w przypadku korelacji opartej na zawartości.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="fb1e8-127">Aby włączyć śledzenie, określ żądane detektory śledzenia w sekcji `system.diagnostics` pliku `web.config`, jeśli usługa przepływu pracy jest hostowana w sieci Web lub plik `app.config`, jeśli usługa przepływu pracy jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="fb1e8-128">Aby dołączyć zawartość komunikatów w pliku śledzenia, określ `true` dla `logEntireMessage` w elemencie `messageLogging` w sekcji `diagnostics` w `system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="fb1e8-129">W poniższym przykładzie informacje o śledzeniu, w tym zawartość wiadomości, są skonfigurowane tak, aby były zapisywane do pliku o nazwie `service.svclog`.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.ServiceModel" switchValue="Information" propagateActivity="true">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
      <source name="System.ServiceModel.MessageLogging">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
    </sources>

    <sharedListeners>
      <add name="corr" type="System.Diagnostics.XmlWriterTraceListener" initializeData="c:\logs\service.svclog">
      </add>
    </sharedListeners>
  </system.diagnostics>

  <system.serviceModel>
    <diagnostics>
      <messageLogging logEntireMessage="true" logMalformedMessages="false"
         logMessagesAtServiceLevel="false" logMessagesAtTransportLevel="true" maxSizeOfMessageToLog="2147483647">
      </messageLogging>
    </diagnostics>
  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="fb1e8-130">Aby wyświetlić informacje o śledzeniu zawarte w `service.svclog`, używany jest [Narzędzie przeglądarka śledzenia usługi (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="fb1e8-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="fb1e8-131">Jest to szczególnie przydatne podczas rozwiązywania problemów z korelacją opartą na zawartości, ponieważ można wyświetlić zawartość komunikatu i zobaczyć dokładnie to, co jest przesyłane, oraz czy jest ona zgodna <xref:System.ServiceModel.CorrelationQuery> z korelacją opartą na zawartości.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> <span data-ttu-id="fb1e8-132">Aby uzyskać więcej informacji na temat śledzenia WCF, zobacz [narzędzie Podgląd śledzenia usług (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)i [Używanie śledzenia do rozwiązywania problemów z aplikacją](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="fb1e8-132">For more information about WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="fb1e8-133">Typowe problemy z korelacją z wymianą kontekstu</span><span class="sxs-lookup"><span data-stu-id="fb1e8-133">Common Context Exchange Correlation Issues</span></span>
 <span data-ttu-id="fb1e8-134">Niektóre typy korelacji wymagają, aby do poprawnego działania korelacji był używany konkretny typ powiązania.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="fb1e8-135">Przykłady obejmują korelację typu żądanie-odpowiedź, która wymaga dwukierunkowego powiązania, takiego jak <xref:System.ServiceModel.BasicHttpBinding>, oraz korelacji z wymianą kontekstu, która wymaga powiązania opartego na kontekście, takiego jak <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="fb1e8-136">Większość powiązań obsługuje operacje dwukierunkowe, dlatego nie jest to typowy problem związany z korelacją typu żądanie-odpowiedź, ale istnieje tylko kilku powiązań opartych na kontekście, w tym <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>i <xref:System.ServiceModel.NetTcpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="fb1e8-137">Jeśli jedno z tych powiązań nie jest używane, początkowe wywołanie usługi przepływu pracy powiedzie się, ale kolejne wywołania zakończą się niepowodzeniem z następującym <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>

```output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 <span data-ttu-id="fb1e8-138">Informacje kontekstowe, które są używane dla korelacji kontekstu, mogą być zwracane przez <xref:System.ServiceModel.Activities.SendReply> do działania <xref:System.ServiceModel.Activities.Receive>, które inicjuje korelację kontekstu przy użyciu operacji dwukierunkowej, lub może być określony przez obiekt wywołujący, jeśli operacja jest jednokierunkowa.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="fb1e8-139">Jeśli kontekst nie jest wysyłany przez obiekt wywołujący lub zwracany przez usługę przepływu pracy, ten sam <xref:System.ServiceModel.FaultException> opisany wcześniej zostanie zwrócony po wywołaniu kolejnej operacji.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>

## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="fb1e8-140">Typowe problemy z korelacją żądań i odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="fb1e8-140">Common Request-Reply Correlation Issues</span></span>
 <span data-ttu-id="fb1e8-141">Korelacja typu żądanie-odpowiedź jest używana z parowaniem <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> w celu zaimplementowania operacji dwukierunkowej w usłudze przepływu pracy i z <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> para, która wywołuje operację dwukierunkową w innej usłudze sieci Web.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-141">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="fb1e8-142">W przypadku wywoływania operacji dwukierunkowej w usłudze WCF usługa może być tradycyjnie zastrzeżonym, autonomiczną usługą WCF lub usługą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-142">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based WCF service or it can be a workflow service.</span></span> <span data-ttu-id="fb1e8-143">Aby można było użyć korelacji typu żądanie-odpowiedź, należy użyć powiązania dwukierunkowego, takiego jak <xref:System.ServiceModel.BasicHttpBinding>, i operacje muszą być dwukierunkowe.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-143">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>

 <span data-ttu-id="fb1e8-144">Jeśli usługa przepływu pracy ma równoległe operacje dwukierunkowe lub nakładające się <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> lub <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply>, to niejawne zarządzanie uchwytami korelacji zapewniane przez <xref:System.ServiceModel.Activities.WorkflowServiceHost> może być niewystarczające, szczególnie w scenariuszach o dużej obciążeniu, a komunikaty mogą nie być poprawnie kierowane.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-144">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="fb1e8-145">Aby zapobiec wystąpieniu tego problemu, zalecamy, aby zawsze jawnie określić <xref:System.ServiceModel.Activities.CorrelationHandle> podczas korzystania z korelacji z odpowiedzią na żądanie.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-145">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="fb1e8-146">W przypadku korzystania z szablonów **SendAndReceiveReply** i **ReceiveAndSendReply** z sekcji Obsługa komunikatów w **przyborniku** w Projektancie przepływów pracy, <xref:System.ServiceModel.Activities.CorrelationHandle> jest jawnie konfigurowana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-146">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="fb1e8-147">Podczas kompilowania przepływu pracy przy użyciu kodu <xref:System.ServiceModel.Activities.CorrelationHandle> jest określony w <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> pierwszego działania w parze.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-147">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="fb1e8-148">W poniższym przykładzie działanie <xref:System.ServiceModel.Activities.Receive> jest skonfigurowane z jawnym <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> określonym w <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-148">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>

```csharp
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();

Receive StartOrder = new Receive
{
    CanCreateInstance = true,
    ServiceContractName = OrderContractName,
    OperationName = "StartOrder",
    CorrelationInitializers =
    {
        new RequestReplyCorrelationInitializer
        {
            CorrelationHandle = RRHandle
        }
    }
};

SendReply ReplyToStartOrder = new SendReply
{
    Request = StartOrder,
    Content = ... // Contains the return value, if any.
};

// Construct a workflow using StartOrder and ReplyToStartOrder.
```

 <span data-ttu-id="fb1e8-149">Nie jest dozwolone utrzymywanie między <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> para lub <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply>.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-149">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="fb1e8-150">Tworzona jest strefa nie utrwalania, która obowiązuje do momentu zakończenia obu działań.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-150">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="fb1e8-151">Jeśli działanie, takie jak działanie opóźnienia, znajduje się w tej strefie no-utrwalania i powoduje, że przepływ pracy staje się bezczynna, przepływ pracy nie będzie trwał nawet wtedy, gdy host jest skonfigurowany do utrwalania przepływów pracy, gdy staną się bezczynne.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-151">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="fb1e8-152">Jeśli działanie, takie jak działanie utrwalania, próbuje jawnie pozostać w strefie no-utrwalania, zostanie zgłoszony wyjątek krytyczny, przepływ pracy zostanie przerwany, a <xref:System.ServiceModel.FaultException> jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-152">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="fb1e8-153">Komunikat o wyjątku krytycznym to "System. InvalidOperationException: działania utrwalania nie mogą być zawarte w blokach trwałości".</span><span class="sxs-lookup"><span data-stu-id="fb1e8-153">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="fb1e8-154">Ten wyjątek nie jest zwracany do obiektu wywołującego, ale można go zaobserwować, jeśli śledzenie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-154">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="fb1e8-155">Komunikat dla <xref:System.ServiceModel.FaultException> zwróconego do obiektu wywołującego to "nie można wykonać operacji, ponieważ obiekt WorkflowInstance" 5836145b-7da2-49d0-a052-a49162adeab6 "został ukończony.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-155">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>

 <span data-ttu-id="fb1e8-156">Aby uzyskać więcej informacji na temat korelacji z żądaniem odpowiedzi, zobacz [żądanie-odpowiedź](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="fb1e8-156">For more information about request-reply correlation, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span></span>

## <a name="common-content-correlation-issues"></a><span data-ttu-id="fb1e8-157">Typowe problemy związane z korelacją zawartości</span><span class="sxs-lookup"><span data-stu-id="fb1e8-157">Common Content Correlation Issues</span></span>
 <span data-ttu-id="fb1e8-158">Korelacja oparta na zawartości jest używana, gdy usługa przepływu pracy odbiera wiele komunikatów, a dane w komunikatach z wymienianymi informacjami identyfikują żądane wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-158">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="fb1e8-159">Korelacja oparta na zawartości używa tych danych w komunikacie, na przykład numeru klienta lub identyfikatora zamówienia, do przesyłania komunikatów do prawidłowego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-159">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="fb1e8-160">W tej sekcji opisano kilka typowych problemów, które mogą wystąpić podczas korzystania z korelacji opartej na zawartości.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-160">This section describes several common issues that may occur when using content-based correlation.</span></span>

### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="fb1e8-161">Upewnij się, że dane identyfikacyjne są unikatowe</span><span class="sxs-lookup"><span data-stu-id="fb1e8-161">Ensure the Identifying Data Is Unique</span></span>
 <span data-ttu-id="fb1e8-162">Dane używane do identyfikowania wystąpienia są skrótem do klucza korelacji.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-162">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="fb1e8-163">Należy pamiętać, aby zagwarantować, że dane, które są używane na potrzeby korelacji, są unikatowe lub mogą wystąpić konflikty w kluczowym skrócie i powodować błędne trasy komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-163">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="fb1e8-164">Na przykład korelacja oparta tylko na nazwie klienta może prowadzić do kolizji, ponieważ może istnieć wielu klientów, którzy mają tę samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-164">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="fb1e8-165">Dwukropek (:) nie należy używać jako części danych, które są używane do skorelowania wiadomości, ponieważ jest ona już używana do rozgraniczania klucza i wartości zapytania komunikatu w celu utworzenia ciągu, który jest następnie używany do mieszania.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-165">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="fb1e8-166">Jeśli jest używana trwałość, upewnij się, że bieżące dane identyfikacyjne nie były używane przez poprzednio utrwalone wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-166">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="fb1e8-167">Tymczasowe wyłączenie trwałości może pomóc w zidentyfikowaniu tego problemu.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-167">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="fb1e8-168">Śledzenie WCF może służyć do wyświetlania obliczonego klucza korelacji i jest przydatne do debugowania tego rodzaju problemu.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-168">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>

### <a name="race-conditions"></a><span data-ttu-id="fb1e8-169">Warunki wyścigu</span><span class="sxs-lookup"><span data-stu-id="fb1e8-169">Race Conditions</span></span>
 <span data-ttu-id="fb1e8-170">Istnieje niewielki odstęp czasu między usługą otrzymującą komunikat i faktycznie inicjowaną korelacją, podczas gdy komunikaty uzupełniające zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-170">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="fb1e8-171">Jeśli usługa przepływu pracy inicjuje korelację opartą na zawartości przy użyciu danych przesyłanych z klienta w ramach operacji jednokierunkowych, a obiekt wywołujący wysyła natychmiastowe komunikaty monitujące, te komunikaty zostaną zignorowane w tym interwale.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-171">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="fb1e8-172">Można to uniknąć przy użyciu operacji dwukierunkowej w celu zainicjowania korelacji lub użycia <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-172">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>

### <a name="correlation-query-issues"></a><span data-ttu-id="fb1e8-173">Problemy z kwerendą korelacji</span><span class="sxs-lookup"><span data-stu-id="fb1e8-173">Correlation Query Issues</span></span>
 <span data-ttu-id="fb1e8-174">Zapytania korelacji służą do określania, które dane w wiadomości są używane do skorelowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-174">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="fb1e8-175">Te dane są określane przy użyciu kwerendy XPath.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-175">This data is specified by using an XPath query.</span></span> <span data-ttu-id="fb1e8-176">Jeśli komunikaty do usługi nie są wysyłane, mimo że wszystko wydaje się prawidłowe, jedna strategia rozwiązywania problemów polega na określeniu wartości literału, która pasuje do wartości danych komunikatu zamiast zapytania XPath.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-176">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="fb1e8-177">Aby określić wartość literału, użyj funkcji `string`.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-177">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="fb1e8-178">W poniższym przykładzie <xref:System.ServiceModel.MessageQuerySet> jest skonfigurowany do używania wartości literału `11445` dla `OrderId`, a zapytanie XPath jest oznaczone jako komentarz.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-178">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>

```csharp
MessageQuerySet = new MessageQuerySet
{
    {
        "OrderId",
        //new XPathMessageQuery("sm:body()/tempuri:StartOrderResponse/tempuri:OrderId")
        new XPathMessageQuery("string('11445')")
    }
}
```

 <span data-ttu-id="fb1e8-179">Jeśli zapytanie XPath jest skonfigurowane nieprawidłowo, tak że nie są pobierane żadne dane korelacji, zwracany jest błąd z następującym komunikatem: "zapytanie korelacji zwróciło pusty zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-179">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="fb1e8-180">Upewnij się, że zapytania korelacji dla punktu końcowego są poprawnie skonfigurowane. "</span><span class="sxs-lookup"><span data-stu-id="fb1e8-180">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="fb1e8-181">Jednym z szybkim sposobem rozwiązania tego problemu jest zastąpienie zapytania XPath wartością literału, zgodnie z opisem w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-181">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="fb1e8-182">Ten problem może wystąpić, jeśli używasz konstruktora kwerend XPath w oknach dialogowych **Dodaj inicjatory korelacji** lub **definicję CorrelatesOn** , a usługa przepływu pracy używa kontraktów komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-182">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="fb1e8-183">W poniższym przykładzie zdefiniowano klasę kontraktu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-183">In the following example, a message contract class is defined.</span></span>

```csharp
[MessageContract]
public class AddItemMessage
{
    [MessageHeader]
    public string CartId;

    [MessageBodyMember]
    public string Item;
}
```

 <span data-ttu-id="fb1e8-184">Ten kontrakt komunikatu jest używany przez działanie <xref:System.ServiceModel.Activities.Receive> w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-184">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="fb1e8-185">`CartId` w nagłówku wiadomości służy do skorelowania komunikatu z właściwym wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-185">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="fb1e8-186">Jeśli zapytanie XPath, które pobiera `CartId` jest tworzone przy użyciu okna dialogowego korelacji w Projektancie przepływu pracy, generowane jest następujące nieprawidłowe zapytanie XPath.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-186">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 <span data-ttu-id="fb1e8-187">To zapytanie XPath byłoby poprawne, jeśli działanie <xref:System.ServiceModel.Activities.Receive> używało parametrów dla danych, ale ponieważ używa ona kontraktu komunikatu, jest on nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-187">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="fb1e8-188">Następujące zapytanie XPath jest poprawnym zapytaniem XPath, aby pobrać `CartId` z nagłówka.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-188">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>

```
sm:header()/tempuri:CartId
```

<span data-ttu-id="fb1e8-189">Można to potwierdzić, badając treść wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-189">This can be confirmed by examining the body of the message.</span></span>

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
    <h:CartId xmlns:h="http://tempuri.org/">80c95b41-c98d-4660-a6c1-99412206e54c</h:CartId>
  </s:Header>
  <s:Body>
    <AddItemMessage xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItemMessage>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="fb1e8-190">Poniższy przykład przedstawia działanie <xref:System.ServiceModel.Activities.Receive> skonfigurowane dla operacji `AddItem`, która używa poprzedniego kontraktu komunikatu do odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-190">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="fb1e8-191">Zapytanie XPath zostało poprawnie skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-191">The XPath query is correctly configured.</span></span>

```xaml
<Receive CorrelatesWith="[CCHandle] OperationName="AddItem" ServiceContractName="p:IService">
  <Receive.CorrelatesOn>
    <XPathMessageQuery x:Key="key1">
      <XPathMessageQuery.Namespaces>
        <ssx:XPathMessageContextMarkup>
          <x:String x:Key="xg0">http://schemas.datacontract.org/2004/07/MessageContractWFService</x:String>
        </ssx:XPathMessageContextMarkup>
      </XPathMessageQuery.Namespaces>sm:header()/tempuri:CartId</XPathMessageQuery>
  </Receive.CorrelatesOn>
  <ReceiveMessageContent DeclaredMessageType="m:AddItemMessage">
    <p1:OutArgument x:TypeArguments="m:AddItemMessage">[AddItemMessage]</p1:OutArgument>
  </ReceiveMessageContent>
</Receive>
```
