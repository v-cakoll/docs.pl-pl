---
title: Korelacja rozwiązywania problemów
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: c597012a5ff69ecb700c51e00ac7d1218962e9ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-correlation"></a>Korelacja rozwiązywania problemów
Korelacji jest używany do tworzenia powiązań komunikatów usługi przepływu pracy i wystąpienia przepływu pracy poprawny, ale jeśli nie jest prawidłowo skonfigurowany, nie będzie można odbierać wiadomości i aplikacje nie będą działać poprawnie. W tym temacie omówiono kilka metod do rozwiązywania problemów korelacji, a także przedstawiono kilka typowych problemów, które mogą wystąpić, gdy używasz korelacji.  
  
## <a name="handle-the-unknownmessagereceived-event"></a>Obsłuż zdarzenie UnknownMessageReceived  
 <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> Zdarzenie wystąpi, gdy nieznany komunikat jest odbierany przez usługę, w tym komunikaty, które nie mogą zostać skorelowane z istniejącego wystąpienia. W przypadku usług hostowania samoobsługowego tego zdarzenia mogą być obsługiwane w aplikacji hosta.  
  
```csharp  
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
{  
    Console.WriteLine("Unknown Message Received:");  
    Console.WriteLine(e.Message);  
};  
```  
  
 W przypadku usług hostowanych w sieci Web to zdarzenie może być obsługiwanych przez wyprowadzanie klasy z <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> i zastępowanie <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.  
  
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
  
 Ten niestandardowy <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> można określić w `svc` plik usługi.  
  
```  
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>  
```  
  
 Po wywołaniu tej obsługi wiadomości mogą być pobierane przy użyciu <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> właściwość <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>i będą podobne do następujących.  
  
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
  
 Zapoznanie się komunikaty wysyłane do <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> obsługi dostarczają wskazówek dotyczących Dlaczego wiadomość nie odnoszą się do wystąpienia usługi przepływu pracy.  
  
## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>Aby monitorować postęp przepływu pracy korzystać ze śledzenia  
 Śledzenie umożliwia monitorowanie postępu przepływu pracy. Domyślnie rekordy śledzenia są emitowane dla zdarzeń cyklu życia przepływu pracy, zdarzenia cyklu życia działań propagacji usterek i wznowienie zakładki. Ponadto rekordów niestandardowych śledzenia może być wysyłany przez działań niestandardowych. Podczas rozwiązywania problemu korelacji, działania śledzenia, rekordy wznowienie zakładki oraz rekordów propagacji błędów są najbardziej przydatne. Działania śledzenia rekordów może służyć do określenia Bieżący postęp przepływu pracy i może ułatwić identyfikację oczekiwaniem działanie (activity) wiadomości dla wiadomości. Zakładka wznowienie rekordy te są przydatne, ponieważ wskazują, że wiadomość została odebrana przez przepływ pracy, oraz błędów Propagacja rekordów rekord żadnych błędów w przepływie pracy. Aby włączyć śledzenie, należy określić żądaną <xref:System.Activities.Tracking.TrackingParticipant> w <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> z <xref:System.ServiceModel.Activities.WorkflowServiceHost>. W poniższym przykładzie `ConsoleTrackingParticipant` (z [śledzenia niestandardowe](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) przykładowe) jest konfigurowana przy użyciu domyślnego profilu śledzenia.  
  
```csharp  
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());  
```  
  
 Uczestnika śledzenia, takich jak ConsoleTrackingParticipant jest przydatne w przypadku usług hostowanie Samoobsługowe przepływu pracy, które mają okna konsoli. Dla usługi hostowanej w sieci Web, która rejestruje informacje o śledzeniu do magazynu trwałego uczestnika śledzenia powinny być używane takie jak wbudowana <xref:System.Activities.Tracking.EtwTrackingParticipant>, lub uczestnika niestandardowych śledzenia, która rejestruje informacje w pliku, na przykład `TextWriterTrackingParticpant` z [ Śledzenie za pomocą pliku tekstowego](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md) próbki.  
  
 Aby uzyskać więcej informacji na temat śledzenia i konfigurowania śledzenia dla usługi sieci Web hostowanych przepływu pracy, zobacz [przepływu pracy śledzenia i śledzenia](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Konfigurowanie śledzenia przepływu pracy](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)i [ Śledzenie &#91;WF — przykłady&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) próbek.  
  
## <a name="use-wcf-tracing"></a>Użyj śledzenia WCF  
 Śledzenie WCF umożliwia śledzenie przepływu wiadomości do i z usługi przepływu pracy. Te informacje śledzenia jest przydatne podczas rozwiązywania problemów korelacji, szczególnie w przypadku korelacji na podstawie zawartości. Aby włączyć śledzenie, określ odbiorniki śledzenia żądaną w `system.diagnostics` sekcji `web.config` plik, jeśli usługi przepływu pracy jest oparta na sieci Web lub `app.config` plik, jeśli jest samodzielnie hostowana usługa przepływu pracy. Aby dołączyć zawartość wiadomości w pliku śledzenia, należy określić `true` dla `logEntireMessage` w `messageLogging` element `diagnostics` części `system.serviceModel`. W poniższym przykładzie informacje śledzenia, łącznie z zawartości wiadomości, jest skonfigurowany do zapisania pliku o nazwie `service.svclog`.  
  
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
  
 Aby wyświetlić informacje o śledzeniu, który jest zawarty w `service.svclog`, [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) jest używany. Jest to szczególnie przydatne podczas rozwiązywania problemów na podstawie zawartości korelacji problemy, ponieważ można wyświetlać zawartość wiadomości i dokładnie co to jest przekazywany i czy jest on zgodny <xref:System.ServiceModel.CorrelationQuery> dla korelacji na podstawie zawartości. Aby uzyskać więcej informacji na temat śledzenia WCF, zobacz [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), i [za pomocą śledzenia Rozwiązywanie problemów z aplikacją](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).  
  
## <a name="common-context-exchange-correlation-issues"></a>Typowe problemy korelacja wymiany kontekstu  
 Niektóre rodzaje korelacji wymagają, czy określony typ powiązania jest używany przez korelację działała prawidłowo. Przykłady obejmują korelacja żądań i odpowiedzi, który wymaga dwukierunkowego powiązania w takich jak <xref:System.ServiceModel.BasicHttpBinding>i korelacja wymiany kontekstu, co wymaga na podstawie kontekstu wiązania takich jak <xref:System.ServiceModel.BasicHttpContextBinding>. Większość powiązań obsługuje dwukierunkowe operacji tak nie jest typowym problemem dla korelacja żądań i odpowiedzi, ale istnieje tylko niewielki podzbiór na podstawie kontekstu wiązania w tym <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, i <xref:System.ServiceModel.NetTcpContextBinding>. Jeśli jeden z tych powiązań nie jest używany, powiedzie się początkowej wywołanie usługi przepływu pracy, ale wezwań zakończy się niepowodzeniem z następującymi <xref:System.ServiceModel.FaultException>.  
  
```Output  
There is no context attached to the incoming message for the service   
and the current operation is not marked with "CanCreateInstance = true".   
In order to communicate with this service check whether the incoming binding   
supports the context protocol and has a valid context initialized.  
```  
  
 Informacje kontekstu, które są używane do korelacji kontekstu może być zwracany przez <xref:System.ServiceModel.Activities.SendReply> do <xref:System.ServiceModel.Activities.Receive> działanie, które inicjuje korelację kontekstu, gdy za pomocą operacji dwukierunkowe, lub można określić przez obiekt wywołujący, gdy operacja jest jednokierunkowe. Jeśli kontekst nie jest wysyłane przez obiekt wywołujący lub zwrócony przez usługę przepływu pracy, a następnie takie same <xref:System.ServiceModel.FaultException> opisanego wcześniej zostanie zwrócona po wywołaniu kolejnych operacji.  
  
 Aby uzyskać więcej informacji, zobacz [wymiana kontekstu](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).  
  
## <a name="common-request-reply-correlation-issues"></a>Typowe problemy korelacji "żądanie-odpowiedź"  
 Korelacja żądań i odpowiedzi jest używany z <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary do zaimplementowania dwukierunkowe operacji w usłudze przepływu pracy oraz <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary, który wywołuje operację dwukierunkowe w innej sieci Web Usługa. Podczas wywoływania dwukierunkowe operacji usługi WCF, usługa może być albo tradycyjną usługi przepływu pracy może być konieczne usługi WCF opartej na kodzie lub go. Umożliwia powiązanie dwustronne muszą być stosowane, takich jak korelacja żądań i odpowiedzi <xref:System.ServiceModel.BasicHttpBinding>, i działania muszą być dwukierunkowe.  
  
 W przypadku usługi przepływu pracy dwukierunkowe operacje równoległe lub nakładanie się <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> lub <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary, a następnie niejawne korelacji obsługiwać zarządzanie zapewniane przez <xref:System.ServiceModel.Activities.WorkflowServiceHost>mogą być niewystarczające, szczególnie w scenariuszach wysokiej akcent i komunikaty mogą nie być poprawnie kierowane. Aby zapobiec wystąpieniu tego problemu, zaleca się, że należy zawsze jawnie określić <xref:System.ServiceModel.Activities.CorrelationHandle> przy użyciu korelacja żądań i odpowiedzi. Korzystając z **SendAndReceiveReply** i **ReceiveAndSendReply** szablony z sekcji wiadomości **przybornika** w Projektancie przepływów pracy <xref:System.ServiceModel.Activities.CorrelationHandle> jawnie jest konfiguracja domyślna. Podczas tworzenia przepływu pracy przy użyciu kodu, <xref:System.ServiceModel.Activities.CorrelationHandle> została określona w <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> pierwszy działania pary. W poniższym przykładzie <xref:System.ServiceModel.Activities.Receive> działania jest skonfigurowana jawnego <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> określonego w <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.  
  
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
  
 Trwałości nie jest dozwolone między <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary lub <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary. Tworzona jest strefa no-persist będzie trwać do obu czynności zostały wykonane. Jeśli działania, takie jak działania opóźnienia, znajduje się w tej strefie no-persist i powoduje, że przepływ pracy w stan bezczynności, przepływ pracy nie zachowa nawet wtedy, gdy host jest skonfigurowany do utrwalenia przepływy pracy, gdy stanie się on w stanie bezczynności. Jeśli działania, takie jak działania będzie nadal występować, próbuje jawnie pozostają w strefie nie utrwalanie, krytyczny jest zwracany wyjątek, przerwanie przepływu pracy i <xref:System.ServiceModel.FaultException> jest zwracany do obiektu wywołującego. Komunikat o wyjątku krytycznego "System.InvalidOperationException: utrwalić działania nie mogą być zawarte w blokach nietrwałości.". Ten wyjątek nie są zwracane do obiektu wywołującego, ale można obserwować, czy śledzenie jest włączone. W komunikacie <xref:System.ServiceModel.FaultException> zwracany do obiektu wywołującego jest "nie można wykonać operacji, ponieważ działanie obiektu WorkflowInstance"5836145b-7da2 - 49 d 0-a052-a49162adeab6"została ukończona".  
  
 Aby uzyskać więcej informacji na temat korelacja żądań i odpowiedzi, zobacz [żądanie-odpowiedź](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).  
  
## <a name="common-content-correlation-issues"></a>Typowe problemy zawartości korelacji  
 Korelacja na podstawie zawartości jest używana, gdy wiele komunikatów odbiera usługi przepływu pracy i element danych w ramach wymiany wiadomości identyfikuje odpowiednie wystąpienie. Na podstawie zawartości korelacji używa tych danych w komunikacie, takie jak liczba lub kolejność ID klienta do wyznaczania tras wiadomościom do wystąpienia przepływu pracy poprawne. W tej sekcji opisano kilka typowych problemów, które mogą wystąpić podczas korzystania na podstawie zawartości korelacji.  
  
### <a name="ensure-the-identifying-data-is-unique"></a>Upewnij się, że dane identyfikacyjne są unikatowe  
 Dane, które służy do identyfikacji wystąpienia jest wartość skrótu na klucz korelacji. Należy uważać, aby zagwarantować, że dane, które jest używane na potrzeby korelacji jest unikatowa w przeciwnym razie kolizji w formie skrótu klucza mogą występować i komunikaty można rozsyłanymi. Na przykład korelacji w oparciu jedynie nazwy klienta może spowodować kolizji, ponieważ może być wielu klientów, którzy mają taką samą nazwę. Nie można używać dwukropka (:) jako część danych, który służy do skorelowania komunikatu, ponieważ jest już używany do ograniczania kluczy i wartości do utworzenia ciąg, który jest następnie mieszany kwerendy komunikatu. Jeśli używane jest trwałości, upewnij się, czy bieżące dane identyfikacyjne nie został użyty przez wystąpienie utrwalonych wcześniej. Tymczasowe wyłączenie trwałości można zidentyfikować ten problem. Śledzenie WCF można wyświetlić obliczony klucz korelacji i jest przydatne w przypadku debugowania tego problemu.  
  
### <a name="race-conditions"></a>Warunki wyścigu  
 Brak małych przerwę w czasie między usługi odbieranie wiadomości i korelacji faktycznie inicjowany, podczas którego adresatem wiadomości są ignorowane. Jeśli usługi przepływu pracy inicjuje korelację na podstawie zawartości przy użyciu danych przesyłanych między klientem za pośrednictwem operacji jednokierunkowych, a obiekt wywołujący wysyła natychmiastowego kolejnych komunikatów, komunikaty te zostaną pominięte w danym przedziale czasu. Można tego uniknąć przy użyciu operacji dwukierunkowe zainicjować korelację lub za pomocą <xref:System.ServiceModel.Activities.TransactedReceiveScope>.  
  
### <a name="correlation-query-issues"></a>Problemy z zapytania korelacji  
 Zapytania dotyczące korelacji są używane do określania, jakie dane w komunikacie służy do skorelowania wiadomości. Te dane jest określona za pomocą kwerendy XPath. Jeśli nie są też wysyłane komunikaty do usługi, mimo wszystko wydaje się być poprawne, jedną ze strategii do rozwiązywania problemów jest określenie wartość literału, która jest zgodna z wartością danych komunikatów, zamiast Kwerenda XPath. Aby określić wartość literału, należy użyć `string` funkcji. W poniższym przykładzie <xref:System.ServiceModel.MessageQuerySet> jest skonfigurowana do używania wartość literału `11445` dla `OrderId` i zapytanie XPath jest oznaczone jako komentarz.  
  
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
  
 Jeśli zapytanie XPath jest niepoprawnie skonfigurowana tak, aby nie korelacji jest pobrać danych, błąd jest zwracany następujący komunikat o błędzie: "zapytanie dotyczące korelacji zwróciło pusty zestaw wyników. Upewnij się, że zapytania dotyczące korelacji dla punktu końcowego są poprawnie skonfigurowane." Szybki sposób rozwiązać ten problem jest kwerenda XPath Zamień na wartość literału zgodnie z opisem w poprzedniej sekcji. Ten problem może wystąpić, jeśli używasz Kwerenda XPath w **dodać inicjatorów korelacji** lub **definicji CorrelatesOn** okien dialogowych i usługi przepływu pracy używa kontraktów komunikatu. W poniższym przykładzie zdefiniowano klasę kontraktu komunikatu.  
  
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
  
 Tego kontraktu komunikatu jest używany przez <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. `CartId` w nagłówku wiadomości jest używane do korelacji wiadomości na prawidłowe wystąpienie. Jeśli zapytanie XPath, który pobiera `CartId` jest tworzony przy użyciu okien dialogowych korelacji w Projektancie przepływów pracy, następujące wygenerować zapytania, jest nieprawidłową wartością XPath.  
  
```  
sm:body()/xg0:AddItemMessage/xg0:CartId  
```  
  
 Ta kwerenda XPath są poprawne Jeśli <xref:System.ServiceModel.Activities.Receive> działanie używane parametry dla danych, ale ponieważ jest użyciem kontraktu komunikatu jest nieprawidłowy. Następujące zapytanie XPath jest prawidłowa Kwerenda XPath można pobrać `CartId` z nagłówka.  
  
```  
sm:header()/tempuri:CartId  
```  
  
 Można to potwierdzić, sprawdzając treści wiadomości.  
  
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
  
 W poniższym przykładzie przedstawiono <xref:System.ServiceModel.Activities.Receive> działania skonfigurowane dla `AddItem` operacja, która używa poprzedniej kontraktu komunikatu do odbierania danych. Zapytanie XPath jest poprawnie skonfigurowany.  
  
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
  
 Aby uzyskać więcej informacji na temat korelacji na podstawie zawartości, zobacz [na podstawie zawartości](../../../../docs/framework/wcf/feature-details/content-based-correlation.md) i [skorelowane Kalkulator](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) próbki.
