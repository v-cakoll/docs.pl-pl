---
title: Korelacja rozwiązywania problemów
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: fecfaf7374823bb19a4ad3d7f6cb2dbbdf139703
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027926"
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="a675f-102">Korelacja rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="a675f-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="a675f-103">Korelacja służy do wiązania komunikatów usługi przepływu pracy i wystąpienia poprawne przepływu pracy, ale jeśli nie jest poprawnie skonfigurowany, nie otrzyma wiadomości i aplikacje nie będą działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="a675f-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="a675f-104">Ten temat zawiera omówienie kilku metod w celu rozwiązywania problemów korelacji i wyświetla także niektóre typowe problemy, które mogą wystąpić, gdy używasz korelacji.</span><span class="sxs-lookup"><span data-stu-id="a675f-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>

## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="a675f-105">Obsługuj zdarzenie UnknownMessageReceived</span><span class="sxs-lookup"><span data-stu-id="a675f-105">Handle the UnknownMessageReceived Event</span></span>
 <span data-ttu-id="a675f-106"><xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> Zdarzenie występuje, gdy nieznany komunikat jest odbierany przez usługę, w tym komunikaty, które nie mogą zostać skorelowane z istniejącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a675f-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="a675f-107">Samodzielnie hostowany usług tego zdarzenia mogą być obsługiwane w aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="a675f-107">For self-hosted services, this event can be handled in the host application.</span></span>

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 <span data-ttu-id="a675f-108">W przypadku usług hostowanych w sieci Web to zdarzenie może zostać obsłużony przez wyprowadzanie klasy z <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> i zastępowanie <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="a675f-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>

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

 <span data-ttu-id="a675f-109">To niestandardowe <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> można określić w `svc` pliku dla usługi.</span><span class="sxs-lookup"><span data-stu-id="a675f-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>

```
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>
```

 <span data-ttu-id="a675f-110">Po wywołaniu tego programu obsługi wiadomości mogą być pobierane przy użyciu <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> właściwość <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>i będą podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="a675f-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>

```Output
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

 <span data-ttu-id="a675f-111">Inspekcja komunikaty wysyłane do <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> program obsługi może zapewnić wskazówek dotyczących przyczyny wiadomość nie odnoszą się do wystąpienia usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a675f-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="a675f-112">Korzystanie ze śledzenia można monitorować postęp przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a675f-112">Use Tracking to Monitor the Progress of the Workflow</span></span>
 <span data-ttu-id="a675f-113">Śledzenie zapewnia sposób, aby monitorować postęp przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a675f-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="a675f-114">Domyślnie są emitowane rekordów śledzenia zdarzeń cyklu życia przepływu pracy, zdarzenia cyklu życia działań, propagacji błędów i wznowienie zakładki.</span><span class="sxs-lookup"><span data-stu-id="a675f-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="a675f-115">Ponadto niestandardowe rekordy śledzenia może być emitowana przez działania niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="a675f-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="a675f-116">Działania śledzenia rekordów, zakładki wznowienie rekordów i rekordy propagacji błędów są najbardziej przydatne, gdy korelacja rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="a675f-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="a675f-117">Śledzenie rekordów działań może służyć do określenia Bieżący postęp przepływu pracy i może ułatwić identyfikację, których działanie komunikatów oczekiwaniem na komunikaty.</span><span class="sxs-lookup"><span data-stu-id="a675f-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="a675f-118">Zakładki wznowienie rekordów są przydatne, ponieważ wskazują, że wiadomość została odebrana przez przepływ pracy, oraz rekordy propagacji błędów rekord wszystkie błędy w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="a675f-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="a675f-119">Aby włączyć śledzenie, określ żądany <xref:System.Activities.Tracking.TrackingParticipant> w <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> z <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a675f-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="a675f-120">W poniższym przykładzie `ConsoleTrackingParticipant` (z [niestandardowe śledzenia](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) przykładowy) jest konfigurowana przy użyciu domyślnego profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a675f-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 <span data-ttu-id="a675f-121">Uczestnika śledzenia, takie jak ConsoleTrackingParticipant przydaje się do usługi samodzielnie hostowanej przepływu pracy, z okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="a675f-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="a675f-122">W przypadku usługi hostowanej w sieci Web śledzenia uczestnika, który rejestruje informacje śledzenia do trwałego magazynu powinny być używane takie jak wbudowane <xref:System.Activities.Tracking.EtwTrackingParticipant>, lub uczestnikiem niestandardowe śledzenia, który rejestruje informacje w pliku.</span><span class="sxs-lookup"><span data-stu-id="a675f-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file.</span></span>

 <span data-ttu-id="a675f-123">Aby uzyskać więcej informacji na temat śledzenia i Konfigurowanie śledzenia dla usługi hostowanej w sieci Web przepływu pracy, zobacz [przepływu pracy i śledzenie](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Konfigurowanie śledzenia przepływu pracy](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)i [ Śledzenie &#91;WF — przykłady&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) przykłady.</span><span class="sxs-lookup"><span data-stu-id="a675f-123">For more information about tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>

## <a name="use-wcf-tracing"></a><span data-ttu-id="a675f-124">Użyj śledzenia WCF</span><span class="sxs-lookup"><span data-stu-id="a675f-124">Use WCF Tracing</span></span>
 <span data-ttu-id="a675f-125">Śledzenie programu WCF zapewnia śledzenie przepływu wiadomości do i z usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a675f-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="a675f-126">Te informacje śledzenia jest przydatne podczas rozwiązywania problemów korelacji, szczególnie w przypadku korelacji na podstawie zawartości.</span><span class="sxs-lookup"><span data-stu-id="a675f-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="a675f-127">Aby włączyć śledzenie, należy określić żądanego śledzenia słuchaczy w `system.diagnostics` części `web.config` plik, jeśli usługa przepływu pracy jest hostowane w sieci Web lub `app.config` plik, jeśli usługa przepływu pracy jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="a675f-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="a675f-128">Aby dołączyć zawartość wiadomości w pliku śledzenia, należy określić `true` dla `logEntireMessage` w `messageLogging` element `diagnostics` części `system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="a675f-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="a675f-129">W poniższym przykładzie skonfigurowano informacji śledzenia, w tym treść wiadomości, są zapisywane w pliku o nazwie `service.svclog`.</span><span class="sxs-lookup"><span data-stu-id="a675f-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>

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

 <span data-ttu-id="a675f-130">Aby wyświetlić informacje o śledzeniu, który jest zawarty w `service.svclog`, [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) jest używany.</span><span class="sxs-lookup"><span data-stu-id="a675f-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="a675f-131">Jest to szczególnie przydatne podczas rozwiązywania problemów na podstawie zawartości korelacji problemy, ponieważ możesz wyświetlać zawartość wiadomości i dokładnie co to jest przekazywana, i czy jest on zgodny <xref:System.ServiceModel.CorrelationQuery> dla korelacji na podstawie zawartości.</span><span class="sxs-lookup"><span data-stu-id="a675f-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> <span data-ttu-id="a675f-132">Aby uzyskać więcej informacji na temat śledzenia WCF, zobacz [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), i [przy użyciu śledzenia Rozwiązywanie problemów z aplikacją](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="a675f-132">For more information about WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="a675f-133">Typowe problemy korelacja wymiany kontekstu</span><span class="sxs-lookup"><span data-stu-id="a675f-133">Common Context Exchange Correlation Issues</span></span>
 <span data-ttu-id="a675f-134">Niektóre rodzaje korelacji wymagają, że określonego typu powiązania służy do korelacji działała prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="a675f-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="a675f-135">Przykłady obejmują korelacji "żądanie-odpowiedź", która wymaga dwukierunkowego powiązania w takich jak <xref:System.ServiceModel.BasicHttpBinding>i korelacja wymiany kontekstu, co wymaga na podstawie kontekstu wiązania takich jak <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="a675f-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="a675f-136">Większość powiązania obsługi operacji dwukierunkową, co nie jest to typowy problem dla korelacji "żądanie-odpowiedź", ale istnieje kilka tylko na podstawie kontekstu powiązania, łącznie z <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, i <xref:System.ServiceModel.NetTcpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="a675f-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="a675f-137">Jeśli jedno z tych powiązań, nie jest używany, początkowe wywołanie usługi przepływu pracy zakończy się powodzeniem, ale kolejne wywołania zakończy się niepowodzeniem z następującym <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="a675f-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>

```Output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 <span data-ttu-id="a675f-138">Informacje o kontekście, które jest używane na potrzeby korelacji kontekstu może zostać zwrócony przez <xref:System.ServiceModel.Activities.SendReply> do <xref:System.ServiceModel.Activities.Receive> działanie, które inicjuje korelacji kontekstu, gdy za pomocą dwukierunkowych operacji lub jest on można określić przez obiekt wywołujący, gdy operacja jest jednokierunkowe.</span><span class="sxs-lookup"><span data-stu-id="a675f-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="a675f-139">Jeśli kontekst nie jest wysyłany przez obiekt wywołujący lub zwrócone przez usługi przepływu pracy, a następnie takie same <xref:System.ServiceModel.FaultException> opisanego wcześniej zostanie zwrócona po wywołaniu kolejna operacja.</span><span class="sxs-lookup"><span data-stu-id="a675f-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>

## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="a675f-140">Typowe problemy korelacji "żądanie-odpowiedź"</span><span class="sxs-lookup"><span data-stu-id="a675f-140">Common Request-Reply Correlation Issues</span></span>
 <span data-ttu-id="a675f-141">Korelacja żądań i odpowiedzi jest używany z <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> Paruj, aby zaimplementować dwukierunkowe operacji w usłudze przepływu pracy i <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> parą, która wywołuje dwukierunkowe operacji w innej sieci Web Usługa.</span><span class="sxs-lookup"><span data-stu-id="a675f-141">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="a675f-142">Podczas wywoływania dwukierunkowe operacji usługi WCF, usługa może być albo tradycyjne usługi WCF na podstawie kodu imperatywnego lub może być usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a675f-142">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based WCF service or it can be a workflow service.</span></span> <span data-ttu-id="a675f-143">Aby użyć korelacji "żądanie-odpowiedź" powiązanie dwustronne należy użyć, takie jak <xref:System.ServiceModel.BasicHttpBinding>, i działania muszą być dwukierunkowe.</span><span class="sxs-lookup"><span data-stu-id="a675f-143">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>

 <span data-ttu-id="a675f-144">Jeśli usługa przepływu pracy ma dwukierunkową operacje w równoległego lub nakładający się <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> lub <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary, a następnie niejawne korelacji obsługiwać zarządzanie zapewniane przez <xref:System.ServiceModel.Activities.WorkflowServiceHost>może nie być wystarczające, szczególnie w scenariuszach wysokiej obciążenia, a komunikaty mogą nie być poprawnie kierowane.</span><span class="sxs-lookup"><span data-stu-id="a675f-144">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="a675f-145">Aby zapobiec występowaniu tego problemu, zaleca się, że należy zawsze jawnie określać <xref:System.ServiceModel.Activities.CorrelationHandle> przy użyciu korelacja żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a675f-145">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="a675f-146">Korzystając z **SendAndReceiveReply** i **ReceiveAndSendReply** szablony komunikatów w sekcji **przybornika** w Projektancie przepływu pracy <xref:System.ServiceModel.Activities.CorrelationHandle> jawnie jest konfiguracja domyślna.</span><span class="sxs-lookup"><span data-stu-id="a675f-146">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="a675f-147">Podczas tworzenia przepływu pracy przy użyciu kodu, <xref:System.ServiceModel.Activities.CorrelationHandle> została określona w <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> pierwszego działania w parze.</span><span class="sxs-lookup"><span data-stu-id="a675f-147">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="a675f-148">W poniższym przykładzie <xref:System.ServiceModel.Activities.Receive> działanie jest skonfigurowane z jawną <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> określonych w <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="a675f-148">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>

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

 <span data-ttu-id="a675f-149">Stan trwały nie jest dozwolone między <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary lub <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary.</span><span class="sxs-lookup"><span data-stu-id="a675f-149">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="a675f-150">Tworzona jest strefa no-persist ważny, dopóki oba działania zostały wykonane.</span><span class="sxs-lookup"><span data-stu-id="a675f-150">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="a675f-151">Jeśli działania, takie jak działanie opóźnienia, znajduje się w tej strefie no-persist, powoduje, że przepływ pracy przejdzie w stan bezczynności przepływu pracy nie zostanie utrzymany, nawet wtedy, gdy jej host jest skonfigurowany do utrwalenia przepływów pracy, gdy staną się bezczynności.</span><span class="sxs-lookup"><span data-stu-id="a675f-151">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="a675f-152">Jeśli działania, takie jak działanie utrwalanie próbuje jawnie utrwalanie w strefie nie utrwalanie, wyjątek krytyczny jest zgłaszany, przerwań przepływu pracy, a <xref:System.ServiceModel.FaultException> jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a675f-152">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="a675f-153">Komunikat o wyjątku krytycznego "System.InvalidOperationException: utrwalanie działania nie może być zawarta w blokach nie trwałości.".</span><span class="sxs-lookup"><span data-stu-id="a675f-153">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="a675f-154">Ten wyjątek nie są zwracane do obiektu wywołującego, ale można zaobserwować, jeśli śledzenie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="a675f-154">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="a675f-155">W komunikacie o <xref:System.ServiceModel.FaultException> zwracane do obiektu wywołującego jest "nie można wykonać operacji, ponieważ wystąpienie przepływu pracy"5836145b-7da2 - 49 d 0-a052-a49162adeab6"została ukończona".</span><span class="sxs-lookup"><span data-stu-id="a675f-155">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>

 <span data-ttu-id="a675f-156">Aby uzyskać więcej informacji na temat korelacji "żądanie-odpowiedź" zobacz ["żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="a675f-156">For more information about request-reply correlation, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span></span>

## <a name="common-content-correlation-issues"></a><span data-ttu-id="a675f-157">Typowe problemy zawartości korelacji</span><span class="sxs-lookup"><span data-stu-id="a675f-157">Common Content Correlation Issues</span></span>
 <span data-ttu-id="a675f-158">Korelacja oparta na zawartości jest używane, gdy usługi przepływu pracy otrzymuje wiele wiadomości i element danych w ramach wymiany komunikatów identyfikuje żądaną wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="a675f-158">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="a675f-159">Korelacja oparta na zawartości używa tych danych w komunikacie, takie jak liczba lub kolejność ID klienta do wyznaczania tras dla wystąpienia przepływu pracy poprawne.</span><span class="sxs-lookup"><span data-stu-id="a675f-159">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="a675f-160">W tej sekcji opisano kilka typowych problemów, które mogą wystąpić podczas korzystania na podstawie zawartości korelacji.</span><span class="sxs-lookup"><span data-stu-id="a675f-160">This section describes several common issues that may occur when using content-based correlation.</span></span>

### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="a675f-161">Upewnij się, że dane identyfikacyjne są unikatowe</span><span class="sxs-lookup"><span data-stu-id="a675f-161">Ensure the Identifying Data Is Unique</span></span>
 <span data-ttu-id="a675f-162">Dane, które służy do identyfikowania wystąpienia jest wyznaczana wartość skrótu na klucz korelacji.</span><span class="sxs-lookup"><span data-stu-id="a675f-162">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="a675f-163">Należy uważać, aby zagwarantować, że dane, które jest używane na potrzeby korelacji jest unikatowa w przeciwnym razie kolizji w formie skrótu klucza mogą występować i komunikaty można rozsyłanymi.</span><span class="sxs-lookup"><span data-stu-id="a675f-163">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="a675f-164">Na przykład korelacji, wyłącznie według nazwy klienta może spowodować kolizji, ponieważ może to być wielu klientów, którzy mają taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="a675f-164">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="a675f-165">Dwukropek (:), nie powinien służyć jako część danych, który służy do skorelowania komunikatu, ponieważ jest już używany do ograniczania klucz i wartość w celu utworzenia ciąg, który jest następnie wartość skrótu dla zapytania o komunikat o.</span><span class="sxs-lookup"><span data-stu-id="a675f-165">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="a675f-166">Jeśli trwałości jest używana, upewnij się, czy bieżące dane identyfikacyjne nie został użyty przez wystąpienie utrwalonych wcześniej.</span><span class="sxs-lookup"><span data-stu-id="a675f-166">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="a675f-167">Tymczasowe wyłączenie trwałości pomaga zidentyfikować ten problem.</span><span class="sxs-lookup"><span data-stu-id="a675f-167">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="a675f-168">Śledzenie programu WCF można wyświetlić klucz korelacji obliczeniowe i jest przydatna podczas debugowania rozwiązania tego problemu.</span><span class="sxs-lookup"><span data-stu-id="a675f-168">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>

### <a name="race-conditions"></a><span data-ttu-id="a675f-169">Warunki wyścigu</span><span class="sxs-lookup"><span data-stu-id="a675f-169">Race Conditions</span></span>
 <span data-ttu-id="a675f-170">Istnieje mały odstęp w czasie między usługa odbiera komunikat i korelacji, faktycznie inicjowany, podczas której zostaną zignorowane komunikaty monitujące o.</span><span class="sxs-lookup"><span data-stu-id="a675f-170">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="a675f-171">Jeśli usługa przepływu pracy inicjuje korelacji na podstawie zawartości przy użyciu danych przesyłanych między klientem za pośrednictwem operacji jednokierunkowych, a obiekt wywołujący wysyła natychmiastowego komunikaty monitujące, te wiadomości będą ignorowane w danym przedziale czasu.</span><span class="sxs-lookup"><span data-stu-id="a675f-171">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="a675f-172">To można uniknąć przy użyciu operacji dwukierunkowe zainicjować korelację lub za pomocą <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="a675f-172">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>

### <a name="correlation-query-issues"></a><span data-ttu-id="a675f-173">Korelacja zapytania problemów</span><span class="sxs-lookup"><span data-stu-id="a675f-173">Correlation Query Issues</span></span>
 <span data-ttu-id="a675f-174">Korelacja zapytania są używane do określania, jakie dane w komunikacie służy do skorelowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a675f-174">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="a675f-175">Te dane są określane za pomocą zapytania XPath.</span><span class="sxs-lookup"><span data-stu-id="a675f-175">This data is specified by using an XPath query.</span></span> <span data-ttu-id="a675f-176">Jeśli nie są też wysyłane komunikaty do usługi, mimo wszystko, co wydaje się być poprawne, jedną ze strategii do rozwiązywania problemów jest określić wartość literału, które pasują do wartości danych komunikatu zamiast zapytania XPath.</span><span class="sxs-lookup"><span data-stu-id="a675f-176">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="a675f-177">Aby określić wartość literału, należy użyć `string` funkcji.</span><span class="sxs-lookup"><span data-stu-id="a675f-177">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="a675f-178">W poniższym przykładzie <xref:System.ServiceModel.MessageQuerySet> jest skonfigurowany do używania wartość literału `11445` dla `OrderId` i zapytanie XPath jest opatrzona komentarzem.</span><span class="sxs-lookup"><span data-stu-id="a675f-178">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>

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

 <span data-ttu-id="a675f-179">Jeśli zapytanie XPath jest niepoprawnie skonfigurowane tak, są pobierane żadne dane korelacji, błąd jest zwracany z następującym komunikatem: "korelacji zapytanie zwróciło pusty zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="a675f-179">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="a675f-180">Upewnij się, że zapytania korelacji dla punktu końcowego są poprawnie skonfigurowane."</span><span class="sxs-lookup"><span data-stu-id="a675f-180">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="a675f-181">Szybki sposób rozwiązać ten problem jest kwerenda XPath Zamień na wartość literału zgodnie z opisem w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="a675f-181">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="a675f-182">Ten problem może wystąpić, jeśli używasz konstruktora zapytań XPath w **Dodaj inicjatory korelacji** lub **definice Vlastnosti Correlateson** usługi przepływu pracy i okien dialogowych używa kontrakty komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a675f-182">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="a675f-183">W poniższym przykładzie zdefiniowano klasę kontraktu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a675f-183">In the following example, a message contract class is defined.</span></span>

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

 <span data-ttu-id="a675f-184">Ten kontrakt komunikatu jest używana przez <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="a675f-184">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="a675f-185">`CartId` w nagłówku komunikatu służy do skorelowania komunikat, który ma prawidłowe wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="a675f-185">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="a675f-186">Jeśli zapytanie XPath, który pobiera `CartId` jest tworzony przy użyciu okien dialogowych korelacji w Projektancie przepływu pracy, następujące nieprawidłową wartością XPath jest generowane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="a675f-186">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 <span data-ttu-id="a675f-187">Ta kwerenda XPath są poprawne Jeśli <xref:System.ServiceModel.Activities.Receive> działanie używane parametry dla danych, ale ponieważ korzysta ona z kontraktu komunikatu jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a675f-187">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="a675f-188">Następujące zapytanie XPath jest prawidłowe zapytanie XPath do pobrania `CartId` z nagłówka.</span><span class="sxs-lookup"><span data-stu-id="a675f-188">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>

```
sm:header()/tempuri:CartId
```

<span data-ttu-id="a675f-189">Można to potwierdzić, sprawdzając treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a675f-189">This can be confirmed by examining the body of the message.</span></span>

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

<span data-ttu-id="a675f-190">W poniższym przykładzie przedstawiono <xref:System.ServiceModel.Activities.Receive> działania skonfigurowane dla `AddItem` operacji, która używa poprzedniego kontraktu komunikatu, aby odbierać dane.</span><span class="sxs-lookup"><span data-stu-id="a675f-190">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="a675f-191">Zapytanie XPath jest poprawnie skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="a675f-191">The XPath query is correctly configured.</span></span>

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
