---
title: Korelacja komunikatów
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: 1f476e94ec3229ee7f5433d54d286165d108e5e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930750"
---
# <a name="message-correlation"></a><span data-ttu-id="3c190-102">Korelacja komunikatów</span><span class="sxs-lookup"><span data-stu-id="3c190-102">Message Correlation</span></span>
<span data-ttu-id="3c190-103">Ten przykład pokazuje, jak aplikacja usługi kolejkowania komunikatów (MSMQ) może wysyłać komunikat usługi MSMQ do usługi Windows Communication Foundation (WCF) oraz jak można skorelować komunikaty między aplikacjami nadawcy i odbiorcy w scenariuszu żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3c190-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="3c190-104">Ten przykład używa powiązania msmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="3c190-104">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="3c190-105">Usługa w tym przypadku jest samoobsługową aplikacją konsolową, która umożliwia obserwowanie usługi, która odbiera wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="3c190-105">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="3c190-106">k</span><span class="sxs-lookup"><span data-stu-id="3c190-106">k</span></span>  
  
 <span data-ttu-id="3c190-107">Usługa przetwarza komunikat odebrany od nadawcy i wysyła komunikat odpowiedzi z powrotem do nadawcy.</span><span class="sxs-lookup"><span data-stu-id="3c190-107">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="3c190-108">Nadawca skorelowanie odpowiedzi otrzymanej na żądanie wysłane pierwotnie.</span><span class="sxs-lookup"><span data-stu-id="3c190-108">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="3c190-109">Właściwości `MessageID` i`CorrelationID` komunikatu są używane do skorelowania komunikatów żądania i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3c190-109">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>  
  
 <span data-ttu-id="3c190-110">Kontrakt `IOrderProcessor` usługi definiuje jednokierunkową operację usługi, która jest odpowiednia do użycia z kolejkami.</span><span class="sxs-lookup"><span data-stu-id="3c190-110">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="3c190-111">Komunikat usługi MSMQ nie zawiera nagłówka akcji, więc nie jest możliwe automatyczne Mapowanie komunikatów usługi MSMQ do kontraktów operacji.</span><span class="sxs-lookup"><span data-stu-id="3c190-111">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="3c190-112">W związku z tym w tym przypadku może istnieć tylko jeden kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="3c190-112">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="3c190-113">Jeśli chcesz zdefiniować więcej kontraktów operacji w usłudze, aplikacja musi podać informacje dotyczące tego, w którym nagłówku wiadomości MSMQ (na przykład etykieta lub identyfikator korelacji) można użyć do określenia, który kontrakt operacji ma zostać przesłany.</span><span class="sxs-lookup"><span data-stu-id="3c190-113">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span> 
  
 <span data-ttu-id="3c190-114">Komunikat MSMQ nie zawiera również informacji o tym, które nagłówki są mapowane na różne parametry kontraktu operacji.</span><span class="sxs-lookup"><span data-stu-id="3c190-114">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="3c190-115">W związku z tym w kontrakcie operacji może istnieć tylko jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="3c190-115">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="3c190-116">Parametr jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, który zawiera źródłowy komunikat MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3c190-116">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, which contains the underlying MSMQ message.</span></span> <span data-ttu-id="3c190-117">Typ "T" w `MsmqMessage<T>` klasie reprezentuje dane, które są serializowane w treści wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3c190-117">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="3c190-118">W tym przykładzie `PurchaseOrder` typ jest serializowany do treści wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3c190-118">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="3c190-119">Operacja usługi przetwarza zamówienie zakupu i wyświetla zawartość zamówienia zakupu oraz jego stan w oknie konsoli usługi.</span><span class="sxs-lookup"><span data-stu-id="3c190-119">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="3c190-120"><xref:System.ServiceModel.OperationBehaviorAttribute> Konfiguruje operację do rejestracji w transakcji z kolejką i oznacza, że transakcja została ukończona, gdy operacja zwróci wartość.</span><span class="sxs-lookup"><span data-stu-id="3c190-120">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="3c190-121">`PurchaseOrder` Zawiera szczegółowe informacje o zamówieniach, które muszą zostać przetworzone przez usługę.</span><span class="sxs-lookup"><span data-stu-id="3c190-121">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>

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

 <span data-ttu-id="3c190-122">Usługa używa klienta `OrderResponseClient` niestandardowego do wysyłania wiadomości MSMQ do kolejki.</span><span class="sxs-lookup"><span data-stu-id="3c190-122">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="3c190-123">Ponieważ aplikacja, która odbiera i przetwarza komunikat, jest aplikacją usługi MSMQ, a nie aplikacją WCF, nie istnieje niejawna Umowa serwisowa między tymi dwiema aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="3c190-123">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="3c190-124">Dlatego nie można utworzyć serwera proxy za pomocą narzędzia Svcutil. exe w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="3c190-124">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="3c190-125">Niestandardowy serwer proxy jest zasadniczo taki sam dla wszystkich aplikacji WCF, które używają `msmqIntegrationBinding` powiązania do wysyłania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3c190-125">The custom proxy is essentially the same for all WCF applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="3c190-126">W przeciwieństwie do innych serwerów proxy, nie obejmuje zakresu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="3c190-126">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="3c190-127">Jest to tylko operacja przesyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3c190-127">It is a submit message operation only.</span></span>

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

 <span data-ttu-id="3c190-128">Usługa jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="3c190-128">The service is self hosted.</span></span> <span data-ttu-id="3c190-129">W przypadku korzystania z transportu integracji usługi MSMQ użyta Kolejka musi zostać utworzona z góry.</span><span class="sxs-lookup"><span data-stu-id="3c190-129">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="3c190-130">Można to zrobić ręcznie lub przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="3c190-130">This can be done manually or through code.</span></span> <span data-ttu-id="3c190-131">W tym przykładzie usługa zawiera <xref:System.Messaging> kod służący do sprawdzania istnienia kolejki i tworzenia jej w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="3c190-131">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="3c190-132">Nazwa kolejki jest odczytywana z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3c190-132">The queue name is read from the configuration file.</span></span>

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

 <span data-ttu-id="3c190-133">Kolejka MSMQ, do której wysyłane są żądania zamówienia, jest określona w sekcji appSettings w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3c190-133">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="3c190-134">Punkty końcowe klienta i usługi są zdefiniowane w sekcji System. serviceModel w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3c190-134">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="3c190-135">Oba określają `msmqIntegrationbinding` powiązanie.</span><span class="sxs-lookup"><span data-stu-id="3c190-135">Both specify the `msmqIntegrationbinding` binding.</span></span>

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

 <span data-ttu-id="3c190-136">Aplikacja kliencka używa <xref:System.Messaging> programu w celu wysyłania trwałych i transakcyjnych komunikatów do kolejki.</span><span class="sxs-lookup"><span data-stu-id="3c190-136">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="3c190-137">Treść wiadomości zawiera zamówienie zakupu.</span><span class="sxs-lookup"><span data-stu-id="3c190-137">The message's body contains the purchase order.</span></span>

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

 <span data-ttu-id="3c190-138">Kolejka MSMQ, z której są odbierane odpowiedzi Orders, została określona w sekcji appSettings w pliku konfiguracji, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="3c190-138">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="3c190-139">Nazwa kolejki używa kropki (.) dla komputera lokalnego i separatorów ukośników odwrotnych.</span><span class="sxs-lookup"><span data-stu-id="3c190-139">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="3c190-140">Adres punktu końcowego WCF określa schemat MSMQ. formatname i używa "localhost" dla komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="3c190-140">The WCF endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="3c190-141">Poprawnie sformułowana nazwa formatu jest zgodna z nazwą MSMQ. formatname w identyfikatorze URI zgodnie z wytycznymi dotyczącymi usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3c190-141">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="3c190-142">Aplikacja kliencka zapisuje `messageID` komunikat żądania zamówienia wysyłany do usługi i czeka na odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="3c190-142">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="3c190-143">Po nadejściu odpowiedzi w kolejce klient korelacji z komunikatem o zamówieniu, który został wysłany przy `correlationID` użyciu właściwości komunikatu, `messageID` zawierającego komunikat o kolejności, który został pierwotnie Wysłany przez klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="3c190-143">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>

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

 <span data-ttu-id="3c190-144">Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="3c190-144">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="3c190-145">Można zobaczyć, że usługa odbiera komunikaty od klienta i wysyła odpowiedź z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="3c190-145">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="3c190-146">Klient wyświetla odpowiedź odebraną z usługi.</span><span class="sxs-lookup"><span data-stu-id="3c190-146">The client displays the response received from the service.</span></span> <span data-ttu-id="3c190-147">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="3c190-147">Press ENTER in each console window to shut down the service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="3c190-148">Ten przykład wymaga instalacji usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="3c190-148">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="3c190-149">Zapoznaj się z instrukcjami dotyczącymi instalacji usługi MSMQ w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="3c190-149">See the MSMQ installation instructions in the See Also section.</span></span>

### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="3c190-150">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="3c190-150">To setup, build, and run the sample</span></span>

1. <span data-ttu-id="3c190-151">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c190-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="3c190-152">Jeśli usługa jest uruchamiana po raz pierwszy, sprawdzi, czy kolejka jest obecna.</span><span class="sxs-lookup"><span data-stu-id="3c190-152">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="3c190-153">Jeśli kolejka nie istnieje, usługa utworzy ją.</span><span class="sxs-lookup"><span data-stu-id="3c190-153">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="3c190-154">Aby utworzyć kolejkę, można najpierw uruchomić tę usługę lub utworzyć ją za pośrednictwem Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3c190-154">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="3c190-155">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="3c190-155">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="3c190-156">Otwórz Menedżer serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="3c190-156">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="3c190-157">Rozwiń kartę **funkcje** .</span><span class="sxs-lookup"><span data-stu-id="3c190-157">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="3c190-158">Kliknij prawym przyciskiem myszy pozycję **prywatne kolejki komunikatów**, a następnie wybierz kolejno pozycje **Nowa**i **prywatne**.</span><span class="sxs-lookup"><span data-stu-id="3c190-158">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="3c190-159">Zaznacz pole **transakcyjne** .</span><span class="sxs-lookup"><span data-stu-id="3c190-159">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="3c190-160">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="3c190-160">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="3c190-161">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c190-161">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="3c190-162">Aby uruchomić przykład w konfiguracji pojedynczego komputera, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c190-162">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="3c190-163">Aby uruchomić przykład na wielu komputerach</span><span class="sxs-lookup"><span data-stu-id="3c190-163">To run the sample across computers</span></span>

1. <span data-ttu-id="3c190-164">Skopiuj pliki programu Service Files z folderu \service\bin\, w obszarze folder specyficzny dla języka, do komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="3c190-164">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="3c190-165">Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputera klienckiego.</span><span class="sxs-lookup"><span data-stu-id="3c190-165">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="3c190-166">W pliku Client. exe. config zmień orderQueueName, aby określić nazwę komputera usługi zamiast ".".</span><span class="sxs-lookup"><span data-stu-id="3c190-166">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="3c190-167">W pliku Service. exe. config zmień adres punktu końcowego klienta, aby określić nazwę komputera klienckiego zamiast ".".</span><span class="sxs-lookup"><span data-stu-id="3c190-167">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>

5. <span data-ttu-id="3c190-168">Na komputerze usługi Uruchom polecenie Service. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3c190-168">On the service computer, launch Service.exe from a command prompt.</span></span>

6. <span data-ttu-id="3c190-169">Na komputerze klienckim uruchom program Client. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3c190-169">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="3c190-170">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3c190-170">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3c190-171">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="3c190-171">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3c190-172">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="3c190-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3c190-173">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3c190-173">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a><span data-ttu-id="3c190-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c190-174">See also</span></span>

- [<span data-ttu-id="3c190-175">Tworzenie kolejek w programie WCF</span><span class="sxs-lookup"><span data-stu-id="3c190-175">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [<span data-ttu-id="3c190-176">Kolejkowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="3c190-176">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
