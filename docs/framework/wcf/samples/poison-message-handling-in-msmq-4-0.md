---
title: Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 54e69d60aabb3793ef4a8d800dd0e6238c28f231
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602443"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="a1334-102">Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="a1334-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="a1334-103">Ten przykład pokazuje, jak przeprowadzić obsługę skażonych komunikatów w usłudze.</span><span class="sxs-lookup"><span data-stu-id="a1334-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="a1334-104">Ten przykład jest oparty na przykładowym [wiązaniem usługi MSMQ](transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="a1334-104">This sample is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="a1334-105">Ten przykład używa `netMsmqBinding` .</span><span class="sxs-lookup"><span data-stu-id="a1334-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="a1334-106">Usługa to samodzielna aplikacja konsolowa, która umożliwia obserwowanie usługi do odebrania komunikatów znajdujących się w kolejce.</span><span class="sxs-lookup"><span data-stu-id="a1334-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="a1334-107">W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="a1334-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="a1334-108">Dokładniej, klient wysyła komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="a1334-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="a1334-109">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="a1334-109">The service receives messages from the queue.</span></span> <span data-ttu-id="a1334-110">W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="a1334-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="a1334-111">Trująca wiadomość jest komunikatem, który jest wielokrotnie odczytywany z kolejki, gdy usługa odczytująca wiadomość nie może przetworzyć komunikatu i w związku z tym kończy transakcję, w ramach której wiadomość jest odczytywana.</span><span class="sxs-lookup"><span data-stu-id="a1334-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="a1334-112">W takich przypadkach komunikat zostanie ponowiony ponownie.</span><span class="sxs-lookup"><span data-stu-id="a1334-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="a1334-113">Może to teoretycznie potrwać w razie wystąpienia problemu z komunikatem.</span><span class="sxs-lookup"><span data-stu-id="a1334-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="a1334-114">Ta sytuacja może wystąpić tylko w przypadku używania transakcji do odczytu z kolejki i wywołania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a1334-114">This can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="a1334-115">Na podstawie wersji usługi MSMQ, usługa msmqbinding obsługuje ograniczone wykrywanie do pełnego wykrywania skażonych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a1334-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="a1334-116">Po wykryciu komunikatu jako trującego można go obsłużyć na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="a1334-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="a1334-117">Ponownie na podstawie wersji usługi MSMQ, usługa msmqbinding obsługuje ograniczoną obsługę do pełnej obsługi skażonych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a1334-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="a1334-118">Ten przykład ilustruje ograniczoną liczbę trujących obiektów zapewnianych na platformie Windows Server 2003 i Windows XP oraz w pełnych obiektach trujących zapewnianych w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="a1334-118">This sample illustrates the limited poison facilities provided on Windows Server 2003 and Windows XP platform and the full poison facilities provided on Windows Vista.</span></span> <span data-ttu-id="a1334-119">W obu przykładach celem jest przeniesienie skażonego komunikatu z kolejki do innej kolejki.</span><span class="sxs-lookup"><span data-stu-id="a1334-119">In both samples, the objective is to move the poison message out of the queue to another queue.</span></span> <span data-ttu-id="a1334-120">Kolejka może być następnie serwisowana przez trującą usługę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a1334-120">That queue can then be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="a1334-121">Przykład obsługi trującej usługi MSMQ v 4.0</span><span class="sxs-lookup"><span data-stu-id="a1334-121">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="a1334-122">W systemie Windows Vista usługa MSMQ udostępnia funkcję podkolejki trującej, która może być używana do przechowywania skażonych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a1334-122">In Windows Vista, MSMQ provides a poison subqueue facility that can be used to store poison messages.</span></span> <span data-ttu-id="a1334-123">Ten przykład ilustruje najlepsze rozwiązanie w zakresie postępowania z skażonymi komunikatami przy użyciu systemu Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="a1334-123">This sample demonstrates the best practice of dealing with poison messages using Windows Vista.</span></span>

 <span data-ttu-id="a1334-124">Wykrywanie skażonych komunikatów w systemie Windows Vista jest zaawansowana.</span><span class="sxs-lookup"><span data-stu-id="a1334-124">The poison message detection in Windows Vista is sophisticated.</span></span> <span data-ttu-id="a1334-125">Istnieją 3 właściwości, które pomagają w wykrywaniu.</span><span class="sxs-lookup"><span data-stu-id="a1334-125">There are 3 properties that help with detection.</span></span> <span data-ttu-id="a1334-126"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A>Jest to liczba przypadków, w których dany komunikat jest ponownie odczytywany z kolejki i wysyłany do aplikacji w celu przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="a1334-126">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="a1334-127">Komunikat jest ponownie odczytywany z kolejki, gdy zostanie przywrócony do kolejki, ponieważ nie można wysłać komunikatu do aplikacji lub aplikacja Wycofuje transakcję w operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a1334-127">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="a1334-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>jest to liczba przenoszonych wiadomości do kolejki ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="a1334-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="a1334-129">Gdy <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> zostanie osiągnięty, wiadomość zostanie przeniesiona do kolejki ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="a1334-129">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="a1334-130">Właściwość <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> jest opóźnieniem, po którym komunikat jest przenoszony z kolejki ponownych prób z powrotem do kolejki głównej.</span><span class="sxs-lookup"><span data-stu-id="a1334-130">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="a1334-131">Wartość <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> zostanie zresetowana do 0.</span><span class="sxs-lookup"><span data-stu-id="a1334-131">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="a1334-132">Wiadomość zostanie ponowiona.</span><span class="sxs-lookup"><span data-stu-id="a1334-132">The message is tried again.</span></span> <span data-ttu-id="a1334-133">Jeśli wszystkie próby odczytu komunikatu zakończyły się niepowodzeniem, komunikat jest oznaczony jako trujący.</span><span class="sxs-lookup"><span data-stu-id="a1334-133">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="a1334-134">Gdy wiadomość zostanie oznaczona jako trująca, komunikat jest rozpatrywany zgodnie z ustawieniami <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a1334-134">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="a1334-135">Aby ponownie powtórzyć możliwe wartości:</span><span class="sxs-lookup"><span data-stu-id="a1334-135">To reiterate the possible values:</span></span>

- <span data-ttu-id="a1334-136">Błąd (domyślnie): w celu wypróbowania odbiornika, a także hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="a1334-136">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="a1334-137">Upuść:, aby usunąć komunikat.</span><span class="sxs-lookup"><span data-stu-id="a1334-137">Drop: To drop the message.</span></span>

- <span data-ttu-id="a1334-138">Przenieś: Aby przenieść komunikat do podkolejki trującej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a1334-138">Move: To move the message to the poison message subqueue.</span></span> <span data-ttu-id="a1334-139">Ta wartość jest dostępna tylko w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="a1334-139">This value is available only on Windows Vista.</span></span>

- <span data-ttu-id="a1334-140">Odrzuć: aby odrzucić komunikat, Wyślij komunikat z powrotem do kolejki utraconych wiadomości nadawcy.</span><span class="sxs-lookup"><span data-stu-id="a1334-140">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="a1334-141">Ta wartość jest dostępna tylko w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="a1334-141">This value is available only on Windows Vista.</span></span>

 <span data-ttu-id="a1334-142">Przykład ilustruje użycie `Move` dyspozycji dla trującej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a1334-142">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="a1334-143">`Move`powoduje, że komunikat jest przenoszony do podrzędnej kolejki trującej.</span><span class="sxs-lookup"><span data-stu-id="a1334-143">`Move` causes the message to move to the poison subqueue.</span></span>

 <span data-ttu-id="a1334-144">Kontrakt usługi to `IOrderProcessor` , który definiuje usługę jednokierunkową, która jest odpowiednia do użycia z kolejkami.</span><span class="sxs-lookup"><span data-stu-id="a1334-144">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="a1334-145">Operacja usługi wyświetla komunikat informujący o przetwarzaniu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="a1334-145">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="a1334-146">Aby zademonstrować działanie trującej wiadomości, `SubmitPurchaseOrder` operacja usługi zgłasza wyjątek, aby wycofać transakcję w losowym wywołaniu usługi.</span><span class="sxs-lookup"><span data-stu-id="a1334-146">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to roll back the transaction on a random invocation of the service.</span></span> <span data-ttu-id="a1334-147">Powoduje to, że komunikat zostanie umieszczony w kolejce.</span><span class="sxs-lookup"><span data-stu-id="a1334-147">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="a1334-148">Ostatecznie wiadomość jest oznaczona jako trująca.</span><span class="sxs-lookup"><span data-stu-id="a1334-148">Eventually the message is marked as poison.</span></span> <span data-ttu-id="a1334-149">Konfiguracja jest ustawiana na przeniesienie skażonego komunikatu do podkolejki trującej.</span><span class="sxs-lookup"><span data-stu-id="a1334-149">The configuration is set to move the poison message to the poison subqueue.</span></span>

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

 <span data-ttu-id="a1334-150">Konfiguracja usługi zawiera następujące właściwości trujących komunikatów: `receiveRetryCount` , `maxRetryCycles` , i, `retryCycleDelay` `receiveErrorHandling` jak pokazano w następującym pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="a1334-150">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

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

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="a1334-151">Przetwarzanie komunikatów z kolejki skażonych komunikatów</span><span class="sxs-lookup"><span data-stu-id="a1334-151">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="a1334-152">Usługa Trująca wiadomość odczytuje komunikaty z kolejki skażonych komunikatów i przetwarza je.</span><span class="sxs-lookup"><span data-stu-id="a1334-152">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="a1334-153">Wiadomości w kolejce trujących komunikatów to komunikaty, które są rozkierowane do usługi przetwarzającej komunikat, co może się różnić od punktu końcowego trującej usługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a1334-153">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="a1334-154">W związku z tym, gdy usługa Trująca wiadomość odczytuje komunikaty z kolejki, warstwa kanału WCF znajdzie niezgodność w punktach końcowych i nie wysyła komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a1334-154">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="a1334-155">W takim przypadku komunikat jest kierowany do usługi przetwarzania zamówień, ale jest odbierany przez usługę trujących komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a1334-155">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="a1334-156">Aby nadal otrzymywać komunikat nawet wtedy, gdy wiadomość jest zakierowane do innego punktu końcowego, należy dodać `ServiceBehavior` do filtru, gdzie kryterium dopasowywania jest zgodne z dowolnymi punktami końcowymi, do których odnosi się komunikat.</span><span class="sxs-lookup"><span data-stu-id="a1334-156">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="a1334-157">Jest to wymagane do pomyślnego przetworzenia komunikatów odczytywanych z kolejki skażonych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a1334-157">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="a1334-158">Sama implementacja usługi trującej wiadomości jest podobna do implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a1334-158">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="a1334-159">Implementuje kontrakt i przetwarza zamówienia.</span><span class="sxs-lookup"><span data-stu-id="a1334-159">It implements the contract and processes the orders.</span></span> <span data-ttu-id="a1334-160">Przykładowy kod jest następujący.</span><span class="sxs-lookup"><span data-stu-id="a1334-160">The code example is as follows.</span></span>

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

 <span data-ttu-id="a1334-161">W przeciwieństwie do usługi przetwarzania zamówień, która odczytuje komunikaty z kolejki kolejności, usługa Trująca wiadomość odczytuje komunikaty z podkolejki trującej.</span><span class="sxs-lookup"><span data-stu-id="a1334-161">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison subqueue.</span></span> <span data-ttu-id="a1334-162">Kolejka Trująca jest podkolejką kolejki głównej, nosi nazwę "Trująca" i jest generowana automatycznie przez usługę MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a1334-162">The poison queue is a subqueue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="a1334-163">Aby uzyskać do niego dostęp, podaj nazwę kolejki głównej, po której następuje ";" i nazwę kolejki podrzędnej, w tym przypadku "trujące", jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="a1334-163">To access it, provide the main queue name followed by a ";" and the subqueue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="a1334-164">W przykładzie dla MSMQ v 3.0 nazwa kolejki trującej nie jest kolejką podrzędną, a nie kolejkę, do której przeniesiono komunikat.</span><span class="sxs-lookup"><span data-stu-id="a1334-164">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

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

 <span data-ttu-id="a1334-165">Po uruchomieniu przykładu działania usług Klient, usługa i Trująca wiadomość są wyświetlane w oknach konsoli.</span><span class="sxs-lookup"><span data-stu-id="a1334-165">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="a1334-166">Możesz zobaczyć, że usługa odbiera komunikaty od klienta.</span><span class="sxs-lookup"><span data-stu-id="a1334-166">You can see the service receive messages from the client.</span></span> <span data-ttu-id="a1334-167">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługi.</span><span class="sxs-lookup"><span data-stu-id="a1334-167">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="a1334-168">Usługa uruchamia się, przetwarza zamówienia i losowo rozpoczyna przetwarzanie.</span><span class="sxs-lookup"><span data-stu-id="a1334-168">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="a1334-169">Jeśli komunikat wskazuje, że przetworzył zamówienie, można ponownie uruchomić klienta, aby wysłać kolejny komunikat, dopóki usługa nie zakończyła się komunikatem.</span><span class="sxs-lookup"><span data-stu-id="a1334-169">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="a1334-170">W oparciu o skonfigurowane ustawienia trujące komunikat jest podejmowany raz na potrzeby przetwarzania przed przeniesieniem go do końcowej kolejki trującej.</span><span class="sxs-lookup"><span data-stu-id="a1334-170">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

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

 <span data-ttu-id="a1334-171">Uruchom usługę trującej wiadomości, aby odczytać trującą wiadomość z kolejki trującej.</span><span class="sxs-lookup"><span data-stu-id="a1334-171">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="a1334-172">W tym przykładzie usługa Trująca wiadomość odczytuje komunikat i przetwarza go.</span><span class="sxs-lookup"><span data-stu-id="a1334-172">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="a1334-173">Można zobaczyć, że zamówienie zakupu, które zostało zakończone i trujące jest odczytywane przez trującą usługę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a1334-173">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

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

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a1334-174">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="a1334-174">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a1334-175">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a1334-175">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a1334-176">Jeśli usługa jest uruchamiana po raz pierwszy, sprawdzi, czy kolejka jest obecna.</span><span class="sxs-lookup"><span data-stu-id="a1334-176">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="a1334-177">Jeśli kolejka nie istnieje, usługa utworzy ją.</span><span class="sxs-lookup"><span data-stu-id="a1334-177">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="a1334-178">Aby utworzyć kolejkę, można najpierw uruchomić tę usługę lub utworzyć ją za pośrednictwem Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a1334-178">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="a1334-179">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="a1334-179">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="a1334-180">Otwórz Menedżer serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="a1334-180">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="a1334-181">Rozwiń kartę **funkcje** .</span><span class="sxs-lookup"><span data-stu-id="a1334-181">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="a1334-182">Kliknij prawym przyciskiem myszy pozycję **prywatne kolejki komunikatów**, a następnie wybierz kolejno pozycje **Nowa**i **prywatne**.</span><span class="sxs-lookup"><span data-stu-id="a1334-182">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="a1334-183">Zaznacz pole **transakcyjne** .</span><span class="sxs-lookup"><span data-stu-id="a1334-183">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="a1334-184">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="a1334-184">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="a1334-185">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a1334-185">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="a1334-186">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, należy zmienić nazwy kolejek, aby odzwierciedlały rzeczywistą nazwę hosta zamiast hosta lokalnego i postępować zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a1334-186">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

 <span data-ttu-id="a1334-187">Domyślnie w przypadku `netMsmqBinding` transportu powiązań jest włączone zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="a1334-187">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="a1334-188">Dwie właściwości, `MsmqAuthenticationMode` a `MsmqProtectionLevel` także określają typ zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="a1334-188">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="a1334-189">Domyślnie tryb uwierzytelniania jest ustawiony na `Windows` , a poziom ochrony jest ustawiony na `Sign` .</span><span class="sxs-lookup"><span data-stu-id="a1334-189">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="a1334-190">Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny.</span><span class="sxs-lookup"><span data-stu-id="a1334-190">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="a1334-191">Jeśli ten przykład zostanie uruchomiony na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "wewnętrzny certyfikat usługi kolejkowania komunikatów użytkownika nie istnieje".</span><span class="sxs-lookup"><span data-stu-id="a1334-191">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="a1334-192">Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej</span><span class="sxs-lookup"><span data-stu-id="a1334-192">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="a1334-193">Jeśli komputer nie jest częścią domeny, Wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom ochrony `None` tak jak pokazano w poniższej konfiguracji przykładowej:</span><span class="sxs-lookup"><span data-stu-id="a1334-193">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="a1334-194">Upewnij się, że punkt końcowy jest skojarzony z powiązaniem, ustawiając atrybut bindingConfiguration punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a1334-194">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="a1334-195">Przed uruchomieniem przykładu należy zmienić konfigurację na PoisonMessageServer, serwerze i kliencie.</span><span class="sxs-lookup"><span data-stu-id="a1334-195">Ensure that you change the configuration on the PoisonMessageServer, server, and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a1334-196">Ustawienie `security mode` odpowiada `None` ustawieniu `MsmqAuthenticationMode` , `MsmqProtectionLevel` i `Message` zabezpieczenia na `None` .</span><span class="sxs-lookup"><span data-stu-id="a1334-196">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="a1334-197">Aby wymiana metadanych działała, rejestrujemy adres URL z powiązaniem HTTP.</span><span class="sxs-lookup"><span data-stu-id="a1334-197">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="a1334-198">Wymaga to uruchomienia usługi w oknie polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="a1334-198">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="a1334-199">W przeciwnym razie zostanie wyświetlony wyjątek, taki jak: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied` .</span><span class="sxs-lookup"><span data-stu-id="a1334-199">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a1334-200">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a1334-200">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a1334-201">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="a1334-201">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a1334-202">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="a1334-202">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a1334-203">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a1334-203">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
