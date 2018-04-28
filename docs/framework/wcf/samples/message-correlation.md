---
title: Korelacja komunikatów
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 52dd8d66a4a28b515ebfaee88c4383889839fff0
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="message-correlation"></a><span data-ttu-id="3a3e1-102">Korelacja komunikatów</span><span class="sxs-lookup"><span data-stu-id="3a3e1-102">Message Correlation</span></span>
<span data-ttu-id="3a3e1-103">W tym przykładzie pokazano, jak aplikacja usługi kolejkowania komunikatów (MSMQ) można wysłać wiadomości MSMQ [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi i jak można skorelować wiadomości między nadawcą i odbiorcą aplikacji w przypadku żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="3a3e1-104">W przykładzie użyto powiązania msmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-104">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="3a3e1-105">Usługa jest w tym przypadku aplikacji konsoli siebie pozwala sprawdzić, czy usługa, która odbiera wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-105">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="3a3e1-106">K</span><span class="sxs-lookup"><span data-stu-id="3a3e1-106">k</span></span>  
  
 <span data-ttu-id="3a3e1-107">Usługa przetwarza wiadomości odebrane od nadawcy i wysyła odpowiedź do nadawcy.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-107">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="3a3e1-108">Nadawca skorelowany odpowiedzi otrzymany na żądanie, które on wysłany.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-108">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="3a3e1-109">`MessageID` i `CorrelationID` właściwości wiadomości są używane do korelacji komunikatów żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-109">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>  
  
 <span data-ttu-id="3a3e1-110">`IOrderProcessor` Operacji usługi jednokierunkowej, które jest odpowiednie do użycia z usługi kolejkowania definiuje kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-110">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="3a3e1-111">Wiadomości MSMQ nie ma nagłówka Action, więc nie jest możliwe do mapowania różnych wiadomości usługi MSMQ kontrakty operacji automatycznie.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-111">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="3a3e1-112">W związku z tym może istnieć tylko jeden kontrakt operacji w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-112">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="3a3e1-113">Jeśli chcesz zdefiniować umów więcej operacji w usłudze, aplikacja musi udostępniać informacje określające, które nagłówka w usłudze MSMQ wiadomości (na przykład etykietę lub correlationID) może służyć do określania, który kontrakt operacji wysłania.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-113">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span> <span data-ttu-id="3a3e1-114">To jest przedstawiona w [niestandardowe demultipleksowanie](../../../../docs/framework/wcf/samples/custom-demux.md).</span><span class="sxs-lookup"><span data-stu-id="3a3e1-114">This is demonstrated in the [Custom Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span></span>  
  
 <span data-ttu-id="3a3e1-115">Wiadomości MSMQ nie zawiera również informacje, które nagłówki są zamapowane na różne parametry kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-115">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="3a3e1-116">W związku z tym może istnieć tylko jeden parametr w kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-116">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="3a3e1-117">Parametr jest typu <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` zawierający podstawowe wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-117">The parameter is of type <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` which contains the underlying MSMQ message.</span></span> <span data-ttu-id="3a3e1-118">Typ "T" w elemencie `MsmqMessage<T>` klasa reprezentuje dane, które jest serializowany w treści wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-118">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="3a3e1-119">W tym przykładzie `PurchaseOrder` jest serializowana w treści wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-119">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```

 <span data-ttu-id="3a3e1-120">Operacja usługi przetwarza zamówienia zakupu i wyświetla zawartość zamówienia zakupu i jego stan w oknie konsoli usługi.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-120">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="3a3e1-121"><xref:System.ServiceModel.OperationBehaviorAttribute> Konfiguruje operacji można zarejestrować w transakcji z kolejki i oznaczania ukończenia transakcji po powrocie z operacji.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-121">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="3a3e1-122">`PurchaseOrder` Zawiera szczegóły zlecenia, które muszą zostać przetworzone przez usługę.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-122">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>  

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

 <span data-ttu-id="3a3e1-123">Usługa używa niestandardowego klienta `OrderResponseClient` do wysłania tej wiadomości usługi MSMQ do kolejki.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-123">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="3a3e1-124">Ponieważ aplikacja, która odbiera i przetwarza komunikat jest aplikacja usługi MSMQ, a nie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji jest nie kontraktu usługi niejawne między dwiema aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-124">Because the application that receives and processes the message is an MSMQ application and not a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="3a3e1-125">Dlatego nie można utworzyć serwer proxy, korzystając z narzędzia Svcutil.exe w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-125">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>  
  
 <span data-ttu-id="3a3e1-126">Niestandardowego serwera proxy jest zasadniczo taki sam dla wszystkich [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji, które używają `msmqIntegrationBinding` powiązania do wysyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-126">The custom proxy is essentially the same for all [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="3a3e1-127">W przeciwieństwie do innych serwerów proxy nie obejmuje szereg operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-127">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="3a3e1-128">Jest tylko operacja komunikat przesyłania.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-128">It is a submit message operation only.</span></span>  

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

 <span data-ttu-id="3a3e1-129">Usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-129">The service is self hosted.</span></span> <span data-ttu-id="3a3e1-130">Przy użyciu transport integracji usługi MSMQ, kolejki używane musi zostać utworzona z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-130">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="3a3e1-131">Można to zrobić ręcznie lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-131">This can be done manually or through code.</span></span> <span data-ttu-id="3a3e1-132">W tym przykładzie Usługa zawiera <xref:System.Messaging> kod, aby sprawdzić obecność kolejki i w razie potrzeby utwórz.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-132">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="3a3e1-133">Nazwa kolejki jest do odczytu z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-133">The queue name is read from the configuration file.</span></span>  

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
  
 <span data-ttu-id="3a3e1-134">Kolejki usługi MSMQ, do którego są wysyłane żądania kolejności jest określona w sekcji appSettings pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-134">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="3a3e1-135">Punkty końcowe klienta i usługi są zdefiniowane w sekcji system.serviceModel pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-135">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="3a3e1-136">Określ zarówno `msmqIntegrationbinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-136">Both specify the `msmqIntegrationbinding` binding.</span></span>  
  
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
  
 <span data-ttu-id="3a3e1-137">Aplikacja kliencka używa <xref:System.Messaging> Aby wysłać wiadomość trwałe i transakcyjne do kolejki.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-137">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="3a3e1-138">Treść wiadomości zawiera zamówienia zakupu.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-138">The message's body contains the purchase order.</span></span>  

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

 <span data-ttu-id="3a3e1-139">Kolejki usługi MSMQ, z którego są odbierane odpowiedzi w kolejności jest określona w sekcji appSettings pliku konfiguracji, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-139">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a3e1-140">Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnika w jego ścieżki.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-140">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="3a3e1-141">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Adres punktu końcowego określa schematu postać msmq.formatname i używane "localhost" na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-141">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="3a3e1-142">Nazwy formatu właściwie uformowanego następuje msmq.formatname w identyfikatorze URI zgodnie z wytycznymi usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-142">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>  
  
```xml  
<appSettings>  
    <add key=" orderResponseQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 <span data-ttu-id="3a3e1-143">Zapisuje aplikacji klienta `messageID` komunikatu żądania kolejności, który wysyła do usługi i czeka na odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-143">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="3a3e1-144">Po odebraniu odpowiedzi w kolejce klienta są powiązane z go z komunikatem kolejności wysyłane, przy użyciu `correlationID` właściwości wiadomości, która zawiera `messageID` zlecenia komunikat, który klient wysłany do usługi.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-144">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>  

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

 <span data-ttu-id="3a3e1-145">Po uruchomieniu próbki działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-145">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="3a3e1-146">Można wyświetlić wiadomości receive usługi z klienta i wysyła odpowiedź z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-146">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="3a3e1-147">Klient jest wyświetlany odpowiedzi otrzymał od usługi.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-147">The client displays the response received from the service.</span></span> <span data-ttu-id="3a3e1-148">Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a3e1-149">W tym przykładzie wymaga zainstalowania programu usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="3a3e1-149">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="3a3e1-150">Zapoznaj się z instrukcjami instalacji usługi MSMQ w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-150">See the MSMQ installation instructions in the See Also section.</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="3a3e1-151">Aby skonfigurować, skompilować i uruchomić próbki</span><span class="sxs-lookup"><span data-stu-id="3a3e1-151">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3a3e1-152">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a3e1-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="3a3e1-153">Jeśli usługa jest uruchamiana pierwszy, sprawdza, upewnij się, że kolejka jest obecny.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-153">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="3a3e1-154">Jeśli kolejka nie jest obecny, będzie utworzyć usługę.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-154">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="3a3e1-155">Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub można go utworzyć za pomocą Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-155">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="3a3e1-156">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-156">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="3a3e1-157">Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a3e1-157">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="3a3e1-158">Rozwiń węzeł **funkcje** kartę.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-158">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="3a3e1-159">Kliknij prawym przyciskiem myszy **kolejki wiadomości prywatne**i wybierz **nowy**, **kolejki prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-159">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="3a3e1-160">Sprawdź **transakcyjna** pole.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-160">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="3a3e1-161">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-161">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="3a3e1-162">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a3e1-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="3a3e1-163">Aby uruchomić przykładowy w konfiguracji pojedynczego komputera, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a3e1-163">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="3a3e1-164">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="3a3e1-164">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="3a3e1-165">Skopiuj pliki programu usługi z folderu \service\bin\ w folderze danego języka na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-165">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="3a3e1-166">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-166">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="3a3e1-167">W pliku Client.exe.config zmienić orderQueueName do określenia nazwy komputera usługi zamiast ".".</span><span class="sxs-lookup"><span data-stu-id="3a3e1-167">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="3a3e1-168">W pliku Service.exe.config zmień adres punktu końcowego klienta, aby określić nazwę komputera klienta, a nie ".".</span><span class="sxs-lookup"><span data-stu-id="3a3e1-168">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>  
  
5.  <span data-ttu-id="3a3e1-169">Na komputerze, usługi uruchom Service.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-169">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
6.  <span data-ttu-id="3a3e1-170">Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-170">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3a3e1-171">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-171">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3a3e1-172">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="3a3e1-172">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3a3e1-173">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3a3e1-174">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3a3e1-174">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a><span data-ttu-id="3a3e1-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a3e1-175">See Also</span></span>  
 [<span data-ttu-id="3a3e1-176">Tworzenie kolejek w programie WCF</span><span class="sxs-lookup"><span data-stu-id="3a3e1-176">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="3a3e1-177">Usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="3a3e1-177">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=94968)
