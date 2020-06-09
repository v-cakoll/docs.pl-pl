---
title: Komunikacja dwukierunkowa
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 291380d656b0e22c7fdf1cb291c45d05359a95c8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591270"
---
# <a name="two-way-communication"></a><span data-ttu-id="30283-102">Komunikacja dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="30283-102">Two-Way Communication</span></span>
<span data-ttu-id="30283-103">W tym przykładzie pokazano, jak wykonać transakcyjne dwukierunkowe połączenia w kolejce za pośrednictwem usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="30283-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="30283-104">Ten przykład używa `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="30283-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="30283-105">W takim przypadku usługa to samodzielna aplikacja konsolowa, która umożliwia obserwowanie usługi do odebrania komunikatów umieszczonych w kolejce.</span><span class="sxs-lookup"><span data-stu-id="30283-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30283-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="30283-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="30283-107">Ten przykład jest oparty na [transakcyjnym powiązaniu MSMQ](transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="30283-107">This sample is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="30283-108">W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="30283-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="30283-109">Klient wysyła komunikaty do kolejki, a usługa otrzymuje komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="30283-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="30283-110">W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="30283-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="30283-111">Ten przykład pokazuje 2-kierunkową komunikację za pomocą kolejek.</span><span class="sxs-lookup"><span data-stu-id="30283-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="30283-112">Klient wysyła zamówienia zakupu do kolejki z zakresu transakcji.</span><span class="sxs-lookup"><span data-stu-id="30283-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="30283-113">Usługa otrzymuje zamówienia, przetwarza zamówienie, a następnie wywołuje klienta przy użyciu stanu zamówienia z kolejki w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="30283-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="30283-114">Aby ułatwić komunikację dwukierunkową, klient i usługa używają kolejek do dodawania do kolejki zamówień zakupu i stanu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="30283-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="30283-115">Kontrakt usługi `IOrderProcessor` definiuje jednokierunkowe operacje usługi, które pasują do korzystania z kolejkowania.</span><span class="sxs-lookup"><span data-stu-id="30283-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="30283-116">Operacja usługi zawiera punkt końcowy odpowiedzi, który służy do wysyłania Stanów zamówienia do.</span><span class="sxs-lookup"><span data-stu-id="30283-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="30283-117">Punkt końcowy odpowiedzi jest identyfikatorem URI kolejki w celu wysłania stanu zamówienia z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="30283-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="30283-118">Aplikacja do przetwarzania zamówień implementuje ten kontrakt.</span><span class="sxs-lookup"><span data-stu-id="30283-118">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="30283-119">Kontrakt odpowiedzi do wysłania stan zamówienia jest określany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="30283-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="30283-120">Klient implementuje kontrakt stanu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="30283-120">The client implements the order status contract.</span></span> <span data-ttu-id="30283-121">Usługa używa wygenerowanego serwera proxy tego kontraktu do wysyłania stanu zamówienia z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="30283-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="30283-122">Operacja usługi przetwarza przesłane zamówienie zakupu.</span><span class="sxs-lookup"><span data-stu-id="30283-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="30283-123"><xref:System.ServiceModel.OperationBehaviorAttribute>Jest stosowana do operacji usługi, aby określić automatyczną rejestrację w transakcji, która jest używana do odbierania komunikatu z kolejki i automatycznego uzupełniania transakcji po zakończeniu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="30283-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="30283-124">`Orders`Klasa hermetyzuje funkcje przetwarzania zamówień.</span><span class="sxs-lookup"><span data-stu-id="30283-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="30283-125">W takim przypadku dodaje zamówienie zakupu do słownika.</span><span class="sxs-lookup"><span data-stu-id="30283-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="30283-126">Transakcja, w której rejestrowana jest operacja usługi, jest dostępna dla operacji w `Orders` klasie.</span><span class="sxs-lookup"><span data-stu-id="30283-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="30283-127">Operacja usługi, poza przetwarzaniem przesłanego zamówienia zakupu, odpowiedzi z powrotem na klienta w stanie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="30283-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
{  
    Orders.Add(po);  
    Console.WriteLine("Processing {0} ", po);  
    Console.WriteLine("Sending back order status information");  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding("ClientCallbackBinding");  
    OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
  
    // Please note that the same transaction that is used to dequeue the purchase order is used  
    // to send back order status.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        client.OrderStatus(po.PONumber, po.Status);  
        scope.Complete();  
    }  
    //Close the client.  
    client.Close();  
}  
```

 <span data-ttu-id="30283-128">Nazwa kolejki MSMQ jest określona w sekcji appSettings w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="30283-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="30283-129">Punkt końcowy usługi jest zdefiniowany w sekcji System. ServiceModel w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="30283-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30283-130">Nazwa kolejki MSMQ i adres punktu końcowego używają nieco różnych konwencji adresowania.</span><span class="sxs-lookup"><span data-stu-id="30283-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="30283-131">Nazwa kolejki MSMQ używa kropki (.) dla komputera lokalnego i separatora odwrotnego ukośnika w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="30283-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="30283-132">Adres punktu końcowego Windows Communication Foundation (WCF) określa obiekt net. MSMQ: schemat, używa "localhost" dla komputera lokalnego i używa ukośników w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="30283-132">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="30283-133">Aby odczytać z kolejki hostowanej na maszynie zdalnej, Zastąp ciąg "." i "localhost" nazwą maszyny zdalnej.</span><span class="sxs-lookup"><span data-stu-id="30283-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="30283-134">Usługa jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="30283-134">The service is self hosted.</span></span> <span data-ttu-id="30283-135">W przypadku korzystania z transportu usługi MSMQ użyta Kolejka musi zostać utworzona z góry.</span><span class="sxs-lookup"><span data-stu-id="30283-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="30283-136">Można to zrobić ręcznie lub przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="30283-136">This can be done manually or through code.</span></span> <span data-ttu-id="30283-137">W tym przykładzie usługa sprawdza obecność kolejki i tworzy ją w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="30283-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="30283-138">Nazwa kolejki jest odczytywana z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="30283-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="30283-139">Adres podstawowy jest używany przez narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania serwera proxy w usłudze.</span><span class="sxs-lookup"><span data-stu-id="30283-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from appSettings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderProcessorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```

 <span data-ttu-id="30283-140">Klient tworzy transakcję.</span><span class="sxs-lookup"><span data-stu-id="30283-140">The client creates a transaction.</span></span> <span data-ttu-id="30283-141">Komunikacja z kolejką odbywa się w zakresie transakcji, co sprawia, że jest ona traktowana jako jednostka niepodzielna, w której wszystkie komunikaty kończą się powodzeniem lub niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="30283-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

```csharp
// Create a ServiceHost for the OrderStatus service type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
  
    // Open the ServiceHostBase to create listeners and start listening for order status messages.  
    serviceHost.Open();  
  
    // Create the purchase order.  
    ...  
  
    // Create a client with given client endpoint configuration.  
    OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        string hostName = Dns.GetHostName();  
  
        // Make a queued call to submit the purchase order.  
        client.SubmitPurchaseOrder(po, "net.msmq://" + hostName + "/private/ServiceModelSamplesTwo-way/OrderStatus");  
  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Close down the client.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHost to shutdown the service.  
    serviceHost.Close();  
}  
```

 <span data-ttu-id="30283-142">Kod klienta implementuje kontrakt, `IOrderStatus` Aby otrzymać stan zamówienia z usługi.</span><span class="sxs-lookup"><span data-stu-id="30283-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="30283-143">W takim przypadku drukuje stan zamówienia.</span><span class="sxs-lookup"><span data-stu-id="30283-143">In this case, it prints out the order status.</span></span>  

```csharp
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ", poNumber ,
                                                           status);  
    }  
}  
```

 <span data-ttu-id="30283-144">Kolejka stanu zamówienia jest tworzona w `Main` metodzie.</span><span class="sxs-lookup"><span data-stu-id="30283-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="30283-145">Konfiguracja klienta zawiera konfigurację usługi stanu zamówienia do hostowania usługi stanu zamówienia, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="30283-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
</appSettings>  
  
<system.serviceModel>  
  
  <services>  
    <service
       name="Microsoft.ServiceModel.Samples.OrderStatusService">  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
    </service>  
  </services>  
  
  <client>  
    <!-- Define NetMsmqEndpoint -->  
    <endpoint name="OrderProcessorEndpoint"  
              address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
              binding="netMsmqBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
  </client>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="30283-146">Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="30283-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="30283-147">Możesz zobaczyć, że usługa odbiera komunikaty od klienta.</span><span class="sxs-lookup"><span data-stu-id="30283-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="30283-148">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="30283-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="30283-149">Usługa wyświetla informacje o zamówieniach zakupu i wskazuje, że wysyła stan zamówienia do kolejki stanu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="30283-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 124a1f69-3699-4b16-9bcc-43147a8756fc  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Sending back order status information  
```  
  
 <span data-ttu-id="30283-150">Klient wyświetla informacje o stanie zamówienia wysyłane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="30283-150">The client displays the order status information sent by the service.</span></span>  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="30283-151">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="30283-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="30283-152">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="30283-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="30283-153">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="30283-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="30283-154">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="30283-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="30283-155">Jeśli używasz programu Svcutil. exe do ponownego wygenerowania konfiguracji dla tego przykładu, pamiętaj o zmodyfikowaniu nazw punktów końcowych w konfiguracji klienta, aby odpowiadały kodowi klienta.</span><span class="sxs-lookup"><span data-stu-id="30283-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="30283-156">Domyślnie z opcją <xref:System.ServiceModel.NetMsmqBinding> jest włączona funkcja zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="30283-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="30283-157">Istnieją dwie istotne właściwości zabezpieczenia transportu usługi MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` tryb uwierzytelniania jest ustawiony na wartość, `Windows` a poziom ochrony jest ustawiony na `Sign` .</span><span class="sxs-lookup"><span data-stu-id="30283-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="30283-158">Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny, a dla usługi MSMQ należy zainstalować opcję Integracja z usługą Active Directory.</span><span class="sxs-lookup"><span data-stu-id="30283-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="30283-159">Jeśli ten przykład zostanie uruchomiony na komputerze, który nie spełnia tych kryteriów, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="30283-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="30283-160">Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej lub bez integracji z usługą Active Directory</span><span class="sxs-lookup"><span data-stu-id="30283-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="30283-161">Jeśli komputer nie jest częścią domeny lub nie zainstalowano integracji z usługą Active Directory, Wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom ochrony `None` tak jak pokazano w poniższej konfiguracji przykładowej:</span><span class="sxs-lookup"><span data-stu-id="30283-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <configuration>  
  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderProcessor" />  
      </appSettings>  
  
      <system.serviceModel>  
        <services>  
          <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding"
                      contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
2. <span data-ttu-id="30283-162">Wyłączenie zabezpieczeń konfiguracji klienta spowoduje wygenerowanie następujących danych:</span><span class="sxs-lookup"><span data-stu-id="30283-162">Turning off security for a client configuration generates the following:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
      </appSettings>  
  
      <system.serviceModel>  
  
        <services>  
          <service
             name="Microsoft.ServiceModel.Samples.OrderStatusService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding" contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
          </service>  
        </services>  
  
        <client>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint name="OrderProcessorEndpoint"  
                    address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
                    binding="netMsmqBinding"
                    bindingConfiguration="TransactedBinding"  
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        </client>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
3. <span data-ttu-id="30283-163">Usługa dla tego przykładu tworzy powiązanie w `OrderProcessorService` .</span><span class="sxs-lookup"><span data-stu-id="30283-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="30283-164">Dodaj wiersz kodu po utworzeniu powiązania, aby ustawić tryb zabezpieczeń `None` .</span><span class="sxs-lookup"><span data-stu-id="30283-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. <span data-ttu-id="30283-165">Przed uruchomieniem przykładu należy zmienić konfigurację na serwerze i kliencie programu.</span><span class="sxs-lookup"><span data-stu-id="30283-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="30283-166">Ustawienie `security mode` odpowiada `None` ustawieniu <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> lub `Message` zabezpieczenia na `None` .</span><span class="sxs-lookup"><span data-stu-id="30283-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="30283-167">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="30283-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="30283-168">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="30283-168">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="30283-169">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="30283-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="30283-170">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="30283-170">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
