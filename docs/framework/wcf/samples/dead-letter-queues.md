---
title: Kolejki utraconych komunikatów
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: a1e9ad000b83aab1e0d17d3443e1bd6f87310c9a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962627"
---
# <a name="dead-letter-queues"></a><span data-ttu-id="de516-102">Kolejki utraconych komunikatów</span><span class="sxs-lookup"><span data-stu-id="de516-102">Dead Letter Queues</span></span>
<span data-ttu-id="de516-103">Ten przykład pokazuje, jak obsługiwać i przetwarzać komunikaty, których dostarczenie nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="de516-103">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="de516-104">Jest on oparty na przykładowym [wiązaniem usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="de516-104">It is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="de516-105">Ten przykład używa `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="de516-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="de516-106">Usługa to samodzielna aplikacja konsolowa, która umożliwia obserwowanie usługi do odebrania komunikatów znajdujących się w kolejce.</span><span class="sxs-lookup"><span data-stu-id="de516-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="de516-107">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="de516-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="de516-108">Ten przykład pokazuje każdą kolejkę utraconych wiadomości aplikacji, która jest [!INCLUDE[wv](../../../../includes/wv-md.md)]dostępna tylko w systemie.</span><span class="sxs-lookup"><span data-stu-id="de516-108">This sample demonstrates each application dead letter queue that is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="de516-109">Przykład można zmodyfikować w taki sposób, aby korzystał z domyślnych kolejek cały system dla usługi [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] MSMQ [!INCLUDE[wxp](../../../../includes/wxp-md.md)]3,0 w systemach i.</span><span class="sxs-lookup"><span data-stu-id="de516-109">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span>

 <span data-ttu-id="de516-110">W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="de516-110">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="de516-111">Dokładniej, klient wysyła komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="de516-111">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="de516-112">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="de516-112">The service receives messages from the queue.</span></span> <span data-ttu-id="de516-113">W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="de516-113">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="de516-114">Ponieważ komunikacja w kolejce może potrwać określoną ilość dormancy, możesz chcieć skojarzyć wartość czasu wygaśnięcia w komunikacie, aby upewnić się, że wiadomość nie zostanie dostarczona do aplikacji w przypadku jej wcześniejszego przekroczenia.</span><span class="sxs-lookup"><span data-stu-id="de516-114">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="de516-115">Istnieją również przypadki, w których aplikacja musi być poinformowana, czy dostarczenie komunikatu nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="de516-115">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="de516-116">We wszystkich tych przypadkach, na przykład gdy czas wygaśnięcia komunikatu wygasł lub dostarczenie komunikatu nie powiodło się, komunikat zostanie umieszczony w kolejce utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de516-116">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="de516-117">Aplikacja wysyłająca może następnie odczytywać komunikaty w kolejce utraconych wiadomości i podejmować działania naprawcze, które nie są wynikiem działania, aby skorygować przyczyny niepowodzenia dostawy i ponownie wysłać wiadomość.</span><span class="sxs-lookup"><span data-stu-id="de516-117">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>

 <span data-ttu-id="de516-118">Kolejka utraconych wiadomości w `NetMsmqBinding` powiązaniu jest wyrażona w następujących właściwościach:</span><span class="sxs-lookup"><span data-stu-id="de516-118">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>

- <span data-ttu-id="de516-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>Właściwość w celu wyrażenia rodzaju kolejki utraconych wiadomości, która jest wymagana przez klienta.</span><span class="sxs-lookup"><span data-stu-id="de516-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="de516-120">To wyliczenie ma następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="de516-120">This enumeration has the following values:</span></span>

- <span data-ttu-id="de516-121">`None`: Klient nie wymaga kolejki utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de516-121">`None`: No dead-letter queue is required by the client.</span></span>

- <span data-ttu-id="de516-122">`System`: Kolejka utraconych wiadomości systemowych służy do przechowywania wiadomości utraconych.</span><span class="sxs-lookup"><span data-stu-id="de516-122">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="de516-123">Kolejka utraconych wiadomości systemowych jest udostępniana przez wszystkie aplikacje uruchomione na komputerze.</span><span class="sxs-lookup"><span data-stu-id="de516-123">The system dead-letter queue is shared by all applications running on the computer.</span></span>

- <span data-ttu-id="de516-124">`Custom`: Niestandardowa Kolejka utraconych wiadomości określona <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> przy użyciu właściwości jest używana do przechowywania wiadomości utraconych.</span><span class="sxs-lookup"><span data-stu-id="de516-124">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="de516-125">Ta funkcja jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)]systemie.</span><span class="sxs-lookup"><span data-stu-id="de516-125">This feature is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="de516-126">Jest on używany, gdy aplikacja musi używać własnej kolejki utraconych wiadomości zamiast udostępniać ją innym aplikacjom uruchomionym na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="de516-126">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>

- <span data-ttu-id="de516-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>Właściwość do wyrażenia określonej kolejki, która ma być używana jako kolejka utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de516-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="de516-128">Jest to możliwe tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)]programie.</span><span class="sxs-lookup"><span data-stu-id="de516-128">This is available only in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="de516-129">W tym przykładzie klient wysyła partię komunikatów do usługi z zakresu transakcji i określa arbitralnie niską wartość "czas wygaśnięcia" dla tych komunikatów (około 2 sekund).</span><span class="sxs-lookup"><span data-stu-id="de516-129">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="de516-130">Klient określa również niestandardową kolejkę utraconych wiadomości, która ma być używana do kolejkowania komunikatów, które wygasły.</span><span class="sxs-lookup"><span data-stu-id="de516-130">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>

 <span data-ttu-id="de516-131">Aplikacja kliencka może odczytać komunikaty w kolejce utraconych wiadomości i ponowić próbę wysłania komunikatu albo rozwiązać błąd, który spowodował umieszczenie oryginalnego komunikatu w kolejce utraconych wiadomości i wysłanie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="de516-131">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="de516-132">W przykładzie klient wyświetli komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="de516-132">In the sample, the client displays an error message.</span></span>

 <span data-ttu-id="de516-133">Kontrakt usługi jest `IOrderProcessor`, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="de516-133">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="de516-134">Kod usługi w przykładzie jest tym, że [transakcyjne powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="de516-134">The service code in the sample is that of the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>

 <span data-ttu-id="de516-135">Komunikacja z usługą odbywa się w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="de516-135">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="de516-136">Usługa odczytuje komunikaty z kolejki, wykonuje operację, a następnie wyświetla wyniki operacji.</span><span class="sxs-lookup"><span data-stu-id="de516-136">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="de516-137">Aplikacja tworzy również kolejkę utraconych wiadomości dla komunikatów utraconych.</span><span class="sxs-lookup"><span data-stu-id="de516-137">The application also creates a dead-letter queue for dead-letter messages.</span></span>

```csharp
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.

//Client implementation code.
class Client
{
    static void Main()
    {
        // Get MSMQ queue name from app settings in configuration
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];

        // Create the transacted MSMQ queue for storing dead message if necessary.
        if (!MessageQueue.Exists(deadLetterQueueName))
            MessageQueue.Create(deadLetterQueueName, true);

        // Create a proxy with given client endpoint configuration
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");

        // Create the purchase order
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

        //Create a transaction scope.
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            // Make a queued call to submit the purchase order
            client.SubmitPurchaseOrder(po);
            // Complete the transaction.
            scope.Complete();
        }

        client.Close();

        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate client.");
        Console.ReadLine();
    }
}
```

 <span data-ttu-id="de516-138">Konfiguracja klienta określa krótki czas trwania wiadomości w celu uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="de516-138">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="de516-139">Jeśli nie można przesłać komunikatu w określonym czasie trwania, komunikat wygaśnie i zostanie przeniesiony do kolejki utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de516-139">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>

> [!NOTE]
> <span data-ttu-id="de516-140">Klient może dostarczyć komunikat do kolejki usług w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="de516-140">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="de516-141">Aby upewnić się, że usługa utraconych wiadomości zostanie wyświetlona, należy uruchomić klienta programu przed uruchomieniem usługi.</span><span class="sxs-lookup"><span data-stu-id="de516-141">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="de516-142">Komunikat przekracza limit czasu i jest dostarczany do usługi utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de516-142">The message times out and is delivered to the dead-letter service.</span></span>

 <span data-ttu-id="de516-143">Aplikacja musi zdefiniować, która kolejka ma być używana jako jej Kolejka utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de516-143">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="de516-144">Jeśli kolejka nie jest określona, domyślna kolejka utraconych wiadomości transakcyjnych w całej systemie jest używana do kolejkowania martwych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="de516-144">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="de516-145">W tym przykładzie aplikacja kliencka określa własną kolejkę utraconych wiadomości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de516-145">In this example, the client application specifies its own application dead-letter queue.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>
  </appSettings>

  <system.serviceModel>
    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                binding="netMsmqBinding"
                bindingConfiguration="PerAppDLQBinding"
                contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="PerAppDLQBinding"
                 deadLetterQueue="Custom"
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                 timeToLive="00:00:02"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="de516-146">Usługa komunikatów utraconych odczytuje komunikaty z kolejki utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de516-146">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="de516-147">Usługa wiadomości utraconych zawiera implementację `IOrderProcessor` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="de516-147">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="de516-148">Jego implementacja nie przetwarza jednak zamówień.</span><span class="sxs-lookup"><span data-stu-id="de516-148">Its implementation however is not to process orders.</span></span> <span data-ttu-id="de516-149">Usługa wiadomości utraconych jest usługą klienta i nie ma możliwości przetwarzania zamówień.</span><span class="sxs-lookup"><span data-stu-id="de516-149">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>

> [!NOTE]
> <span data-ttu-id="de516-150">Kolejka utraconych wiadomości jest kolejką klienta i jest lokalna dla Menedżera kolejki klienta.</span><span class="sxs-lookup"><span data-stu-id="de516-150">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>

 <span data-ttu-id="de516-151">Implementacja usługi komunikatów utraconych wiadomości sprawdza, czy nie powiodło się dostarczenie komunikatu i podejmuje środki naprawcze.</span><span class="sxs-lookup"><span data-stu-id="de516-151">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="de516-152">Przyczyna niepowodzenia komunikatu jest przechwytywana w dwóch wyliczeniach <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> i. <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A></span><span class="sxs-lookup"><span data-stu-id="de516-152">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="de516-153">Możesz pobrać <xref:System.ServiceModel.Channels.MsmqMessageProperty> <xref:System.ServiceModel.OperationContext> z programu, tak jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="de516-153">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succeed ", po);
    MsmqMessageProperty mqProp =
                  OperationContext.Current.IncomingMessageProperties[
                  MsmqMessageProperty.Name] as MsmqMessageProperty;
    Console.WriteLine("Message Delivery Status: {0} ",
                                                mqProp.DeliveryStatus);
    Console.WriteLine("Message Delivery Failure: {0}",
                                               mqProp.DeliveryFailure);
    Console.WriteLine();
    …
}
```

 <span data-ttu-id="de516-154">Komunikaty w kolejce utraconych wiadomości to komunikaty, które są rozkierowane do usługi, która przetwarza komunikat.</span><span class="sxs-lookup"><span data-stu-id="de516-154">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="de516-155">W związku z tym, gdy usługa wiadomości utraconych odczytuje komunikaty z kolejki, warstwa kanału Windows Communication Foundation (WCF) znajdzie niezgodność w punktach końcowych i nie wyśle komunikatu.</span><span class="sxs-lookup"><span data-stu-id="de516-155">Therefore, when the dead-letter message service reads messages from the queue, the Windows Communication Foundation (WCF) channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="de516-156">W takim przypadku komunikat jest kierowany do usługi przetwarzania zamówień, ale jest odbierany przez usługę wiadomości utraconych.</span><span class="sxs-lookup"><span data-stu-id="de516-156">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="de516-157">Aby odebrać komunikat, który jest rozkierowany do innego punktu końcowego, filtr adresów w celu dopasowania do dowolnego adresu jest określony `ServiceBehavior`w.</span><span class="sxs-lookup"><span data-stu-id="de516-157">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="de516-158">Jest to wymagane do pomyślnego przetworzenia komunikatów, które są odczytywane z kolejki utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de516-158">This is required to successfully process messages that are read from the dead-letter queue.</span></span>

 <span data-ttu-id="de516-159">W tym przykładzie usługa wiadomości utraconych wysyła komunikat, jeśli przyczyną niepowodzenia jest komunikat z limitem czasu. Ze względu na to, że wyświetla błąd dostarczania, jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="de516-159">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]
public class PurchaseOrderDLQService : IOrderProcessor
{
    OrderProcessorClient orderProcessorService;
    public PurchaseOrderDLQService()
    {
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Submitting purchase order did not succeed ", po);
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;

        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);
        Console.WriteLine();

        // resend the message if timed out
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)
        {
            // re-send
            Console.WriteLine("Purchase order Time To Live expired");
            Console.WriteLine("Trying to resend the message");

            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue
            orderProcessorService.SubmitPurchaseOrder(po);
            Console.WriteLine("Purchase order resent");
        }
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Create a ServiceHost for the PurchaseOrderDLQService type.
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))
        {
            // Open the ServiceHostBase to create listeners and start listening for messages.
            serviceHost.Open();

            // The service can now be accessed.
            Console.WriteLine("The dead letter service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.WriteLine();
            Console.ReadLine();
        }
    }
}
```

 <span data-ttu-id="de516-160">Poniższy przykład pokazuje konfigurację wiadomości utraconej:</span><span class="sxs-lookup"><span data-stu-id="de516-160">The following sample shows the configuration for a dead-letter message:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                  binding="netMsmqBinding"
                  bindingConfiguration="DefaultBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                 binding="netMsmqBinding"
                 bindingConfiguration="SystemDLQBinding"
                 contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="DefaultBinding" />
        <binding name="SystemDLQBinding"
                 deadLetterQueue="System"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="de516-161">W trakcie uruchamiania przykładu dostępne są 3 pliki wykonywalne, aby zobaczyć, jak Kolejka utraconych komunikatów działa dla każdej aplikacji; Klient, usługa i utracona usługa, która odczytuje z kolejki utraconych wiadomości dla każdej aplikacji i ponownie wysyła komunikat do usługi.</span><span class="sxs-lookup"><span data-stu-id="de516-161">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="de516-162">Wszystkie są aplikacjami konsolowymi z danymi wyjściowymi w oknach konsoli.</span><span class="sxs-lookup"><span data-stu-id="de516-162">All are console applications with output in console windows.</span></span>

> [!NOTE]
> <span data-ttu-id="de516-163">Ponieważ kolejkowanie jest w użyciu, klient i usługa nie muszą działać w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="de516-163">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="de516-164">Można uruchomić klienta programu, zamknąć go, a następnie uruchomić usługę i nadal otrzymywać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de516-164">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="de516-165">Należy uruchomić usługę i zamknąć ją, aby można było utworzyć kolejkę.</span><span class="sxs-lookup"><span data-stu-id="de516-165">You should start the service and shut it down so that the queue can be created.</span></span>

 <span data-ttu-id="de516-166">W przypadku uruchamiania klienta klient wyświetla komunikat:</span><span class="sxs-lookup"><span data-stu-id="de516-166">When running the client, the client displays the message:</span></span>

```
Press <ENTER> to terminate client.
```

 <span data-ttu-id="de516-167">Klient podjął próbę wysłania komunikatu, ale z krótkim limitem czasu, wiadomość wygasła i została teraz umieszczona w kolejce do kolejki utraconych wiadomości dla każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de516-167">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>

 <span data-ttu-id="de516-168">Następnie uruchamiasz usługę utraconych wiadomości, która odczytuje komunikat i wyświetla kod błędu i ponownie wysyła komunikat z powrotem do usługi.</span><span class="sxs-lookup"><span data-stu-id="de516-168">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>

```
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 <span data-ttu-id="de516-169">Usługa uruchamia się, a następnie odczytuje ponownie wysłaną wiadomość i przetwarza ją.</span><span class="sxs-lookup"><span data-stu-id="de516-169">The service starts and then reads the resent message and processes it.</span></span>

```
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="de516-170">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="de516-170">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="de516-171">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="de516-171">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="de516-172">Jeśli usługa jest uruchamiana po raz pierwszy, sprawdzi, czy kolejka jest obecna.</span><span class="sxs-lookup"><span data-stu-id="de516-172">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="de516-173">Jeśli kolejka nie istnieje, usługa utworzy ją.</span><span class="sxs-lookup"><span data-stu-id="de516-173">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="de516-174">Aby utworzyć kolejkę, można najpierw uruchomić tę usługę lub utworzyć ją za pośrednictwem Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="de516-174">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="de516-175">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="de516-175">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="de516-176">Otwórz Menedżer serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="de516-176">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="de516-177">Rozwiń kartę **funkcje** .</span><span class="sxs-lookup"><span data-stu-id="de516-177">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="de516-178">Kliknij prawym przyciskiem myszy pozycję **prywatne kolejki komunikatów**, a następnie wybierz kolejno pozycje **Nowa**i **prywatne**.</span><span class="sxs-lookup"><span data-stu-id="de516-178">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="de516-179">Zaznacz pole **transakcyjne** .</span><span class="sxs-lookup"><span data-stu-id="de516-179">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="de516-180">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="de516-180">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="de516-181">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="de516-181">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="de516-182">Aby uruchomić przykład w odpowiedniej nazwie kolejki zmian konfiguracji na jednym lub wielu komputerach, zastępując localhost pełną nazwą komputera i postępuj zgodnie z instrukcjami w temacie [uruchamianie Windows Communication Foundation przykładów](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="de516-182">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="de516-183">Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej</span><span class="sxs-lookup"><span data-stu-id="de516-183">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="de516-184">Jeśli komputer nie jest częścią domeny, Wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom `None` ochrony tak jak pokazano w poniższej konfiguracji przykładowej:</span><span class="sxs-lookup"><span data-stu-id="de516-184">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="de516-185">Upewnij się, że punkt końcowy jest skojarzony z powiązaniem przez ustawienie `bindingConfiguration` atrybutu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="de516-185">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>

2. <span data-ttu-id="de516-186">Przed uruchomieniem przykładu należy zmienić konfigurację na DeadLetterService, serwerze i kliencie.</span><span class="sxs-lookup"><span data-stu-id="de516-186">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="de516-187">`security mode` Ustawienieodpowiada`MsmqProtectionLevel` ustawieniu i`MsmqAuthenticationMode` zabezpieczeniana`None`. `None` `Message`</span><span class="sxs-lookup"><span data-stu-id="de516-187">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

## <a name="comments"></a><span data-ttu-id="de516-188">Komentarze</span><span class="sxs-lookup"><span data-stu-id="de516-188">Comments</span></span>
 <span data-ttu-id="de516-189">Domyślnie w przypadku `netMsmqBinding` transportu powiązań jest włączone zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="de516-189">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="de516-190">Dwie właściwości, `MsmqAuthenticationMode` a `MsmqProtectionLevel`także określają typ zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="de516-190">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="de516-191">Domyślnie tryb uwierzytelniania jest ustawiony na `Windows` , a poziom ochrony jest ustawiony na. `Sign`</span><span class="sxs-lookup"><span data-stu-id="de516-191">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="de516-192">Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny.</span><span class="sxs-lookup"><span data-stu-id="de516-192">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="de516-193">Jeśli ten przykład zostanie uruchomiony na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "Wewnętrzny certyfikat usługi kolejkowania komunikatów użytkownika nie istnieje".</span><span class="sxs-lookup"><span data-stu-id="de516-193">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="de516-194">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="de516-194">The samples may already be installed on your computer.</span></span> <span data-ttu-id="de516-195">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="de516-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="de516-196">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="de516-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="de516-197">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="de516-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
