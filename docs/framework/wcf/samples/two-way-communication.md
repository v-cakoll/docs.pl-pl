---
title: Komunikacja dwukierunkowa
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 56f789fe185cb2885c215e9512e82ae2fbb64a36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143762"
---
# <a name="two-way-communication"></a><span data-ttu-id="cc10a-102">Komunikacja dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="cc10a-102">Two-Way Communication</span></span>
<span data-ttu-id="cc10a-103">W tym przykładzie pokazano, jak wykonać transacted dwukierunkowej komunikacji w kolejce za sprawą usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="cc10a-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="cc10a-104">W tym przykładzie użyto `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="cc10a-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="cc10a-105">W takim przypadku usługa jest samodzielną aplikacją konsoli, która umożliwia obserwowanie usługi odbierającej wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="cc10a-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc10a-106">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cc10a-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cc10a-107">Ten przykład jest oparty na [powiązaniu Z MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)transakcji .</span><span class="sxs-lookup"><span data-stu-id="cc10a-107">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="cc10a-108">W komunikacji w kolejce klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="cc10a-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="cc10a-109">Klient wysyła wiadomości do kolejki, a usługa odbiera wiadomości z kolejki.</span><span class="sxs-lookup"><span data-stu-id="cc10a-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="cc10a-110">W związku z tym usługi i klienta, nie muszą być uruchomione w tym samym czasie do komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="cc10a-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="cc10a-111">W tym przykładzie pokazano komunikacji dwukierunkowej przy użyciu kolejek.</span><span class="sxs-lookup"><span data-stu-id="cc10a-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="cc10a-112">Klient wysyła zamówienia zakupu do kolejki z zakresu transakcji.</span><span class="sxs-lookup"><span data-stu-id="cc10a-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="cc10a-113">Usługa odbiera zamówienia, przetwarza zamówienie, a następnie odwołuje klienta ze stanem zamówienia z kolejki w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="cc10a-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="cc10a-114">Aby ułatwić komunikację dwukierunkową, klient i usługa używają kolejek do umieszczania w kolejce zamówień zakupu i stanu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="cc10a-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="cc10a-115">Umowa serwisowa `IOrderProcessor` definiuje jednokierunkowe operacje serwisowe, które odpowiadają użyciu kolejkowania.</span><span class="sxs-lookup"><span data-stu-id="cc10a-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="cc10a-116">Operacja usługi obejmuje punkt końcowy odpowiedzi, który służy do wysyłania stanów zamówienia.</span><span class="sxs-lookup"><span data-stu-id="cc10a-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="cc10a-117">Punkt końcowy odpowiedzi jest identyfikatorem URI kolejki, aby wysłać stan zamówienia z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="cc10a-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="cc10a-118">Aplikacja do przetwarzania zamówień implementuje tę umowę.</span><span class="sxs-lookup"><span data-stu-id="cc10a-118">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="cc10a-119">Kontrakt odpowiedzi do wysłania stanu zamówienia jest określony przez klienta.</span><span class="sxs-lookup"><span data-stu-id="cc10a-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="cc10a-120">Klient implementuje kontrakt o stanie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="cc10a-120">The client implements the order status contract.</span></span> <span data-ttu-id="cc10a-121">Usługa używa wygenerowanego serwera proxy tej umowy, aby wysłać stan zamówienia z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="cc10a-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="cc10a-122">Operacja serwisowa przetwarza przesłane zamówienie zakupu.</span><span class="sxs-lookup"><span data-stu-id="cc10a-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="cc10a-123">Jest <xref:System.ServiceModel.OperationBehaviorAttribute> stosowany do operacji usługi, aby określić automatyczne rejestrowanie w transakcji, która jest używana do odbierania wiadomości z kolejki i automatycznego zakończenia transakcji po zakończeniu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="cc10a-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="cc10a-124">Klasa `Orders` hermetyzuje funkcje przetwarzania zamówień.</span><span class="sxs-lookup"><span data-stu-id="cc10a-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="cc10a-125">W takim przypadku dodaje zamówienie zakupu do słownika.</span><span class="sxs-lookup"><span data-stu-id="cc10a-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="cc10a-126">Transakcja, w którą zarejestrowano operację usługi, jest `Orders` dostępna dla operacji w klasie.</span><span class="sxs-lookup"><span data-stu-id="cc10a-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="cc10a-127">Operacja usługi, oprócz przetwarzania przesłanego zamówienia zakupu, odpowiada klientowi na stan zamówienia.</span><span class="sxs-lookup"><span data-stu-id="cc10a-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

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

 <span data-ttu-id="cc10a-128">Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cc10a-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="cc10a-129">Punkt końcowy usługi jest zdefiniowany w sekcji System.ServiceModel pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="cc10a-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc10a-130">Nazwa kolejki usługi MSMQ i adres punktu końcowego używają nieco innych konwencji adresowania.</span><span class="sxs-lookup"><span data-stu-id="cc10a-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="cc10a-131">Nazwa kolejki usługi MSMQ używa kropki (.) dla komputera lokalnego i separatorów ukośnika odwrotnego w jego ścieżce.</span><span class="sxs-lookup"><span data-stu-id="cc10a-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="cc10a-132">Adres punktu końcowego Programu Komunikacji systemu Windows (WCF) określa schemat net.msmq: używa "localhost" dla komputera lokalnego i używa ukośników do przodu w swojej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="cc10a-132">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="cc10a-133">Aby odczytać z kolejki hostowanej na komputerze zdalnym, należy zastąpić "." i "localhost" nazwą komputera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="cc10a-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="cc10a-134">Usługa jest hostowana samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="cc10a-134">The service is self hosted.</span></span> <span data-ttu-id="cc10a-135">Podczas korzystania z transportu usługi MSMQ używana kolejka musi zostać utworzona z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="cc10a-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="cc10a-136">Można to zrobić ręcznie lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="cc10a-136">This can be done manually or through code.</span></span> <span data-ttu-id="cc10a-137">W tym przykładzie usługa sprawdza istnienie kolejki i tworzy go, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="cc10a-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="cc10a-138">Nazwa kolejki jest odczytywana z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cc10a-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="cc10a-139">Adres podstawowy jest używany przez [narzędzie narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania serwera proxy do usługi.</span><span class="sxs-lookup"><span data-stu-id="cc10a-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

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

 <span data-ttu-id="cc10a-140">Klient tworzy transakcję.</span><span class="sxs-lookup"><span data-stu-id="cc10a-140">The client creates a transaction.</span></span> <span data-ttu-id="cc10a-141">Komunikacja z kolejką odbywa się w zakresie transakcji, powodując, że jest traktowana jako jednostka niepodzielna, w której wszystkie wiadomości powiodą się lub nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="cc10a-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

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

 <span data-ttu-id="cc10a-142">Kod klienta implementuje `IOrderStatus` kontrakt, aby otrzymać stan zamówienia z usługi.</span><span class="sxs-lookup"><span data-stu-id="cc10a-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="cc10a-143">W takim przypadku drukuje stan zamówienia.</span><span class="sxs-lookup"><span data-stu-id="cc10a-143">In this case, it prints out the order status.</span></span>  

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

 <span data-ttu-id="cc10a-144">Kolejka stanu zamówienia jest `Main` tworzona w metodzie.</span><span class="sxs-lookup"><span data-stu-id="cc10a-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="cc10a-145">Konfiguracja klienta zawiera konfigurację usługi stanu zamówienia do obsługi usługi stanu zamówienia, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="cc10a-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="cc10a-146">Po uruchomieniu przykładu działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="cc10a-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="cc10a-147">Możesz zobaczyć, że usługa odbiera wiadomości od klienta.</span><span class="sxs-lookup"><span data-stu-id="cc10a-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="cc10a-148">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="cc10a-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="cc10a-149">Usługa wyświetla informacje o zamówieniu zakupu i wskazuje, że wysyła stan zamówienia z powrotem do kolejki stanu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="cc10a-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
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
  
 <span data-ttu-id="cc10a-150">Klient wyświetla informacje o stanie zamówienia wysyłane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="cc10a-150">The client displays the order status information sent by the service.</span></span>  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cc10a-151">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="cc10a-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cc10a-152">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cc10a-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cc10a-153">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cc10a-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cc10a-154">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cc10a-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cc10a-155">Jeśli używasz Svcutil.exe do ponownego wygenerowania konfiguracji dla tego przykładu, należy zmodyfikować nazwy punktów końcowych w konfiguracji klienta, aby dopasować kod klienta.</span><span class="sxs-lookup"><span data-stu-id="cc10a-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="cc10a-156">Domyślnie z <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczenia transportu jest włączona.</span><span class="sxs-lookup"><span data-stu-id="cc10a-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="cc10a-157">Istnieją dwie odpowiednie właściwości zabezpieczeń transportu usługi <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` MSMQ, a domyślnie `Windows` jest ustawiony na `Sign`tryb uwierzytelniania, a poziom ochrony jest ustawiony na .</span><span class="sxs-lookup"><span data-stu-id="cc10a-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="cc10a-158">Aby usługa MSMQ udostępniała funkcję uwierzytelniania i podpisywania, musi ona być częścią domeny, a opcja integracji usługi Active Directory dla usługi MSMQ musi być zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="cc10a-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="cc10a-159">Jeśli uruchomisz ten przykład na komputerze, który nie spełnia tych kryteriów, zostanie wyświetlony błąd.</span><span class="sxs-lookup"><span data-stu-id="cc10a-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="cc10a-160">Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej lub bez integracji z usługą Active Directory</span><span class="sxs-lookup"><span data-stu-id="cc10a-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="cc10a-161">Jeśli komputer nie należy do domeny lub nie ma zainstalowanej integracji z aktywną funkcją `None` katalogową, wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom ochrony na pokazano w poniższej przykładowej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="cc10a-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
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
  
2. <span data-ttu-id="cc10a-162">Wyłączenie zabezpieczeń dla konfiguracji klienta generuje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="cc10a-162">Turning off security for a client configuration generates the following:</span></span>  
  
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
  
3. <span data-ttu-id="cc10a-163">Usługa dla tego przykładu tworzy `OrderProcessorService`powiązanie w .</span><span class="sxs-lookup"><span data-stu-id="cc10a-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="cc10a-164">Dodaj wiersz kodu po utworzeniu wystąpienia powiązania, aby `None`ustawić tryb zabezpieczeń na .</span><span class="sxs-lookup"><span data-stu-id="cc10a-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. <span data-ttu-id="cc10a-165">Przed uruchomieniem przykładu upewnij się, że konfiguracja jest zmieniana zarówno na serwerze, jak i na kliencie.</span><span class="sxs-lookup"><span data-stu-id="cc10a-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cc10a-166">Ustawienie `security mode` `None` jest równoważne <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> z `Message` ustawieniem lub zabezpieczeniem `None`.</span><span class="sxs-lookup"><span data-stu-id="cc10a-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cc10a-167">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="cc10a-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cc10a-168">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="cc10a-168">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="cc10a-169">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="cc10a-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cc10a-170">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cc10a-170">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
