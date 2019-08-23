---
title: Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 88ce22c9376313db26a5cbe377bdc8aaee83c118
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965558"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="3d452-102">Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="3d452-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="3d452-103">Ten przykład pokazuje, jak przeprowadzić obsługę skażonych komunikatów w usłudze.</span><span class="sxs-lookup"><span data-stu-id="3d452-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="3d452-104">Ten przykład jest oparty na przykładowym [wiązaniem usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="3d452-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="3d452-105">Ten przykład używa `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="3d452-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="3d452-106">Usługa to samodzielna aplikacja konsolowa, która umożliwia obserwowanie usługi do odebrania komunikatów znajdujących się w kolejce.</span><span class="sxs-lookup"><span data-stu-id="3d452-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="3d452-107">W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="3d452-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="3d452-108">Dokładniej, klient wysyła komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="3d452-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="3d452-109">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="3d452-109">The service receives messages from the queue.</span></span> <span data-ttu-id="3d452-110">W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="3d452-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="3d452-111">Trująca wiadomość jest komunikatem, który jest wielokrotnie odczytywany z kolejki, gdy usługa odczytująca wiadomość nie może przetworzyć komunikatu i w związku z tym kończy transakcję, w ramach której wiadomość jest odczytywana.</span><span class="sxs-lookup"><span data-stu-id="3d452-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="3d452-112">W takich przypadkach komunikat zostanie ponowiony ponownie.</span><span class="sxs-lookup"><span data-stu-id="3d452-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="3d452-113">Może to teoretycznie potrwać w razie wystąpienia problemu z komunikatem.</span><span class="sxs-lookup"><span data-stu-id="3d452-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="3d452-114">Należy zauważyć, że może się to zdarzyć tylko w przypadku używania transakcji do odczytu z kolejki i wywołania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="3d452-114">Note that this can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="3d452-115">Na podstawie wersji usługi MSMQ, usługa msmqbinding obsługuje ograniczone wykrywanie do pełnego wykrywania skażonych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3d452-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="3d452-116">Po wykryciu komunikatu jako trującego można go obsłużyć na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="3d452-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="3d452-117">Ponownie na podstawie wersji usługi MSMQ, usługa msmqbinding obsługuje ograniczoną obsługę do pełnej obsługi skażonych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3d452-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="3d452-118">Ten przykład ilustruje ograniczoną liczbę skażonych obiektów, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] które [!INCLUDE[wxp](../../../../includes/wxp-md.md)] są dostępne dla i na platformie i [!INCLUDE[wv](../../../../includes/wv-md.md)]pełnych trujących obiektów.</span><span class="sxs-lookup"><span data-stu-id="3d452-118">This sample illustrates the limited poison facilities provided on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform and the full poison facilities provided on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="3d452-119">W obu przykładach celem jest przeniesienie skażonego komunikatu z kolejki do innej kolejki, która następnie może być serwisowana przez trującą usługę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3d452-119">In both samples, the objective is move the poison message out of the queue to another queue which then can be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="3d452-120">Przykład obsługi trującej usługi MSMQ v 4.0</span><span class="sxs-lookup"><span data-stu-id="3d452-120">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="3d452-121">W [!INCLUDE[wv](../../../../includes/wv-md.md)]programie usługa MSMQ udostępnia funkcję podkolejki trującej, która może być używana do przechowywania skażonych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3d452-121">In [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ provides a poison sub-queue facility that can be used to store poison messages.</span></span> <span data-ttu-id="3d452-122">Ten przykład pokazuje najlepsze rozwiązanie dotyczące postępowania z trującymi komunikatami [!INCLUDE[wv](../../../../includes/wv-md.md)]przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="3d452-122">This sample demonstrates the best practice of dealing with poison messages using [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="3d452-123">Wykrywanie skażonych komunikatów w [!INCLUDE[wv](../../../../includes/wv-md.md)] programie jest dość zaawansowane.</span><span class="sxs-lookup"><span data-stu-id="3d452-123">The poison message detection in [!INCLUDE[wv](../../../../includes/wv-md.md)] is quite sophisticated.</span></span> <span data-ttu-id="3d452-124">Istnieją 3 właściwości, które pomagają w wykrywaniu.</span><span class="sxs-lookup"><span data-stu-id="3d452-124">There are 3 properties that help with detection.</span></span> <span data-ttu-id="3d452-125"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Jest to liczba przypadków, w których dany komunikat jest ponownie odczytywany z kolejki i wysyłany do aplikacji w celu przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="3d452-125">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="3d452-126">Komunikat jest ponownie odczytywany z kolejki, gdy zostanie przywrócony do kolejki, ponieważ nie można wysłać komunikatu do aplikacji lub aplikacja Wycofuje transakcję w operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="3d452-126">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="3d452-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>jest to liczba przenoszonych wiadomości do kolejki ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="3d452-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="3d452-128">Gdy <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> zostanie osiągnięty, wiadomość zostanie przeniesiona do kolejki ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="3d452-128">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="3d452-129">Właściwość <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> jest opóźnieniem, po którym komunikat jest przenoszony z kolejki ponownych prób z powrotem do kolejki głównej.</span><span class="sxs-lookup"><span data-stu-id="3d452-129">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="3d452-130">Wartość <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> zostanie zresetowana do 0.</span><span class="sxs-lookup"><span data-stu-id="3d452-130">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="3d452-131">Wiadomość zostanie ponowiona.</span><span class="sxs-lookup"><span data-stu-id="3d452-131">The message is tried again.</span></span> <span data-ttu-id="3d452-132">Jeśli wszystkie próby odczytu komunikatu zakończyły się niepowodzeniem, komunikat jest oznaczony jako trujący.</span><span class="sxs-lookup"><span data-stu-id="3d452-132">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="3d452-133">Gdy wiadomość zostanie oznaczona jako trująca, komunikat jest rozpatrywany zgodnie z ustawieniami <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3d452-133">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="3d452-134">Aby ponownie powtórzyć możliwe wartości:</span><span class="sxs-lookup"><span data-stu-id="3d452-134">To reiterate the possible values:</span></span>

- <span data-ttu-id="3d452-135">Błąd (domyślnie): Aby wypróbować odbiornik, a także hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="3d452-135">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="3d452-136">Listy rozwijanej , Aby usunąć komunikat.</span><span class="sxs-lookup"><span data-stu-id="3d452-136">Drop: To drop the message.</span></span>

- <span data-ttu-id="3d452-137">Przenieś Aby przenieść komunikat do podkolejki trujących komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3d452-137">Move: To move the message to the poison message sub-queue.</span></span> <span data-ttu-id="3d452-138">Ta wartość jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)]systemie.</span><span class="sxs-lookup"><span data-stu-id="3d452-138">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

- <span data-ttu-id="3d452-139">Oznacza Aby odrzucić komunikat, należy wysłać wiadomość z powrotem do kolejki utraconych wiadomości nadawcy.</span><span class="sxs-lookup"><span data-stu-id="3d452-139">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="3d452-140">Ta wartość jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)]systemie.</span><span class="sxs-lookup"><span data-stu-id="3d452-140">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="3d452-141">Przykład ilustruje użycie `Move` dyspozycji dla trującej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3d452-141">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="3d452-142">`Move`powoduje, że komunikat jest przenoszony do podkolejki trującej.</span><span class="sxs-lookup"><span data-stu-id="3d452-142">`Move` causes the message to move to the poison sub-queue.</span></span>

 <span data-ttu-id="3d452-143">Kontrakt usługi to `IOrderProcessor`, który definiuje usługę jednokierunkową, która jest odpowiednia do użycia z kolejkami.</span><span class="sxs-lookup"><span data-stu-id="3d452-143">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="3d452-144">Operacja usługi wyświetla komunikat informujący o przetwarzaniu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="3d452-144">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="3d452-145">Aby zademonstrować działanie trującej wiadomości `SubmitPurchaseOrder` , operacja usługi zgłasza wyjątek, aby wycofać transakcję w losowym wywołaniu usługi.</span><span class="sxs-lookup"><span data-stu-id="3d452-145">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to rollback the transaction on a random invocation of the service.</span></span> <span data-ttu-id="3d452-146">Powoduje to, że komunikat zostanie umieszczony w kolejce.</span><span class="sxs-lookup"><span data-stu-id="3d452-146">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="3d452-147">Ostatecznie wiadomość jest oznaczona jako trująca.</span><span class="sxs-lookup"><span data-stu-id="3d452-147">Eventually the message is marked as poison.</span></span> <span data-ttu-id="3d452-148">Konfiguracja jest ustawiona tak, aby przenieść skażony komunikat do podkolejki trującej.</span><span class="sxs-lookup"><span data-stu-id="3d452-148">The configuration is set to move the poison message to the poison sub-queue.</span></span>

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

 <span data-ttu-id="3d452-149">Konfiguracja usługi zawiera następujące `receiveRetryCount`właściwości trujących komunikatów:, `maxRetryCycles`, `retryCycleDelay`i `receiveErrorHandling` , jak pokazano w następującym pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="3d452-149">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

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

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="3d452-150">Przetwarzanie komunikatów z kolejki skażonych komunikatów</span><span class="sxs-lookup"><span data-stu-id="3d452-150">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="3d452-151">Usługa Trująca wiadomość odczytuje komunikaty z kolejki skażonych komunikatów i przetwarza je.</span><span class="sxs-lookup"><span data-stu-id="3d452-151">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="3d452-152">Wiadomości w kolejce trujących komunikatów to komunikaty, które są rozkierowane do usługi przetwarzającej komunikat, co może się różnić od punktu końcowego trującej usługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3d452-152">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="3d452-153">W związku z tym, gdy usługa Trująca wiadomość odczytuje komunikaty z kolejki, warstwa kanału WCF znajdzie niezgodność w punktach końcowych i nie wysyła komunikatu.</span><span class="sxs-lookup"><span data-stu-id="3d452-153">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="3d452-154">W takim przypadku komunikat jest kierowany do usługi przetwarzania zamówień, ale jest odbierany przez usługę trujących komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3d452-154">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="3d452-155">Aby nadal otrzymywać komunikat nawet wtedy, gdy wiadomość jest zakierowane do innego punktu końcowego, należy dodać `ServiceBehavior` do filtru, gdzie kryterium dopasowywania jest zgodne z dowolnymi punktami końcowymi, do których odnosi się komunikat.</span><span class="sxs-lookup"><span data-stu-id="3d452-155">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="3d452-156">Jest to wymagane do pomyślnego przetworzenia komunikatów odczytywanych z kolejki skażonych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3d452-156">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="3d452-157">Sama implementacja usługi trującej wiadomości jest podobna do implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="3d452-157">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="3d452-158">Implementuje kontrakt i przetwarza zamówienia.</span><span class="sxs-lookup"><span data-stu-id="3d452-158">It implements the contract and processes the orders.</span></span> <span data-ttu-id="3d452-159">Przykładowy kod jest następujący.</span><span class="sxs-lookup"><span data-stu-id="3d452-159">The code example is as follows.</span></span>

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

 <span data-ttu-id="3d452-160">W przeciwieństwie do usługi przetwarzania zamówień, która odczytuje komunikaty z kolejki kolejności, usługa Trująca wiadomość odczytuje komunikaty z podkolejki trującej.</span><span class="sxs-lookup"><span data-stu-id="3d452-160">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison sub-queue.</span></span> <span data-ttu-id="3d452-161">Kolejka Trująca jest podkolejki kolejki głównej, nosi nazwę "Trująca" i jest generowana automatycznie przez usługę MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3d452-161">The poison queue is a sub-queue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="3d452-162">Aby uzyskać do niego dostęp, podaj nazwę kolejki głównej, po której następuje ";" i nazwę kolejki podrzędnej, w tym przypadku "trujące", jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="3d452-162">To access it, provide the main queue name followed by a ";" and the sub-queue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="3d452-163">W przykładzie dla MSMQ v 3.0 nazwa kolejki trującej nie jest kolejką podrzędną, a nie kolejkę, do której przeniesiono komunikat.</span><span class="sxs-lookup"><span data-stu-id="3d452-163">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

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

 <span data-ttu-id="3d452-164">Po uruchomieniu przykładu działania usług Klient, usługa i Trująca wiadomość są wyświetlane w oknach konsoli.</span><span class="sxs-lookup"><span data-stu-id="3d452-164">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="3d452-165">Możesz zobaczyć, że usługa odbiera komunikaty od klienta.</span><span class="sxs-lookup"><span data-stu-id="3d452-165">You can see the service receive messages from the client.</span></span> <span data-ttu-id="3d452-166">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługi.</span><span class="sxs-lookup"><span data-stu-id="3d452-166">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="3d452-167">Usługa uruchamia się, przetwarza zamówienia i losowo rozpoczyna przetwarzanie.</span><span class="sxs-lookup"><span data-stu-id="3d452-167">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="3d452-168">Jeśli komunikat wskazuje, że przetworzył zamówienie, można ponownie uruchomić klienta, aby wysłać kolejny komunikat, dopóki usługa nie zakończyła się komunikatem.</span><span class="sxs-lookup"><span data-stu-id="3d452-168">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="3d452-169">W oparciu o skonfigurowane ustawienia trujące komunikat jest podejmowany raz na potrzeby przetwarzania przed przeniesieniem go do końcowej kolejki trującej.</span><span class="sxs-lookup"><span data-stu-id="3d452-169">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

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

 <span data-ttu-id="3d452-170">Uruchom usługę trującej wiadomości, aby odczytać trującą wiadomość z kolejki trującej.</span><span class="sxs-lookup"><span data-stu-id="3d452-170">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="3d452-171">W tym przykładzie usługa Trująca wiadomość odczytuje komunikat i przetwarza go.</span><span class="sxs-lookup"><span data-stu-id="3d452-171">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="3d452-172">Można zobaczyć, że zamówienie zakupu, które zostało zakończone i trujące jest odczytywane przez trującą usługę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3d452-172">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

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

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3d452-173">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="3d452-173">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3d452-174">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d452-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="3d452-175">Jeśli usługa jest uruchamiana po raz pierwszy, sprawdzi, czy kolejka jest obecna.</span><span class="sxs-lookup"><span data-stu-id="3d452-175">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="3d452-176">Jeśli kolejka nie istnieje, usługa utworzy ją.</span><span class="sxs-lookup"><span data-stu-id="3d452-176">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="3d452-177">Aby utworzyć kolejkę, można najpierw uruchomić tę usługę lub utworzyć ją za pośrednictwem Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3d452-177">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="3d452-178">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="3d452-178">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="3d452-179">Otwórz Menedżer serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="3d452-179">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="3d452-180">Rozwiń kartę **funkcje** .</span><span class="sxs-lookup"><span data-stu-id="3d452-180">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="3d452-181">Kliknij prawym przyciskiem myszy pozycję **prywatne kolejki komunikatów**, a następnie wybierz kolejno pozycje **Nowa**i **prywatne**.</span><span class="sxs-lookup"><span data-stu-id="3d452-181">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="3d452-182">Zaznacz pole **transakcyjne** .</span><span class="sxs-lookup"><span data-stu-id="3d452-182">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="3d452-183">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="3d452-183">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="3d452-184">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d452-184">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="3d452-185">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, należy zmienić nazwy kolejek, aby odzwierciedlały rzeczywistą nazwę hosta zamiast hosta lokalnego i postępować zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d452-185">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="3d452-186">Domyślnie w przypadku `netMsmqBinding` transportu powiązań jest włączone zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="3d452-186">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="3d452-187">Dwie właściwości, `MsmqAuthenticationMode` a `MsmqProtectionLevel`także określają typ zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="3d452-187">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="3d452-188">Domyślnie tryb uwierzytelniania jest ustawiony na `Windows` , a poziom ochrony jest ustawiony na. `Sign`</span><span class="sxs-lookup"><span data-stu-id="3d452-188">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="3d452-189">Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny.</span><span class="sxs-lookup"><span data-stu-id="3d452-189">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="3d452-190">Jeśli ten przykład zostanie uruchomiony na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "Wewnętrzny certyfikat usługi kolejkowania komunikatów użytkownika nie istnieje".</span><span class="sxs-lookup"><span data-stu-id="3d452-190">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="3d452-191">Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej</span><span class="sxs-lookup"><span data-stu-id="3d452-191">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="3d452-192">Jeśli komputer nie jest częścią domeny, Wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom `None` ochrony tak jak pokazano w poniższej konfiguracji przykładowej:</span><span class="sxs-lookup"><span data-stu-id="3d452-192">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="3d452-193">Upewnij się, że punkt końcowy jest skojarzony z powiązaniem, ustawiając atrybut bindingConfiguration punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3d452-193">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="3d452-194">Przed uruchomieniem przykładu należy zmienić konfigurację na PoisonMessageServer, serwerze i kliencie.</span><span class="sxs-lookup"><span data-stu-id="3d452-194">Ensure that you change the configuration on the PoisonMessageServer, server and the client before you run the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="3d452-195">`security mode` Ustawienieodpowiada`MsmqAuthenticationMode`ustawieniu ,`MsmqProtectionLevel` i`None`zabezpieczenia na. `Message` `None`</span><span class="sxs-lookup"><span data-stu-id="3d452-195">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="3d452-196">Aby wymiana metadanych działała, rejestrujemy adres URL z powiązaniem HTTP.</span><span class="sxs-lookup"><span data-stu-id="3d452-196">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="3d452-197">Wymaga to uruchomienia usługi w oknie polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="3d452-197">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="3d452-198">W przeciwnym razie zostanie wyświetlony wyjątek, taki jak `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`:.</span><span class="sxs-lookup"><span data-stu-id="3d452-198">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3d452-199">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3d452-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3d452-200">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="3d452-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3d452-201">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="3d452-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3d452-202">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3d452-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
