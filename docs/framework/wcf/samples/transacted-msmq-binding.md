---
title: Transakcyjne powiązanie MSMQ
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: a3592195f853dd97bf8e4351526bf0fff9ce78fd
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715631"
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="3c047-102">Transakcyjne powiązanie MSMQ</span><span class="sxs-lookup"><span data-stu-id="3c047-102">Transacted MSMQ Binding</span></span>

<span data-ttu-id="3c047-103">Ten przykład pokazuje, jak przeprowadzić komunikację z kolejką w kolejce przy użyciu usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="3c047-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>

> [!NOTE]
> <span data-ttu-id="3c047-104">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="3c047-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="3c047-105">W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="3c047-105">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="3c047-106">Dokładniej, klient wysyła komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="3c047-106">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="3c047-107">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="3c047-107">The service receives messages from the queue.</span></span> <span data-ttu-id="3c047-108">W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="3c047-108">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="3c047-109">Gdy transakcje są używane do wysyłania i odbierania wiadomości, istnieją w rzeczywistości dwie osobne transakcje.</span><span class="sxs-lookup"><span data-stu-id="3c047-109">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="3c047-110">Gdy klient wysyła komunikaty w zakresie transakcji, transakcja jest lokalna dla klienta i Menedżera kolejki klienta.</span><span class="sxs-lookup"><span data-stu-id="3c047-110">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="3c047-111">Gdy usługa odbiera komunikaty w zakresie transakcji, transakcja jest lokalna dla usługi i Menedżera kolejki odbierającej.</span><span class="sxs-lookup"><span data-stu-id="3c047-111">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="3c047-112">Bardzo ważne jest, aby pamiętać, że klient i usługa nie uczestniczą w tej samej transakcji. Zamiast tego korzystają z różnych transakcji podczas wykonywania operacji (takich jak wysyłanie i odbieranie) z kolejką.</span><span class="sxs-lookup"><span data-stu-id="3c047-112">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>

<span data-ttu-id="3c047-113">W tym przykładzie klient wysyła partię komunikatów do usługi z zakresu transakcji.</span><span class="sxs-lookup"><span data-stu-id="3c047-113">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="3c047-114">Komunikaty wysyłane do kolejki są następnie odbierane przez usługę w zakresie transakcji zdefiniowanym przez usługę.</span><span class="sxs-lookup"><span data-stu-id="3c047-114">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>

<span data-ttu-id="3c047-115">Kontrakt usługi jest `IOrderProcessor`, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="3c047-115">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="3c047-116">Interfejs definiuje jednokierunkową usługę, która jest odpowiednia do użycia z kolejkami.</span><span class="sxs-lookup"><span data-stu-id="3c047-116">The interface defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

<span data-ttu-id="3c047-117">Zachowanie usługi definiuje zachowanie operacji z `TransactionScopeRequired`m ustawionym na `true`.</span><span class="sxs-lookup"><span data-stu-id="3c047-117">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="3c047-118">Gwarantuje to, że ten sam zakres transakcji, który jest używany do pobierania wiadomości z kolejki jest używany przez menedżerów zasobów, do których uzyskuje dostęp Metoda.</span><span class="sxs-lookup"><span data-stu-id="3c047-118">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="3c047-119">Gwarantuje również, że jeśli metoda zgłasza wyjątek, komunikat jest zwracany do kolejki.</span><span class="sxs-lookup"><span data-stu-id="3c047-119">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="3c047-120">Bez ustawiania tego zachowania, kanał umieszczony w kolejce tworzy transakcję odczytu wiadomości z kolejki i zatwierdza ją automatycznie przed wysłaniem, jeśli operacja nie powiedzie się, komunikat zostanie utracony.</span><span class="sxs-lookup"><span data-stu-id="3c047-120">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="3c047-121">Najbardziej typowym scenariuszem jest to, że operacje usługi mogą być rejestrowane w transakcji, która jest używana do odczytywania wiadomości z kolejki, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="3c047-121">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>

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

<span data-ttu-id="3c047-122">Usługa jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="3c047-122">The service is self hosted.</span></span> <span data-ttu-id="3c047-123">W przypadku korzystania z transportu usługi MSMQ użyta Kolejka musi zostać utworzona z góry.</span><span class="sxs-lookup"><span data-stu-id="3c047-123">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="3c047-124">Można to zrobić ręcznie lub przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="3c047-124">This can be done manually or through code.</span></span> <span data-ttu-id="3c047-125">W tym przykładzie usługa zawiera kod służący do sprawdzania istnienia kolejki i tworzenia kolejki, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="3c047-125">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="3c047-126">Nazwa kolejki jest odczytywana z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3c047-126">The queue name is read from the configuration file.</span></span> <span data-ttu-id="3c047-127">Adres podstawowy jest używany przez narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania serwera proxy w usłudze.</span><span class="sxs-lookup"><span data-stu-id="3c047-127">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>

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

<span data-ttu-id="3c047-128">Nazwa kolejki MSMQ jest określona w sekcji appSettings w pliku konfiguracji, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="3c047-128">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="3c047-129">Nazwa kolejki używa kropki (.) dla komputera lokalnego i separatorów ukośników odwrotnych w ścieżce podczas tworzenia kolejki przy użyciu <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="3c047-129">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="3c047-130">Punkt końcowy Windows Communication Foundation (WCF) używa adresu kolejki w schemacie net. MSMQ, używa "localhost" do określenia komputera lokalnego i używa ukośników w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="3c047-130">The Windows Communication Foundation (WCF) endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>

<span data-ttu-id="3c047-131">Klient tworzy zakres transakcji.</span><span class="sxs-lookup"><span data-stu-id="3c047-131">The client creates a transaction scope.</span></span> <span data-ttu-id="3c047-132">Komunikacja z kolejką odbywa się w zakresie transakcji, co sprawia, że jest ona traktowana jako jednostka niepodzielna, w której wszystkie komunikaty są wysyłane do kolejki lub żaden z komunikatów nie jest wysyłany do kolejki.</span><span class="sxs-lookup"><span data-stu-id="3c047-132">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="3c047-133">Transakcja jest zatwierdzana przez wywołanie <xref:System.Transactions.TransactionScope.Complete%2A> w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="3c047-133">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>

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

<span data-ttu-id="3c047-134">Aby sprawdzić, czy transakcje działają, zmodyfikuj klienta, dodając komentarz do zakresu transakcji, jak pokazano w poniższym przykładowym kodzie, Skompiluj ponownie rozwiązanie i uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="3c047-134">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>

```csharp
//scope.Complete();
```

<span data-ttu-id="3c047-135">Ponieważ transakcja nie została ukończona, wiadomości nie są wysyłane do kolejki.</span><span class="sxs-lookup"><span data-stu-id="3c047-135">Because the transaction is not completed, the messages are not sent to the queue.</span></span>

<span data-ttu-id="3c047-136">Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="3c047-136">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="3c047-137">Możesz zobaczyć, że usługa odbiera komunikaty od klienta.</span><span class="sxs-lookup"><span data-stu-id="3c047-137">You can see the service receive messages from the client.</span></span> <span data-ttu-id="3c047-138">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="3c047-138">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="3c047-139">Należy pamiętać, że ponieważ usługa kolejkowania jest w użyciu, klient i usługi nie muszą działać w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="3c047-139">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="3c047-140">Można uruchomić klienta programu, zamknąć go, a następnie uruchomić usługę i nadal otrzymuje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="3c047-140">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3c047-141">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="3c047-141">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3c047-142">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c047-142">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="3c047-143">Jeśli usługa jest uruchamiana po raz pierwszy, sprawdzi, czy kolejka jest obecna.</span><span class="sxs-lookup"><span data-stu-id="3c047-143">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="3c047-144">Jeśli kolejka nie istnieje, usługa utworzy ją.</span><span class="sxs-lookup"><span data-stu-id="3c047-144">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="3c047-145">Aby utworzyć kolejkę, można najpierw uruchomić tę usługę lub utworzyć ją za pośrednictwem Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3c047-145">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="3c047-146">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="3c047-146">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="3c047-147">Otwórz Menedżer serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="3c047-147">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="3c047-148">Rozwiń kartę **funkcje** .</span><span class="sxs-lookup"><span data-stu-id="3c047-148">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="3c047-149">Kliknij prawym przyciskiem myszy pozycję **prywatne kolejki komunikatów**, a następnie wybierz kolejno pozycje **Nowa**i **prywatne**.</span><span class="sxs-lookup"><span data-stu-id="3c047-149">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="3c047-150">Zaznacz pole **transakcyjne** .</span><span class="sxs-lookup"><span data-stu-id="3c047-150">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="3c047-151">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="3c047-151">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="3c047-152">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c047-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="3c047-153">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c047-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

<span data-ttu-id="3c047-154">Domyślnie przy <xref:System.ServiceModel.NetMsmqBinding>włączono zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="3c047-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="3c047-155">Istnieją dwie istotne właściwości zabezpieczeń transportu usługi MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="3c047-155">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="3c047-156">Domyślnie tryb uwierzytelniania jest ustawiony na `Windows`, a poziom ochrony jest ustawiony na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="3c047-156">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="3c047-157">Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny i należy zainstalować opcję integracji Active Directory dla usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3c047-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="3c047-158">Jeśli ten przykład zostanie uruchomiony na komputerze, który nie spełnia tych kryteriów, zostanie wyświetlony komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="3c047-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="3c047-159">Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej lub bez integracji z Active Directory</span><span class="sxs-lookup"><span data-stu-id="3c047-159">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>

1. <span data-ttu-id="3c047-160">Jeśli komputer nie jest częścią domeny lub nie ma zainstalowanej integracji Active Directory, Wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom ochrony na `None`, jak pokazano w poniższym przykładowym kodzie konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="3c047-160">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>

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
          <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
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

2. <span data-ttu-id="3c047-161">Przed uruchomieniem przykładu należy zmienić konfigurację na serwerze i kliencie programu.</span><span class="sxs-lookup"><span data-stu-id="3c047-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3c047-162">Ustawienie `security mode` `None` jest równoznaczne z ustawieniem <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>i `Message` zabezpieczenia `None`.</span><span class="sxs-lookup"><span data-stu-id="3c047-162">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3c047-163">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3c047-163">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3c047-164">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="3c047-164">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="3c047-165">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c047-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3c047-166">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3c047-166">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`
