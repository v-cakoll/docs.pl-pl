---
title: Kolejki utraconych komunikatów
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 4f30e9486c8798e3610e13e6abe1c2612c70b69f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417136"
---
# <a name="dead-letter-queues"></a><span data-ttu-id="4ce39-102">Kolejki utraconych komunikatów</span><span class="sxs-lookup"><span data-stu-id="4ce39-102">Dead Letter Queues</span></span>
<span data-ttu-id="4ce39-103">W tym przykładzie pokazano, jak obsługiwać i przetwarzać komunikaty, które dostarczania nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="4ce39-103">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="4ce39-104">Jest on oparty na [dokonana transakcja powiązania usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="4ce39-104">It is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="4ce39-105">W tym przykładzie użyto `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="4ce39-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="4ce39-106">Usługa jest aplikacji konsoli Self-Hosted umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="4ce39-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ce39-107">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4ce39-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ce39-108">W tym przykładzie przedstawiono kolejkę z utraconymi każdej aplikacji, która jest dostępna tylko na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ce39-108">This sample demonstrates each application dead letter queue that is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="4ce39-109">Przykład można zmodyfikować, aby użyć domyślnej kolejki systemowe dla usługi MSMQ 3.0 na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ce39-109">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span>  
  
 <span data-ttu-id="4ce39-110">W komunikacie w kolejce klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="4ce39-110">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="4ce39-111">Mówiąc ściślej klient wysyła komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="4ce39-111">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="4ce39-112">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="4ce39-112">The service receives messages from the queue.</span></span> <span data-ttu-id="4ce39-113">Usługi i klienta w związku z tym, nie musi być uruchomiona w tym samym czasie do komunikowania się za pomocą kolejki.</span><span class="sxs-lookup"><span data-stu-id="4ce39-113">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="4ce39-114">Ponieważ komunikacja umieszczonych w kolejce może obejmować określoną ilość spoczynku, można skojarzyć wartości czasu wygaśnięcia na komunikat, aby zapewnić, że komunikat nie uzyskać dostarczane do aplikacji, gdy stała się późniejsza niż godzina.</span><span class="sxs-lookup"><span data-stu-id="4ce39-114">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="4ce39-115">Istnieją przypadki, gdzie aplikacja należy poinformować, czy komunikat zakończyło się niepowodzeniem dostarczania.</span><span class="sxs-lookup"><span data-stu-id="4ce39-115">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="4ce39-116">We wszystkich przypadkach takich jak time-to-live w komunikacie wygasła lub komunikat dostarczania nie powiodło się, komunikat jest umieszczany w kolejce utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-116">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="4ce39-117">Aplikacji wysyłającej można odczytywać wiadomości z kolejki utraconych wiadomości i podejmuj akcje naprawcze, z zakresu od żadnych działań do poprawiania przyczyn dostawy nie powiodło się i ponowne wysyłanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-117">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>  
  
 <span data-ttu-id="4ce39-118">Kolejki utraconych wiadomości w `NetMsmqBinding` wiązanie danych jest wyrażona w następujących właściwościach:</span><span class="sxs-lookup"><span data-stu-id="4ce39-118">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>  
  
-   <span data-ttu-id="4ce39-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> Właściwość wyrażenia rodzaju kolejki utraconych wiadomości wymagane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="4ce39-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="4ce39-120">To wyliczenie ma następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="4ce39-120">This enumeration has the following values:</span></span>  
  
-   <span data-ttu-id="4ce39-121">`None`: Brak kolejki utraconych wiadomości jest wymagane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="4ce39-121">`None`: No dead-letter queue is required by the client.</span></span>  
  
-   <span data-ttu-id="4ce39-122">`System`Kolejki utraconych wiadomości system służy do przechowywania utracone wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-122">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="4ce39-123">Kolejka utraconych wiadomości systemu jest współużytkowana przez wszystkie aplikacje uruchomione na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4ce39-123">The system dead-letter queue is shared by all applications running on the computer.</span></span>  
  
-   <span data-ttu-id="4ce39-124">`Custom`Niestandardowe kolejki utraconych wiadomości, które są określone za pomocą <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> właściwość jest używana do przechowywania utracone wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-124">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="4ce39-125">Ta funkcja jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ce39-125">This feature is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="4ce39-126">Służy to, gdy aplikacja musi używać własnej kolejki utraconych wiadomości zamiast udostępnianie innym aplikacjom działającym na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4ce39-126">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>  
  
-   <span data-ttu-id="4ce39-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> Właściwość do określonej kolejki do użycia jako kolejki utraconych wiadomości express.</span><span class="sxs-lookup"><span data-stu-id="4ce39-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="4ce39-128">Ta opcja jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ce39-128">This is available only in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>  
  
 <span data-ttu-id="4ce39-129">W tym przykładzie klient wysyła komunikaty zbiorczo do usługi z zakresu transakcji i określa arbitralnie niska wartość "time-to-live" dla tych wiadomości (około 2 sekund).</span><span class="sxs-lookup"><span data-stu-id="4ce39-129">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="4ce39-130">Klient określa również niestandardowych kolejki utraconych wiadomości do użycia można umieścić w kolejce komunikatów, które wygasły.</span><span class="sxs-lookup"><span data-stu-id="4ce39-130">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>  
  
 <span data-ttu-id="4ce39-131">Aplikacja kliencka może odczytywać wiadomości z kolejki utraconych wiadomości i albo ponownych prób wysyłania komunikatu lub naprawić błąd, który spowodował oryginalna wiadomość ma zostać umieszczone w kolejce utraconych wiadomości, a następnie wysłać wiadomość.</span><span class="sxs-lookup"><span data-stu-id="4ce39-131">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="4ce39-132">W tym przykładzie klient jest wyświetlany komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="4ce39-132">In the sample, the client displays an error message.</span></span>  
  
 <span data-ttu-id="4ce39-133">Umowa serwisowa jest `IOrderProcessor`, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4ce39-133">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 <span data-ttu-id="4ce39-134">Kod usługi, w przykładzie jest [dokonana transakcja powiązania usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="4ce39-134">The service code in the sample is that of the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="4ce39-135">Komunikacja z usługą odbywa się w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="4ce39-135">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="4ce39-136">Usługa odczytuje komunikaty z kolejki, wykonuje operację, a następnie wyświetla wyniki operacji.</span><span class="sxs-lookup"><span data-stu-id="4ce39-136">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="4ce39-137">Aplikacja tworzy również kolejka utraconych wiadomości utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-137">The application also creates a dead-letter queue for dead-letter messages.</span></span>  

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

 <span data-ttu-id="4ce39-138">Konfiguracja klienta określa krótki czas trwania komunikatu w celu dotarcia do usługi.</span><span class="sxs-lookup"><span data-stu-id="4ce39-138">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="4ce39-139">Jeśli komunikat nie mogą być przekazywane w trakcie trwania określone, komunikat wygaśnie i zostanie przeniesiona do kolejki utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-139">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ce39-140">Istnieje możliwość dla klienta w celu dostarczenia komunikatu do kolejki usługi w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="4ce39-140">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="4ce39-141">Aby wyświetlić usługę wiadomości utraconych w akcji, należy uruchomić przed uruchomieniem usługi klienta.</span><span class="sxs-lookup"><span data-stu-id="4ce39-141">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="4ce39-142">Komunikat upłynie limit czasu i jest dostarczana z usługą utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-142">The message times out and is delivered to the dead-letter service.</span></span>  
  
 <span data-ttu-id="4ce39-143">Aplikacja musi definiować której kolejki do użycia jako swojej kolejki utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-143">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="4ce39-144">Jeśli kolejka nie zostanie określony, domyślna systemowe transakcyjnej kolejki utraconych wiadomości jest używany do kolejki martwych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-144">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="4ce39-145">W tym przykładzie aplikacja kliencka określa własnej kolejki utraconych wiadomości dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ce39-145">In this example, the client application specifies its own application dead-letter queue.</span></span>  
  
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
  
 <span data-ttu-id="4ce39-146">Usługa wiadomości utraconych odczytuje komunikaty z kolejki utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-146">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="4ce39-147">Implementuje usługi wiadomości utraconych `IOrderProcessor` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4ce39-147">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="4ce39-148">Jego implementacja nie jest jednak aby przetwarzać zamówienia.</span><span class="sxs-lookup"><span data-stu-id="4ce39-148">Its implementation however is not to process orders.</span></span> <span data-ttu-id="4ce39-149">Usługa utraconych wiadomości usługi klienta i nie ma możliwości przetwarzania zamówień.</span><span class="sxs-lookup"><span data-stu-id="4ce39-149">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ce39-150">Kolejki utraconych wiadomości jest kolejką klienta i lokalny Menedżer kolejki klienta.</span><span class="sxs-lookup"><span data-stu-id="4ce39-150">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>  
  
 <span data-ttu-id="4ce39-151">Sprawdza implementacji usługi wiadomości utraconych z powodu komunikatu nie powiodła się, dostarczanie i środki naprawcze przyjmuje.</span><span class="sxs-lookup"><span data-stu-id="4ce39-151">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="4ce39-152">Przyczyną niepowodzenia wiadomości są przechwytywane w dwóch wyliczenia <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> i <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ce39-152">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="4ce39-153">Możesz pobrać <xref:System.ServiceModel.Channels.MsmqMessageProperty> z <xref:System.ServiceModel.OperationContext> jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="4ce39-153">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>  

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)  
{  
    Console.WriteLine("Submitting purchase order did not succed ", po);  
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

 <span data-ttu-id="4ce39-154">Wiadomości w kolejce wiadomości utraconych to komunikaty, które są kierowane do usługi, która przetwarza wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-154">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="4ce39-155">W związku z tym gdy usługa wiadomości utraconych odczytuje komunikaty z kolejki, warstwy kanału usługi Windows Communication Foundation (WCF) umożliwia znalezienie niezgodność punktów końcowych i nie wysyła komunikat.</span><span class="sxs-lookup"><span data-stu-id="4ce39-155">Therefore, when the dead-letter message service reads messages from the queue, the Windows Communication Foundation (WCF) channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="4ce39-156">W takich przypadkach komunikat jest skierowana do Usługa przetwarzania zamówień, ale są odbierane przez usługę utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-156">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="4ce39-157">Aby otrzymywać wiadomość, która jest skierowana do innego punktu końcowego, filtr adresów, aby dopasować dowolny adres jest określony w `ServiceBehavior`.</span><span class="sxs-lookup"><span data-stu-id="4ce39-157">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="4ce39-158">Jest to wymagane, aby pomyślnie przetwarzania komunikatów, które są odczytywane z kolejki utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-158">This is required to successfully process messages that are read from the dead-letter queue.</span></span>  
  
 <span data-ttu-id="4ce39-159">W tym przykładzie Usługa utraconych wiadomości umożliwia ponowne wysłanie wiadomości Jeśli przyczyna niepowodzenia jest fakt, że komunikat upłynął limit czasu. Z innych przyczyn wyświetla błąd dostarczania, jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="4ce39-159">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>  

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

 <span data-ttu-id="4ce39-160">Poniższy przykład przedstawia konfigurację dla wiadomości utraconych wiadomości:</span><span class="sxs-lookup"><span data-stu-id="4ce39-160">The following sample shows the configuration for a dead-letter message:</span></span>  
  
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
  
 <span data-ttu-id="4ce39-161">W działa aplikacja przykładowa, istnieją 3 pliki wykonywalne uruchomić, aby zobaczyć, jak działa kolejki utraconych wiadomości dla każdej aplikacji; Klient usługi i usługi utraconych wiadomości, odczytuje z kolejki utraconych wiadomości dla każdej aplikacji, która umożliwia ponowne wysłanie wiadomości w usłudze.</span><span class="sxs-lookup"><span data-stu-id="4ce39-161">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="4ce39-162">Wszystkie są aplikacje konsoli z danych wyjściowych okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="4ce39-162">All are console applications with output in console windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ce39-163">Ponieważ usługi kolejkowania wiadomości jest używany, klient i usługa ma być uruchomiona w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="4ce39-163">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="4ce39-164">Można uruchomić klienta, zamknij go, a następnie uruchom usługi i wciąż otrzymuje jego wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ce39-164">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="4ce39-165">Należy uruchomić usługę i zamknij go, tak że można utworzyć kolejki.</span><span class="sxs-lookup"><span data-stu-id="4ce39-165">You should start the service and shut it down so that the queue can be created.</span></span>  
  
 <span data-ttu-id="4ce39-166">Podczas uruchamiania klienta, klient jest wyświetlany komunikat:</span><span class="sxs-lookup"><span data-stu-id="4ce39-166">When running the client, the client displays the message:</span></span>  
  
```  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="4ce39-167">Klient próbował wysłać wiadomość, ale z krótki limit czasu, wiadomość wygasł i jest obecnie w kolejce kolejki utraconych wiadomości dla każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ce39-167">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>  
  
 <span data-ttu-id="4ce39-168">Następnie uruchom usługę utraconych wiadomości, która odczytuje komunikat i wyświetla kod błędu: umożliwia ponowne wysłanie wiadomości do usługi.</span><span class="sxs-lookup"><span data-stu-id="4ce39-168">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>  
  
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
  
 <span data-ttu-id="4ce39-169">Uruchamiania i następnie odczytuje komunikat wysłane ponownie i przetwarza je.</span><span class="sxs-lookup"><span data-stu-id="4ce39-169">The service starts and then reads the resent message and processes it.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4ce39-170">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="4ce39-170">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4ce39-171">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4ce39-171">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4ce39-172">Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny.</span><span class="sxs-lookup"><span data-stu-id="4ce39-172">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="4ce39-173">Jeśli kolejka nie jest obecny, będzie utworzyć usługę.</span><span class="sxs-lookup"><span data-stu-id="4ce39-173">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="4ce39-174">Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4ce39-174">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="4ce39-175">Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="4ce39-175">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="4ce39-176">Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ce39-176">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="4ce39-177">Rozwiń **funkcji** kartę.</span><span class="sxs-lookup"><span data-stu-id="4ce39-177">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="4ce39-178">Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="4ce39-178">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="4ce39-179">Sprawdź **transakcyjna** pole.</span><span class="sxs-lookup"><span data-stu-id="4ce39-179">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="4ce39-180">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="4ce39-180">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="4ce39-181">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4ce39-181">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="4ce39-182">Do uruchomienia przykładu w kolejce zmiany konfiguracji komputera jednego lub wielu nazw odpowiednio zastępowanie localhost z pełną nazwę komputera i postępuj zgodnie z instrukcjami w [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4ce39-182">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="4ce39-183">Do uruchomienia przykładu na komputer przyłączony do grupy roboczej</span><span class="sxs-lookup"><span data-stu-id="4ce39-183">To run the sample on a computer joined to a workgroup</span></span>  
  
1.  <span data-ttu-id="4ce39-184">Jeśli komputer nie jest częścią domeny, należy wyłączyć zabezpieczenia transportu, ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższym Przykładowa konfiguracja:</span><span class="sxs-lookup"><span data-stu-id="4ce39-184">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding name="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="4ce39-185">Upewnij się, punkt końcowy jest skojarzony z powiązaniem przez ustawienie punktu końcowego `bindingConfiguration` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4ce39-185">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>  
  
2.  <span data-ttu-id="4ce39-186">Upewnij się, zmień konfigurację na DeadLetterService, serwera i klienta, przed uruchomieniem przykładu.</span><span class="sxs-lookup"><span data-stu-id="4ce39-186">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ce39-187">Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia `MsmqAuthenticationMode`, `MsmqProtectionLevel` i `Message` security `None`.</span><span class="sxs-lookup"><span data-stu-id="4ce39-187">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="4ce39-188">Komentarze</span><span class="sxs-lookup"><span data-stu-id="4ce39-188">Comments</span></span>  
 <span data-ttu-id="4ce39-189">Domyślnie `netMsmqBinding` powiązania transportu, zabezpieczeń jest włączone.</span><span class="sxs-lookup"><span data-stu-id="4ce39-189">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="4ce39-190">Dwie właściwości `MsmqAuthenticationMode` i `MsmqProtectionLevel`, wspólnie określić typ zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="4ce39-190">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="4ce39-191">Domyślny tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="4ce39-191">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="4ce39-192">Dla usługi MSMQ zapewniać uwierzytelnianie i funkcji podpisywania należy do domeny.</span><span class="sxs-lookup"><span data-stu-id="4ce39-192">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="4ce39-193">Po uruchomieniu tego przykładu na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "Wiadomość użytkownika wewnętrzny certyfikat usługi kolejkowania nie istnieje".</span><span class="sxs-lookup"><span data-stu-id="4ce39-193">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4ce39-194">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4ce39-194">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4ce39-195">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4ce39-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4ce39-196">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="4ce39-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4ce39-197">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4ce39-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
  
## <a name="see-also"></a><span data-ttu-id="4ce39-198">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ce39-198">See Also</span></span>
