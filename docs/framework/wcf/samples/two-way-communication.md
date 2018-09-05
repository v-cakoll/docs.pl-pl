---
title: Komunikacja dwukierunkowa
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 319b63ff1eefdab4c23932294c3f1970f204601e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43539423"
---
# <a name="two-way-communication"></a><span data-ttu-id="2e209-102">Komunikacja dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="2e209-102">Two-Way Communication</span></span>
<span data-ttu-id="2e209-103">Niniejszy przykład pokazuje sposób wykonywania transakcyjne dwukierunkowej komunikacji w kolejce za pośrednictwem usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="2e209-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="2e209-104">W tym przykładzie użyto `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="2e209-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="2e209-105">W tym przypadku usługa jest aplikacja konsolowa samodzielnie hostowanej która pozwala obserwować usługę otrzymywania wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="2e209-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e209-106">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2e209-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2e209-107">Ten przykład jest oparty na [dokonana transakcja powiązania usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="2e209-107">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="2e209-108">W komunikacie w kolejce klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="2e209-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="2e209-109">Klient wysyła komunikaty do kolejki, a usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="2e209-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="2e209-110">Usługi i klienta w związku z tym, nie musi być uruchomiona w tym samym czasie do komunikowania się za pomocą kolejki.</span><span class="sxs-lookup"><span data-stu-id="2e209-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="2e209-111">Niniejszy przykład pokazuje sposób 2 komunikacji przy użyciu funkcji kolejek.</span><span class="sxs-lookup"><span data-stu-id="2e209-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="2e209-112">Klient wysyła zamówienia zakupu w kolejce z zakresu transakcji.</span><span class="sxs-lookup"><span data-stu-id="2e209-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="2e209-113">Usługa odbiera zamówienia, przetworzy to zamówienie, a następnie wywołuje ponownie klienta z stan zamówienia z kolejki w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="2e209-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="2e209-114">Ułatwianie dwukierunkowej komunikacji klienta i usługi użyj kolejki, aby umieścić zakupów i stanu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="2e209-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="2e209-115">Kontrakt usługi `IOrderProcessor` definiuje operacje usługi jednokierunkowej, spełniające użycie usługi kolejkowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2e209-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="2e209-116">Operacja usługi zawiera punkt końcowy odpowiedź do wysłania stanów zlecenia do.</span><span class="sxs-lookup"><span data-stu-id="2e209-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="2e209-117">Punkt końcowy odpowiedzi jest identyfikator URI kolejki wysyłania stan zamówienia do klienta.</span><span class="sxs-lookup"><span data-stu-id="2e209-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="2e209-118">Kolejność przetwarzania aplikacji implementuje ten kontrakt.</span><span class="sxs-lookup"><span data-stu-id="2e209-118">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="2e209-119">Kontrakt odpowiedź do wysłania stan zamówienia jest określony przez klienta.</span><span class="sxs-lookup"><span data-stu-id="2e209-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="2e209-120">Klient implementuje ten kontrakt stan zamówienia.</span><span class="sxs-lookup"><span data-stu-id="2e209-120">The client implements the order status contract.</span></span> <span data-ttu-id="2e209-121">Usługa używa wygenerowany serwer proxy niniejszej Umowy do odesłania stan zamówienia do klienta.</span><span class="sxs-lookup"><span data-stu-id="2e209-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="2e209-122">Operacja usługi przetworzy to zamówienie zakupu przesłane.</span><span class="sxs-lookup"><span data-stu-id="2e209-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="2e209-123"><xref:System.ServiceModel.OperationBehaviorAttribute> Jest stosowany do operacji usługi, aby określić automatycznej rejestracji w transakcji, która umożliwia odbieranie wiadomości z kolejki i automatycznego uzupełniania transakcji po zakończeniu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="2e209-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="2e209-124">`Orders` Klasa hermetyzuje funkcjonalność przetwarzania zamówienia.</span><span class="sxs-lookup"><span data-stu-id="2e209-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="2e209-125">W tym przypadku dodaje zamówienia zakupu w słowniku.</span><span class="sxs-lookup"><span data-stu-id="2e209-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="2e209-126">Operacja usługi zarejestrowany w transakcji jest dostępna dla operacji w `Orders` klasy.</span><span class="sxs-lookup"><span data-stu-id="2e209-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="2e209-127">Operacja usługi, oprócz przetwarzania zamówienia zakupu przesłanych odpowiedzi do klienta na stan zamówienia.</span><span class="sxs-lookup"><span data-stu-id="2e209-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

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

 <span data-ttu-id="2e209-128">Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2e209-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="2e209-129">Punkt końcowy usługi jest zdefiniowany w sekcji System.ServiceModel pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2e209-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e209-130">Adres nazwy i punkt końcowy kolejki usługi MSMQ Użyj nieco Konwencji adresowania.</span><span class="sxs-lookup"><span data-stu-id="2e209-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="2e209-131">Nazwa kolejki usługi MSMQ używa pojedynczego znaku kropki (.) dla lokalnego separatory maszyny i ukośnika odwrotnego w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="2e209-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="2e209-132">Adres punktu końcowego usługi Windows Communication Foundation (WCF) określa net.msmq: schemat, używa "localhost" dla komputera lokalnego i korzysta z ukośników w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="2e209-132">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="2e209-133">Aby odczytać z kolejki, która znajduje się na komputerze zdalnym, zastąp "." i "localhost", aby nazwy maszyny zdalnej.</span><span class="sxs-lookup"><span data-stu-id="2e209-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="2e209-134">Usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="2e209-134">The service is self hosted.</span></span> <span data-ttu-id="2e209-135">Za pomocą transportu MSMQ, kolejki, używane musi zostać utworzona wcześniej.</span><span class="sxs-lookup"><span data-stu-id="2e209-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="2e209-136">Można to zrobić ręcznie lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="2e209-136">This can be done manually or through code.</span></span> <span data-ttu-id="2e209-137">W tym przykładzie usługa sprawdza istnienie kolejki i utworzy go, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="2e209-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="2e209-138">Nazwa kolejki jest do odczytu z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2e209-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="2e209-139">Adres podstawowy jest używany przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania serwera proxy do usługi.</span><span class="sxs-lookup"><span data-stu-id="2e209-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

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

 <span data-ttu-id="2e209-140">Klient tworzy transakcji.</span><span class="sxs-lookup"><span data-stu-id="2e209-140">The client creates a transaction.</span></span> <span data-ttu-id="2e209-141">Komunikacja z kolejką odbywa się w zakresie transakcji, co powoduje powinien być traktowany jako pojedynczej Atomowej jednostki, której wszystkie komunikaty sukces lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="2e209-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

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

 <span data-ttu-id="2e209-142">Kod klienta implementuje `IOrderStatus` umowę odbierać stan zamówienia z usługi.</span><span class="sxs-lookup"><span data-stu-id="2e209-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="2e209-143">W tym przypadku wyświetla się stan zamówienia.</span><span class="sxs-lookup"><span data-stu-id="2e209-143">In this case, it prints out the order status.</span></span>  

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

 <span data-ttu-id="2e209-144">Kolejkę stanu zamówienia jest tworzony w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="2e209-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="2e209-145">Konfiguracja klienta obejmuje konfigurację usługi stanu zamówienia do hostowania usługi stanu zamówienia, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="2e209-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="2e209-146">Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="2e209-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="2e209-147">Możesz zobaczyć komunikaty odbierania usługi z klienta.</span><span class="sxs-lookup"><span data-stu-id="2e209-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="2e209-148">Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="2e209-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="2e209-149">Usługa Wyświetla informacje o zamówieniu zakupu i wskazuje, że wysyła ponownie stan zamówienia w kolejce stan zamówienia.</span><span class="sxs-lookup"><span data-stu-id="2e209-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
```  
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
  
 <span data-ttu-id="2e209-150">Klient Wyświetla informacje o stanie zamówienia, które zostały wysłane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="2e209-150">The client displays the order status information sent by the service.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2e209-151">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="2e209-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2e209-152">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e209-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="2e209-153">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e209-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="2e209-154">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e209-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2e209-155">Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwy punktów końcowych w konfiguracji klienta, aby dopasować kod klienta.</span><span class="sxs-lookup"><span data-stu-id="2e209-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="2e209-156">Domyślnie <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczenia transportu jest włączona.</span><span class="sxs-lookup"><span data-stu-id="2e209-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="2e209-157">Istnieją dwie właściwości istotnych dla zabezpieczeń transportu usługi MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` domyślny tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="2e209-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="2e209-158">Dla usługi MSMQ zapewniać uwierzytelnianie i podpisywania funkcji musi być częścią domeny i musi być zainstalowany opcji integracji usługi active directory dla usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="2e209-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="2e209-159">Jeśli w tym przykładzie jest uruchomiony na komputerze, który nie spełnia tych kryteriów otrzymasz komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="2e209-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="2e209-160">Do uruchomienia przykładu na komputer przyłączony do grupy roboczej lub bez integracji usługi active directory</span><span class="sxs-lookup"><span data-stu-id="2e209-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="2e209-161">Jeśli komputer nie jest częścią domeny lub nie ma zainstalowaną integracją usługi active directory, należy wyłączyć zabezpieczenia transportu, ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższym Przykładowa konfiguracja:</span><span class="sxs-lookup"><span data-stu-id="2e209-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
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
  
2.  <span data-ttu-id="2e209-162">Wyłączenie zabezpieczeń dla konfiguracji klienta generuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="2e209-162">Turning off security for a client configuration generates the following:</span></span>  
  
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
  
3.  <span data-ttu-id="2e209-163">Usługi w tym przykładzie tworzy powiązanie w `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="2e209-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="2e209-164">Dodaj wiersz kodu po wiązanie zostanie uruchomiony, aby ustawić tryb zabezpieczeń `None`.</span><span class="sxs-lookup"><span data-stu-id="2e209-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4.  <span data-ttu-id="2e209-165">Upewnij się, zmień konfigurację serwera i klienta, przed uruchomieniem przykładu.</span><span class="sxs-lookup"><span data-stu-id="2e209-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2e209-166">Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> lub `Message` security `None`.</span><span class="sxs-lookup"><span data-stu-id="2e209-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2e209-167">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2e209-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2e209-168">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2e209-168">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2e209-169">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="2e209-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e209-170">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2e209-170">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
  
## <a name="see-also"></a><span data-ttu-id="2e209-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e209-171">See Also</span></span>
