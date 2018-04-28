---
title: Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
caps.latest.revision: 32
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2ea59c7f1ef2ac6f22500a13eb9bb4456149b7c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="49d69-102">Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="49d69-102">Windows Communication Foundation to Message Queuing</span></span>
<span data-ttu-id="49d69-103">W przykładzie pokazano, jak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji można wysłać wiadomości do aplikacji usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="49d69-103">This sample demonstrates how a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="49d69-104">Usługa jest aplikacji konsoli siebie umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="49d69-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="49d69-105">Usługa i klient ma być uruchomiona w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="49d69-105">The service and client do not have to be running at the same time.</span></span>  
  
 <span data-ttu-id="49d69-106">Usługa odbiera komunikaty z kolejki i przetwarza zamówienia.</span><span class="sxs-lookup"><span data-stu-id="49d69-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="49d69-107">Usługa tworzy kolejkę transakcyjną i ustawia program obsługi komunikatów Odebrano komunikat, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="49d69-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>  

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

 <span data-ttu-id="49d69-108">Po odebraniu wiadomości w kolejce, program obsługi komunikatów `ProcessOrder` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="49d69-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>  

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

 <span data-ttu-id="49d69-109">Wyodrębnia usługi `ProcessOrder` z usługi MSMQ treść komunikatu i przetwarza kolejności.</span><span class="sxs-lookup"><span data-stu-id="49d69-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>  
  
 <span data-ttu-id="49d69-110">Nazwa kolejki usługi MSMQ określono w sekcji appSettings pliku konfiguracji, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="49d69-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="49d69-111">Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnika w jego ścieżki.</span><span class="sxs-lookup"><span data-stu-id="49d69-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>  
  
 <span data-ttu-id="49d69-112">Klient tworzy zamówienia zakupu i przesyła zamówienia zakupu w zakresie transakcji, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="49d69-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>  

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

 <span data-ttu-id="49d69-113">Klient używa niestandardowego klienta w kolejności do wysłania tej wiadomości usługi MSMQ do kolejki.</span><span class="sxs-lookup"><span data-stu-id="49d69-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="49d69-114">Ponieważ aplikacja, która odbiera i przetwarza komunikat jest aplikacja usługi MSMQ, a nie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji jest nie kontraktu usługi niejawne między dwiema aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="49d69-114">Because the application that receives and processes the message is an MSMQ application and not a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="49d69-115">Dlatego nie można utworzyć serwer proxy, korzystając z narzędzia Svcutil.exe w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="49d69-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>  
  
 <span data-ttu-id="49d69-116">Niestandardowe klienta jest zasadniczo taki sam dla wszystkich [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji, które używają `MsmqIntegration` powiązania do wysyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="49d69-116">The custom client is essentially the same for all [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="49d69-117">W odróżnieniu od innych klientów nie obejmuje szereg operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="49d69-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="49d69-118">Jest tylko operacja komunikat przesyłania.</span><span class="sxs-lookup"><span data-stu-id="49d69-118">It is a submit message operation only.</span></span>  

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

 <span data-ttu-id="49d69-119">Po uruchomieniu próbki działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="49d69-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="49d69-120">Można wyświetlić wiadomości receive usługi z klienta.</span><span class="sxs-lookup"><span data-stu-id="49d69-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="49d69-121">Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="49d69-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="49d69-122">Należy zauważyć, że usługi kolejkowania wiadomości jest w użyciu, klient i usługa nie być uruchomiona w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="49d69-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="49d69-123">Na przykład można uruchomić klienta, zamknij go, a następnie uruchom usługi i nadal otrzyma jego wiadomości.</span><span class="sxs-lookup"><span data-stu-id="49d69-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49d69-124">W tym przykładzie wymaga instalacji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="49d69-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="49d69-125">Zapoznaj się z instrukcjami instalacji w [usługi kolejkowania komunikatów](http://go.microsoft.com/fwlink/?LinkId=94968).</span><span class="sxs-lookup"><span data-stu-id="49d69-125">See the installation instructions in [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=94968).</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="49d69-126">Aby skonfigurować, skompilować i uruchomić próbki</span><span class="sxs-lookup"><span data-stu-id="49d69-126">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="49d69-127">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="49d69-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="49d69-128">Jeśli usługa jest uruchamiana pierwszy, sprawdza, upewnij się, że kolejka jest obecny.</span><span class="sxs-lookup"><span data-stu-id="49d69-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="49d69-129">Jeśli kolejka nie jest obecny, będzie utworzyć usługę.</span><span class="sxs-lookup"><span data-stu-id="49d69-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="49d69-130">Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub można go utworzyć za pomocą Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="49d69-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="49d69-131">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="49d69-131">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="49d69-132">Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49d69-132">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="49d69-133">Rozwiń węzeł **funkcje** kartę.</span><span class="sxs-lookup"><span data-stu-id="49d69-133">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="49d69-134">Kliknij prawym przyciskiem myszy **kolejki wiadomości prywatne**i wybierz **nowy**, **kolejki prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="49d69-134">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="49d69-135">Sprawdź **transakcyjna** pole.</span><span class="sxs-lookup"><span data-stu-id="49d69-135">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="49d69-136">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="49d69-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="49d69-137">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="49d69-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="49d69-138">Aby uruchomić przykładowy w konfiguracji pojedynczego komputera, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="49d69-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="49d69-139">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="49d69-139">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="49d69-140">Skopiuj pliki programu usługi z folderu \service\bin\ w folderze danego języka na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="49d69-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="49d69-141">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="49d69-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="49d69-142">W pliku Client.exe.config zmień adres punktu końcowego klienta do określenia nazwy komputera usługi zamiast ".".</span><span class="sxs-lookup"><span data-stu-id="49d69-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="49d69-143">Na komputerze, usługi uruchom Service.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="49d69-143">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="49d69-144">Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="49d69-144">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="49d69-145">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="49d69-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="49d69-146">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="49d69-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="49d69-147">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="49d69-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="49d69-148">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="49d69-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a><span data-ttu-id="49d69-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49d69-149">See Also</span></span>  
 [<span data-ttu-id="49d69-150">Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów</span><span class="sxs-lookup"><span data-stu-id="49d69-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="49d69-151">Usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="49d69-151">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=94968)
