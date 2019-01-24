---
title: Obsługa kolejek komunikatów programu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: fa8bb6036b38456066922c0c2991a4893a22c117
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676656"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="9d296-102">Obsługa kolejek komunikatów programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9d296-102">Message Queuing to Windows Communication Foundation</span></span>
<span data-ttu-id="9d296-103">Niniejszy przykład pokazuje, jak aplikacja usługi kolejkowania komunikatów (MSMQ) można wysłać wiadomości usługi MSMQ do usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9d296-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="9d296-104">Usługa jest aplikacji konsoli Self-Hosted umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="9d296-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="9d296-105">Umowa serwisowa jest `IOrderProcessor`, definiujący usługi jednokierunkowej, który jest odpowiedni do użytku z kolejki.</span><span class="sxs-lookup"><span data-stu-id="9d296-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="9d296-106">Wiadomości usługi MSMQ nie ma nagłówek akcji, więc nie jest możliwe do mapowania różnych wiadomości usługi MSMQ kontrakty operacji automatycznie.</span><span class="sxs-lookup"><span data-stu-id="9d296-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="9d296-107">W związku z tym może istnieć tylko jedno operacji kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9d296-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="9d296-108">Jeśli chcesz zdefiniować więcej niż jeden kontrakt operacji dla usługi, aplikacja musi udostępniać informacje, które nagłówka wiadomości usługi MSMQ (na przykład etykiety lub correlationID) może służyć do określania, który kontrakt operacji wysłania.</span><span class="sxs-lookup"><span data-stu-id="9d296-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span>
  
 <span data-ttu-id="9d296-109">Wiadomości usługi MSMQ nie zawiera informacje, które nagłówki są zamapowane na różne parametry kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="9d296-109">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="9d296-110">Parametr jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), który zawiera podstawowe wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9d296-110">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="9d296-111">Typ "T" w elemencie <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) klasa reprezentuje dane, które jest serializowana w treści wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9d296-111">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="9d296-112">W tym przykładzie `PurchaseOrder` typ jest serializowana w treści wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9d296-112">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
 <span data-ttu-id="9d296-113">Następujący przykładowy kod przedstawia kontrakt usługi Usługa przetwarzania zamówień.</span><span class="sxs-lookup"><span data-stu-id="9d296-113">The following sample code shows the service contract of the order processing service.</span></span>  

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

 <span data-ttu-id="9d296-114">Usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="9d296-114">The service is self hosted.</span></span> <span data-ttu-id="9d296-115">Podczas korzystania z usługi MSMQ kolejki używanej musi zostać utworzona wcześniej.</span><span class="sxs-lookup"><span data-stu-id="9d296-115">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="9d296-116">Można to zrobić ręcznie lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="9d296-116">This can be done manually or through code.</span></span> <span data-ttu-id="9d296-117">W tym przykładzie usługa sprawdza istnienie kolejki i utworzy go, jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="9d296-117">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="9d296-118">Nazwa kolejki jest do odczytu z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9d296-118">The queue name is read from the configuration file.</span></span>

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

 <span data-ttu-id="9d296-119">Usługa tworzy i otwiera <xref:System.ServiceModel.ServiceHost> dla `OrderProcessorService`, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9d296-119">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="9d296-120">Nazwa kolejki usługi MSMQ jest określony w sekcji appSettings pliku konfiguracji, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="9d296-120">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
>  <span data-ttu-id="9d296-121">Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnik odwrotny w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="9d296-121">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="9d296-122">Adres punktu końcowego WCF Określa schemat msmq.formatname i używane host_lokalny na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="9d296-122">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="9d296-123">Adres kolejki dla każdej nazwy formatu MSMQ adresowania wytycznych jest zgodna schematu msmq.formatname.</span><span class="sxs-lookup"><span data-stu-id="9d296-123">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="9d296-124">Aplikacja kliencka jest aplikacja usługi MSMQ, która używa <xref:System.Messaging.MessageQueue.Send%2A> metodę, aby wysłać wiadomość trwały i transakcyjnych w kolejce, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9d296-124">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="9d296-125">Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="9d296-125">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="9d296-126">Możesz zobaczyć komunikaty odbierania usługi z klienta.</span><span class="sxs-lookup"><span data-stu-id="9d296-126">You can see the service receive messages from the client.</span></span> <span data-ttu-id="9d296-127">Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="9d296-127">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="9d296-128">Należy zauważyć, że ponieważ kolejkowania wiadomości jest używany, klient i usługa musi być uruchomiona w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="9d296-128">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="9d296-129">Na przykład można uruchomić klienta, zamknij go, a następnie uruchom usługi i nadal będzie ona otrzymywać jego wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9d296-129">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="9d296-130">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="9d296-130">To setup, build, and run the sample</span></span>

1.  <span data-ttu-id="9d296-131">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9d296-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="9d296-132">Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny.</span><span class="sxs-lookup"><span data-stu-id="9d296-132">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="9d296-133">Jeśli kolejka nie jest obecny, będzie utworzyć usługę.</span><span class="sxs-lookup"><span data-stu-id="9d296-133">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="9d296-134">Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9d296-134">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="9d296-135">Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="9d296-135">Follow these steps to create a queue in Windows 2008.</span></span>

    1.  <span data-ttu-id="9d296-136">Otwórz Menedżera serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="9d296-136">Open Server Manager in Visual Studio 2012.</span></span>

    2.  <span data-ttu-id="9d296-137">Rozwiń **funkcji** kartę.</span><span class="sxs-lookup"><span data-stu-id="9d296-137">Expand the **Features** tab.</span></span>

    3.  <span data-ttu-id="9d296-138">Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="9d296-138">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4.  <span data-ttu-id="9d296-139">Sprawdź **transakcyjna** pole.</span><span class="sxs-lookup"><span data-stu-id="9d296-139">Check the **Transactional** box.</span></span>

    5.  <span data-ttu-id="9d296-140">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="9d296-140">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3.  <span data-ttu-id="9d296-141">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9d296-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4.  <span data-ttu-id="9d296-142">Do uruchomienia przykładu w konfiguracji o jednym komputerze, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9d296-142">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="9d296-143">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="9d296-143">To run the sample across computers</span></span>

1.  <span data-ttu-id="9d296-144">Skopiuj pliki programu usługi z folderu \service\bin\ w folderze specyficzny dla języka na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="9d296-144">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2.  <span data-ttu-id="9d296-145">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="9d296-145">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3.  <span data-ttu-id="9d296-146">W pliku Client.exe.config zmienić orderQueueName do określenia nazwy komputera usługi zamiast ".".</span><span class="sxs-lookup"><span data-stu-id="9d296-146">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4.  <span data-ttu-id="9d296-147">Na komputerze usługi Service.exe należy uruchomić z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9d296-147">On the service computer, launch Service.exe from a command prompt.</span></span>

5.  <span data-ttu-id="9d296-148">Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9d296-148">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="9d296-149">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9d296-149">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9d296-150">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="9d296-150">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9d296-151">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="9d296-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9d296-152">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9d296-152">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a><span data-ttu-id="9d296-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d296-153">See also</span></span>
- [<span data-ttu-id="9d296-154">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="9d296-154">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="9d296-155">Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów</span><span class="sxs-lookup"><span data-stu-id="9d296-155">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="9d296-156">Usługa kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="9d296-156">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
