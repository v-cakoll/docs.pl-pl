---
title: Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: 2e37a6efac6b979645b2dbb338b64f698b3b97e0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344610"
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="c7f09-102">Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="c7f09-102">Windows Communication Foundation to Message Queuing</span></span>

<span data-ttu-id="c7f09-103">Ten przykład pokazuje, jak aplikacja Windows Communication Foundation (WCF) może wysłać komunikat do aplikacji usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="c7f09-103">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="c7f09-104">Usługa to samodzielna aplikacja konsolowa, która umożliwia obserwowanie usługi do odebrania komunikatów znajdujących się w kolejce.</span><span class="sxs-lookup"><span data-stu-id="c7f09-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="c7f09-105">Usługa i klient nie muszą być uruchomione w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="c7f09-105">The service and client do not have to be running at the same time.</span></span>

 <span data-ttu-id="c7f09-106">Usługa odbiera komunikaty z kolejki i przetwarza je.</span><span class="sxs-lookup"><span data-stu-id="c7f09-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="c7f09-107">Usługa tworzy kolejkę transakcyjną i konfiguruje komunikat z obsługą wiadomości, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c7f09-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="c7f09-108">Po odebraniu komunikatu w kolejce zostanie wywołana procedura obsługi komunikatów `ProcessOrder`.</span><span class="sxs-lookup"><span data-stu-id="c7f09-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>

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

 <span data-ttu-id="c7f09-109">Usługa wyodrębnia `ProcessOrder` z treści wiadomości MSMQ i przetwarza kolejność.</span><span class="sxs-lookup"><span data-stu-id="c7f09-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>

 <span data-ttu-id="c7f09-110">Nazwa kolejki MSMQ jest określona w sekcji appSettings w pliku konfiguracji, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="c7f09-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="c7f09-111">Nazwa kolejki używa kropki (.) dla komputera lokalnego i separatorów ukośników odwrotnych.</span><span class="sxs-lookup"><span data-stu-id="c7f09-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>

 <span data-ttu-id="c7f09-112">Klient tworzy zamówienie zakupu i przesyła zamówienie zakupu w zakresie transakcji, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c7f09-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="c7f09-113">Klient używa niestandardowego klienta w usłudze w celu wysłania komunikatu MSMQ do kolejki.</span><span class="sxs-lookup"><span data-stu-id="c7f09-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="c7f09-114">Ponieważ aplikacja, która odbiera i przetwarza komunikat, jest aplikacją usługi MSMQ, a nie aplikacją WCF, nie istnieje niejawna Umowa serwisowa między tymi dwiema aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="c7f09-114">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="c7f09-115">Dlatego nie można utworzyć serwera proxy za pomocą narzędzia Svcutil. exe w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="c7f09-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="c7f09-116">Klient niestandardowy jest zasadniczo taki sam dla wszystkich aplikacji WCF, które używają powiązania `MsmqIntegration` do wysyłania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c7f09-116">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="c7f09-117">W przeciwieństwie do innych klientów, nie obejmuje ona zakresu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="c7f09-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="c7f09-118">Jest to tylko operacja przesyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c7f09-118">It is a submit message operation only.</span></span>

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

 <span data-ttu-id="c7f09-119">Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="c7f09-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="c7f09-120">Możesz zobaczyć, że usługa odbiera komunikaty od klienta.</span><span class="sxs-lookup"><span data-stu-id="c7f09-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="c7f09-121">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="c7f09-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="c7f09-122">Należy pamiętać, że ponieważ usługa kolejkowania jest w użyciu, klient i usługi nie muszą działać w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="c7f09-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="c7f09-123">Na przykład można uruchomić klienta programu, zamknąć go, a następnie uruchomić usługę i nadal otrzymywać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c7f09-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

> [!NOTE]
> <span data-ttu-id="c7f09-124">Ten przykład wymaga instalacji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c7f09-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="c7f09-125">Zapoznaj się z instrukcjami dotyczącymi instalacji w usłudze [kolejkowania komunikatów](https://go.microsoft.com/fwlink/?LinkId=94968).</span><span class="sxs-lookup"><span data-stu-id="c7f09-125">See the installation instructions in [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968).</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="c7f09-126">Konfigurowanie, kompilowanie i uruchamianie przykładu</span><span class="sxs-lookup"><span data-stu-id="c7f09-126">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="c7f09-127">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7f09-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="c7f09-128">Jeśli usługa jest uruchamiana po raz pierwszy, sprawdzi, czy kolejka jest obecna.</span><span class="sxs-lookup"><span data-stu-id="c7f09-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="c7f09-129">Jeśli kolejka nie istnieje, usługa utworzy ją.</span><span class="sxs-lookup"><span data-stu-id="c7f09-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="c7f09-130">Aby utworzyć kolejkę, można najpierw uruchomić tę usługę lub utworzyć ją za pośrednictwem Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c7f09-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="c7f09-131">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="c7f09-131">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="c7f09-132">Otwórz Menedżer serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="c7f09-132">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="c7f09-133">Rozwiń kartę **funkcje** .</span><span class="sxs-lookup"><span data-stu-id="c7f09-133">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="c7f09-134">Kliknij prawym przyciskiem myszy pozycję **prywatne kolejki komunikatów**, a następnie wybierz pozycję **Nowa** > **Kolejka prywatna**.</span><span class="sxs-lookup"><span data-stu-id="c7f09-134">Right-click **Private Message Queues**, and then select **New** > **Private Queue**.</span></span>

    4. <span data-ttu-id="c7f09-135">Zaznacz pole **transakcyjne** .</span><span class="sxs-lookup"><span data-stu-id="c7f09-135">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="c7f09-136">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="c7f09-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="c7f09-137">Aby skompilować C# lub Visual Basic wersję rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie próbek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7f09-137">To build the C# or Visual Basic edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="c7f09-138">Aby uruchomić przykład w konfiguracji pojedynczego komputera, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7f09-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="c7f09-139">Uruchamianie przykładu między komputerami</span><span class="sxs-lookup"><span data-stu-id="c7f09-139">Run the sample across computers</span></span>

1. <span data-ttu-id="c7f09-140">Skopiuj pliki programu Service Files z folderu \service\bin\, w obszarze folder specyficzny dla języka, do komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="c7f09-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="c7f09-141">Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputera klienckiego.</span><span class="sxs-lookup"><span data-stu-id="c7f09-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="c7f09-142">W pliku Client. exe. config zmień adres punktu końcowego klienta, aby określić nazwę komputera usługi zamiast ".".</span><span class="sxs-lookup"><span data-stu-id="c7f09-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="c7f09-143">Na komputerze usługi Uruchom polecenie Service. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c7f09-143">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="c7f09-144">Na komputerze klienckim uruchom program Client. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c7f09-144">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7f09-145">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c7f09-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c7f09-146">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="c7f09-146">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c7f09-147">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7f09-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7f09-148">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c7f09-148">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`

## <a name="see-also"></a><span data-ttu-id="c7f09-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7f09-149">See also</span></span>

- [<span data-ttu-id="c7f09-150">Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów</span><span class="sxs-lookup"><span data-stu-id="c7f09-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="c7f09-151">Kolejkowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="c7f09-151">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
