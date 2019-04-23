---
title: Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: b4711d344a6ce08adc6e993c19f2c3d97f56e7b4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316469"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="a7749-102">Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="a7749-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="a7749-103">Niniejszy przykład pokazuje sposób wykonywania skażonych komunikatów w usłudze.</span><span class="sxs-lookup"><span data-stu-id="a7749-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="a7749-104">Ten przykład jest oparty na [dokonana transakcja powiązania usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="a7749-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="a7749-105">W tym przykładzie użyto `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="a7749-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="a7749-106">Usługa jest aplikacji konsoli Self-Hosted umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="a7749-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="a7749-107">W komunikacie w kolejce klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="a7749-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="a7749-108">Mówiąc ściślej klient wysyła komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="a7749-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="a7749-109">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="a7749-109">The service receives messages from the queue.</span></span> <span data-ttu-id="a7749-110">Usługi i klienta w związku z tym, nie musi być uruchomiona w tym samym czasie do komunikowania się za pomocą kolejki.</span><span class="sxs-lookup"><span data-stu-id="a7749-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="a7749-111">Zarządzanie skażonymi komunikatami jest komunikat, który jest regularnie odczytany z kolejki, gdy usługa odczytanie komunikatu o nie może przetworzyć komunikatu i w związku z tym kończy się transakcji, w którym komunikat został odczytany.</span><span class="sxs-lookup"><span data-stu-id="a7749-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="a7749-112">W takich przypadkach komunikat zostanie ponowiony ponownie.</span><span class="sxs-lookup"><span data-stu-id="a7749-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="a7749-113">To może teoretycznie Przejdź w nieskończoność w przypadku problemu z komunikatem.</span><span class="sxs-lookup"><span data-stu-id="a7749-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="a7749-114">Należy pamiętać, że to można tylko wówczas, gdy użycie transakcji do odczytu z kolejki i wywoływanie operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a7749-114">Note that this can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="a7749-115">Na podstawie wersji usługi MSMQ, NetMsmqBinding obsługuje ograniczone wykrywania pełne wykrywanie skażonych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a7749-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="a7749-116">Po komunikat został wykryty jako intoksykowane, a następnie mogą być obsługiwane na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="a7749-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="a7749-117">Ponownie na podstawie wersji usługi MSMQ, NetMsmqBinding obsługuje ograniczoną obsługę pełnej obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7749-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="a7749-118">W tym przykładzie pokazano ograniczone instrumenty skażone na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platformy i pełne zarządzanie skażonymi urządzeń, dostępnym na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a7749-118">This sample illustrates the limited poison facilities provided on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform and the full poison facilities provided on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="a7749-119">W obu przykładach celem jest Przenieś skażonych komunikatów z kolejki do innej kolejki, które następnie mogą być obsługiwane przez usługę, zarządzanie skażonymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="a7749-119">In both samples, the objective is move the poison message out of the queue to another queue which then can be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="a7749-120">Usługi MSMQ 4.0 Poison obsługi próbki</span><span class="sxs-lookup"><span data-stu-id="a7749-120">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="a7749-121">W [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ zapewnia funkcji skażone kolejki podrzędnej, który może służyć do przechowywania skażonych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a7749-121">In [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ provides a poison sub-queue facility that can be used to store poison messages.</span></span> <span data-ttu-id="a7749-122">W tym przykładzie przedstawiono najlepsze rozwiązanie polegające na obsłudze skażonych komunikatów za pomocą [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a7749-122">This sample demonstrates the best practice of dealing with poison messages using [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="a7749-123">Wykrywanie skażonych komunikatów w [!INCLUDE[wv](../../../../includes/wv-md.md)] jest dość złożone.</span><span class="sxs-lookup"><span data-stu-id="a7749-123">The poison message detection in [!INCLUDE[wv](../../../../includes/wv-md.md)] is quite sophisticated.</span></span> <span data-ttu-id="a7749-124">Istnieją 3 właściwości, które pomagają wykrywania.</span><span class="sxs-lookup"><span data-stu-id="a7749-124">There are 3 properties that help with detection.</span></span> <span data-ttu-id="a7749-125"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Razy danej komunikatów jest ponownie odczytany z kolejki i wysłane do aplikacji w celu przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="a7749-125">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="a7749-126">Komunikat został odczytany z kolejki ponownie, gdy zostanie ono przełączone powrót do kolejki ponieważ nie można wysłać wiadomości do aplikacji lub aplikacji powoduje wycofanie transakcji w ramach operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a7749-126">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="a7749-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> jest to liczba przypadków, gdy wiadomość zostaje przeniesiona do kolejki ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="a7749-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="a7749-128">Gdy <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> jest osiągnięty, wiadomość zostanie przeniesiona do kolejki ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="a7749-128">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="a7749-129">Właściwość <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> jest czas opóźnienia, po upływie którego wiadomość zostanie przeniesiona z kolejki ponawiania powrót do kolejki głównej.</span><span class="sxs-lookup"><span data-stu-id="a7749-129">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="a7749-130"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Zostaje zresetowana do 0.</span><span class="sxs-lookup"><span data-stu-id="a7749-130">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="a7749-131">Komunikat zostanie podjęta próba ponownie.</span><span class="sxs-lookup"><span data-stu-id="a7749-131">The message is tried again.</span></span> <span data-ttu-id="a7749-132">Jeśli wszystkie próby Przeczytaj komunikat nie powiodły się, komunikat jest oznaczony jako intoksykowane.</span><span class="sxs-lookup"><span data-stu-id="a7749-132">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="a7749-133">Gdy komunikat jest oznaczony jako intoksykowane, wiadomość została omówiona zgodnie z ustawieniami <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a7749-133">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="a7749-134">Zgodnie z możliwe wartości:</span><span class="sxs-lookup"><span data-stu-id="a7749-134">To reiterate the possible values:</span></span>

-   <span data-ttu-id="a7749-135">Odporność (ustawienie domyślne): Aby błędów odbiornik, a także hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="a7749-135">Fault (default): To fault the listener and also the service host.</span></span>

-   <span data-ttu-id="a7749-136">Upuść: Można usunąć wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7749-136">Drop: To drop the message.</span></span>

-   <span data-ttu-id="a7749-137">Przenieś: Przenoszenie wiadomości do podrzędnej kolejki Zarządzanie skażonymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="a7749-137">Move: To move the message to the poison message sub-queue.</span></span> <span data-ttu-id="a7749-138">Ta wartość jest dostępna tylko na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a7749-138">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

-   <span data-ttu-id="a7749-139">Odrzuć: Aby odrzucić wiadomości, wysyła komunikat do kolejki utraconych wiadomości przez nadawcę.</span><span class="sxs-lookup"><span data-stu-id="a7749-139">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="a7749-140">Ta wartość jest dostępna tylko na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a7749-140">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="a7749-141">Przykład demonstruje użycie `Move` dyspozycja dla Zarządzanie skażonymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="a7749-141">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="a7749-142">`Move` powoduje, że komunikat, aby przejść do skażone kolejki podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="a7749-142">`Move` causes the message to move to the poison sub-queue.</span></span>

 <span data-ttu-id="a7749-143">Umowa serwisowa jest `IOrderProcessor`, definiujący usługi jednokierunkowej, który jest odpowiedni do użytku z kolejki.</span><span class="sxs-lookup"><span data-stu-id="a7749-143">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="a7749-144">Operacja usługi wyświetla komunikat informujący, że kolejność przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="a7749-144">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="a7749-145">Aby zademonstrować funkcje zarządzanie skażonymi komunikatami `SubmitPurchaseOrder` operacji usługi występuje wyjątek, można wycofać transakcji w losowych wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="a7749-145">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to rollback the transaction on a random invocation of the service.</span></span> <span data-ttu-id="a7749-146">Powoduje to komunikatu powinna być umieszczona w kolejce.</span><span class="sxs-lookup"><span data-stu-id="a7749-146">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="a7749-147">Po pewnym czasie komunikat jest oznaczana poison.</span><span class="sxs-lookup"><span data-stu-id="a7749-147">Eventually the message is marked as poison.</span></span> <span data-ttu-id="a7749-148">Aby przenieść Zarządzanie skażonymi komunikatami skażone kolejki podrzędnej ustawieniu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a7749-148">The configuration is set to move the poison message to the poison sub-queue.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    static Random r = new Random(137);

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {

        int randomNumber = r.Next(10);

        if (randomNumber % 2 == 0)
        {
            Orders.Add(po);
            Console.WriteLine("Processing {0} ", po);
        }
        else
        {
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);
            Console.WriteLine();
            throw new Exception("Cannot process purchase order: " + po.PONumber);
        }
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted");
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Get MSMQ queue name from app settings in configuration.
        string queueName = ConfigurationManager.AppSettings["queueName"];

        // Create the transacted MSMQ queue if necessary.
        if (!System.Messaging.MessageQueue.Exists(queueName))
            System.Messaging.MessageQueue.Create(queueName, true);

        // Get the base address that is used to listen for WS-MetaDataExchange requests.
        // This is useful to generate a proxy for the client.
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        // Open the ServiceHostBase to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        if(serviceHost.State != CommunicationState.Faulted) {
            serviceHost.Close();
        }

    }
}
```

 <span data-ttu-id="a7749-149">Konfiguracja usługi zawiera następujące właściwości Zarządzanie skażonymi komunikatami: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, i `receiveErrorHandling` jak pokazano w następującym pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a7749-149">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>
  </appSettings>
  <system.serviceModel>
    <services>
      <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"
                  binding="netMsmqBinding"
                  bindingConfiguration="PoisonBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <bindings>
      <netMsmqBinding>
        <binding name="PoisonBinding"
                 receiveRetryCount="0"
                 maxRetryCycles="1"
                 retryCycleDelay="00:00:05"
                 receiveErrorHandling="Move">
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="a7749-150">Przetwarzanie komunikatów z kolejki Zarządzanie skażonymi komunikatami</span><span class="sxs-lookup"><span data-stu-id="a7749-150">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="a7749-151">Usługa Zarządzanie skażonymi komunikatami odczytuje komunikaty z kolejki końcowego skażone wiadomości i przetwarza je.</span><span class="sxs-lookup"><span data-stu-id="a7749-151">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="a7749-152">Komunikaty w kolejce Zarządzanie skażonymi komunikatami to komunikaty, które są kierowane do usługi, która przetwarza komunikat, który może być inny niż punkt końcowy usługi Zarządzanie skażonymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="a7749-152">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="a7749-153">W związku z tym gdy usługa Zarządzanie skażonymi komunikatami odczytuje komunikaty z kolejki, warstwy kanału WCF umożliwia znalezienie niezgodność punktów końcowych, a nie wysyła komunikat.</span><span class="sxs-lookup"><span data-stu-id="a7749-153">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="a7749-154">W takich przypadkach komunikat jest skierowana do Usługa przetwarzania zamówień, ale są odbierane przez usługę Zarządzanie skażonymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="a7749-154">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="a7749-155">Aby nadal odbierać wiadomości, nawet wtedy, gdy komunikat jest skierowana do innego punktu końcowego, należy można dodać `ServiceBehavior` adresy filtr, gdzie kryterium dopasowywania ma zgodny komunikat jest skierowana do dowolnego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="a7749-155">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="a7749-156">Jest to wymagane do pomyślnie przetwarzania komunikatów, które odczytany z kolejki Zarządzanie skażonymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="a7749-156">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="a7749-157">Implementacji usługi Zarządzanie skażonymi komunikatami, sama jest bardzo podobny do implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a7749-157">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="a7749-158">On implementuje ten kontrakt i przetwarza zamówienia.</span><span class="sxs-lookup"><span data-stu-id="a7749-158">It implements the contract and processes the orders.</span></span> <span data-ttu-id="a7749-159">Przykład kodu jest w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="a7749-159">The code example is as follows.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted...exiting app");
        Environment.Exit(1);
    }

    // Host the service within this EXE console application.
    public static void Main()
    {

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The poison message service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHostBase to shutdown the service.
        if(serviceHost.State != CommunicationState.Faulted)
        {
            serviceHost.Close();
        }
    }
```

 <span data-ttu-id="a7749-160">W odróżnieniu od kolejności, usługa, która odczytuje komunikaty z kolejki kolejności przetwarzania Zarządzanie skażonymi komunikatami usługi odczytuje komunikaty z poison kolejki podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="a7749-160">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison sub-queue.</span></span> <span data-ttu-id="a7749-161">Skażone kolejki jest kolejką podrzędnych kolejki głównej, nosi nazwę "poison" i jest generowany automatycznie przez usługę MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a7749-161">The poison queue is a sub-queue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="a7749-162">Aby uzyskać do niego dostęp, należy podać nazwę kolejki głównej, a następnie ";" i podrzędny nazwę kolejki, w tym przypadku — "skażone", jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="a7749-162">To access it, provide the main queue name followed by a ";" and the sub-queue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
>  <span data-ttu-id="a7749-163">W tym przykładzie dla usługi MSMQ w wersji 3.0 Nazwa kolejki skażone nie jest kolejką podrzędnych zamiast przenieśliśmy komunikat do kolejki.</span><span class="sxs-lookup"><span data-stu-id="a7749-163">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >
        </endpoint>
      </service>
    </services>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="a7749-164">Po uruchomieniu przykładu klienta, usług i zarządzanie skażonymi komunikatami usługi działań są wyświetlane w konsoli systemu windows.</span><span class="sxs-lookup"><span data-stu-id="a7749-164">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="a7749-165">Możesz zobaczyć komunikaty odbierania usługi z klienta.</span><span class="sxs-lookup"><span data-stu-id="a7749-165">You can see the service receive messages from the client.</span></span> <span data-ttu-id="a7749-166">Naciśnij klawisz ENTER w oknie konsoli, każdy zamknięcia usługi.</span><span class="sxs-lookup"><span data-stu-id="a7749-166">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="a7749-167">Usługa rozpoczyna się systemem, przetwarzania zamówień i losowo rozpoczyna się o zakończeniu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="a7749-167">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="a7749-168">Jeśli komunikat wskazuje, że został przetworzony, kolejność, można uruchomić klienta ponownie, aby wysłać kolejną wiadomość, aż zobaczysz, że usługa rzeczywiście został zakończony wiadomość.</span><span class="sxs-lookup"><span data-stu-id="a7749-168">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="a7749-169">Na podstawie skonfigurowanych ustawień skażone wiadomości zostanie podjęta próba raz do przetwarzania przed jego przeniesieniem do końcowego skażone kolejki.</span><span class="sxs-lookup"><span data-stu-id="a7749-169">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

```
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
```

 <span data-ttu-id="a7749-170">Uruchom usługę Zarządzanie skażonymi komunikatami, można odczytać uszkodzone kolejką komunikatu z kolejki skażone.</span><span class="sxs-lookup"><span data-stu-id="a7749-170">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="a7749-171">W tym przykładzie Usługa Zarządzanie skażonymi komunikatami odczytuje komunikat i przetwarza je.</span><span class="sxs-lookup"><span data-stu-id="a7749-171">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="a7749-172">Można zobaczyć, czy zamówienie zakupu, które zostały zakończone, a następnie intoksykowane jest odczytywany przez usługę Zarządzanie skażonymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="a7749-172">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

```
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a7749-173">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="a7749-173">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a7749-174">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a7749-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a7749-175">Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny.</span><span class="sxs-lookup"><span data-stu-id="a7749-175">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="a7749-176">Jeśli kolejka nie jest obecny, będzie utworzyć usługę.</span><span class="sxs-lookup"><span data-stu-id="a7749-176">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="a7749-177">Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a7749-177">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="a7749-178">Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="a7749-178">Follow these steps to create a queue in Windows 2008.</span></span>

    1.  <span data-ttu-id="a7749-179">Otwórz Menedżera serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="a7749-179">Open Server Manager in Visual Studio 2012.</span></span>

    2.  <span data-ttu-id="a7749-180">Rozwiń **funkcji** kartę.</span><span class="sxs-lookup"><span data-stu-id="a7749-180">Expand the **Features** tab.</span></span>

    3.  <span data-ttu-id="a7749-181">Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="a7749-181">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4.  <span data-ttu-id="a7749-182">Sprawdź **transakcyjna** pole.</span><span class="sxs-lookup"><span data-stu-id="a7749-182">Check the **Transactional** box.</span></span>

    5.  <span data-ttu-id="a7749-183">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="a7749-183">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="a7749-184">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a7749-184">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="a7749-185">Do uruchomienia przykładu w konfiguracji o jednym lub wielu komputera, należy zmienić nazwy kolejki, aby odzwierciedlić rzeczywiste nazwy hosta zamiast nazwy localhost i postępuj zgodnie z instrukcjami w [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a7749-185">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="a7749-186">Domyślnie `netMsmqBinding` powiązania transportu, zabezpieczeń jest włączone.</span><span class="sxs-lookup"><span data-stu-id="a7749-186">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="a7749-187">Dwie właściwości `MsmqAuthenticationMode` i `MsmqProtectionLevel`, wspólnie określić typ zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="a7749-187">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="a7749-188">Domyślnie, tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="a7749-188">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="a7749-189">Dla usługi MSMQ zapewniać uwierzytelnianie i funkcji podpisywania należy do domeny.</span><span class="sxs-lookup"><span data-stu-id="a7749-189">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="a7749-190">Po uruchomieniu tego przykładu na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "Użytkownika wewnętrznego kolejkowania certyfikatu nie istnieje".</span><span class="sxs-lookup"><span data-stu-id="a7749-190">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="a7749-191">Do uruchomienia przykładu na komputer przyłączony do grupy roboczej</span><span class="sxs-lookup"><span data-stu-id="a7749-191">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="a7749-192">Jeśli komputer nie jest częścią domeny, należy wyłączyć zabezpieczenia transportu, ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższym Przykładowa konfiguracja:</span><span class="sxs-lookup"><span data-stu-id="a7749-192">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="a7749-193">Upewnij się, że punkt końcowy jest skojarzony z powiązaniem przez ustawienie atrybutu bindingConfiguration punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a7749-193">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="a7749-194">Upewnij się, zmień konfigurację na PoisonMessageServer, serwera i klienta, przed uruchomieniem przykładu.</span><span class="sxs-lookup"><span data-stu-id="a7749-194">Ensure that you change the configuration on the PoisonMessageServer, server and the client before you run the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="a7749-195">Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia `MsmqAuthenticationMode`, `MsmqProtectionLevel`, i `Message` security `None`.</span><span class="sxs-lookup"><span data-stu-id="a7749-195">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="a7749-196">Aby Meta wymiany danych do pracy zarejestrujemy adres URL dla wiązania http.</span><span class="sxs-lookup"><span data-stu-id="a7749-196">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="a7749-197">Wymaga to, że usługa jest uruchomiona w oknie wiersza polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="a7749-197">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="a7749-198">W przeciwnym razie użytkownik uzyska wyjątek, takich jak: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span><span class="sxs-lookup"><span data-stu-id="a7749-198">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a7749-199">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a7749-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a7749-200">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a7749-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a7749-201">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="a7749-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a7749-202">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a7749-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`