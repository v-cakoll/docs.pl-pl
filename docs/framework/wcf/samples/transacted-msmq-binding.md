---
title: Transakcyjne powiązanie MSMQ
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: 381304bcef40245bac882a4fe4ae18a6998665cf
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085095"
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="45248-102">Transakcyjne powiązanie MSMQ</span><span class="sxs-lookup"><span data-stu-id="45248-102">Transacted MSMQ Binding</span></span>
<span data-ttu-id="45248-103">W tym przykładzie pokazano, jak wykonać transakcyjnych w kolejce komunikacji przy użyciu usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="45248-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45248-104">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="45248-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="45248-105">W komunikacie w kolejce klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="45248-105">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="45248-106">Mówiąc ściślej klient wysyła komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="45248-106">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="45248-107">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="45248-107">The service receives messages from the queue.</span></span> <span data-ttu-id="45248-108">Usługi i klienta, więc nie musi być uruchomiona w tym samym czasie do komunikowania się za pomocą kolejki.</span><span class="sxs-lookup"><span data-stu-id="45248-108">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="45248-109">Jeśli transakcje są używane do wysyłania i odbierania komunikatów, są faktycznie dwóch oddzielnych transakcji.</span><span class="sxs-lookup"><span data-stu-id="45248-109">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="45248-110">Gdy klient wysyła komunikaty w zakresie transakcji, transakcja jest lokalny dla klienta i Menedżer kolejki klienta.</span><span class="sxs-lookup"><span data-stu-id="45248-110">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="45248-111">Gdy usługa odbiera komunikaty w zakresie transakcji, transakcja jest lokalnego do usługi i odbieranie Menedżer kolejki.</span><span class="sxs-lookup"><span data-stu-id="45248-111">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="45248-112">Jest bardzo ważne, należy pamiętać, że klient i usługa nie uczestniczą w tej samej transakcji; przeciwnie używają różnych transakcji podczas ich działania (takie jak wysyłanie i odbieranie) z kolejką.</span><span class="sxs-lookup"><span data-stu-id="45248-112">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>  
  
 <span data-ttu-id="45248-113">W tym przykładzie klient wysyła komunikaty zbiorczo do usługi z zakresu transakcji.</span><span class="sxs-lookup"><span data-stu-id="45248-113">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="45248-114">Komunikaty wysyłane do kolejki następnie są odbierane przez usługę w zakresie transakcji, zdefiniowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="45248-114">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>  
  
 <span data-ttu-id="45248-115">Umowa serwisowa jest `IOrderProcessor`, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="45248-115">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="45248-116">Interfejs definiuje usługi jednokierunkowej, który jest odpowiedni do użytku z kolejki.</span><span class="sxs-lookup"><span data-stu-id="45248-116">The interface defines a one-way service that is suitable for use with queues.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 <span data-ttu-id="45248-117">Zachowanie usługi definiuje zachowanie operacji za pomocą `TransactionScopeRequired` równa `true`.</span><span class="sxs-lookup"><span data-stu-id="45248-117">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="45248-118">Gwarantuje to, że ten sam zakres transakcji, który służy do pobierania komunikatu z kolejki jest używany przez wszystkie menedżerów zasobów uzyskiwał dostęp do metody.</span><span class="sxs-lookup"><span data-stu-id="45248-118">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="45248-119">Gwarantuje również, że jeśli metoda zgłasza wyjątek, zwracany jest komunikat do kolejki.</span><span class="sxs-lookup"><span data-stu-id="45248-119">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="45248-120">Bez ustawienia tego zachowania operacji, kanał umieszczonych w kolejce tworzy transakcji, aby odczytać wiadomość z kolejki i zatwierdzeń go automatycznie przed wysyłką tak, jeśli operacja nie powiedzie się, komunikat zostanie utracony.</span><span class="sxs-lookup"><span data-stu-id="45248-120">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="45248-121">Najbardziej typowym scenariuszem jest dla operacji usługi można zarejestrować w transakcji, który jest używany do odczytu komunikatu z kolejki, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="45248-121">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>  

```csharp
 // This service class that implements the service contract.  
 // This added code writes output to the console window.  
 public class OrderProcessorService : IOrderProcessor  
 {  
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
     public void SubmitPurchaseOrder(PurchaseOrder po)  
     {  
         Orders.Add(po);  
         Console.WriteLine("Processing {0} ", po);  
     }  
  …  
}  
```

 <span data-ttu-id="45248-122">Usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="45248-122">The service is self hosted.</span></span> <span data-ttu-id="45248-123">Za pomocą transportu MSMQ, kolejki, używane musi zostać utworzona wcześniej.</span><span class="sxs-lookup"><span data-stu-id="45248-123">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="45248-124">Można to zrobić ręcznie lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="45248-124">This can be done manually or through code.</span></span> <span data-ttu-id="45248-125">W tym przykładzie Usługa zawiera kod, aby sprawdzić istnienia kolejki i utworzyć kolejkę, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="45248-125">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="45248-126">Nazwa kolejki jest do odczytu z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="45248-126">The queue name is read from the configuration file.</span></span> <span data-ttu-id="45248-127">Adres podstawowy jest używany przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania serwera proxy do usługi.</span><span class="sxs-lookup"><span data-stu-id="45248-127">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get the MSMQ queue name from appSettings in configuration.  
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
  
        // Close the ServiceHost to shut down the service.  
        serviceHost.Close();  
    }  
}  
```

 <span data-ttu-id="45248-128">Nazwa kolejki usługi MSMQ jest określony w sekcji appSettings pliku konfiguracji, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="45248-128">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="45248-129">Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnik odwrotny w ścieżce do utworzenia przy użyciu kolejki <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="45248-129">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="45248-130">Punkt końcowy usługi Windows Communication Foundation (WCF) używa adresu kolejki ze schematem net.msmq używa "localhost" do określenia komputera lokalnego i używa ukośników w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="45248-130">The Windows Communication Foundation (WCF) endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>  
  
 <span data-ttu-id="45248-131">Klient tworzy zakres transakcji.</span><span class="sxs-lookup"><span data-stu-id="45248-131">The client creates a transaction scope.</span></span> <span data-ttu-id="45248-132">Komunikacja z kolejką odbywa się w zakresie transakcji, co powoduje powinien być traktowany jako pojedynczej Atomowej jednostki, w którym wszystkie komunikaty są wysyłane do kolejki lub żadne komunikaty są wysyłane do kolejki.</span><span class="sxs-lookup"><span data-stu-id="45248-132">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="45248-133">Transakcja została zatwierdzona przez wywołanie metody <xref:System.Transactions.TransactionScope.Complete%2A> w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="45248-133">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>  

```csharp
// Create a client.  
OrderProcessorClient client = new OrderProcessorClient();  
  
// Create the purchase order.  
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
  
// Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Make a queued call to submit the purchase order.  
    client.SubmitPurchaseOrder(po);  
    // Complete the transaction.  
    scope.Complete();  
}  
  
// Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```

 <span data-ttu-id="45248-134">Aby sprawdzić, czy działają transakcji, zmodyfikować klienta, oznaczając zakresu transakcji, jak pokazano w poniższym przykładowym kodzie, ponownie skompiluj rozwiązanie i uruchomić klienta.</span><span class="sxs-lookup"><span data-stu-id="45248-134">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>  

```csharp
//scope.Complete();  
```

 <span data-ttu-id="45248-135">Ponieważ transakcja nie jest zakończona, nie są wysyłane komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="45248-135">Because the transaction is not completed, the messages are not sent to the queue.</span></span>  
  
 <span data-ttu-id="45248-136">Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="45248-136">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="45248-137">Możesz zobaczyć komunikaty odbierania usługi z klienta.</span><span class="sxs-lookup"><span data-stu-id="45248-137">You can see the service receive messages from the client.</span></span> <span data-ttu-id="45248-138">Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="45248-138">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="45248-139">Należy zauważyć, że ponieważ kolejkowania wiadomości jest używany, klient i usługa musi być uruchomiona w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="45248-139">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="45248-140">Można uruchomić klienta, zamknij go, a następnie uruchom usługi i wciąż otrzymuje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="45248-140">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="45248-141">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="45248-141">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="45248-142">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45248-142">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="45248-143">Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny.</span><span class="sxs-lookup"><span data-stu-id="45248-143">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="45248-144">Jeśli kolejka nie jest obecny, będzie utworzyć usługę.</span><span class="sxs-lookup"><span data-stu-id="45248-144">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="45248-145">Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="45248-145">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="45248-146">Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="45248-146">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="45248-147">Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45248-147">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="45248-148">Rozwiń **funkcji** kartę.</span><span class="sxs-lookup"><span data-stu-id="45248-148">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="45248-149">Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="45248-149">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="45248-150">Sprawdź **transakcyjna** pole.</span><span class="sxs-lookup"><span data-stu-id="45248-150">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="45248-151">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="45248-151">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="45248-152">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45248-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="45248-153">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45248-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="45248-154">Domyślnie <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczenia transportu jest włączona.</span><span class="sxs-lookup"><span data-stu-id="45248-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="45248-155">Istnieją dwie właściwości istotnych dla zabezpieczeń transportu usługi MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="45248-155">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="45248-156">Domyślnie, tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="45248-156">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="45248-157">Dla usługi MSMQ zapewniać uwierzytelnianie i podpisywania funkcji musi być częścią domeny i musi być zainstalowany opcji integracji usługi Active Directory dla usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="45248-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="45248-158">Jeśli w tym przykładzie jest uruchomiony na komputerze, który nie spełnia tych kryteriów, otrzymasz komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="45248-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="45248-159">Do uruchomienia przykładu na komputer przyłączony do grupy roboczej lub bez integracji usługi Active Directory</span><span class="sxs-lookup"><span data-stu-id="45248-159">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>  
  
1.  <span data-ttu-id="45248-160">Jeśli komputer nie jest częścią domeny lub nie ma zainstalowaną integracją usługi Active Directory, należy wyłączyć zabezpieczenia transportu, ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższym kodzie przykładowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="45248-160">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"  
                 behaviorConfiguration="OrderProcessorServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint. -->  
          <endpoint  
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <!-- The mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex. -->  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="OrderProcessorServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="45248-161">Upewnij się, zmień konfigurację serwera i klienta, przed uruchomieniem przykładu.</span><span class="sxs-lookup"><span data-stu-id="45248-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="45248-162">Ustawienie `security``mode` do `None` jest odpowiednikiem ustawienia <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, i `Message` security `None`.</span><span class="sxs-lookup"><span data-stu-id="45248-162">Setting `security``mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="45248-163">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="45248-163">The samples may already be installed on your computer.</span></span> <span data-ttu-id="45248-164">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="45248-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="45248-165">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="45248-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="45248-166">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="45248-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`  
  
## <a name="see-also"></a><span data-ttu-id="45248-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45248-167">See Also</span></span>
