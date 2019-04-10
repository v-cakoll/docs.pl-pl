---
title: Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: 1551ab407049e871a9275d148b1c84dc2791ccad
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343392"
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="bea5e-102">Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="bea5e-102">Windows Communication Foundation to Message Queuing</span></span>
<span data-ttu-id="bea5e-103">Niniejszy przykład pokazuje, jak aplikacja Windows Communication Foundation (WCF) może także wysłać komunikat do aplikacji usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="bea5e-103">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="bea5e-104">Usługa jest aplikacji konsoli Self-Hosted umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="bea5e-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="bea5e-105">Usługa i klient nie musi być uruchomiona w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="bea5e-105">The service and client do not have to be running at the same time.</span></span>

 <span data-ttu-id="bea5e-106">Ta usługa odbiera komunikaty z kolejki i przetwarza zamówienia.</span><span class="sxs-lookup"><span data-stu-id="bea5e-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="bea5e-107">Usługa tworzy kolejkę transakcyjną i konfiguruje program obsługi komunikatów odebranego komunikatu, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bea5e-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>

```csharp
static void Main(string[] args)
{
    if (!MessageQueue.Exists(
              ConfigurationManager.AppSettings["queueName"]))
       MessageQueue.Create(
           ConfigurationManager.AppSettings["queueName"], true);
        //Connect to the queue
        MessageQueue Queue = new
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);
    Queue.ReceiveCompleted +=
                 new ReceiveCompletedEventHandler(ProcessOrder);
    Queue.BeginReceive();
    Console.WriteLine("Order Service is running");
    Console.ReadLine();
}
```

 <span data-ttu-id="bea5e-108">Gdy wiadomość zostaje odebrana w kolejce, program obsługi komunikatów `ProcessOrder` zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="bea5e-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>

```csharp
public static void ProcessOrder(Object source,
    ReceiveCompletedEventArgs asyncResult)
{
    try
    {
        // Connect to the queue.
        MessageQueue Queue = (MessageQueue)source;
        // End the asynchronous receive operation.
        System.Messaging.Message msg =
                     Queue.EndReceive(asyncResult.AsyncResult);
        msg.Formatter = new System.Messaging.XmlMessageFormatter(
                                new Type[] { typeof(PurchaseOrder) });
        PurchaseOrder po = (PurchaseOrder) msg.Body;
        Random statusIndexer = new Random();
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
        Console.WriteLine("Processing {0} ", po);
        Queue.BeginReceive();
    }
    catch (System.Exception ex)
    {
        Console.WriteLine(ex.Message);
    }

}
```

 <span data-ttu-id="bea5e-109">Wyodrębnia usługi `ProcessOrder` treść komunikatu z usługi MSMQ i przetworzy to zamówienie.</span><span class="sxs-lookup"><span data-stu-id="bea5e-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>

 <span data-ttu-id="bea5e-110">Nazwa kolejki usługi MSMQ jest określony w sekcji appSettings pliku konfiguracji, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="bea5e-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
>  <span data-ttu-id="bea5e-111">Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnik odwrotny w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="bea5e-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>

 <span data-ttu-id="bea5e-112">Klient tworzy zamówienie zakupu i przesyła zamówienia zakupu w zakresie transakcji, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bea5e-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>

```csharp
// Create the purchase order
PurchaseOrder po = new PurchaseOrder();
// Fill in the details
...

OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");

MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    client.SubmitPurchaseOrder(ordermsg);
    scope.Complete();
}
Console.WriteLine("Order has been submitted:{0}", po);

//Closing the client gracefully closes the connection and cleans up resources
client.Close();
```

 <span data-ttu-id="bea5e-113">Klient używa niestandardowego klienta w prawidłowej kolejności do wysyłania wiadomości usługi MSMQ do kolejki.</span><span class="sxs-lookup"><span data-stu-id="bea5e-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="bea5e-114">Ponieważ aplikacja, która odbiera i przetwarza komunikat jest aplikacją usługi MSMQ, a nie aplikacji WCF, istnieje nie niejawne Umowa serwisowa między dwiema aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="bea5e-114">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="bea5e-115">Dlatego nie można utworzyć serwera proxy, korzystając z narzędzia Svcutil.exe w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="bea5e-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="bea5e-116">Klient niestandardowy jest zasadniczo taki sam dla wszystkich aplikacji WCF, które używają `MsmqIntegration` powiązania do wysyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bea5e-116">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="bea5e-117">W odróżnieniu od innych klientów nie obejmuje szereg operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="bea5e-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="bea5e-118">Jest tylko operacja komunikatu przesyłania.</span><span class="sxs-lookup"><span data-stu-id="bea5e-118">It is a submit message operation only.</span></span>

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor
{
    public OrderProcessorClient(){}

    public OrderProcessorClient(string configurationName)
        : base(configurationName)
    { }

    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SubmitPurchaseOrder(msg);
    }
}
```

 <span data-ttu-id="bea5e-119">Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="bea5e-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="bea5e-120">Możesz zobaczyć komunikaty odbierania usługi z klienta.</span><span class="sxs-lookup"><span data-stu-id="bea5e-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="bea5e-121">Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="bea5e-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="bea5e-122">Należy zauważyć, że ponieważ kolejkowania wiadomości jest używany, klient i usługa musi być uruchomiona w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="bea5e-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="bea5e-123">Na przykład można uruchomić klienta, zamknij go, a następnie uruchom usługi i nadal będzie ona otrzymywać jego wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bea5e-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

> [!NOTE]
>  <span data-ttu-id="bea5e-124">Ten przykładowy skrypt wymaga instalacji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="bea5e-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="bea5e-125">Zapoznaj się z instrukcjami instalacji w [usługi kolejkowania komunikatów](https://go.microsoft.com/fwlink/?LinkId=94968).</span><span class="sxs-lookup"><span data-stu-id="bea5e-125">See the installation instructions in [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968).</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="bea5e-126">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="bea5e-126">To setup, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bea5e-127">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bea5e-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="bea5e-128">Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny.</span><span class="sxs-lookup"><span data-stu-id="bea5e-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="bea5e-129">Jeśli kolejka nie jest obecny, będzie utworzyć usługę.</span><span class="sxs-lookup"><span data-stu-id="bea5e-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="bea5e-130">Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="bea5e-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="bea5e-131">Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="bea5e-131">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="bea5e-132">Otwórz Menedżera serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="bea5e-132">Open Server Manager in Visual Studio 2012.</span></span>  
  
    2.  <span data-ttu-id="bea5e-133">Rozwiń **funkcji** kartę.</span><span class="sxs-lookup"><span data-stu-id="bea5e-133">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="bea5e-134">Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="bea5e-134">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="bea5e-135">Sprawdź **transakcyjna** pole.</span><span class="sxs-lookup"><span data-stu-id="bea5e-135">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="bea5e-136">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="bea5e-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3. <span data-ttu-id="bea5e-137">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bea5e-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="bea5e-138">Do uruchomienia przykładu w konfiguracji o jednym komputerze, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bea5e-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="bea5e-139">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="bea5e-139">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="bea5e-140">Skopiuj pliki programu usługi z folderu \service\bin\ w folderze specyficzny dla języka na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="bea5e-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2. <span data-ttu-id="bea5e-141">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="bea5e-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3. <span data-ttu-id="bea5e-142">W pliku Client.exe.config, Zmień adres punktu końcowego klienta do określania nazwy komputera usługi, a nie ".".</span><span class="sxs-lookup"><span data-stu-id="bea5e-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>  
  
4. <span data-ttu-id="bea5e-143">Na komputerze usługi Service.exe należy uruchomić z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bea5e-143">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="bea5e-144">Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bea5e-144">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bea5e-145">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bea5e-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bea5e-146">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="bea5e-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bea5e-147">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="bea5e-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bea5e-148">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="bea5e-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a><span data-ttu-id="bea5e-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bea5e-149">See also</span></span>

- [<span data-ttu-id="bea5e-150">Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów</span><span class="sxs-lookup"><span data-stu-id="bea5e-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="bea5e-151">Usługa kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="bea5e-151">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
