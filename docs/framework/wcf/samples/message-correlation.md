---
title: Korelacja komunikatów
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: 657f7c6e3fd544614e193d9e6843a8ed58881387
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039410"
---
# <a name="message-correlation"></a>Korelacja komunikatów
Ten przykład pokazuje, jak aplikacja usługi kolejkowania komunikatów (MSMQ) może wysyłać komunikat usługi MSMQ do usługi Windows Communication Foundation (WCF) oraz jak można skorelować komunikaty między aplikacjami nadawcy i odbiorcy w scenariuszu żądania/odpowiedzi. Ten przykład używa powiązania msmqIntegrationBinding. Usługa w tym przypadku jest samoobsługową aplikacją konsolową, która umożliwia obserwowanie usługi, która odbiera wiadomości w kolejce. k  
  
 Usługa przetwarza komunikat odebrany od nadawcy i wysyła komunikat odpowiedzi z powrotem do nadawcy. Nadawca skorelowanie odpowiedzi otrzymanej na żądanie wysłane pierwotnie. Właściwości `MessageID` i`CorrelationID` komunikatu są używane do skorelowania komunikatów żądania i odpowiedzi.  
  
 Kontrakt `IOrderProcessor` usługi definiuje jednokierunkową operację usługi, która jest odpowiednia do użycia z kolejkami. Komunikat usługi MSMQ nie zawiera nagłówka akcji, więc nie jest możliwe automatyczne Mapowanie komunikatów usługi MSMQ do kontraktów operacji. W związku z tym w tym przypadku może istnieć tylko jeden kontrakt operacji. Jeśli chcesz zdefiniować więcej kontraktów operacji w usłudze, aplikacja musi podać informacje dotyczące tego, w którym nagłówku wiadomości MSMQ (na przykład etykieta lub identyfikator korelacji) można użyć do określenia, który kontrakt operacji ma zostać przesłany. 
  
 Komunikat MSMQ nie zawiera również informacji o tym, które nagłówki są mapowane na różne parametry kontraktu operacji. W związku z tym w kontrakcie operacji może istnieć tylko jeden parametr. Parametr jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, który zawiera źródłowy komunikat MSMQ. Typ "T" w `MsmqMessage<T>` klasie reprezentuje dane, które są serializowane w treści wiadomości MSMQ. W tym przykładzie `PurchaseOrder` typ jest serializowany do treści wiadomości MSMQ.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 Operacja usługi przetwarza zamówienie zakupu i wyświetla zawartość zamówienia zakupu oraz jego stan w oknie konsoli usługi. <xref:System.ServiceModel.OperationBehaviorAttribute> Konfiguruje operację do rejestracji w transakcji z kolejką i oznacza, że transakcja została ukończona, gdy operacja zwróci wartość. `PurchaseOrder` Zawiera szczegółowe informacje o zamówieniach, które muszą zostać przetworzone przez usługę.

```csharp
// Service class that implements the service contract.
public class OrderProcessorService : IOrderProcessor
{
   [OperationBehavior(TransactionScopeRequired = true,
          TransactionAutoComplete = true)]
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)
   {
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;
       Random statusIndexer = new Random();
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
       Console.WriteLine("Processing {0} ", po);
       //Send a response to the client that the order has been received
         and is pending fullfillment.
       SendResponse(ordermsg);
    }

    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)
    {
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");

        //Set the correlation ID such that the client can correlate the response to the order.
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);
        orderResponsemsg.CorrelationId = ordermsg.Id;
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.SendOrderResponse(orderResponsemsg);
            scope.Complete();
        }

        client.Close();
    }
}
```

 Usługa używa klienta `OrderResponseClient` niestandardowego do wysyłania wiadomości MSMQ do kolejki. Ponieważ aplikacja, która odbiera i przetwarza komunikat, jest aplikacją usługi MSMQ, a nie aplikacją WCF, nie istnieje niejawna Umowa serwisowa między tymi dwiema aplikacjami. Dlatego nie można utworzyć serwera proxy za pomocą narzędzia Svcutil. exe w tym scenariuszu.

 Niestandardowy serwer proxy jest zasadniczo taki sam dla wszystkich aplikacji WCF, które używają `msmqIntegrationBinding` powiązania do wysyłania komunikatów. W przeciwieństwie do innych serwerów proxy, nie obejmuje zakresu operacji usługi. Jest to tylko operacja przesyłania wiadomości.

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderResponse
{

    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse
{

    public OrderResponseClient()
    { }

    public OrderResponseClient(string configurationName)
        : base(configurationName)
    { }

    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SendOrderResponse(msg);
    }
}
```

 Usługa jest samodzielna. W przypadku korzystania z transportu integracji usługi MSMQ użyta Kolejka musi zostać utworzona z góry. Można to zrobić ręcznie lub przy użyciu kodu. W tym przykładzie usługa zawiera <xref:System.Messaging> kod służący do sprawdzania istnienia kolejki i tworzenia jej w razie potrzeby. Nazwa kolejki jest odczytywana z pliku konfiguracji.

```csharp
public static void Main()
{
       // Get the MSMQ queue name from application settings in configuration.
      string queueName =
                ConfigurationManager.AppSettings["orderQueueName"];
      // Create the transacted MSMQ queue if necessary.
      if (!MessageQueue.Exists(queueName))
                MessageQueue.Create(queueName, true);
     // Create a ServiceHost for the OrderProcessorService type.
     using (ServiceHost serviceHost = new
                   ServiceHost(typeof(OrderProcessorService)))
     {
            serviceHost.Open();
            // The service can now be accessed.
            Console.WriteLine("The service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.ReadLine();
            // Close the ServiceHost to shutdown the service.
            serviceHost.Close();
      }
}
```

 Kolejka MSMQ, do której wysyłane są żądania zamówienia, jest określona w sekcji appSettings w pliku konfiguracji. Punkty końcowe klienta i usługi są zdefiniowane w sekcji System. serviceModel w pliku konfiguracji. Oba określają `msmqIntegrationbinding` powiązanie.

```xml
<appSettings>
  <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>

<system.serviceModel>
  <client>
    <endpoint    name="OrderResponseEndpoint"
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"
              binding="msmqIntegrationBinding"
              bindingConfiguration="OrderProcessorBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">
    </endpoint>
  </client>

  <services>
    <service
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"
                            binding="msmqIntegrationBinding"
                bindingConfiguration="OrderProcessorBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">
      </endpoint>
    </service>
  </services>

  <bindings>
    <msmqIntegrationBinding>
      <binding name="OrderProcessorBinding" >
        <security mode="None" />
      </binding>
    </msmqIntegrationBinding>
  </bindings>

</system.serviceModel>
```

 Aplikacja kliencka używa <xref:System.Messaging> programu w celu wysyłania trwałych i transakcyjnych komunikatów do kolejki. Treść wiadomości zawiera zamówienie zakupu.

```csharp
static void PlaceOrder()
{
    //Connect to the queue
    MessageQueue orderQueue =
            new MessageQueue(
                    ConfigurationManager.AppSettings["orderQueueName"])
    // Create the purchase order.
    PurchaseOrder po = new PurchaseOrder();
    po.CustomerId = "somecustomer.com";
    po.PONumber = Guid.NewGuid().ToString();
    PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();
    lineItem1.ProductId = "Blue Widget";
    lineItem1.Quantity = 54;
    lineItem1.UnitCost = 29.99F;

    PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();
    lineItem2.ProductId = "Red Widget";
    lineItem2.Quantity = 890;
    lineItem2.UnitCost = 45.89F;

    po.orderLineItems = new PurchaseOrderLineItem[2];
    po.orderLineItems[0] = lineItem1;
    po.orderLineItems[1] = lineItem2;

    Message msg = new Message();
    msg.UseDeadLetterQueue = true;
    msg.Body = po;

    //Create a transaction scope.
    using (TransactionScope scope = new
     TransactionScope(TransactionScopeOption.Required))
    {
        // Submit the purchase order.
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
        // Complete the transaction.
        scope.Complete();
    }
    //Save the messageID for order response correlation.
    orderMessageID = msg.Id;
    Console.WriteLine("Placed the order, waiting for response...");
}
```

 Kolejka MSMQ, z której są odbierane odpowiedzi Orders, została określona w sekcji appSettings w pliku konfiguracji, jak pokazano w poniższej konfiguracji przykładowej.

> [!NOTE]
> Nazwa kolejki używa kropki (.) dla komputera lokalnego i separatorów ukośników odwrotnych. Adres punktu końcowego WCF określa schemat MSMQ. formatname i używa "localhost" dla komputera lokalnego. Poprawnie sformułowana nazwa formatu jest zgodna z nazwą MSMQ. formatname w identyfikatorze URI zgodnie z wytycznymi dotyczącymi usługi MSMQ.

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 Aplikacja kliencka zapisuje `messageID` komunikat żądania zamówienia wysyłany do usługi i czeka na odpowiedź z usługi. Po nadejściu odpowiedzi w kolejce klient korelacji z komunikatem o zamówieniu, który został wysłany przy `correlationID` użyciu właściwości komunikatu, `messageID` zawierającego komunikat o kolejności, który został pierwotnie Wysłany przez klienta do usługi.

```csharp
static void DisplayOrderStatus()
{
    MessageQueue orderResponseQueue = new
     MessageQueue(ConfigurationManager.AppSettings
                  ["orderResponseQueueName"]);
    //Create a transaction scope.
    bool responseReceived = false;
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;
    while (!responseReceived)
    {
       Message responseMsg;
       using (TransactionScope scope2 = new
         TransactionScope(TransactionScopeOption.Required))
       {
          //Receive the Order Response message.
          responseMsg =
              orderResponseQueue.Receive
                   (MessageQueueTransactionType.Automatic);
          scope2.Complete();
     }
     responseMsg.Formatter = new
     System.Messaging.XmlMessageFormatter(new Type[] {
         typeof(PurchaseOrder) });
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;
    //Check if the response is for the order placed.
    if (orderMessageID == responseMsg.CorrelationId)
    {
       responseReceived = true;
       Console.WriteLine("Status of current Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
    else
    {
       Console.WriteLine("Status of previous Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
  }
}
```

 Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta. Można zobaczyć, że usługa odbiera komunikaty od klienta i wysyła odpowiedź z powrotem do klienta. Klient wyświetla odpowiedź odebraną z usługi. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.

> [!NOTE]
> Ten przykład wymaga instalacji usługi kolejkowania komunikatów (MSMQ). Zapoznaj się z instrukcjami dotyczącymi instalacji usługi MSMQ w sekcji Zobacz też.

### <a name="to-setup-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Jeśli usługa jest uruchamiana po raz pierwszy, sprawdzi, czy kolejka jest obecna. Jeśli kolejka nie istnieje, usługa utworzy ją. Aby utworzyć kolejkę, można najpierw uruchomić tę usługę lub utworzyć ją za pośrednictwem Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.

    1. Otwórz Menedżer serwera w programie Visual Studio 2012.

    2. Rozwiń kartę **funkcje** .

    3. Kliknij prawym przyciskiem myszy pozycję **prywatne kolejki komunikatów**, a następnie wybierz kolejno pozycje **Nowa**i **prywatne**.

    4. Zaznacz pole **transakcyjne** .

    5. Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.

3. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Aby uruchomić przykład w konfiguracji pojedynczego komputera, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na wielu komputerach

1. Skopiuj pliki programu Service Files z folderu \service\bin\, w obszarze folder specyficzny dla języka, do komputera usługi.

2. Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputera klienckiego.

3. W pliku Client. exe. config zmień orderQueueName, aby określić nazwę komputera usługi zamiast ".".

4. W pliku Service. exe. config zmień adres punktu końcowego klienta, aby określić nazwę komputera klienckiego zamiast ".".

5. Na komputerze usługi Uruchom polecenie Service. exe z wiersza polecenia.

6. Na komputerze klienckim uruchom program Client. exe z wiersza polecenia.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Kolejkowanie komunikatów](https://go.microsoft.com/fwlink/?LinkId=94968)
