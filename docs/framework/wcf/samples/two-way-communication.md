---
title: Komunikacja dwukierunkowa
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d17c9c97e98a62cf0cbda38bae4adad32c4b5eae
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="two-way-communication"></a><span data-ttu-id="ecf5a-102">Komunikacja dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="ecf5a-102">Two-Way Communication</span></span>
<span data-ttu-id="ecf5a-103">W tym przykładzie pokazano, jak wykonać transakcyjne dwukierunkowej komunikacji w kolejce przez usługę MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="ecf5a-104">W przykładzie użyto `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="ecf5a-105">W takim przypadku usługa jest aplikacji konsoli siebie umożliwiający obserwowanie usługi odbieranie wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecf5a-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ecf5a-107">Ten przykład jest oparty na [nietransakcyjnego powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="ecf5a-107">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="ecf5a-108">W kolejce komunikacji klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="ecf5a-109">Klient wysyła wiadomości do kolejki, a usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="ecf5a-110">Usługi i klienta w związku z tym ma być uruchomiona, w tym samym czasie do komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="ecf5a-111">W przykładzie pokazano sposób 2 komunikacji przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="ecf5a-112">Klient wysyła zakupów do kolejki w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="ecf5a-113">Usługa odbiera zamówienia, przetwarza kolejność i następnie wywołuje klienta z stan zlecenia z kolejki w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="ecf5a-114">Aby ułatwić dwukierunkowej komunikacji klienta i usługi użyj kolejki, aby umieścić w kolejce zakupów i stanu zlecenia.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="ecf5a-115">Kontrakt usługi `IOrderProcessor` definiuje operacje usługi jednokierunkowej, spełniającej korzystanie z usługi kolejkowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="ecf5a-116">Operacja usługi zawiera punkt końcowy odpowiedzi do stanów zlecenia do wysłania.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="ecf5a-117">Punkt końcowy odpowiedzi jest identyfikator URI kolejki do odesłania do klienta stan zlecenia.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="ecf5a-118">Kolejność przetwarzania aplikacji implementuje tego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-118">The order processing application implements this contract.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}  
```  
  
 <span data-ttu-id="ecf5a-119">Kontrakt odpowiedź do wysłania stanu zlecenia jest określony przez klienta.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="ecf5a-120">Klient implementuje kontraktu stan zlecenia.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-120">The client implements the order status contract.</span></span> <span data-ttu-id="ecf5a-121">Usługa używa tego kontraktu wygenerowany serwer proxy do odesłania do klienta stan zlecenia.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  
  
```  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 <span data-ttu-id="ecf5a-122">Operacja usługi przetwarza zamówienia zakupu zostało przesłane.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="ecf5a-123"><xref:System.ServiceModel.OperationBehaviorAttribute> Jest stosowany do operacji usługi, aby określić automatycznej rejestracji w transakcji, która służy do odbierania wiadomości z kolejki i automatycznego uzupełniania transakcji po zakończeniu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="ecf5a-124">`Orders` Klasa hermetyzuje funkcjonalność przetwarzania zamówienia.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="ecf5a-125">W takim przypadku dodaje zamówienie do słownika.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="ecf5a-126">Operacja usługi jest zarejestrowana w transakcji jest dostępny do operacji w `Orders` klasy.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="ecf5a-127">Operacja usługi, oprócz przetwarzania zamówienia zakupu zostało przesłane odpowiedzi do klienta na stan zlecenia.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  
  
```  
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
  
 <span data-ttu-id="ecf5a-128">Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="ecf5a-129">Punkt końcowy usługi jest zdefiniowany w sekcji System.ServiceModel pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecf5a-130">Adres nazwy i punktu końcowego kolejki usługi MSMQ Użyj konwencji adresowania nieco inne.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="ecf5a-131">Nazwa kolejki usługi MSMQ używa pojedynczego znaku kropki (.) dla lokalnych separatory maszyny i ukośnika w jego ścieżki.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="ecf5a-132">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Net.msmq Określa adres punktu końcowego: schemat, korzysta "localhost" na komputerze lokalnym, a ukośniki w swojej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-132">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="ecf5a-133">Aby odczytać z kolejki znajdującej się na komputerze zdalnym, zastąp "." i "localhost" na nazwę komputera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="ecf5a-134">Usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-134">The service is self hosted.</span></span> <span data-ttu-id="ecf5a-135">Za pomocą transportu MSMQ, kolejki używane musi zostać utworzona z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="ecf5a-136">Można to zrobić ręcznie lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-136">This can be done manually or through code.</span></span> <span data-ttu-id="ecf5a-137">W tym przykładzie usługa sprawdza istnienie kolejki i tworzy, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="ecf5a-138">Nazwa kolejki jest do odczytu z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="ecf5a-139">Adres podstawowy jest używany przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania serwera proxy do usługi.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="ecf5a-140">Klient tworzy transakcję.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-140">The client creates a transaction.</span></span> <span data-ttu-id="ecf5a-141">Komunikacja z kolejki odbywa się w zakresie transakcji, co powoduje traktowane jako Atomowej jednostki, w którym wszystkie komunikaty powodzenie lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  
  
```  
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
  
 <span data-ttu-id="ecf5a-142">Kod klienta implementuje `IOrderStatus` kontraktu do odbierania stanu zlecenia z usługi.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="ecf5a-143">W takim przypadku wyświetla się stan zlecenia.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-143">In this case, it prints out the order status.</span></span>  
  
```  
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
  
 <span data-ttu-id="ecf5a-144">Kolejność kolejkę stanu jest tworzony w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="ecf5a-145">Konfiguracja klienta obejmuje konfiguracji kolejności stanu usługi do obsługi usługi stanu kolejności, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="ecf5a-146">Po uruchomieniu próbki działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ecf5a-147">Można wyświetlić wiadomości receive usługi z klienta.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="ecf5a-148">Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="ecf5a-149">Usługa Wyświetla informacje o zamówieniu zakupu i wskazuje, że jego odsyła stan zlecenia do kolejki stanu kolejności.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
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
  
 <span data-ttu-id="ecf5a-150">Klient jest wyświetlany kolejności informacje o stanie wysyłane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-150">The client displays the order status information sent by the service.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ecf5a-151">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="ecf5a-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ecf5a-152">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ecf5a-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ecf5a-153">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ecf5a-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ecf5a-154">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ecf5a-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ecf5a-155">Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwy punktu końcowego w konfiguracji klienta, aby dopasować kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="ecf5a-156">Domyślnie z <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczeń transportu jest włączona.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="ecf5a-157">Istnieją dwa odpowiednie właściwości dla zabezpieczeń transportu MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` domyślnie tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="ecf5a-158">Dla usługi MSMQ w celu zapewnienia uwierzytelniania oraz podpisywania funkcji musi być częścią domeny, a opcja integracji usługi active directory dla usługi MSMQ musi być zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="ecf5a-159">Jeśli w tym przykładzie jest uruchomiony na komputerze, który nie spełnia te kryteria, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="ecf5a-160">Aby uruchomić na komputerze, na przykład dołączona do grupy roboczej lub bez integracji z usługą active directory</span><span class="sxs-lookup"><span data-stu-id="ecf5a-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="ecf5a-161">Jeśli komputer nie jest częścią domeny lub nie ma zainstalowanych integracji usługi active directory, należy wyłączyć zabezpieczeń transportu przez ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższych Przykładowa konfiguracja:</span><span class="sxs-lookup"><span data-stu-id="ecf5a-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
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
  
2.  <span data-ttu-id="ecf5a-162">Wyłączenie zabezpieczeń dla konfiguracji klienta generuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ecf5a-162">Turning off security for a client configuration generates the following:</span></span>  
  
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
  
3.  <span data-ttu-id="ecf5a-163">Usługi dla tego przykładu tworzy powiązanie w `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="ecf5a-164">Dodaj wiersz kodu po wiązanie zostanie uruchomiony, aby ustawić tryb zabezpieczeń `None`.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4.  <span data-ttu-id="ecf5a-165">Sprawdź, czy zmian konfiguracji na serwerze i kliencie, przed uruchomieniem próbki.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ecf5a-166">Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> lub `Message` zabezpieczeń do `None`.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ecf5a-167">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ecf5a-168">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ecf5a-168">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ecf5a-169">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ecf5a-170">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ecf5a-170">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
  
## <a name="see-also"></a><span data-ttu-id="ecf5a-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecf5a-171">See Also</span></span>
