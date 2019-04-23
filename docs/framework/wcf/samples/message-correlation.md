---
title: Korelacja komunikatów
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: ed6fc8f5d16ae2d604cdbdf4659ecfaaa83bfa02
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333278"
---
# <a name="message-correlation"></a><span data-ttu-id="adf31-102">Korelacja komunikatów</span><span class="sxs-lookup"><span data-stu-id="adf31-102">Message Correlation</span></span>
<span data-ttu-id="adf31-103">Niniejszy przykład pokazuje, jak aplikacja usługi kolejkowania komunikatów (MSMQ) można wysłać wiadomości usługi MSMQ do usługi Windows Communication Foundation (WCF) i jak można skorelować wiadomości między nadawcą i odbiorcą aplikacji w przypadku żądań/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="adf31-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="adf31-104">W tym przykładzie użyto powiązania msmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="adf31-104">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="adf31-105">Usługa jest w tym przypadku aplikacji konsoli Self-Hosted aby możliwe było zaobserwować, że usługa, która odbiera wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="adf31-105">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="adf31-106">k</span><span class="sxs-lookup"><span data-stu-id="adf31-106">k</span></span>  
  
 <span data-ttu-id="adf31-107">Usługa przetwarza wiadomości odebrane od nadawcy i wysyła odpowiedź do nadawcy.</span><span class="sxs-lookup"><span data-stu-id="adf31-107">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="adf31-108">Nadawca jest odpowiedzi, Odebrano żądanie, pierwotnie wysłany.</span><span class="sxs-lookup"><span data-stu-id="adf31-108">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="adf31-109">`MessageID` i `CorrelationID` właściwości wiadomości są używane do korelacji komunikatów żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="adf31-109">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>  
  
 <span data-ttu-id="adf31-110">`IOrderProcessor` Kontrakt usługi określa operację usługi jednokierunkowej, który jest odpowiedni do użycia z usługą kolejkowania.</span><span class="sxs-lookup"><span data-stu-id="adf31-110">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="adf31-111">Wiadomości usługi MSMQ nie ma nagłówek akcji, więc nie jest możliwe do mapowania różnych wiadomości usługi MSMQ kontrakty operacji automatycznie.</span><span class="sxs-lookup"><span data-stu-id="adf31-111">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="adf31-112">W związku z tym może istnieć tylko jeden kontrakt operacji w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="adf31-112">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="adf31-113">Jeśli chcesz zdefiniować więcej operacji kontraktów w usłudze, aplikacja musi udostępniać co który nagłówek w usłudze MSMQ komunikatu (na przykład, etykietę lub correlationID) może służyć do określania, który kontrakt operacji na wysłanie informacji.</span><span class="sxs-lookup"><span data-stu-id="adf31-113">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span> 
  
 <span data-ttu-id="adf31-114">Wiadomości usługi MSMQ nie zawiera również informacje, które nagłówki są zamapowane na różne parametry kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="adf31-114">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="adf31-115">W związku z tym może istnieć tylko jeden parametr w kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="adf31-115">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="adf31-116">Parametr jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, który zawiera podstawowe wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="adf31-116">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, which contains the underlying MSMQ message.</span></span> <span data-ttu-id="adf31-117">Typ "T" w elemencie `MsmqMessage<T>` klasa reprezentuje dane, które jest serializowana w treści wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="adf31-117">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="adf31-118">W tym przykładzie `PurchaseOrder` typ jest serializowana w treści wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="adf31-118">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="adf31-119">Operacja usługi przetworzy to zamówienie zakupu i wyświetla zawartość zamówienia zakupu i jego stan w oknie konsoli usługi.</span><span class="sxs-lookup"><span data-stu-id="adf31-119">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="adf31-120"><xref:System.ServiceModel.OperationBehaviorAttribute> Konfiguruje operacji można zarejestrować w transakcji z kolejki i do oznaczania transakcji ukończone po powrocie z operacji.</span><span class="sxs-lookup"><span data-stu-id="adf31-120">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="adf31-121">`PurchaseOrder` Zawiera szczegóły zamówienia, które muszą zostać przetworzone przez usługę.</span><span class="sxs-lookup"><span data-stu-id="adf31-121">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>

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

 <span data-ttu-id="adf31-122">Usługa używa niestandardowego klienta `OrderResponseClient` do wysyłania wiadomości usługi MSMQ do kolejki.</span><span class="sxs-lookup"><span data-stu-id="adf31-122">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="adf31-123">Ponieważ aplikacja, która odbiera i przetwarza komunikat jest aplikacją usługi MSMQ, a nie aplikacji WCF, istnieje nie niejawne Umowa serwisowa między dwiema aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="adf31-123">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="adf31-124">Dlatego nie można utworzyć serwera proxy, korzystając z narzędzia Svcutil.exe w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="adf31-124">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="adf31-125">Niestandardowy serwer proxy jest zasadniczo taki sam dla wszystkich aplikacji WCF, które używają `msmqIntegrationBinding` powiązania do wysyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="adf31-125">The custom proxy is essentially the same for all WCF applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="adf31-126">W przeciwieństwie do innych serwerów proxy nie obejmuje szereg operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="adf31-126">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="adf31-127">Jest tylko operacja komunikatu przesyłania.</span><span class="sxs-lookup"><span data-stu-id="adf31-127">It is a submit message operation only.</span></span>

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

 <span data-ttu-id="adf31-128">Usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="adf31-128">The service is self hosted.</span></span> <span data-ttu-id="adf31-129">Korzystając z transport integracji usługi MSMQ, kolejki, używane musi zostać utworzona wcześniej.</span><span class="sxs-lookup"><span data-stu-id="adf31-129">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="adf31-130">Można to zrobić ręcznie lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="adf31-130">This can be done manually or through code.</span></span> <span data-ttu-id="adf31-131">W tym przykładzie Usługa zawiera <xref:System.Messaging> kod do sprawdzania istnienia kolejki i utwórz ją, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="adf31-131">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="adf31-132">Nazwa kolejki jest do odczytu z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="adf31-132">The queue name is read from the configuration file.</span></span>

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

 <span data-ttu-id="adf31-133">Kolejki usługi MSMQ, do którego są wysyłane żądania zamówień jest określona w sekcji appSettings pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="adf31-133">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="adf31-134">Punkty końcowe klienta i usługi są zdefiniowane w sekcji system.serviceModel pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="adf31-134">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="adf31-135">Określ zarówno `msmqIntegrationbinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="adf31-135">Both specify the `msmqIntegrationbinding` binding.</span></span>

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

 <span data-ttu-id="adf31-136">Aplikacja kliencka używa <xref:System.Messaging> do wysyłania komunikatu trwały i transakcyjnych w kolejce.</span><span class="sxs-lookup"><span data-stu-id="adf31-136">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="adf31-137">Treść wiadomości zawiera zamówienia zakupu.</span><span class="sxs-lookup"><span data-stu-id="adf31-137">The message's body contains the purchase order.</span></span>

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

 <span data-ttu-id="adf31-138">Kolejki usługi MSMQ, z którego są odbierane odpowiedzi w kolejności jest określona w sekcji appSettings pliku konfiguracji, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="adf31-138">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
>  <span data-ttu-id="adf31-139">Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnik odwrotny w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="adf31-139">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="adf31-140">Adres punktu końcowego WCF Określa schemat msmq.formatname i używane "localhost" na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="adf31-140">The WCF endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="adf31-141">Nazwa formatu poprawnie sformułowany następuje msmq.formatname w identyfikatorze URI, zgodnie z wytycznymi usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="adf31-141">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="adf31-142">Zapisuje aplikacji klienta `messageID` kolejności komunikatu żądania, który wysyła do usługi i czeka na odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="adf31-142">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="adf31-143">Po nadejściu kolejki odpowiedzi klienta korelowany z komunikatem o kolejności wysyłane, za pomocą `correlationID` właściwości komunikatu, która zawiera `messageID` zamówienia komunikat, który klient wysłany do usługi.</span><span class="sxs-lookup"><span data-stu-id="adf31-143">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>

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

 <span data-ttu-id="adf31-144">Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="adf31-144">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="adf31-145">Można wyświetlić wiadomości odbierania usługi z klienta i wysyła odpowiedź z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="adf31-145">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="adf31-146">Klient jest wyświetlany odpowiedzi otrzymanych z usługi.</span><span class="sxs-lookup"><span data-stu-id="adf31-146">The client displays the response received from the service.</span></span> <span data-ttu-id="adf31-147">Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="adf31-147">Press ENTER in each console window to shut down the service and client.</span></span>

> [!NOTE]
>  <span data-ttu-id="adf31-148">Ten przykładowy skrypt wymaga instalacji z usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="adf31-148">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="adf31-149">Zapoznaj się z instrukcjami instalacji usługi MSMQ w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="adf31-149">See the MSMQ installation instructions in the See Also section.</span></span>

### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="adf31-150">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="adf31-150">To setup, build, and run the sample</span></span>

1. <span data-ttu-id="adf31-151">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="adf31-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="adf31-152">Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny.</span><span class="sxs-lookup"><span data-stu-id="adf31-152">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="adf31-153">Jeśli kolejka nie jest obecny, będzie utworzyć usługę.</span><span class="sxs-lookup"><span data-stu-id="adf31-153">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="adf31-154">Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="adf31-154">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="adf31-155">Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="adf31-155">Follow these steps to create a queue in Windows 2008.</span></span>

    1.  <span data-ttu-id="adf31-156">Otwórz Menedżera serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="adf31-156">Open Server Manager in Visual Studio 2012.</span></span>

    2.  <span data-ttu-id="adf31-157">Rozwiń **funkcji** kartę.</span><span class="sxs-lookup"><span data-stu-id="adf31-157">Expand the **Features** tab.</span></span>

    3.  <span data-ttu-id="adf31-158">Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="adf31-158">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4.  <span data-ttu-id="adf31-159">Sprawdź **transakcyjna** pole.</span><span class="sxs-lookup"><span data-stu-id="adf31-159">Check the **Transactional** box.</span></span>

    5.  <span data-ttu-id="adf31-160">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="adf31-160">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="adf31-161">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="adf31-161">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="adf31-162">Do uruchomienia przykładu w konfiguracji o jednym komputerze, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="adf31-162">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="adf31-163">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="adf31-163">To run the sample across computers</span></span>

1. <span data-ttu-id="adf31-164">Skopiuj pliki programu usługi z folderu \service\bin\ w folderze specyficzny dla języka na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="adf31-164">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="adf31-165">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="adf31-165">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="adf31-166">W pliku Client.exe.config zmienić orderQueueName do określenia nazwy komputera usługi zamiast ".".</span><span class="sxs-lookup"><span data-stu-id="adf31-166">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="adf31-167">W pliku Service.exe.config, Zmień adres punktu końcowego klienta, aby określić nazwę komputera klienta, a nie ".".</span><span class="sxs-lookup"><span data-stu-id="adf31-167">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>

5. <span data-ttu-id="adf31-168">Na komputerze usługi Service.exe należy uruchomić z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="adf31-168">On the service computer, launch Service.exe from a command prompt.</span></span>

6. <span data-ttu-id="adf31-169">Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="adf31-169">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="adf31-170">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="adf31-170">The samples may already be installed on your computer.</span></span> <span data-ttu-id="adf31-171">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="adf31-171">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="adf31-172">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="adf31-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="adf31-173">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="adf31-173">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a><span data-ttu-id="adf31-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="adf31-174">See also</span></span>

- [<span data-ttu-id="adf31-175">Tworzenie kolejek w programie WCF</span><span class="sxs-lookup"><span data-stu-id="adf31-175">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [<span data-ttu-id="adf31-176">Usługa kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="adf31-176">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
