---
title: Obsługa kolejek komunikatów programu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 541ea23e6748242db57661ceda8e1fedecb66884
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747120"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="35271-102">Obsługa kolejek komunikatów programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="35271-102">Message Queuing to Windows Communication Foundation</span></span>

<span data-ttu-id="35271-103">Ten przykład pokazuje, jak aplikacja usługi kolejkowania komunikatów (MSMQ) może wysyłać komunikat usługi MSMQ do usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="35271-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="35271-104">Usługa to samodzielna aplikacja konsolowa, która umożliwia obserwowanie usługi do odebrania komunikatów znajdujących się w kolejce.</span><span class="sxs-lookup"><span data-stu-id="35271-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="35271-105">Kontrakt usługi jest `IOrderProcessor`, który definiuje usługę jednokierunkową, która jest odpowiednia do użycia z kolejkami.</span><span class="sxs-lookup"><span data-stu-id="35271-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="35271-106">Komunikat usługi MSMQ nie zawiera nagłówka akcji, więc nie jest możliwe automatyczne Mapowanie komunikatów usługi MSMQ do kontraktów operacji.</span><span class="sxs-lookup"><span data-stu-id="35271-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="35271-107">W związku z tym może istnieć tylko jeden kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="35271-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="35271-108">Jeśli chcesz zdefiniować więcej niż jeden kontrakt operacji dla usługi, aplikacja musi podać informacje o nagłówku wiadomości MSMQ (na przykład etykieta lub identyfikator korelacji), aby określić, którą umowę operacji wysłać.</span><span class="sxs-lookup"><span data-stu-id="35271-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="35271-109">Komunikat MSMQ nie zawiera informacji o tym, które nagłówki są mapowane na różne parametry kontraktu operacji.</span><span class="sxs-lookup"><span data-stu-id="35271-109">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="35271-110">Parametr jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), który zawiera źródłowy komunikat MSMQ.</span><span class="sxs-lookup"><span data-stu-id="35271-110">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="35271-111">Typ "T" w klasie <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) reprezentuje dane, które są serializowane w treści wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="35271-111">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="35271-112">W tym przykładzie typ `PurchaseOrder` jest serializowany do treści wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="35271-112">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

 <span data-ttu-id="35271-113">Następujący przykładowy kod przedstawia kontrakt usługi dla usługi przetwarzania zamówień.</span><span class="sxs-lookup"><span data-stu-id="35271-113">The following sample code shows the service contract of the order processing service.</span></span>

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

 <span data-ttu-id="35271-114">Usługa jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="35271-114">The service is self hosted.</span></span> <span data-ttu-id="35271-115">W przypadku korzystania z usługi MSMQ, użyta Kolejka musi być utworzona z góry.</span><span class="sxs-lookup"><span data-stu-id="35271-115">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="35271-116">Można to zrobić ręcznie lub przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="35271-116">This can be done manually or through code.</span></span> <span data-ttu-id="35271-117">W tym przykładzie usługa sprawdza obecność kolejki i tworzy ją, jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="35271-117">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="35271-118">Nazwa kolejki jest odczytywana z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="35271-118">The queue name is read from the configuration file.</span></span>

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

 <span data-ttu-id="35271-119">Usługa tworzy i otwiera <xref:System.ServiceModel.ServiceHost> dla `OrderProcessorService`, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="35271-119">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="35271-120">Nazwa kolejki MSMQ jest określona w sekcji appSettings w pliku konfiguracji, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="35271-120">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="35271-121">Nazwa kolejki używa kropki (.) dla komputera lokalnego i separatorów ukośników odwrotnych.</span><span class="sxs-lookup"><span data-stu-id="35271-121">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="35271-122">Adres punktu końcowego programu WCF określa schemat MSMQ. formatname, a na komputerze lokalnym używa hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="35271-122">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="35271-123">Adres kolejki dla każdej nazwy formatu usługi MSMQ wskazówki dotyczące adresowania są zgodne ze schematem MSMQ. formatname.</span><span class="sxs-lookup"><span data-stu-id="35271-123">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="35271-124">Aplikacja kliencka jest aplikacją usługi MSMQ, która używa metody <xref:System.Messaging.MessageQueue.Send%2A> do wysyłania trwałych i transakcyjnych komunikatów do kolejki, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="35271-124">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="35271-125">Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="35271-125">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="35271-126">Możesz zobaczyć, że usługa odbiera komunikaty od klienta.</span><span class="sxs-lookup"><span data-stu-id="35271-126">You can see the service receive messages from the client.</span></span> <span data-ttu-id="35271-127">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="35271-127">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="35271-128">Należy pamiętać, że ponieważ usługa kolejkowania jest w użyciu, klient i usługi nie muszą działać w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="35271-128">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="35271-129">Na przykład można uruchomić klienta programu, zamknąć go, a następnie uruchomić usługę i nadal otrzymywać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="35271-129">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="35271-130">Konfigurowanie, kompilowanie i uruchamianie przykładu</span><span class="sxs-lookup"><span data-stu-id="35271-130">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="35271-131">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35271-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="35271-132">Jeśli usługa jest uruchamiana po raz pierwszy, sprawdzi, czy kolejka jest obecna.</span><span class="sxs-lookup"><span data-stu-id="35271-132">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="35271-133">Jeśli kolejka nie istnieje, usługa utworzy ją.</span><span class="sxs-lookup"><span data-stu-id="35271-133">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="35271-134">Aby utworzyć kolejkę, można najpierw uruchomić tę usługę lub utworzyć ją za pośrednictwem Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="35271-134">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="35271-135">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="35271-135">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="35271-136">Otwórz Menedżer serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="35271-136">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="35271-137">Rozwiń kartę **funkcje** .</span><span class="sxs-lookup"><span data-stu-id="35271-137">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="35271-138">Kliknij prawym przyciskiem myszy pozycję **prywatne kolejki komunikatów**, a następnie wybierz kolejno pozycje **Nowa**i **prywatne**.</span><span class="sxs-lookup"><span data-stu-id="35271-138">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="35271-139">Zaznacz pole **transakcyjne** .</span><span class="sxs-lookup"><span data-stu-id="35271-139">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="35271-140">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="35271-140">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="35271-141">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35271-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="35271-142">Aby uruchomić przykład w konfiguracji pojedynczego komputera, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35271-142">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="35271-143">Uruchamianie przykładu między komputerami</span><span class="sxs-lookup"><span data-stu-id="35271-143">Run the sample across computers</span></span>

1. <span data-ttu-id="35271-144">Skopiuj pliki programu Service Files z folderu \service\bin\, w obszarze folder specyficzny dla języka, do komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="35271-144">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="35271-145">Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputera klienckiego.</span><span class="sxs-lookup"><span data-stu-id="35271-145">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="35271-146">W pliku Client. exe. config zmień orderQueueName, aby określić nazwę komputera usługi zamiast ".".</span><span class="sxs-lookup"><span data-stu-id="35271-146">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="35271-147">Na komputerze usługi Uruchom polecenie Service. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="35271-147">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="35271-148">Na komputerze klienckim uruchom program Client. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="35271-148">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35271-149">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="35271-149">The samples may already be installed on your computer.</span></span> <span data-ttu-id="35271-150">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="35271-150">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="35271-151">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="35271-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="35271-152">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="35271-152">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`

## <a name="see-also"></a><span data-ttu-id="35271-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35271-153">See also</span></span>

- [<span data-ttu-id="35271-154">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="35271-154">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="35271-155">Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów</span><span class="sxs-lookup"><span data-stu-id="35271-155">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- <span data-ttu-id="35271-156">[Kolejkowanie komunikatów](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="35271-156">[Message Queuing](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
