---
title: Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 4b662094923c85e825edcc9025a73f1a1b42cb9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144243"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="08cf6-102">Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="08cf6-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="08cf6-103">W tym przykładzie pokazano, jak wykonać trujące obsługi wiadomości w usłudze.</span><span class="sxs-lookup"><span data-stu-id="08cf6-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="08cf6-104">Ten przykład jest oparty na próbce [wiązania transacted MSMQ.](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)</span><span class="sxs-lookup"><span data-stu-id="08cf6-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="08cf6-105">W tym przykładzie użyto pliku `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="08cf6-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="08cf6-106">Usługa jest samodzielną aplikacją konsoli, która umożliwia obserwowanie usługi odbierającej wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="08cf6-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="08cf6-107">W komunikacji w kolejce klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="08cf6-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="08cf6-108">Dokładniej, klient wysyła wiadomości do kolejki.</span><span class="sxs-lookup"><span data-stu-id="08cf6-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="08cf6-109">Usługa odbiera wiadomości z kolejki.</span><span class="sxs-lookup"><span data-stu-id="08cf6-109">The service receives messages from the queue.</span></span> <span data-ttu-id="08cf6-110">W związku z tym usługi i klienta, nie muszą być uruchomione w tym samym czasie do komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="08cf6-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="08cf6-111">Trująca wiadomość to wiadomość, która jest wielokrotnie odczytywana z kolejki, gdy usługa odczytywana wiadomości nie może przetworzyć wiadomości i w związku z tym kończy transakcję, w ramach której jest odczytywana wiadomość.</span><span class="sxs-lookup"><span data-stu-id="08cf6-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="08cf6-112">W takich przypadkach wiadomość zostanie ponownie ponowiona.</span><span class="sxs-lookup"><span data-stu-id="08cf6-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="08cf6-113">Teoretycznie może to trwać wiecznie, jeśli pojawi się problem z przesłaniem.</span><span class="sxs-lookup"><span data-stu-id="08cf6-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="08cf6-114">Może to nastąpić tylko wtedy, gdy używasz transakcji do odczytu z kolejki i wywołania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="08cf6-114">This can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="08cf6-115">Na podstawie wersji usługi MSMQ NetMsmqBinding obsługuje ograniczone wykrywanie do pełnego wykrywania wiadomości poison.</span><span class="sxs-lookup"><span data-stu-id="08cf6-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="08cf6-116">Po wykryciu wiadomości jako zatrutej, można ją obsłużyć na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="08cf6-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="08cf6-117">Ponownie, na podstawie wersji usługi MSMQ, NetMsmqBinding obsługuje ograniczoną obsługę do pełnej obsługi wiadomości trujących.</span><span class="sxs-lookup"><span data-stu-id="08cf6-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="08cf6-118">W tym przykładzie przedstawiono ograniczone udogodnienia dotyczące trucizn na platformie Windows Server 2003 i Windows XP oraz pełne udogodnienia dotyczące trucizny dostępne w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="08cf6-118">This sample illustrates the limited poison facilities provided on Windows Server 2003 and Windows XP platform and the full poison facilities provided on Windows Vista.</span></span> <span data-ttu-id="08cf6-119">W obu przykładach celem jest przeniesienie trującej wiadomości z kolejki do innej kolejki.</span><span class="sxs-lookup"><span data-stu-id="08cf6-119">In both samples, the objective is to move the poison message out of the queue to another queue.</span></span> <span data-ttu-id="08cf6-120">Ta kolejka może być następnie obsługiwana przez usługę trująca wiadomość.</span><span class="sxs-lookup"><span data-stu-id="08cf6-120">That queue can then be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="08cf6-121">Msmq v4.0 Próbka obsługi trucizny</span><span class="sxs-lookup"><span data-stu-id="08cf6-121">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="08cf6-122">W systemie Windows Vista usługa MSMQ udostępnia zatrutą zajemkę, która może służyć do przechowywania wiadomości o truciznach.</span><span class="sxs-lookup"><span data-stu-id="08cf6-122">In Windows Vista, MSMQ provides a poison subqueue facility that can be used to store poison messages.</span></span> <span data-ttu-id="08cf6-123">W tym przykładzie przedstawiono najlepsze praktyki radzenia sobie z trującymi wiadomościami przy użyciu systemu Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="08cf6-123">This sample demonstrates the best practice of dealing with poison messages using Windows Vista.</span></span>

 <span data-ttu-id="08cf6-124">Wykrywanie trujących komunikatów w systemie Windows Vista jest zaawansowane.</span><span class="sxs-lookup"><span data-stu-id="08cf6-124">The poison message detection in Windows Vista is sophisticated.</span></span> <span data-ttu-id="08cf6-125">Istnieją 3 właściwości, które pomagają w wykrywaniu.</span><span class="sxs-lookup"><span data-stu-id="08cf6-125">There are 3 properties that help with detection.</span></span> <span data-ttu-id="08cf6-126">Jest <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> liczba razy dana wiadomość jest ponownie odczytywany z kolejki i wysyłane do aplikacji do przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="08cf6-126">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="08cf6-127">Komunikat jest ponownie odczytywany z kolejki, gdy jest odłożony z powrotem do kolejki, ponieważ nie można wysłać wiadomości do aplikacji lub aplikacja wycofuje transakcję w operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="08cf6-127">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="08cf6-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>to liczba przenoszona wiadomości do kolejki ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="08cf6-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="08cf6-129">Po <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> osiągnięciu wiadomości zostanie przeniesiona do kolejki ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="08cf6-129">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="08cf6-130">Właściwość <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> jest opóźnieniem czasowym, po którym wiadomość jest przenoszona z kolejki ponawiania próby z powrotem do kolejki głównej.</span><span class="sxs-lookup"><span data-stu-id="08cf6-130">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="08cf6-131">Jest <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> resetowany do 0.</span><span class="sxs-lookup"><span data-stu-id="08cf6-131">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="08cf6-132">Wiadomość zostanie ponownie wypróbowana.</span><span class="sxs-lookup"><span data-stu-id="08cf6-132">The message is tried again.</span></span> <span data-ttu-id="08cf6-133">Jeśli wszystkie próby odczytania wiadomości nie powiodły się, wiadomość jest oznaczona jako zatruta.</span><span class="sxs-lookup"><span data-stu-id="08cf6-133">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="08cf6-134">Gdy wiadomość jest oznaczona jako zatruta, wiadomość jest rozpatrywana zgodnie z ustawieniami w <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="08cf6-134">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="08cf6-135">Aby powtórzyć możliwe wartości:</span><span class="sxs-lookup"><span data-stu-id="08cf6-135">To reiterate the possible values:</span></span>

- <span data-ttu-id="08cf6-136">Błąd (domyślnie): Aby zaćterować odbiornika, a także hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="08cf6-136">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="08cf6-137">Upuść: Aby usunąć wiadomość.</span><span class="sxs-lookup"><span data-stu-id="08cf6-137">Drop: To drop the message.</span></span>

- <span data-ttu-id="08cf6-138">Przenieś: Aby przenieść wiadomość do podzasady zatrutej.</span><span class="sxs-lookup"><span data-stu-id="08cf6-138">Move: To move the message to the poison message subqueue.</span></span> <span data-ttu-id="08cf6-139">Ta wartość jest dostępna tylko w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="08cf6-139">This value is available only on Windows Vista.</span></span>

- <span data-ttu-id="08cf6-140">Odrzucić: Aby odrzucić wiadomość, wysyłając wiadomość z powrotem do kolejki utraconych wiadomości nadawcy.</span><span class="sxs-lookup"><span data-stu-id="08cf6-140">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="08cf6-141">Ta wartość jest dostępna tylko w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="08cf6-141">This value is available only on Windows Vista.</span></span>

 <span data-ttu-id="08cf6-142">Próbka pokazuje przy `Move` użyciu dyspozycji dla wiadomości trucizny.</span><span class="sxs-lookup"><span data-stu-id="08cf6-142">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="08cf6-143">`Move`powoduje, że wiadomość, aby przejść do podkiełki trucizny.</span><span class="sxs-lookup"><span data-stu-id="08cf6-143">`Move` causes the message to move to the poison subqueue.</span></span>

 <span data-ttu-id="08cf6-144">Umowa serwisowa `IOrderProcessor`jest , która definiuje usługę jednokierunkową, która nadaje się do użytku z kolejkami.</span><span class="sxs-lookup"><span data-stu-id="08cf6-144">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="08cf6-145">Operacja usługi wyświetla komunikat informujący, że przetwarza zamówienie.</span><span class="sxs-lookup"><span data-stu-id="08cf6-145">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="08cf6-146">Aby zademonstrować funkcję trująca `SubmitPurchaseOrder` wiadomość, operacja usługi zgłasza wyjątek, aby wycofać transakcję przy losowym wywołaniu usługi.</span><span class="sxs-lookup"><span data-stu-id="08cf6-146">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to roll back the transaction on a random invocation of the service.</span></span> <span data-ttu-id="08cf6-147">Powoduje to, że wiadomość ma zostać odłożona z powrotem w kolejce.</span><span class="sxs-lookup"><span data-stu-id="08cf6-147">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="08cf6-148">Ostatecznie wiadomość jest oznaczona jako trucizna.</span><span class="sxs-lookup"><span data-stu-id="08cf6-148">Eventually the message is marked as poison.</span></span> <span data-ttu-id="08cf6-149">Konfiguracja jest ustawiona na przeniesienie wiadomości o trucinie do podkiełka trucizny.</span><span class="sxs-lookup"><span data-stu-id="08cf6-149">The configuration is set to move the poison message to the poison subqueue.</span></span>

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

 <span data-ttu-id="08cf6-150">Konfiguracja usługi zawiera następujące właściwości `receiveRetryCount`trującego komunikatu: , `maxRetryCycles` `retryCycleDelay`, i `receiveErrorHandling` jak pokazano w następującym pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="08cf6-150">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

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

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="08cf6-151">Przetwarzanie wiadomości z kolejki trujących komunikatów</span><span class="sxs-lookup"><span data-stu-id="08cf6-151">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="08cf6-152">Usługa trująca wiadomość odczytuje wiadomości z kolejki ostatecznej trującej wiadomości i przetwarza je.</span><span class="sxs-lookup"><span data-stu-id="08cf6-152">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="08cf6-153">Wiadomości w kolejce trujących komunikatów są wiadomościami, które są adresowane do usługi, która przetwarza wiadomość, która może się różnić od punktu końcowego usługi trująca wiadomość.</span><span class="sxs-lookup"><span data-stu-id="08cf6-153">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="08cf6-154">W związku z tym gdy usługa trująca wiadomość odczytuje wiadomości z kolejki, warstwa kanału WCF znajduje niezgodność w punktach końcowych i nie wysyła wiadomości.</span><span class="sxs-lookup"><span data-stu-id="08cf6-154">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="08cf6-155">W takim przypadku wiadomość jest adresowany do usługi przetwarzania zamówień, ale jest odbierany przez usługę trująca wiadomość.</span><span class="sxs-lookup"><span data-stu-id="08cf6-155">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="08cf6-156">Aby nadal odbierać wiadomość, nawet jeśli wiadomość jest adresowany do `ServiceBehavior` innego punktu końcowego, musimy dodać do filtru adresy, gdzie kryterium dopasowania jest zgodne z dowolnym punktem końcowym usługi, do którego jest zaadresowany.</span><span class="sxs-lookup"><span data-stu-id="08cf6-156">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="08cf6-157">Jest to wymagane do pomyślnego przetwarzania wiadomości odczytywanych z kolejki trujących komunikatów.</span><span class="sxs-lookup"><span data-stu-id="08cf6-157">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="08cf6-158">Sama implementacja usługi trująca wiadomość jest bardzo podobna do implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="08cf6-158">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="08cf6-159">Realizuje kontrakt i przetwarza zamówienia.</span><span class="sxs-lookup"><span data-stu-id="08cf6-159">It implements the contract and processes the orders.</span></span> <span data-ttu-id="08cf6-160">Przykład kodu jest następujący.</span><span class="sxs-lookup"><span data-stu-id="08cf6-160">The code example is as follows.</span></span>

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

 <span data-ttu-id="08cf6-161">W przeciwieństwie do usługi przetwarzania zamówień, która odczytuje wiadomości z kolejki zamówień, usługa trująca wiadomość odczytuje wiadomości z podokazji trucizny.</span><span class="sxs-lookup"><span data-stu-id="08cf6-161">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison subqueue.</span></span> <span data-ttu-id="08cf6-162">Kolejka trucizny jest podk.</span><span class="sxs-lookup"><span data-stu-id="08cf6-162">The poison queue is a subqueue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="08cf6-163">Aby uzyskać do niego dostęp, podaj nazwę kolejki głównej, po której następuje ";" i nazwa podoka, w tym przypadku -"poison", jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="08cf6-163">To access it, provide the main queue name followed by a ";" and the subqueue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="08cf6-164">W przykładzie dla usługi MSMQ w wersji 3.0 nazwa kolejki trucicieli nie jest kolejką podrzędną, a kolejką, do których przenieśliśmy wiadomość.</span><span class="sxs-lookup"><span data-stu-id="08cf6-164">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

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

 <span data-ttu-id="08cf6-165">Po uruchomieniu przykładu działania usługi klienta, usługi i trucić komunikatów są wyświetlane w oknach konsoli.</span><span class="sxs-lookup"><span data-stu-id="08cf6-165">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="08cf6-166">Możesz zobaczyć, że usługa odbiera wiadomości od klienta.</span><span class="sxs-lookup"><span data-stu-id="08cf6-166">You can see the service receive messages from the client.</span></span> <span data-ttu-id="08cf6-167">Naciśnij klawisz ENTER w każdym oknie konsoli, aby wyłączyć usługi.</span><span class="sxs-lookup"><span data-stu-id="08cf6-167">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="08cf6-168">Usługa rozpoczyna działanie, przetwarzanie zamówień i losowo rozpoczyna przetwarzanie.</span><span class="sxs-lookup"><span data-stu-id="08cf6-168">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="08cf6-169">Jeśli komunikat wskazuje, że przetworzył zamówienie, można uruchomić klienta ponownie, aby wysłać inną wiadomość, dopóki nie zobaczysz, że usługa faktycznie zakończyła wiadomość.</span><span class="sxs-lookup"><span data-stu-id="08cf6-169">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="08cf6-170">Na podstawie skonfigurowanych ustawień trucizny, komunikat jest próbowany raz do przetworzenia przed przeniesieniem go do ostatecznej kolejki trucizny.</span><span class="sxs-lookup"><span data-stu-id="08cf6-170">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

```console
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

 <span data-ttu-id="08cf6-171">Uruchom usługę trująca wiadomość, aby odczytać zatrutą wiadomość z kolejki trucizny.</span><span class="sxs-lookup"><span data-stu-id="08cf6-171">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="08cf6-172">W tym przykładzie usługa trująca wiadomość odczytuje komunikat i przetwarza ją.</span><span class="sxs-lookup"><span data-stu-id="08cf6-172">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="08cf6-173">Można zobaczyć, że zamówienie zakupu, które zostało zakończone i zatrute jest odczytywane przez usługę trująca wiadomość.</span><span class="sxs-lookup"><span data-stu-id="08cf6-173">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

```console
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

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="08cf6-174">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="08cf6-174">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="08cf6-175">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08cf6-175">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="08cf6-176">Jeśli usługa jest uruchamiana jako pierwsza, sprawdzi, czy kolejka jest obecna.</span><span class="sxs-lookup"><span data-stu-id="08cf6-176">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="08cf6-177">Jeśli kolejka nie jest obecny, usługa utworzy jeden.</span><span class="sxs-lookup"><span data-stu-id="08cf6-177">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="08cf6-178">Usługę można uruchomić najpierw, aby utworzyć kolejkę, lub utworzyć ją za pośrednictwem Menedżera kolejek usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="08cf6-178">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="08cf6-179">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="08cf6-179">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="08cf6-180">Otwórz Menedżera serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="08cf6-180">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="08cf6-181">Rozwiń kartę **Funkcje.**</span><span class="sxs-lookup"><span data-stu-id="08cf6-181">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="08cf6-182">Kliknij prawym przyciskiem myszy **pozycję Kolejki wiadomości prywatnych**i wybierz polecenie **Nowa**, **Kolejka prywatna**.</span><span class="sxs-lookup"><span data-stu-id="08cf6-182">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="08cf6-183">Zaznacz pole **Transakcyjne.**</span><span class="sxs-lookup"><span data-stu-id="08cf6-183">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="08cf6-184">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="08cf6-184">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="08cf6-185">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08cf6-185">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="08cf6-186">Aby uruchomić przykład w konfiguracji jedno- lub międzykomputerowej, zmień nazwy kolejki, aby odzwierciedlić rzeczywistą nazwa hosta zamiast localhost i postępuj zgodnie z instrukcjami w [uruchomionych przykładach fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08cf6-186">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="08cf6-187">Domyślnie z `netMsmqBinding` transportu powiązania zabezpieczeń jest włączona.</span><span class="sxs-lookup"><span data-stu-id="08cf6-187">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="08cf6-188">Dwie właściwości `MsmqAuthenticationMode` i `MsmqProtectionLevel`, razem określić typ zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="08cf6-188">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="08cf6-189">Domyślnie tryb uwierzytelniania jest `Windows` ustawiony, a poziom `Sign`ochrony jest ustawiony na .</span><span class="sxs-lookup"><span data-stu-id="08cf6-189">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="08cf6-190">Aby usługa MSMQ udostępniała funkcję uwierzytelniania i podpisywania, musi ona być częścią domeny.</span><span class="sxs-lookup"><span data-stu-id="08cf6-190">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="08cf6-191">Po uruchomieniu tego przykładu na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "Certyfikat kolejkowania wiadomości wewnętrznych użytkownika nie istnieje".</span><span class="sxs-lookup"><span data-stu-id="08cf6-191">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="08cf6-192">Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej</span><span class="sxs-lookup"><span data-stu-id="08cf6-192">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="08cf6-193">Jeśli komputer nie należy do domeny, wyłącz zabezpieczenia transportu, ustawiając `None` tryb uwierzytelniania i poziom ochrony na pokazano w poniższej przykładowej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="08cf6-193">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="08cf6-194">Upewnij się, że punkt końcowy jest skojarzony z powiązaniem, ustawiając atrybut powiązania punktu końcowegoKonfiguracja.</span><span class="sxs-lookup"><span data-stu-id="08cf6-194">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="08cf6-195">Przed uruchomieniem przykładu upewnij się, że konfiguracja na serwerze PoisonMessageServer, serwerze i kliencie została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="08cf6-195">Ensure that you change the configuration on the PoisonMessageServer, server, and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="08cf6-196">Ustawienie `security mode` `None` jest równoważne `MsmqAuthenticationMode` `MsmqProtectionLevel`z `Message` ustawieniem `None`i zabezpieczeniami .</span><span class="sxs-lookup"><span data-stu-id="08cf6-196">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="08cf6-197">Aby meta data exchange działała, rejestrujemy adres URL za pomocą powiązania http.</span><span class="sxs-lookup"><span data-stu-id="08cf6-197">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="08cf6-198">Wymaga to, aby usługa została uruchomiony w oknie polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="08cf6-198">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="08cf6-199">W przeciwnym razie zostanie zgłoszony `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`wyjątek, taki jak: .</span><span class="sxs-lookup"><span data-stu-id="08cf6-199">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="08cf6-200">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="08cf6-200">The samples may already be installed on your computer.</span></span> <span data-ttu-id="08cf6-201">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="08cf6-201">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="08cf6-202">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="08cf6-202">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="08cf6-203">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="08cf6-203">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
