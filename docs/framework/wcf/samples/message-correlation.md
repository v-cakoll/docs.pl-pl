---
title: Korelacja komunikatów
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: e4cd5dfd6f03370a408dc6f8fb39c983db3d43df
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389412"
---
# <a name="message-correlation"></a>Korelacja komunikatów
Niniejszy przykład pokazuje, jak aplikacja usługi kolejkowania komunikatów (MSMQ) można wysłać wiadomości usługi MSMQ do usługi Windows Communication Foundation (WCF) i jak można skorelować wiadomości między nadawcą i odbiorcą aplikacji w przypadku żądań/odpowiedzi. W tym przykładzie użyto powiązania msmqIntegrationBinding. Usługa jest w tym przypadku aplikacji konsoli Self-Hosted aby możliwe było zaobserwować, że usługa, która odbiera wiadomości w kolejce. K  
  
 Usługa przetwarza wiadomości odebrane od nadawcy i wysyła odpowiedź do nadawcy. Nadawca jest odpowiedzi, Odebrano żądanie, pierwotnie wysłany. `MessageID` i `CorrelationID` właściwości wiadomości są używane do korelacji komunikatów żądań i odpowiedzi.  
  
 `IOrderProcessor` Kontrakt usługi określa operację usługi jednokierunkowej, który jest odpowiedni do użycia z usługą kolejkowania. Wiadomości usługi MSMQ nie ma nagłówek akcji, więc nie jest możliwe do mapowania różnych wiadomości usługi MSMQ kontrakty operacji automatycznie. W związku z tym może istnieć tylko jeden kontrakt operacji w tym przypadku. Jeśli chcesz zdefiniować więcej operacji kontraktów w usłudze, aplikacja musi udostępniać co który nagłówek w usłudze MSMQ komunikatu (na przykład, etykietę lub correlationID) może służyć do określania, który kontrakt operacji na wysłanie informacji. Jest to zaprezentowane w [niestandardowe demultipleksowanie](../../../../docs/framework/wcf/samples/custom-demux.md).  
  
 Wiadomości usługi MSMQ nie zawiera również informacje, które nagłówki są zamapowane na różne parametry kontrakt operacji. W związku z tym może istnieć tylko jeden parametr w kontrakt operacji. Parametr jest typu <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` zawierający komunikat o podstawowym usługi MSMQ. Typ "T" w elemencie `MsmqMessage<T>` klasa reprezentuje dane, które jest serializowana w treści wiadomości usługi MSMQ. W tym przykładzie `PurchaseOrder` typ jest serializowana w treści wiadomości usługi MSMQ.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```

 Operacja usługi przetworzy to zamówienie zakupu i wyświetla zawartość zamówienia zakupu i jego stan w oknie konsoli usługi. <xref:System.ServiceModel.OperationBehaviorAttribute> Konfiguruje operacji można zarejestrować w transakcji z kolejki i do oznaczania transakcji ukończone po powrocie z operacji. `PurchaseOrder` Zawiera szczegóły zamówienia, które muszą zostać przetworzone przez usługę.  

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

 Usługa używa niestandardowego klienta `OrderResponseClient` do wysyłania wiadomości usługi MSMQ do kolejki. Ponieważ aplikacja, która odbiera i przetwarza komunikat jest aplikacją usługi MSMQ, a nie aplikacji WCF, istnieje nie niejawne Umowa serwisowa między dwiema aplikacjami. Dlatego nie można utworzyć serwera proxy, korzystając z narzędzia Svcutil.exe w tym scenariuszu.  
  
 Niestandardowy serwer proxy jest zasadniczo taki sam dla wszystkich aplikacji WCF, które używają `msmqIntegrationBinding` powiązania do wysyłania wiadomości. W przeciwieństwie do innych serwerów proxy nie obejmuje szereg operacji usługi. Jest tylko operacja komunikatu przesyłania.  

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

 Usługa jest samodzielnie hostowana. Korzystając z transport integracji usługi MSMQ, kolejki, używane musi zostać utworzona wcześniej. Można to zrobić ręcznie lub za pomocą kodu. W tym przykładzie Usługa zawiera <xref:System.Messaging> kod do sprawdzania istnienia kolejki i utwórz ją, jeśli to konieczne. Nazwa kolejki jest do odczytu z pliku konfiguracji.  

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
  
 Kolejki usługi MSMQ, do którego są wysyłane żądania zamówień jest określona w sekcji appSettings pliku konfiguracji. Punkty końcowe klienta i usługi są zdefiniowane w sekcji system.serviceModel pliku konfiguracji. Określ zarówno `msmqIntegrationbinding` powiązania.  
  
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
  
 Aplikacja kliencka używa <xref:System.Messaging> do wysyłania komunikatu trwały i transakcyjnych w kolejce. Treść wiadomości zawiera zamówienia zakupu.  

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

 Kolejki usługi MSMQ, z którego są odbierane odpowiedzi w kolejności jest określona w sekcji appSettings pliku konfiguracji, jak pokazano w poniższym Przykładowa konfiguracja.  
  
> [!NOTE]
>  Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnik odwrotny w ścieżce. Adres punktu końcowego WCF Określa schemat msmq.formatname i używane "localhost" na komputerze lokalnym. Nazwa formatu poprawnie sformułowany następuje msmq.formatname w identyfikatorze URI, zgodnie z wytycznymi usługi MSMQ.  
  
```xml  
<appSettings>  
    <add key=" orderResponseQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 Zapisuje aplikacji klienta `messageID` kolejności komunikatu żądania, który wysyła do usługi i czeka na odpowiedź z usługi. Po nadejściu kolejki odpowiedzi klienta korelowany z komunikatem o kolejności wysyłane, za pomocą `correlationID` właściwości komunikatu, która zawiera `messageID` zamówienia komunikat, który klient wysłany do usługi.  

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

 Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Można wyświetlić wiadomości odbierania usługi z klienta i wysyła odpowiedź z powrotem do klienta. Klient jest wyświetlany odpowiedzi otrzymanych z usługi. Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.  
  
> [!NOTE]
>  Ten przykładowy skrypt wymaga instalacji z usługi kolejkowania komunikatów (MSMQ). Zapoznaj się z instrukcjami instalacji usługi MSMQ w sekcji Zobacz też.  
  
### <a name="to-setup-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny. Jeśli kolejka nie jest obecny, będzie utworzyć usługę. Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.  
  
    1.  Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozwiń **funkcji** kartę.  
  
    3.  Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.  
  
    4.  Sprawdź **transakcyjna** pole.  
  
    5.  Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.  
  
3.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym komputerze, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1.  Skopiuj pliki programu usługi z folderu \service\bin\ w folderze specyficzny dla języka na komputerze usługi.  
  
2.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.  
  
3.  W pliku Client.exe.config zmienić orderQueueName do określenia nazwy komputera usługi zamiast ".".  
  
4.  W pliku Service.exe.config, Zmień adres punktu końcowego klienta, aby określić nazwę komputera klienta, a nie ".".  
  
5.  Na komputerze usługi Service.exe należy uruchomić z wiersza polecenia.  
  
6.  Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Usługa kolejkowania komunikatów](https://go.microsoft.com/fwlink/?LinkId=94968)
