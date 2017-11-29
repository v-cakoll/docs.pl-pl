---
title: "Obsługa kolejek komunikatów programu Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
caps.latest.revision: "34"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a57e8d4f03406f975d0788d3ad085985478d59e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="c41d5-102">Obsługa kolejek komunikatów programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c41d5-102">Message Queuing to Windows Communication Foundation</span></span>
<span data-ttu-id="c41d5-103">W tym przykładzie pokazano, jak aplikacja usługi kolejkowania komunikatów (MSMQ) można wysłać wiadomości MSMQ [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="c41d5-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="c41d5-104">Usługa jest aplikacji konsoli siebie umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="c41d5-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="c41d5-105">Kontrakt usługi jest `IOrderProcessor`, który definiuje jednokierunkowe usługa, która jest odpowiednia do użycia w przypadku kolejek.</span><span class="sxs-lookup"><span data-stu-id="c41d5-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="c41d5-106">Wiadomości MSMQ nie ma nagłówka Action, więc nie jest możliwe do mapowania różnych wiadomości usługi MSMQ kontrakty operacji automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c41d5-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="c41d5-107">W związku z tym może istnieć tylko jeden kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="c41d5-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="c41d5-108">Jeśli chcesz zdefiniować więcej niż jeden kontrakt operacji usługi, aplikacja musi udostępniać informacje, które nagłówka wiadomości usługi MSMQ (na przykład etykieta lub correlationID) może służyć do określania, który kontrakt operacji wysłania.</span><span class="sxs-lookup"><span data-stu-id="c41d5-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span> <span data-ttu-id="c41d5-109">To jest przedstawiona w [niestandardowe demultipleksowanie](../../../../docs/framework/wcf/samples/custom-demux.md).</span><span class="sxs-lookup"><span data-stu-id="c41d5-109">This is demonstrated in the [Custom Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span></span>  
  
 <span data-ttu-id="c41d5-110">Wiadomości MSMQ nie zawiera informacji, które nagłówki są zamapowane na różne parametry kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="c41d5-110">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="c41d5-111">Parametr jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), który zawiera podstawowe wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c41d5-111">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="c41d5-112">Typ "T" w elemencie <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) klasa reprezentuje dane, które jest serializowany w treści wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c41d5-112">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="c41d5-113">W tym przykładzie `PurchaseOrder` jest serializowana w treści wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c41d5-113">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
 <span data-ttu-id="c41d5-114">Następujący przykładowy kod przedstawia kontraktu usługi usługę przetwarzania zamówienia.</span><span class="sxs-lookup"><span data-stu-id="c41d5-114">The following sample code shows the service contract of the order processing service.</span></span>  
  
```  
// Define a service contract.  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```  
  
 <span data-ttu-id="c41d5-115">Usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="c41d5-115">The service is self hosted.</span></span> <span data-ttu-id="c41d5-116">Podczas korzystania z usługi MSMQ z wyprzedzeniem należy utworzyć kolejkę.</span><span class="sxs-lookup"><span data-stu-id="c41d5-116">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="c41d5-117">Można to zrobić ręcznie lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="c41d5-117">This can be done manually or through code.</span></span> <span data-ttu-id="c41d5-118">W tym przykładzie usługa sprawdza istnienie kolejki i tworzy go, jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="c41d5-118">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="c41d5-119">Nazwa kolejki jest do odczytu z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c41d5-119">The queue name is read from the configuration file.</span></span>  
  
```  
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
  
 <span data-ttu-id="c41d5-120">Usługa tworzy i otwiera <xref:System.ServiceModel.ServiceHost> dla `OrderProcessorService`, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="c41d5-120">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>  
  
```  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
{  
    serviceHost.Open();  
    Console.WriteLine("The service is ready.");  
    Console.WriteLine("Press <ENTER> to terminate service.");  
    Console.ReadLine();  
    serviceHost.Close();  
}  
```  
  
 <span data-ttu-id="c41d5-121">Nazwa kolejki usługi MSMQ określono w sekcji appSettings pliku konfiguracji, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="c41d5-121">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c41d5-122">Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnika w jego ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c41d5-122">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="c41d5-123">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Adres punktu końcowego określa schematu postać msmq.formatname i korzysta z hosta lokalnego na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="c41d5-123">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="c41d5-124">Adres kolejki dla każdej nazwy formatu MSMQ adresowania wytycznych następuje schematu postać msmq.formatname.</span><span class="sxs-lookup"><span data-stu-id="c41d5-124">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 <span data-ttu-id="c41d5-125">Aplikacja kliencka aplikacji usługi MSMQ, która używa <xref:System.Messaging.MessageQueue.Send%2A> metody, aby wysłać wiadomość trwałe i transakcyjne do kolejki, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="c41d5-125">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="c41d5-126">Po uruchomieniu próbki działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="c41d5-126">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="c41d5-127">Można wyświetlić wiadomości receive usługi z klienta.</span><span class="sxs-lookup"><span data-stu-id="c41d5-127">You can see the service receive messages from the client.</span></span> <span data-ttu-id="c41d5-128">Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="c41d5-128">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="c41d5-129">Należy zauważyć, że usługi kolejkowania wiadomości jest w użyciu, klient i usługa nie być uruchomiona w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="c41d5-129">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="c41d5-130">Na przykład można uruchomić klienta, zamknij go, a następnie uruchom usługi i nadal otrzyma jego wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c41d5-130">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="c41d5-131">Aby skonfigurować, skompilować i uruchomić próbki</span><span class="sxs-lookup"><span data-stu-id="c41d5-131">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c41d5-132">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c41d5-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c41d5-133">Jeśli usługa jest uruchamiana pierwszy, sprawdza, upewnij się, że kolejka jest obecny.</span><span class="sxs-lookup"><span data-stu-id="c41d5-133">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="c41d5-134">Jeśli kolejka nie jest obecny, będzie utworzyć usługę.</span><span class="sxs-lookup"><span data-stu-id="c41d5-134">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="c41d5-135">Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub można go utworzyć za pomocą Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c41d5-135">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="c41d5-136">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="c41d5-136">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="c41d5-137">Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c41d5-137">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="c41d5-138">Rozwiń węzeł **funkcje** kartę.</span><span class="sxs-lookup"><span data-stu-id="c41d5-138">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="c41d5-139">Kliknij prawym przyciskiem myszy **kolejki wiadomości prywatne**i wybierz **nowy**, **kolejki prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="c41d5-139">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="c41d5-140">Sprawdź **transakcyjna** pole.</span><span class="sxs-lookup"><span data-stu-id="c41d5-140">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="c41d5-141">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="c41d5-141">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="c41d5-142">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c41d5-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="c41d5-143">Aby uruchomić przykładowy w konfiguracji pojedynczego komputera, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c41d5-143">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="c41d5-144">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="c41d5-144">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="c41d5-145">Skopiuj pliki programu usługi z folderu \service\bin\ w folderze danego języka na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="c41d5-145">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="c41d5-146">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="c41d5-146">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="c41d5-147">W pliku Client.exe.config zmienić orderQueueName do określenia nazwy komputera usługi zamiast ".".</span><span class="sxs-lookup"><span data-stu-id="c41d5-147">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="c41d5-148">Na komputerze, usługi uruchom Service.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c41d5-148">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="c41d5-149">Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c41d5-149">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c41d5-150">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c41d5-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c41d5-151">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c41d5-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c41d5-152">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="c41d5-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c41d5-153">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c41d5-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a><span data-ttu-id="c41d5-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c41d5-154">See Also</span></span>  
 [<span data-ttu-id="c41d5-155">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="c41d5-155">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="c41d5-156">Porady: wymiana komunikatów z punktami końcowymi WCF i aplikacji usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="c41d5-156">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="c41d5-157">Usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="c41d5-157">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=94968)
