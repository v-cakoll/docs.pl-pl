---
title: Korelacja rozwiązywania problemów
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: fecfaf7374823bb19a4ad3d7f6cb2dbbdf139703
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932824"
---
# <a name="troubleshooting-correlation"></a>Korelacja rozwiązywania problemów
Korelacja służy do wiązania komunikatów usługi przepływu pracy i wystąpienia poprawne przepływu pracy, ale jeśli nie jest poprawnie skonfigurowany, nie otrzyma wiadomości i aplikacje nie będą działać poprawnie. Ten temat zawiera omówienie kilku metod w celu rozwiązywania problemów korelacji i wyświetla także niektóre typowe problemy, które mogą wystąpić, gdy używasz korelacji.

## <a name="handle-the-unknownmessagereceived-event"></a>Obsługuj zdarzenie UnknownMessageReceived
 <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> Zdarzenie występuje, gdy nieznany komunikat jest odbierany przez usługę, w tym komunikaty, które nie mogą zostać skorelowane z istniejącego wystąpienia. Samodzielnie hostowany usług tego zdarzenia mogą być obsługiwane w aplikacji hosta.

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 W przypadku usług hostowanych w sieci Web to zdarzenie może zostać obsłużony przez wyprowadzanie klasy z <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> i zastępowanie <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.

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

 To niestandardowe <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> można określić w `svc` pliku dla usługi.

```
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>
```

 Po wywołaniu tego programu obsługi wiadomości mogą być pobierane przy użyciu <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> właściwość <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>i będą podobne do następujących.

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

 Inspekcja komunikaty wysyłane do <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> program obsługi może zapewnić wskazówek dotyczących przyczyny wiadomość nie odnoszą się do wystąpienia usługi przepływu pracy.

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>Korzystanie ze śledzenia można monitorować postęp przepływu pracy
 Śledzenie zapewnia sposób, aby monitorować postęp przepływu pracy. Domyślnie są emitowane rekordów śledzenia zdarzeń cyklu życia przepływu pracy, zdarzenia cyklu życia działań, propagacji błędów i wznowienie zakładki. Ponadto niestandardowe rekordy śledzenia może być emitowana przez działania niestandardowe. Działania śledzenia rekordów, zakładki wznowienie rekordów i rekordy propagacji błędów są najbardziej przydatne, gdy korelacja rozwiązywania problemów. Śledzenie rekordów działań może służyć do określenia Bieżący postęp przepływu pracy i może ułatwić identyfikację, których działanie komunikatów oczekiwaniem na komunikaty. Zakładki wznowienie rekordów są przydatne, ponieważ wskazują, że wiadomość została odebrana przez przepływ pracy, oraz rekordy propagacji błędów rekord wszystkie błędy w przepływie pracy. Aby włączyć śledzenie, określ żądany <xref:System.Activities.Tracking.TrackingParticipant> w <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> z <xref:System.ServiceModel.Activities.WorkflowServiceHost>. W poniższym przykładzie `ConsoleTrackingParticipant` (z [niestandardowe śledzenia](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) przykładowy) jest konfigurowana przy użyciu domyślnego profilu śledzenia.

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 Uczestnika śledzenia, takie jak ConsoleTrackingParticipant przydaje się do usługi samodzielnie hostowanej przepływu pracy, z okna konsoli. W przypadku usługi hostowanej w sieci Web śledzenia uczestnika, który rejestruje informacje śledzenia do trwałego magazynu powinny być używane takie jak wbudowane <xref:System.Activities.Tracking.EtwTrackingParticipant>, lub uczestnikiem niestandardowe śledzenia, który rejestruje informacje w pliku.

 Aby uzyskać więcej informacji na temat śledzenia i Konfigurowanie śledzenia dla usługi hostowanej w sieci Web przepływu pracy, zobacz [przepływu pracy i śledzenie](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Konfigurowanie śledzenia przepływu pracy](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)i [ Śledzenie &#91;WF — przykłady&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) przykłady.

## <a name="use-wcf-tracing"></a>Użyj śledzenia WCF
 Śledzenie programu WCF zapewnia śledzenie przepływu wiadomości do i z usługi przepływu pracy. Te informacje śledzenia jest przydatne podczas rozwiązywania problemów korelacji, szczególnie w przypadku korelacji na podstawie zawartości. Aby włączyć śledzenie, należy określić żądanego śledzenia słuchaczy w `system.diagnostics` części `web.config` plik, jeśli usługa przepływu pracy jest hostowane w sieci Web lub `app.config` plik, jeśli usługa przepływu pracy jest samodzielnie hostowana. Aby dołączyć zawartość wiadomości w pliku śledzenia, należy określić `true` dla `logEntireMessage` w `messageLogging` element `diagnostics` części `system.serviceModel`. W poniższym przykładzie skonfigurowano informacji śledzenia, w tym treść wiadomości, są zapisywane w pliku o nazwie `service.svclog`.

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

 Aby wyświetlić informacje o śledzeniu, który jest zawarty w `service.svclog`, [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) jest używany. Jest to szczególnie przydatne podczas rozwiązywania problemów na podstawie zawartości korelacji problemy, ponieważ możesz wyświetlać zawartość wiadomości i dokładnie co to jest przekazywana, i czy jest on zgodny <xref:System.ServiceModel.CorrelationQuery> dla korelacji na podstawie zawartości. Aby uzyskać więcej informacji na temat śledzenia WCF, zobacz [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), i [przy użyciu śledzenia Rozwiązywanie problemów z aplikacją](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="common-context-exchange-correlation-issues"></a>Typowe problemy korelacja wymiany kontekstu
 Niektóre rodzaje korelacji wymagają, że określonego typu powiązania służy do korelacji działała prawidłowo. Przykłady obejmują korelacji "żądanie-odpowiedź", która wymaga dwukierunkowego powiązania w takich jak <xref:System.ServiceModel.BasicHttpBinding>i korelacja wymiany kontekstu, co wymaga na podstawie kontekstu wiązania takich jak <xref:System.ServiceModel.BasicHttpContextBinding>. Większość powiązania obsługi operacji dwukierunkową, co nie jest to typowy problem dla korelacji "żądanie-odpowiedź", ale istnieje kilka tylko na podstawie kontekstu powiązania, łącznie z <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, i <xref:System.ServiceModel.NetTcpContextBinding>. Jeśli jedno z tych powiązań, nie jest używany, początkowe wywołanie usługi przepływu pracy zakończy się powodzeniem, ale kolejne wywołania zakończy się niepowodzeniem z następującym <xref:System.ServiceModel.FaultException>.

```Output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 Informacje o kontekście, które jest używane na potrzeby korelacji kontekstu może zostać zwrócony przez <xref:System.ServiceModel.Activities.SendReply> do <xref:System.ServiceModel.Activities.Receive> działanie, które inicjuje korelacji kontekstu, gdy za pomocą dwukierunkowych operacji lub jest on można określić przez obiekt wywołujący, gdy operacja jest jednokierunkowe. Jeśli kontekst nie jest wysyłany przez obiekt wywołujący lub zwrócone przez usługi przepływu pracy, a następnie takie same <xref:System.ServiceModel.FaultException> opisanego wcześniej zostanie zwrócona po wywołaniu kolejna operacja.

## <a name="common-request-reply-correlation-issues"></a>Typowe problemy korelacji "żądanie-odpowiedź"
 Korelacja żądań i odpowiedzi jest używany z <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> Paruj, aby zaimplementować dwukierunkowe operacji w usłudze przepływu pracy i <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> parą, która wywołuje dwukierunkowe operacji w innej sieci Web Usługa. Podczas wywoływania dwukierunkowe operacji usługi WCF, usługa może być albo tradycyjne usługi WCF na podstawie kodu imperatywnego lub może być usługi przepływu pracy. Aby użyć korelacji "żądanie-odpowiedź" powiązanie dwustronne należy użyć, takie jak <xref:System.ServiceModel.BasicHttpBinding>, i działania muszą być dwukierunkowe.

 Jeśli usługa przepływu pracy ma dwukierunkową operacje w równoległego lub nakładający się <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> lub <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary, a następnie niejawne korelacji obsługiwać zarządzanie zapewniane przez <xref:System.ServiceModel.Activities.WorkflowServiceHost>może nie być wystarczające, szczególnie w scenariuszach wysokiej obciążenia, a komunikaty mogą nie być poprawnie kierowane. Aby zapobiec występowaniu tego problemu, zaleca się, że należy zawsze jawnie określać <xref:System.ServiceModel.Activities.CorrelationHandle> przy użyciu korelacja żądań i odpowiedzi. Korzystając z **SendAndReceiveReply** i **ReceiveAndSendReply** szablony komunikatów w sekcji **przybornika** w Projektancie przepływu pracy <xref:System.ServiceModel.Activities.CorrelationHandle> jawnie jest konfiguracja domyślna. Podczas tworzenia przepływu pracy przy użyciu kodu, <xref:System.ServiceModel.Activities.CorrelationHandle> została określona w <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> pierwszego działania w parze. W poniższym przykładzie <xref:System.ServiceModel.Activities.Receive> działanie jest skonfigurowane z jawną <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> określonych w <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.

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

 Stan trwały nie jest dozwolone między <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary lub <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary. Tworzona jest strefa no-persist ważny, dopóki oba działania zostały wykonane. Jeśli działania, takie jak działanie opóźnienia, znajduje się w tej strefie no-persist, powoduje, że przepływ pracy przejdzie w stan bezczynności przepływu pracy nie zostanie utrzymany, nawet wtedy, gdy jej host jest skonfigurowany do utrwalenia przepływów pracy, gdy staną się bezczynności. Jeśli działania, takie jak działanie utrwalanie próbuje jawnie utrwalanie w strefie nie utrwalanie, wyjątek krytyczny jest zgłaszany, przerwań przepływu pracy, a <xref:System.ServiceModel.FaultException> jest zwracany do obiektu wywołującego. Komunikat o wyjątku krytycznego "System.InvalidOperationException: Utrwalanie działania nie może być zawarta w blokach nie trwałości. ". Ten wyjątek nie są zwracane do obiektu wywołującego, ale można zaobserwować, jeśli śledzenie jest wyłączone. W komunikacie o <xref:System.ServiceModel.FaultException> zwracane do obiektu wywołującego jest "nie można wykonać operacji, ponieważ wystąpienie przepływu pracy"5836145b-7da2 - 49 d 0-a052-a49162adeab6"została ukończona".

 Aby uzyskać więcej informacji na temat korelacji "żądanie-odpowiedź" zobacz ["żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).

## <a name="common-content-correlation-issues"></a>Typowe problemy zawartości korelacji
 Korelacja oparta na zawartości jest używane, gdy usługi przepływu pracy otrzymuje wiele wiadomości i element danych w ramach wymiany komunikatów identyfikuje żądaną wystąpienie. Korelacja oparta na zawartości używa tych danych w komunikacie, takie jak liczba lub kolejność ID klienta do wyznaczania tras dla wystąpienia przepływu pracy poprawne. W tej sekcji opisano kilka typowych problemów, które mogą wystąpić podczas korzystania na podstawie zawartości korelacji.

### <a name="ensure-the-identifying-data-is-unique"></a>Upewnij się, że dane identyfikacyjne są unikatowe
 Dane, które służy do identyfikowania wystąpienia jest wyznaczana wartość skrótu na klucz korelacji. Należy uważać, aby zagwarantować, że dane, które jest używane na potrzeby korelacji jest unikatowa w przeciwnym razie kolizji w formie skrótu klucza mogą występować i komunikaty można rozsyłanymi. Na przykład korelacji, wyłącznie według nazwy klienta może spowodować kolizji, ponieważ może to być wielu klientów, którzy mają taką samą nazwę. Dwukropek (:), nie powinien służyć jako część danych, który służy do skorelowania komunikatu, ponieważ jest już używany do ograniczania klucz i wartość w celu utworzenia ciąg, który jest następnie wartość skrótu dla zapytania o komunikat o. Jeśli trwałości jest używana, upewnij się, czy bieżące dane identyfikacyjne nie został użyty przez wystąpienie utrwalonych wcześniej. Tymczasowe wyłączenie trwałości pomaga zidentyfikować ten problem. Śledzenie programu WCF można wyświetlić klucz korelacji obliczeniowe i jest przydatna podczas debugowania rozwiązania tego problemu.

### <a name="race-conditions"></a>Warunki wyścigu
 Istnieje mały odstęp w czasie między usługa odbiera komunikat i korelacji, faktycznie inicjowany, podczas której zostaną zignorowane komunikaty monitujące o. Jeśli usługa przepływu pracy inicjuje korelacji na podstawie zawartości przy użyciu danych przesyłanych między klientem za pośrednictwem operacji jednokierunkowych, a obiekt wywołujący wysyła natychmiastowego komunikaty monitujące, te wiadomości będą ignorowane w danym przedziale czasu. To można uniknąć przy użyciu operacji dwukierunkowe zainicjować korelację lub za pomocą <xref:System.ServiceModel.Activities.TransactedReceiveScope>.

### <a name="correlation-query-issues"></a>Korelacja zapytania problemów
 Korelacja zapytania są używane do określania, jakie dane w komunikacie służy do skorelowania wiadomości. Te dane są określane za pomocą zapytania XPath. Jeśli nie są też wysyłane komunikaty do usługi, mimo wszystko, co wydaje się być poprawne, jedną ze strategii do rozwiązywania problemów jest określić wartość literału, które pasują do wartości danych komunikatu zamiast zapytania XPath. Aby określić wartość literału, należy użyć `string` funkcji. W poniższym przykładzie <xref:System.ServiceModel.MessageQuerySet> jest skonfigurowany do używania wartość literału `11445` dla `OrderId` i zapytanie XPath jest opatrzona komentarzem.

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

 Jeśli zapytanie XPath jest niepoprawnie skonfigurowane tak, są pobierane żadne dane korelacji, błąd jest zwracany z następującym komunikatem: "Korelacji zapytanie zwróciło pusty zestaw wyników. Upewnij się, że zapytania korelacji dla punktu końcowego są poprawnie skonfigurowane." Szybki sposób rozwiązać ten problem jest kwerenda XPath Zamień na wartość literału zgodnie z opisem w poprzedniej sekcji. Ten problem może wystąpić, jeśli używasz konstruktora zapytań XPath w **Dodaj inicjatory korelacji** lub **definice Vlastnosti Correlateson** usługi przepływu pracy i okien dialogowych używa kontrakty komunikatów. W poniższym przykładzie zdefiniowano klasę kontraktu komunikatu.

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

 Ten kontrakt komunikatu jest używana przez <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. `CartId` w nagłówku komunikatu służy do skorelowania komunikat, który ma prawidłowe wystąpienie. Jeśli zapytanie XPath, który pobiera `CartId` jest tworzony przy użyciu okien dialogowych korelacji w Projektancie przepływu pracy, następujące nieprawidłową wartością XPath jest generowane zapytanie.

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 Ta kwerenda XPath są poprawne Jeśli <xref:System.ServiceModel.Activities.Receive> działanie używane parametry dla danych, ale ponieważ korzysta ona z kontraktu komunikatu jest nieprawidłowy. Następujące zapytanie XPath jest prawidłowe zapytanie XPath do pobrania `CartId` z nagłówka.

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

W poniższym przykładzie przedstawiono <xref:System.ServiceModel.Activities.Receive> działania skonfigurowane dla `AddItem` operacji, która używa poprzedniego kontraktu komunikatu, aby odbierać dane. Zapytanie XPath jest poprawnie skonfigurowany.

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
