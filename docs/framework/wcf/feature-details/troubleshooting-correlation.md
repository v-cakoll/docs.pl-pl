---
title: Korelacja rozwiązywania problemów
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2de3a8cac6e12d898173f8181b295c3e2e461cc7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="608e3-102">Korelacja rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="608e3-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="608e3-103">Korelacji jest używany do tworzenia powiązań komunikatów usługi przepływu pracy i wystąpienia przepływu pracy poprawny, ale jeśli nie jest prawidłowo skonfigurowany, nie będzie można odbierać wiadomości i aplikacje nie będą działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="608e3-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="608e3-104">W tym temacie omówiono kilka metod do rozwiązywania problemów korelacji, a także przedstawiono kilka typowych problemów, które mogą wystąpić, gdy używasz korelacji.</span><span class="sxs-lookup"><span data-stu-id="608e3-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>  
  
## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="608e3-105">Obsłuż zdarzenie UnknownMessageReceived</span><span class="sxs-lookup"><span data-stu-id="608e3-105">Handle the UnknownMessageReceived Event</span></span>  
 <span data-ttu-id="608e3-106"><xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> Zdarzenie wystąpi, gdy nieznany komunikat jest odbierany przez usługę, w tym komunikaty, które nie mogą zostać skorelowane z istniejącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="608e3-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="608e3-107">W przypadku usług hostowania samoobsługowego tego zdarzenia mogą być obsługiwane w aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="608e3-107">For self-hosted services, this event can be handled in the host application.</span></span>  
  
```csharp  
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
{  
    Console.WriteLine("Unknown Message Received:");  
    Console.WriteLine(e.Message);  
};  
```  
  
 <span data-ttu-id="608e3-108">W przypadku usług hostowanych w sieci Web to zdarzenie może być obsługiwanych przez wyprowadzanie klasy z <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> i zastępowanie <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="608e3-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>  
  
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
  
 <span data-ttu-id="608e3-109">Ten niestandardowy <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> można określić w `svc` plik usługi.</span><span class="sxs-lookup"><span data-stu-id="608e3-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>  
  
```  
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>  
```  
  
 <span data-ttu-id="608e3-110">Po wywołaniu tej obsługi wiadomości mogą być pobierane przy użyciu <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> właściwość <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>i będą podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="608e3-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>  
  
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
  
 <span data-ttu-id="608e3-111">Zapoznanie się komunikaty wysyłane do <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> obsługi dostarczają wskazówek dotyczących Dlaczego wiadomość nie odnoszą się do wystąpienia usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="608e3-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>  
  
## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="608e3-112">Aby monitorować postęp przepływu pracy korzystać ze śledzenia</span><span class="sxs-lookup"><span data-stu-id="608e3-112">Use Tracking to Monitor the Progress of the Workflow</span></span>  
 <span data-ttu-id="608e3-113">Śledzenie umożliwia monitorowanie postępu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="608e3-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="608e3-114">Domyślnie rekordy śledzenia są emitowane dla zdarzeń cyklu życia przepływu pracy, zdarzenia cyklu życia działań propagacji usterek i wznowienie zakładki.</span><span class="sxs-lookup"><span data-stu-id="608e3-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="608e3-115">Ponadto rekordów niestandardowych śledzenia może być wysyłany przez działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="608e3-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="608e3-116">Podczas rozwiązywania problemu korelacji, działania śledzenia, rekordy wznowienie zakładki oraz rekordów propagacji błędów są najbardziej przydatne.</span><span class="sxs-lookup"><span data-stu-id="608e3-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="608e3-117">Działania śledzenia rekordów może służyć do określenia Bieżący postęp przepływu pracy i może ułatwić identyfikację oczekiwaniem działanie (activity) wiadomości dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="608e3-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="608e3-118">Zakładka wznowienie rekordy te są przydatne, ponieważ wskazują, że wiadomość została odebrana przez przepływ pracy, oraz błędów Propagacja rekordów rekord żadnych błędów w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="608e3-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="608e3-119">Aby włączyć śledzenie, należy określić żądaną <xref:System.Activities.Tracking.TrackingParticipant> w <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> z <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="608e3-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="608e3-120">W poniższym przykładzie `ConsoleTrackingParticipant` (z [śledzenia niestandardowe](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) przykładowe) jest konfigurowana przy użyciu domyślnego profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="608e3-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>  
  
```csharp  
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="608e3-121">Uczestnika śledzenia, takich jak ConsoleTrackingParticipant jest przydatne w przypadku usług hostowanie Samoobsługowe przepływu pracy, które mają okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="608e3-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="608e3-122">Dla usługi hostowanej w sieci Web, która rejestruje informacje o śledzeniu do magazynu trwałego uczestnika śledzenia powinny być używane takie jak wbudowana <xref:System.Activities.Tracking.EtwTrackingParticipant>, lub uczestnika niestandardowych śledzenia, która rejestruje informacje w pliku, na przykład `TextWriterTrackingParticpant` z [ Śledzenie za pomocą pliku tekstowego](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="608e3-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file, such as the `TextWriterTrackingParticpant` from the [Tracking Using a Text File](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md) sample.</span></span>  
  
 <span data-ttu-id="608e3-123">Aby uzyskać więcej informacji na temat śledzenia i konfigurowania śledzenia dla usługi sieci Web hostowanych przepływu pracy, zobacz [przepływu pracy śledzenia i śledzenia](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Konfigurowanie śledzenia przepływu pracy](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)i [ Śledzenie &#91;WF — przykłady&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) próbek.</span><span class="sxs-lookup"><span data-stu-id="608e3-123">For more information about tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>  
  
## <a name="use-wcf-tracing"></a><span data-ttu-id="608e3-124">Użyj śledzenia WCF</span><span class="sxs-lookup"><span data-stu-id="608e3-124">Use WCF Tracing</span></span>  
 <span data-ttu-id="608e3-125">Śledzenie WCF umożliwia śledzenie przepływu wiadomości do i z usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="608e3-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="608e3-126">Te informacje śledzenia jest przydatne podczas rozwiązywania problemów korelacji, szczególnie w przypadku korelacji na podstawie zawartości.</span><span class="sxs-lookup"><span data-stu-id="608e3-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="608e3-127">Aby włączyć śledzenie, określ odbiorniki śledzenia żądaną w `system.diagnostics` sekcji `web.config` plik, jeśli usługi przepływu pracy jest oparta na sieci Web lub `app.config` plik, jeśli jest samodzielnie hostowana usługa przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="608e3-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="608e3-128">Aby dołączyć zawartość wiadomości w pliku śledzenia, należy określić `true` dla `logEntireMessage` w `messageLogging` element `diagnostics` części `system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="608e3-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="608e3-129">W poniższym przykładzie informacje śledzenia, łącznie z zawartości wiadomości, jest skonfigurowany do zapisania pliku o nazwie `service.svclog`.</span><span class="sxs-lookup"><span data-stu-id="608e3-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>  
  
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
  
 <span data-ttu-id="608e3-130">Aby wyświetlić informacje o śledzeniu, który jest zawarty w `service.svclog`, [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) jest używany.</span><span class="sxs-lookup"><span data-stu-id="608e3-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="608e3-131">Jest to szczególnie przydatne podczas rozwiązywania problemów na podstawie zawartości korelacji problemy, ponieważ można wyświetlać zawartość wiadomości i dokładnie co to jest przekazywany i czy jest on zgodny <xref:System.ServiceModel.CorrelationQuery> dla korelacji na podstawie zawartości.</span><span class="sxs-lookup"><span data-stu-id="608e3-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> <span data-ttu-id="608e3-132">Aby uzyskać więcej informacji na temat śledzenia WCF, zobacz [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), i [za pomocą śledzenia Rozwiązywanie problemów z aplikacją](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="608e3-132">For more information about WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>  
  
## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="608e3-133">Typowe problemy korelacja wymiany kontekstu</span><span class="sxs-lookup"><span data-stu-id="608e3-133">Common Context Exchange Correlation Issues</span></span>  
 <span data-ttu-id="608e3-134">Niektóre rodzaje korelacji wymagają, czy określony typ powiązania jest używany przez korelację działała prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="608e3-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="608e3-135">Przykłady obejmują korelacja żądań i odpowiedzi, który wymaga dwukierunkowego powiązania w takich jak <xref:System.ServiceModel.BasicHttpBinding>i korelacja wymiany kontekstu, co wymaga na podstawie kontekstu wiązania takich jak <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="608e3-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="608e3-136">Większość powiązań obsługuje dwukierunkowe operacji tak nie jest typowym problemem dla korelacja żądań i odpowiedzi, ale istnieje tylko niewielki podzbiór na podstawie kontekstu wiązania w tym <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, i <xref:System.ServiceModel.NetTcpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="608e3-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="608e3-137">Jeśli jeden z tych powiązań nie jest używany, powiedzie się początkowej wywołanie usługi przepływu pracy, ale wezwań zakończy się niepowodzeniem z następującymi <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="608e3-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>  
  
```Output  
There is no context attached to the incoming message for the service   
and the current operation is not marked with "CanCreateInstance = true".   
In order to communicate with this service check whether the incoming binding   
supports the context protocol and has a valid context initialized.  
```  
  
 <span data-ttu-id="608e3-138">Informacje kontekstu, które są używane do korelacji kontekstu może być zwracany przez <xref:System.ServiceModel.Activities.SendReply> do <xref:System.ServiceModel.Activities.Receive> działanie, które inicjuje korelację kontekstu, gdy za pomocą operacji dwukierunkowe, lub można określić przez obiekt wywołujący, gdy operacja jest jednokierunkowe.</span><span class="sxs-lookup"><span data-stu-id="608e3-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="608e3-139">Jeśli kontekst nie jest wysyłane przez obiekt wywołujący lub zwrócony przez usługę przepływu pracy, a następnie takie same <xref:System.ServiceModel.FaultException> opisanego wcześniej zostanie zwrócona po wywołaniu kolejnych operacji.</span><span class="sxs-lookup"><span data-stu-id="608e3-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>  
  
 <span data-ttu-id="608e3-140">Aby uzyskać więcej informacji, zobacz [wymiana kontekstu](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="608e3-140">For more information, see [Context Exchange](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).</span></span>  
  
## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="608e3-141">Typowe problemy korelacji "żądanie-odpowiedź"</span><span class="sxs-lookup"><span data-stu-id="608e3-141">Common Request-Reply Correlation Issues</span></span>  
 <span data-ttu-id="608e3-142">Korelacja żądań i odpowiedzi jest używany z <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary do zaimplementowania dwukierunkowe operacji w usłudze przepływu pracy oraz <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary, który wywołuje operację dwukierunkowe w innej sieci Web Usługa.</span><span class="sxs-lookup"><span data-stu-id="608e3-142">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="608e3-143">Podczas wywoływania dwukierunkowe operacji usługi WCF, usługa może być albo tradycyjnych imperatywne opartej na kodzie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługę albo mogą być usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="608e3-143">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or it can be a workflow service.</span></span> <span data-ttu-id="608e3-144">Umożliwia powiązanie dwustronne muszą być stosowane, takich jak korelacja żądań i odpowiedzi <xref:System.ServiceModel.BasicHttpBinding>, i działania muszą być dwukierunkowe.</span><span class="sxs-lookup"><span data-stu-id="608e3-144">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>  
  
 <span data-ttu-id="608e3-145">W przypadku usługi przepływu pracy dwukierunkowe operacje równoległe lub nakładanie się <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> lub <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary, a następnie niejawne korelacji obsługiwać zarządzanie zapewniane przez <xref:System.ServiceModel.Activities.WorkflowServiceHost>mogą być niewystarczające, szczególnie w scenariuszach wysokiej akcent i komunikaty mogą nie być poprawnie kierowane.</span><span class="sxs-lookup"><span data-stu-id="608e3-145">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="608e3-146">Aby zapobiec wystąpieniu tego problemu, zaleca się, że należy zawsze jawnie określić <xref:System.ServiceModel.Activities.CorrelationHandle> przy użyciu korelacja żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="608e3-146">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="608e3-147">Korzystając z **SendAndReceiveReply** i **ReceiveAndSendReply** szablony z sekcji wiadomości **przybornika** w Projektancie przepływów pracy <xref:System.ServiceModel.Activities.CorrelationHandle> jawnie jest konfiguracja domyślna.</span><span class="sxs-lookup"><span data-stu-id="608e3-147">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="608e3-148">Podczas tworzenia przepływu pracy przy użyciu kodu, <xref:System.ServiceModel.Activities.CorrelationHandle> została określona w <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> pierwszy działania pary.</span><span class="sxs-lookup"><span data-stu-id="608e3-148">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="608e3-149">W poniższym przykładzie <xref:System.ServiceModel.Activities.Receive> działania jest skonfigurowana jawnego <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> określonego w <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="608e3-149">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>  
  
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
  
 <span data-ttu-id="608e3-150">Trwałości nie jest dozwolone między <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary lub <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary.</span><span class="sxs-lookup"><span data-stu-id="608e3-150">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="608e3-151">Tworzona jest strefa no-persist będzie trwać do obu czynności zostały wykonane.</span><span class="sxs-lookup"><span data-stu-id="608e3-151">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="608e3-152">Jeśli działania, takie jak działania opóźnienia, znajduje się w tej strefie no-persist i powoduje, że przepływ pracy w stan bezczynności, przepływ pracy nie zachowa nawet wtedy, gdy host jest skonfigurowany do utrwalenia przepływy pracy, gdy stanie się on w stanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="608e3-152">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="608e3-153">Jeśli działania, takie jak działania będzie nadal występować, próbuje jawnie pozostają w strefie nie utrwalanie, krytyczny jest zwracany wyjątek, przerwanie przepływu pracy i <xref:System.ServiceModel.FaultException> jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="608e3-153">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="608e3-154">Komunikat o wyjątku krytycznego "System.InvalidOperationException: utrwalić działania nie mogą być zawarte w blokach nietrwałości.".</span><span class="sxs-lookup"><span data-stu-id="608e3-154">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="608e3-155">Ten wyjątek nie są zwracane do obiektu wywołującego, ale można obserwować, czy śledzenie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="608e3-155">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="608e3-156">W komunikacie <xref:System.ServiceModel.FaultException> zwracany do obiektu wywołującego jest "nie można wykonać operacji, ponieważ działanie obiektu WorkflowInstance"5836145b-7da2 - 49 d 0-a052-a49162adeab6"została ukończona".</span><span class="sxs-lookup"><span data-stu-id="608e3-156">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>  
  
 <span data-ttu-id="608e3-157">Aby uzyskać więcej informacji na temat korelacja żądań i odpowiedzi, zobacz [żądanie-odpowiedź](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="608e3-157">For more information about request-reply correlation, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span></span>  
  
## <a name="common-content-correlation-issues"></a><span data-ttu-id="608e3-158">Typowe problemy zawartości korelacji</span><span class="sxs-lookup"><span data-stu-id="608e3-158">Common Content Correlation Issues</span></span>  
 <span data-ttu-id="608e3-159">Korelacja na podstawie zawartości jest używana, gdy wiele komunikatów odbiera usługi przepływu pracy i element danych w ramach wymiany wiadomości identyfikuje odpowiednie wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="608e3-159">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="608e3-160">Na podstawie zawartości korelacji używa tych danych w komunikacie, takie jak liczba lub kolejność ID klienta do wyznaczania tras wiadomościom do wystąpienia przepływu pracy poprawne.</span><span class="sxs-lookup"><span data-stu-id="608e3-160">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="608e3-161">W tej sekcji opisano kilka typowych problemów, które mogą wystąpić podczas korzystania na podstawie zawartości korelacji.</span><span class="sxs-lookup"><span data-stu-id="608e3-161">This section describes several common issues that may occur when using content-based correlation.</span></span>  
  
### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="608e3-162">Upewnij się, że dane identyfikacyjne są unikatowe</span><span class="sxs-lookup"><span data-stu-id="608e3-162">Ensure the Identifying Data Is Unique</span></span>  
 <span data-ttu-id="608e3-163">Dane, które służy do identyfikacji wystąpienia jest wartość skrótu na klucz korelacji.</span><span class="sxs-lookup"><span data-stu-id="608e3-163">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="608e3-164">Należy uważać, aby zagwarantować, że dane, które jest używane na potrzeby korelacji jest unikatowa w przeciwnym razie kolizji w formie skrótu klucza mogą występować i komunikaty można rozsyłanymi.</span><span class="sxs-lookup"><span data-stu-id="608e3-164">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="608e3-165">Na przykład korelacji w oparciu jedynie nazwy klienta może spowodować kolizji, ponieważ może być wielu klientów, którzy mają taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="608e3-165">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="608e3-166">Nie można używać dwukropka (:) jako część danych, który służy do skorelowania komunikatu, ponieważ jest już używany do ograniczania kluczy i wartości do utworzenia ciąg, który jest następnie mieszany kwerendy komunikatu.</span><span class="sxs-lookup"><span data-stu-id="608e3-166">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="608e3-167">Jeśli używane jest trwałości, upewnij się, czy bieżące dane identyfikacyjne nie został użyty przez wystąpienie utrwalonych wcześniej.</span><span class="sxs-lookup"><span data-stu-id="608e3-167">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="608e3-168">Tymczasowe wyłączenie trwałości można zidentyfikować ten problem.</span><span class="sxs-lookup"><span data-stu-id="608e3-168">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="608e3-169">Śledzenie WCF można wyświetlić obliczony klucz korelacji i jest przydatne w przypadku debugowania tego problemu.</span><span class="sxs-lookup"><span data-stu-id="608e3-169">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>  
  
### <a name="race-conditions"></a><span data-ttu-id="608e3-170">Warunki wyścigu</span><span class="sxs-lookup"><span data-stu-id="608e3-170">Race Conditions</span></span>  
 <span data-ttu-id="608e3-171">Brak małych przerwę w czasie między usługi odbieranie wiadomości i korelacji faktycznie inicjowany, podczas którego adresatem wiadomości są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="608e3-171">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="608e3-172">Jeśli usługi przepływu pracy inicjuje korelację na podstawie zawartości przy użyciu danych przesyłanych między klientem za pośrednictwem operacji jednokierunkowych, a obiekt wywołujący wysyła natychmiastowego kolejnych komunikatów, komunikaty te zostaną pominięte w danym przedziale czasu.</span><span class="sxs-lookup"><span data-stu-id="608e3-172">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="608e3-173">Można tego uniknąć przy użyciu operacji dwukierunkowe zainicjować korelację lub za pomocą <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="608e3-173">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>  
  
### <a name="correlation-query-issues"></a><span data-ttu-id="608e3-174">Problemy z zapytania korelacji</span><span class="sxs-lookup"><span data-stu-id="608e3-174">Correlation Query Issues</span></span>  
 <span data-ttu-id="608e3-175">Zapytania dotyczące korelacji są używane do określania, jakie dane w komunikacie służy do skorelowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="608e3-175">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="608e3-176">Te dane jest określona za pomocą kwerendy XPath.</span><span class="sxs-lookup"><span data-stu-id="608e3-176">This data is specified by using an XPath query.</span></span> <span data-ttu-id="608e3-177">Jeśli nie są też wysyłane komunikaty do usługi, mimo wszystko wydaje się być poprawne, jedną ze strategii do rozwiązywania problemów jest określenie wartość literału, która jest zgodna z wartością danych komunikatów, zamiast Kwerenda XPath.</span><span class="sxs-lookup"><span data-stu-id="608e3-177">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="608e3-178">Aby określić wartość literału, należy użyć `string` funkcji.</span><span class="sxs-lookup"><span data-stu-id="608e3-178">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="608e3-179">W poniższym przykładzie <xref:System.ServiceModel.MessageQuerySet> jest skonfigurowana do używania wartość literału `11445` dla `OrderId` i zapytanie XPath jest oznaczone jako komentarz.</span><span class="sxs-lookup"><span data-stu-id="608e3-179">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>  
  
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
  
 <span data-ttu-id="608e3-180">Jeśli zapytanie XPath jest niepoprawnie skonfigurowana tak, aby nie korelacji jest pobrać danych, błąd jest zwracany następujący komunikat o błędzie: "zapytanie dotyczące korelacji zwróciło pusty zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="608e3-180">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="608e3-181">Upewnij się, że zapytania dotyczące korelacji dla punktu końcowego są poprawnie skonfigurowane."</span><span class="sxs-lookup"><span data-stu-id="608e3-181">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="608e3-182">Szybki sposób rozwiązać ten problem jest kwerenda XPath Zamień na wartość literału zgodnie z opisem w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="608e3-182">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="608e3-183">Ten problem może wystąpić, jeśli używasz Kwerenda XPath w **dodać inicjatorów korelacji** lub **definicji CorrelatesOn** okien dialogowych i usługi przepływu pracy używa kontraktów komunikatu.</span><span class="sxs-lookup"><span data-stu-id="608e3-183">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="608e3-184">W poniższym przykładzie zdefiniowano klasę kontraktu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="608e3-184">In the following example, a message contract class is defined.</span></span>  
  
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
  
 <span data-ttu-id="608e3-185">Tego kontraktu komunikatu jest używany przez <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="608e3-185">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="608e3-186">`CartId` w nagłówku wiadomości jest używane do korelacji wiadomości na prawidłowe wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="608e3-186">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="608e3-187">Jeśli zapytanie XPath, który pobiera `CartId` jest tworzony przy użyciu okien dialogowych korelacji w Projektancie przepływów pracy, następujące wygenerować zapytania, jest nieprawidłową wartością XPath.</span><span class="sxs-lookup"><span data-stu-id="608e3-187">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>  
  
```  
sm:body()/xg0:AddItemMessage/xg0:CartId  
```  
  
 <span data-ttu-id="608e3-188">Ta kwerenda XPath są poprawne Jeśli <xref:System.ServiceModel.Activities.Receive> działanie używane parametry dla danych, ale ponieważ jest użyciem kontraktu komunikatu jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="608e3-188">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="608e3-189">Następujące zapytanie XPath jest prawidłowa Kwerenda XPath można pobrać `CartId` z nagłówka.</span><span class="sxs-lookup"><span data-stu-id="608e3-189">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>  
  
```  
sm:header()/tempuri:CartId  
```  
  
 <span data-ttu-id="608e3-190">Można to potwierdzić, sprawdzając treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="608e3-190">This can be confirmed by examining the body of the message.</span></span>  
  
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
  
 <span data-ttu-id="608e3-191">W poniższym przykładzie przedstawiono <xref:System.ServiceModel.Activities.Receive> działania skonfigurowane dla `AddItem` operacja, która używa poprzedniej kontraktu komunikatu do odbierania danych.</span><span class="sxs-lookup"><span data-stu-id="608e3-191">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="608e3-192">Zapytanie XPath jest poprawnie skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="608e3-192">The XPath query is correctly configured.</span></span>  
  
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
  
 <span data-ttu-id="608e3-193">Aby uzyskać więcej informacji na temat korelacji na podstawie zawartości, zobacz [na podstawie zawartości](../../../../docs/framework/wcf/feature-details/content-based-correlation.md) i [skorelowane Kalkulator](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="608e3-193">For more information about content-based correlation, see [Content Based](../../../../docs/framework/wcf/feature-details/content-based-correlation.md) and the [Correlated Calculator](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) sample.</span></span>
