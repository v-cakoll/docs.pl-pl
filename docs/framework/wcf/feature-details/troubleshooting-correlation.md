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
# <a name="troubleshooting-correlation"></a>Korelacja rozwiązywania problemów
Korelacja jest używana do powiązania komunikatów usługi przepływu pracy ze sobą i do prawidłowego wystąpienia przepływu pracy, ale jeśli nie jest prawidłowo skonfigurowana, komunikaty nie będą odbierane, a aplikacje nie będą działać prawidłowo. Ten temat zawiera omówienie kilku metod rozwiązywania problemów z korelacją, a także listę typowych problemów, które mogą wystąpić w przypadku korzystania z korelacji.

## <a name="handle-the-unknownmessagereceived-event"></a>Obsługuj zdarzenie UnknownMessageReceived
 Zdarzenie <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> występuje po odebraniu przez usługę nieznanego komunikatu, w tym komunikatów, które nie mogą być skorelowane z istniejącym wystąpieniem. W przypadku usług samoobsługowych to zdarzenie może być obsługiwane w aplikacji hosta.

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 W przypadku usług hostowanych w sieci Web to zdarzenie może być obsługiwane przez wyznaczanie klasy z <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> i zastępowanie <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.

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

 Ten niestandardowy <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> można następnie określić w pliku `svc` dla usługi.

`<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>`

 Po wywołaniu tej procedury obsługi wiadomości można pobrać przy użyciu właściwości <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>i będzie wyglądać następująco.

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

 Inspekcja komunikatów wysłanych do procedury obsługi <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> może przedstawiać wskazówki dotyczące przyczyny nieskorelowania komunikatu z wystąpieniem usługi przepływu pracy.

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>Monitorowanie postępu przepływu pracy przy użyciu funkcji śledzenia
 Śledzenie umożliwia monitorowanie postępu przepływu pracy. Domyślnie śledzenie rekordów jest emitowane w przypadku zdarzeń cyklu życia przepływu pracy, zdarzeń cyklu życia aktywności, propagacji błędów i wznowienia zakładki. Ponadto niestandardowe rekordy śledzenia mogą być emitowane przez działania niestandardowe. W przypadku rozwiązywania problemów z korelacją rekordy śledzenia działań, rekordy wznawiania z zakładkami i rekordy propagacji błędów są najbardziej przydatne. Rekordy śledzenia działań mogą służyć do określenia bieżącego postępu przepływu pracy i mogą ułatwić identyfikację działania komunikatów oczekujących na komunikaty. Rekordy wznawiania zakładki są przydatne, ponieważ wskazują, że komunikat został odebrany przez przepływ pracy, a rekordy propagacji błędów zawierają rekord błędów w przepływie pracy. Aby włączyć śledzenie, określ odpowiednie <xref:System.Activities.Tracking.TrackingParticipant> w <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> <xref:System.ServiceModel.Activities.WorkflowServiceHost>. W poniższym przykładzie `ConsoleTrackingParticipant` (z niestandardowego przykładu [śledzenia](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) ) jest konfigurowany przy użyciu domyślnego profilu śledzenia.

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 Uczestnik śledzenia, taki jak ConsoleTrackingParticipant, jest przydatny w przypadku samodzielnej usługi przepływu pracy, która ma okno konsoli. W przypadku usługi hostowanej przez sieć Web Uczestnik śledzenia, który rejestruje informacje o śledzeniu do magazynu trwałego, powinien być używany, taki jak wbudowana <xref:System.Activities.Tracking.EtwTrackingParticipant>lub uczestnik śledzenia niestandardowego, który rejestruje informacje w pliku.

 Aby uzyskać więcej informacji na temat śledzenia i konfigurowania śledzenia dla usługi przepływu pracy hostowanej w sieci Web, zobacz [śledzenie i śledzenie przepływów pracy](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Konfigurowanie śledzenia dla przepływu pracy](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)oraz próbkowanie próbek [ &#91;WF&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) .

## <a name="use-wcf-tracing"></a>Korzystanie z funkcji śledzenia WCF
 Śledzenie WCF umożliwia śledzenie przepływów komunikatów do i z usługi przepływu pracy. Te informacje śledzenia są przydatne podczas rozwiązywania problemów z korelacją, szczególnie w przypadku korelacji opartej na zawartości. Aby włączyć śledzenie, określ żądane detektory śledzenia w sekcji `system.diagnostics` pliku `web.config`, jeśli usługa przepływu pracy jest hostowana w sieci Web lub plik `app.config`, jeśli usługa przepływu pracy jest samodzielna. Aby dołączyć zawartość komunikatów w pliku śledzenia, określ `true` dla `logEntireMessage` w elemencie `messageLogging` w sekcji `diagnostics` w `system.serviceModel`. W poniższym przykładzie informacje o śledzeniu, w tym zawartość wiadomości, są skonfigurowane tak, aby były zapisywane do pliku o nazwie `service.svclog`.

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

 Aby wyświetlić informacje o śledzeniu zawarte w `service.svclog`, używany jest [Narzędzie przeglądarka śledzenia usługi (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) . Jest to szczególnie przydatne podczas rozwiązywania problemów z korelacją opartą na zawartości, ponieważ można wyświetlić zawartość komunikatu i zobaczyć dokładnie to, co jest przesyłane, oraz czy jest ona zgodna <xref:System.ServiceModel.CorrelationQuery> z korelacją opartą na zawartości. Aby uzyskać więcej informacji na temat śledzenia WCF, zobacz [narzędzie Podgląd śledzenia usług (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)i [Używanie śledzenia do rozwiązywania problemów z aplikacją](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="common-context-exchange-correlation-issues"></a>Typowe problemy z korelacją z wymianą kontekstu
 Niektóre typy korelacji wymagają, aby do poprawnego działania korelacji był używany konkretny typ powiązania. Przykłady obejmują korelację typu żądanie-odpowiedź, która wymaga dwukierunkowego powiązania, takiego jak <xref:System.ServiceModel.BasicHttpBinding>, oraz korelacji z wymianą kontekstu, która wymaga powiązania opartego na kontekście, takiego jak <xref:System.ServiceModel.BasicHttpContextBinding>. Większość powiązań obsługuje operacje dwukierunkowe, dlatego nie jest to typowy problem związany z korelacją typu żądanie-odpowiedź, ale istnieje tylko kilku powiązań opartych na kontekście, w tym <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>i <xref:System.ServiceModel.NetTcpContextBinding>. Jeśli jedno z tych powiązań nie jest używane, początkowe wywołanie usługi przepływu pracy powiedzie się, ale kolejne wywołania zakończą się niepowodzeniem z następującym <xref:System.ServiceModel.FaultException>.

```output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 Informacje kontekstowe, które są używane dla korelacji kontekstu, mogą być zwracane przez <xref:System.ServiceModel.Activities.SendReply> do działania <xref:System.ServiceModel.Activities.Receive>, które inicjuje korelację kontekstu przy użyciu operacji dwukierunkowej, lub może być określony przez obiekt wywołujący, jeśli operacja jest jednokierunkowa. Jeśli kontekst nie jest wysyłany przez obiekt wywołujący lub zwracany przez usługę przepływu pracy, ten sam <xref:System.ServiceModel.FaultException> opisany wcześniej zostanie zwrócony po wywołaniu kolejnej operacji.

## <a name="common-request-reply-correlation-issues"></a>Typowe problemy z korelacją żądań i odpowiedzi
 Korelacja typu żądanie-odpowiedź jest używana z parowaniem <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> w celu zaimplementowania operacji dwukierunkowej w usłudze przepływu pracy i z <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> para, która wywołuje operację dwukierunkową w innej usłudze sieci Web. W przypadku wywoływania operacji dwukierunkowej w usłudze WCF usługa może być tradycyjnie zastrzeżonym, autonomiczną usługą WCF lub usługą przepływu pracy. Aby można było użyć korelacji typu żądanie-odpowiedź, należy użyć powiązania dwukierunkowego, takiego jak <xref:System.ServiceModel.BasicHttpBinding>, i operacje muszą być dwukierunkowe.

 Jeśli usługa przepływu pracy ma równoległe operacje dwukierunkowe lub nakładające się <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> lub <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply>, to niejawne zarządzanie uchwytami korelacji zapewniane przez <xref:System.ServiceModel.Activities.WorkflowServiceHost> może być niewystarczające, szczególnie w scenariuszach o dużej obciążeniu, a komunikaty mogą nie być poprawnie kierowane. Aby zapobiec wystąpieniu tego problemu, zalecamy, aby zawsze jawnie określić <xref:System.ServiceModel.Activities.CorrelationHandle> podczas korzystania z korelacji z odpowiedzią na żądanie. W przypadku korzystania z szablonów **SendAndReceiveReply** i **ReceiveAndSendReply** z sekcji Obsługa komunikatów w **przyborniku** w Projektancie przepływów pracy, <xref:System.ServiceModel.Activities.CorrelationHandle> jest jawnie konfigurowana domyślnie. Podczas kompilowania przepływu pracy przy użyciu kodu <xref:System.ServiceModel.Activities.CorrelationHandle> jest określony w <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> pierwszego działania w parze. W poniższym przykładzie działanie <xref:System.ServiceModel.Activities.Receive> jest skonfigurowane z jawnym <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> określonym w <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.

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

 Nie jest dozwolone utrzymywanie między <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> para lub <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply>. Tworzona jest strefa nie utrwalania, która obowiązuje do momentu zakończenia obu działań. Jeśli działanie, takie jak działanie opóźnienia, znajduje się w tej strefie no-utrwalania i powoduje, że przepływ pracy staje się bezczynna, przepływ pracy nie będzie trwał nawet wtedy, gdy host jest skonfigurowany do utrwalania przepływów pracy, gdy staną się bezczynne. Jeśli działanie, takie jak działanie utrwalania, próbuje jawnie pozostać w strefie no-utrwalania, zostanie zgłoszony wyjątek krytyczny, przepływ pracy zostanie przerwany, a <xref:System.ServiceModel.FaultException> jest zwracany do obiektu wywołującego. Komunikat o wyjątku krytycznym to "System. InvalidOperationException: działania utrwalania nie mogą być zawarte w blokach trwałości". Ten wyjątek nie jest zwracany do obiektu wywołującego, ale można go zaobserwować, jeśli śledzenie jest włączone. Komunikat dla <xref:System.ServiceModel.FaultException> zwróconego do obiektu wywołującego to "nie można wykonać operacji, ponieważ obiekt WorkflowInstance" 5836145b-7da2-49d0-a052-a49162adeab6 "został ukończony.

 Aby uzyskać więcej informacji na temat korelacji z żądaniem odpowiedzi, zobacz [żądanie-odpowiedź](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).

## <a name="common-content-correlation-issues"></a>Typowe problemy związane z korelacją zawartości
 Korelacja oparta na zawartości jest używana, gdy usługa przepływu pracy odbiera wiele komunikatów, a dane w komunikatach z wymienianymi informacjami identyfikują żądane wystąpienie. Korelacja oparta na zawartości używa tych danych w komunikacie, na przykład numeru klienta lub identyfikatora zamówienia, do przesyłania komunikatów do prawidłowego wystąpienia przepływu pracy. W tej sekcji opisano kilka typowych problemów, które mogą wystąpić podczas korzystania z korelacji opartej na zawartości.

### <a name="ensure-the-identifying-data-is-unique"></a>Upewnij się, że dane identyfikacyjne są unikatowe
 Dane używane do identyfikowania wystąpienia są skrótem do klucza korelacji. Należy pamiętać, aby zagwarantować, że dane, które są używane na potrzeby korelacji, są unikatowe lub mogą wystąpić konflikty w kluczowym skrócie i powodować błędne trasy komunikatów. Na przykład korelacja oparta tylko na nazwie klienta może prowadzić do kolizji, ponieważ może istnieć wielu klientów, którzy mają tę samą nazwę. Dwukropek (:) nie należy używać jako części danych, które są używane do skorelowania wiadomości, ponieważ jest ona już używana do rozgraniczania klucza i wartości zapytania komunikatu w celu utworzenia ciągu, który jest następnie używany do mieszania. Jeśli jest używana trwałość, upewnij się, że bieżące dane identyfikacyjne nie były używane przez poprzednio utrwalone wystąpienie. Tymczasowe wyłączenie trwałości może pomóc w zidentyfikowaniu tego problemu. Śledzenie WCF może służyć do wyświetlania obliczonego klucza korelacji i jest przydatne do debugowania tego rodzaju problemu.

### <a name="race-conditions"></a>Warunki wyścigu
 Istnieje niewielki odstęp czasu między usługą otrzymującą komunikat i faktycznie inicjowaną korelacją, podczas gdy komunikaty uzupełniające zostaną zignorowane. Jeśli usługa przepływu pracy inicjuje korelację opartą na zawartości przy użyciu danych przesyłanych z klienta w ramach operacji jednokierunkowych, a obiekt wywołujący wysyła natychmiastowe komunikaty monitujące, te komunikaty zostaną zignorowane w tym interwale. Można to uniknąć przy użyciu operacji dwukierunkowej w celu zainicjowania korelacji lub użycia <xref:System.ServiceModel.Activities.TransactedReceiveScope>.

### <a name="correlation-query-issues"></a>Problemy z kwerendą korelacji
 Zapytania korelacji służą do określania, które dane w wiadomości są używane do skorelowania wiadomości. Te dane są określane przy użyciu kwerendy XPath. Jeśli komunikaty do usługi nie są wysyłane, mimo że wszystko wydaje się prawidłowe, jedna strategia rozwiązywania problemów polega na określeniu wartości literału, która pasuje do wartości danych komunikatu zamiast zapytania XPath. Aby określić wartość literału, użyj funkcji `string`. W poniższym przykładzie <xref:System.ServiceModel.MessageQuerySet> jest skonfigurowany do używania wartości literału `11445` dla `OrderId`, a zapytanie XPath jest oznaczone jako komentarz.

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

 Jeśli zapytanie XPath jest skonfigurowane nieprawidłowo, tak że nie są pobierane żadne dane korelacji, zwracany jest błąd z następującym komunikatem: "zapytanie korelacji zwróciło pusty zestaw wyników. Upewnij się, że zapytania korelacji dla punktu końcowego są poprawnie skonfigurowane. " Jednym z szybkim sposobem rozwiązania tego problemu jest zastąpienie zapytania XPath wartością literału, zgodnie z opisem w poprzedniej sekcji. Ten problem może wystąpić, jeśli używasz konstruktora kwerend XPath w oknach dialogowych **Dodaj inicjatory korelacji** lub **definicję CorrelatesOn** , a usługa przepływu pracy używa kontraktów komunikatów. W poniższym przykładzie zdefiniowano klasę kontraktu komunikatu.

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

 Ten kontrakt komunikatu jest używany przez działanie <xref:System.ServiceModel.Activities.Receive> w przepływie pracy. `CartId` w nagłówku wiadomości służy do skorelowania komunikatu z właściwym wystąpieniem. Jeśli zapytanie XPath, które pobiera `CartId` jest tworzone przy użyciu okna dialogowego korelacji w Projektancie przepływu pracy, generowane jest następujące nieprawidłowe zapytanie XPath.

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 To zapytanie XPath byłoby poprawne, jeśli działanie <xref:System.ServiceModel.Activities.Receive> używało parametrów dla danych, ale ponieważ używa ona kontraktu komunikatu, jest on nieprawidłowy. Następujące zapytanie XPath jest poprawnym zapytaniem XPath, aby pobrać `CartId` z nagłówka.

```
sm:header()/tempuri:CartId
```

Można to potwierdzić, badając treść wiadomości.

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

Poniższy przykład przedstawia działanie <xref:System.ServiceModel.Activities.Receive> skonfigurowane dla operacji `AddItem`, która używa poprzedniego kontraktu komunikatu do odbierania danych. Zapytanie XPath zostało poprawnie skonfigurowane.

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
