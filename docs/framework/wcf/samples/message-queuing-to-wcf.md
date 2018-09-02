---
title: Obsługa kolejek komunikatów programu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 983fd2ef7338e24c67e3556849e73c2feaf97a60
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423377"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="f8bad-102">Obsługa kolejek komunikatów programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f8bad-102">Message Queuing to Windows Communication Foundation</span></span>
<span data-ttu-id="f8bad-103">Niniejszy przykład pokazuje, jak aplikacja usługi kolejkowania komunikatów (MSMQ) można wysłać wiadomości usługi MSMQ do usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f8bad-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="f8bad-104">Usługa jest aplikacji konsoli Self-Hosted umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f8bad-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="f8bad-105">Umowa serwisowa jest `IOrderProcessor`, definiujący usługi jednokierunkowej, który jest odpowiedni do użytku z kolejki.</span><span class="sxs-lookup"><span data-stu-id="f8bad-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="f8bad-106">Wiadomości usługi MSMQ nie ma nagłówek akcji, więc nie jest możliwe do mapowania różnych wiadomości usługi MSMQ kontrakty operacji automatycznie.</span><span class="sxs-lookup"><span data-stu-id="f8bad-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="f8bad-107">W związku z tym może istnieć tylko jedno operacji kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f8bad-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="f8bad-108">Jeśli chcesz zdefiniować więcej niż jeden kontrakt operacji dla usługi, aplikacja musi udostępniać informacje, które nagłówka wiadomości usługi MSMQ (na przykład etykiety lub correlationID) może służyć do określania, który kontrakt operacji wysłania.</span><span class="sxs-lookup"><span data-stu-id="f8bad-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span> <span data-ttu-id="f8bad-109">Jest to zaprezentowane w [niestandardowe demultipleksowanie](../../../../docs/framework/wcf/samples/custom-demux.md).</span><span class="sxs-lookup"><span data-stu-id="f8bad-109">This is demonstrated in the [Custom Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span></span>  
  
 <span data-ttu-id="f8bad-110">Wiadomości usługi MSMQ nie zawiera informacje, które nagłówki są zamapowane na różne parametry kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="f8bad-110">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="f8bad-111">Parametr jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), który zawiera podstawowe wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f8bad-111">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="f8bad-112">Typ "T" w elemencie <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) klasa reprezentuje dane, które jest serializowana w treści wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f8bad-112">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="f8bad-113">W tym przykładzie `PurchaseOrder` typ jest serializowana w treści wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f8bad-113">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
 <span data-ttu-id="f8bad-114">Następujący przykładowy kod przedstawia kontrakt usługi Usługa przetwarzania zamówień.</span><span class="sxs-lookup"><span data-stu-id="f8bad-114">The following sample code shows the service contract of the order processing service.</span></span>  

```csharp
// Define a service contract.  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```

 <span data-ttu-id="f8bad-115">Usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="f8bad-115">The service is self hosted.</span></span> <span data-ttu-id="f8bad-116">Podczas korzystania z usługi MSMQ kolejki używanej musi zostać utworzona wcześniej.</span><span class="sxs-lookup"><span data-stu-id="f8bad-116">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="f8bad-117">Można to zrobić ręcznie lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="f8bad-117">This can be done manually or through code.</span></span> <span data-ttu-id="f8bad-118">W tym przykładzie usługa sprawdza istnienie kolejki i utworzy go, jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="f8bad-118">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="f8bad-119">Nazwa kolejki jest do odczytu z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f8bad-119">The queue name is read from the configuration file.</span></span>  

```csharp
public static void Main()  
{  
    // Get the MSMQ queue name from the application settings in   
    // configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
    // Create the MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
    …  
}  
```

 <span data-ttu-id="f8bad-120">Usługa tworzy i otwiera <xref:System.ServiceModel.ServiceHost> dla `OrderProcessorService`, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f8bad-120">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>  

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
{  
    serviceHost.Open();  
    Console.WriteLine("The service is ready.");  
    Console.WriteLine("Press <ENTER> to terminate service.");  
    Console.ReadLine();  
    serviceHost.Close();  
}  
```

 <span data-ttu-id="f8bad-121">Nazwa kolejki usługi MSMQ jest określony w sekcji appSettings pliku konfiguracji, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="f8bad-121">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8bad-122">Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnik odwrotny w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="f8bad-122">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="f8bad-123">Adres punktu końcowego WCF Określa schemat msmq.formatname i używane host_lokalny na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="f8bad-123">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="f8bad-124">Adres kolejki dla każdej nazwy formatu MSMQ adresowania wytycznych jest zgodna schematu msmq.formatname.</span><span class="sxs-lookup"><span data-stu-id="f8bad-124">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 <span data-ttu-id="f8bad-125">Aplikacja kliencka jest aplikacja usługi MSMQ, która używa <xref:System.Messaging.MessageQueue.Send%2A> metodę, aby wysłać wiadomość trwały i transakcyjnych w kolejce, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f8bad-125">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>  

```csharp
//Connect to the queue.  
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);  
  
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
  
// Submit the purchase order.  
Message msg = new Message();  
msg.Body = po;  
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
  
    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);  
    // Complete the transaction.  
    scope.Complete();  
  
}  
Console.WriteLine("Placed the order:{0}", po);  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```

 <span data-ttu-id="f8bad-126">Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="f8bad-126">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="f8bad-127">Możesz zobaczyć komunikaty odbierania usługi z klienta.</span><span class="sxs-lookup"><span data-stu-id="f8bad-127">You can see the service receive messages from the client.</span></span> <span data-ttu-id="f8bad-128">Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="f8bad-128">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="f8bad-129">Należy zauważyć, że ponieważ kolejkowania wiadomości jest używany, klient i usługa musi być uruchomiona w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="f8bad-129">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="f8bad-130">Na przykład można uruchomić klienta, zamknij go, a następnie uruchom usługi i nadal będzie ona otrzymywać jego wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f8bad-130">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="f8bad-131">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="f8bad-131">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f8bad-132">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8bad-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f8bad-133">Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny.</span><span class="sxs-lookup"><span data-stu-id="f8bad-133">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="f8bad-134">Jeśli kolejka nie jest obecny, będzie utworzyć usługę.</span><span class="sxs-lookup"><span data-stu-id="f8bad-134">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="f8bad-135">Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f8bad-135">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="f8bad-136">Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="f8bad-136">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="f8bad-137">Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8bad-137">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="f8bad-138">Rozwiń **funkcji** kartę.</span><span class="sxs-lookup"><span data-stu-id="f8bad-138">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="f8bad-139">Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="f8bad-139">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="f8bad-140">Sprawdź **transakcyjna** pole.</span><span class="sxs-lookup"><span data-stu-id="f8bad-140">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="f8bad-141">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="f8bad-141">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="f8bad-142">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8bad-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="f8bad-143">Do uruchomienia przykładu w konfiguracji o jednym komputerze, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8bad-143">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="f8bad-144">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="f8bad-144">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="f8bad-145">Skopiuj pliki programu usługi z folderu \service\bin\ w folderze specyficzny dla języka na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="f8bad-145">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="f8bad-146">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="f8bad-146">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="f8bad-147">W pliku Client.exe.config zmienić orderQueueName do określenia nazwy komputera usługi zamiast ".".</span><span class="sxs-lookup"><span data-stu-id="f8bad-147">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="f8bad-148">Na komputerze usługi Service.exe należy uruchomić z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="f8bad-148">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="f8bad-149">Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="f8bad-149">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f8bad-150">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f8bad-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f8bad-151">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f8bad-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f8bad-152">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="f8bad-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f8bad-153">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f8bad-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a><span data-ttu-id="f8bad-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8bad-154">See Also</span></span>  
 [<span data-ttu-id="f8bad-155">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="f8bad-155">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="f8bad-156">Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów</span><span class="sxs-lookup"><span data-stu-id="f8bad-156">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="f8bad-157">Usługa kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="f8bad-157">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
