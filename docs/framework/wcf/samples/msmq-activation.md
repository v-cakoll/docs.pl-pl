---
title: Aktywacja usługi MSMQ
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 0dbd24a612d56c0fe88066f625be2a8369b7df5b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602545"
---
# <a name="msmq-activation"></a><span data-ttu-id="fc25c-102">Aktywacja usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="fc25c-102">MSMQ Activation</span></span>

<span data-ttu-id="fc25c-103">Ten przykład pokazuje, jak hostować aplikacje w usłudze aktywacji procesów systemu Windows (WAS) odczytywane z kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fc25c-103">This sample demonstrates how to host applications in Windows Process Activation Service (WAS) that are read from a message queue.</span></span> <span data-ttu-id="fc25c-104">Ten przykład używa `netMsmqBinding` i jest oparty na [dwukierunkowej](two-way-communication.md) próbce komunikacji.</span><span class="sxs-lookup"><span data-stu-id="fc25c-104">This sample uses the `netMsmqBinding` and is based on the [Two-Way Communication](two-way-communication.md) sample.</span></span> <span data-ttu-id="fc25c-105">Usługa w tym przypadku jest aplikacją hostowaną w sieci Web, a klient jest samoobsługowy i wyprowadza do konsoli, aby obserwować stan przesłanych zamówień zakupu.</span><span class="sxs-lookup"><span data-stu-id="fc25c-105">The service in this case is a Web-hosted application and the client is self-hosted and outputs to the console to observe the status of purchase orders submitted.</span></span>

> [!NOTE]
> <span data-ttu-id="fc25c-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="fc25c-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="fc25c-107">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="fc25c-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="fc25c-108">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="fc25c-108">Check for the following (default) directory before continuing.</span></span>
>
> <span data-ttu-id="fc25c-109">\<InstallDrive>: \ WF_WCF_Samples</span><span class="sxs-lookup"><span data-stu-id="fc25c-109">\<InstallDrive>:\WF_WCF_Samples</span></span>
>
> <span data-ttu-id="fc25c-110">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie WCF i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="fc25c-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all WCF and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc25c-111">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fc25c-111">This sample is located in the following directory.</span></span>
>
> <span data-ttu-id="fc25c-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span><span class="sxs-lookup"><span data-stu-id="fc25c-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span></span>

<span data-ttu-id="fc25c-113">Usługa aktywacji procesów systemu Windows (WAS), nowy mechanizm aktywacji procesu dla systemu Windows Server 2008, zapewnia funkcje podobne do usług IIS, które były wcześniej dostępne tylko dla aplikacji opartych na protokole HTTP, do aplikacji korzystających z protokołów innych niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="fc25c-113">Windows Process Activation Service (WAS), the new process activation mechanism for Windows Server 2008, provides IIS-like features that were previously only available to HTTP-based applications to applications that use non-HTTP protocols.</span></span> <span data-ttu-id="fc25c-114">Windows Communication Foundation (WCF) używa interfejsu adaptera odbiornika do przekazywania żądań aktywacji odbieranych za pośrednictwem protokołów innych niż HTTP obsługiwanych przez funkcję WCF, takich jak TCP, nazwane potoki i MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fc25c-114">Windows Communication Foundation (WCF) uses the Listener Adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, Named Pipes, and MSMQ.</span></span> <span data-ttu-id="fc25c-115">Funkcja otrzymywania żądań za pośrednictwem protokołów innych niż HTTP jest hostowana przez zarządzane usługi systemu Windows działające w SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="fc25c-115">The functionality for receiving requests over non-HTTP protocols is hosted by managed Windows services running in SMSvcHost.exe.</span></span>

<span data-ttu-id="fc25c-116">Usługa adaptera odbiornika NET. msmq (NetMsmqActivator) aktywuje aplikacje znajdujące się w kolejce na podstawie komunikatów w kolejce.</span><span class="sxs-lookup"><span data-stu-id="fc25c-116">The Net.Msmq Listener Adapter service (NetMsmqActivator) activates queued applications based on messages in the queue.</span></span>

<span data-ttu-id="fc25c-117">Klient wysyła zamówienia zakupu do usługi z zakresu transakcji.</span><span class="sxs-lookup"><span data-stu-id="fc25c-117">The client sends purchase orders to the service from within the scope of a transaction.</span></span> <span data-ttu-id="fc25c-118">Usługa otrzymuje zamówienia w transakcji i przetwarza je.</span><span class="sxs-lookup"><span data-stu-id="fc25c-118">The service receives the orders in a transaction and processes them.</span></span> <span data-ttu-id="fc25c-119">Następnie usługa wywołuje klienta przy użyciu stanu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="fc25c-119">The service then calls back the client with the status of the order.</span></span> <span data-ttu-id="fc25c-120">Aby ułatwić komunikację dwukierunkową, klient i usługa używają kolejek do dodawania do kolejki zamówień zakupu i stanu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="fc25c-120">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>

<span data-ttu-id="fc25c-121">Kontrakt usługi `IOrderProcessor` definiuje jednokierunkowe operacje usługi, które działają z kolejkowanie.</span><span class="sxs-lookup"><span data-stu-id="fc25c-121">The service contract `IOrderProcessor` defines the one-way service operations that work with queuing.</span></span> <span data-ttu-id="fc25c-122">Operacja usługi używa punktu końcowego odpowiedzi do wysyłania do klienta stanu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="fc25c-122">The service operation uses the reply endpoint to send order statuses to the client.</span></span> <span data-ttu-id="fc25c-123">Adres punktu końcowego odpowiedzi to identyfikator URI kolejki użytej do wysłania stanu zamówienia z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="fc25c-123">The reply endpoint's address is the URI of the queue used to send the order status back to the client.</span></span> <span data-ttu-id="fc25c-124">Aplikacja do przetwarzania zamówień implementuje ten kontrakt.</span><span class="sxs-lookup"><span data-stu-id="fc25c-124">The order processing application implements this contract.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po,
                                           string reportOrderStatusTo);
}
```

<span data-ttu-id="fc25c-125">Kontrakt odpowiedzi, do którego ma zostać wysłana stan zamówienia, jest określany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="fc25c-125">The reply contract to send order status to is specified by the client.</span></span> <span data-ttu-id="fc25c-126">Klient implementuje kontrakt stanu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="fc25c-126">The client implements the order status contract.</span></span> <span data-ttu-id="fc25c-127">Usługa używa wygenerowanego klienta tego kontraktu do wysyłania stanu zamówienia z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="fc25c-127">The service uses the generated client of this contract to send order status back to the client.</span></span>

```csharp
[ServiceContract]
public interface IOrderStatus
{
    [OperationContract(IsOneWay = true)]
    void OrderStatus(string poNumber, string status);
}
```

<span data-ttu-id="fc25c-128">Operacja usługi przetwarza przesłane zamówienie zakupu.</span><span class="sxs-lookup"><span data-stu-id="fc25c-128">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="fc25c-129"><xref:System.ServiceModel.OperationBehaviorAttribute>Jest stosowana do operacji usługi, aby określić automatyczną rejestrację w transakcji, która jest używana do odbierania komunikatu z kolejki i automatycznego uzupełniania transakcji po zakończeniu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="fc25c-129">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in the transaction that is used to receive the message from the queue and automatic completion of the transaction on completion of the service operation.</span></span> <span data-ttu-id="fc25c-130">`Orders`Klasa hermetyzuje funkcje przetwarzania zamówień.</span><span class="sxs-lookup"><span data-stu-id="fc25c-130">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="fc25c-131">W takim przypadku dodaje zamówienie zakupu do słownika.</span><span class="sxs-lookup"><span data-stu-id="fc25c-131">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="fc25c-132">Transakcja, w której rejestrowana jest operacja usługi, jest dostępna dla operacji w `Orders` klasie.</span><span class="sxs-lookup"><span data-stu-id="fc25c-132">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>

<span data-ttu-id="fc25c-133">Operacja usługi, oprócz przetwarzania przesłanego zamówienia zakupu, odpowiada klientowi na informacje o stanie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="fc25c-133">The service operation, in addition to processing the submitted purchase order, replies back to the client about the status of the order.</span></span>

```csharp
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
        Console.WriteLine("Sending back order status information");
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));
        // please note that the same transaction that is used to dequeue purchase order is used
        // to send back order status
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.OrderStatus(po.PONumber, po.Status);
            scope.Complete();
        }
    }
}
```

<span data-ttu-id="fc25c-134">Powiązanie klienta do użycia jest określone przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fc25c-134">The client binding to use is specified using a configuration file.</span></span>

<span data-ttu-id="fc25c-135">Nazwa kolejki MSMQ jest określona w sekcji appSettings w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fc25c-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="fc25c-136">Punkt końcowy usługi jest zdefiniowany w sekcji System. serviceModel w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fc25c-136">The endpoint for the service is defined in the System.serviceModel section of the configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="fc25c-137">Nazwa kolejki MSMQ i adres punktu końcowego używają nieco różnych konwencji adresowania.</span><span class="sxs-lookup"><span data-stu-id="fc25c-137">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="fc25c-138">Nazwa kolejki MSMQ używa kropki (.) dla komputera lokalnego i separatorów ukośników odwrotnych.</span><span class="sxs-lookup"><span data-stu-id="fc25c-138">The MSMQ queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="fc25c-139">Adres punktu końcowego programu WCF określa obiekt net. MSMQ: schemat, używa "localhost" dla komputera lokalnego i używa ukośników w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="fc25c-139">The WCF endpoint address specifies a net.msmq: scheme, uses "localhost" for the local computer, and uses forward slashes in its path.</span></span> <span data-ttu-id="fc25c-140">Aby odczytać z kolejki hostowanej na komputerze zdalnym, Zastąp ciąg "." i "localhost" nazwą komputera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="fc25c-140">To read from a queue that is hosted on the remote computer, replace the "." and "localhost" to the remote computer name.</span></span>

<span data-ttu-id="fc25c-141">Plik. svc o nazwie klasy jest używany do hostowania kodu usługi w programie.</span><span class="sxs-lookup"><span data-stu-id="fc25c-141">A .svc file with the name of the class is used to host the service code in WAS.</span></span>

<span data-ttu-id="fc25c-142">Sam plik Service. svc zawiera dyrektywę służącą do utworzenia `OrderProcessorService` .</span><span class="sxs-lookup"><span data-stu-id="fc25c-142">The Service.svc file itself contains a directive to create the `OrderProcessorService`.</span></span>

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>`

<span data-ttu-id="fc25c-143">Plik Service. svc zawiera także dyrektywę zestawu, aby upewnić się, że system. Transactions. dll jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="fc25c-143">The Service.svc file also contains an assembly directive to ensure that System.Transactions.dll is loaded.</span></span>

`<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>`

<span data-ttu-id="fc25c-144">Klient tworzy zakres transakcji.</span><span class="sxs-lookup"><span data-stu-id="fc25c-144">The client creates a transaction scope.</span></span> <span data-ttu-id="fc25c-145">Komunikacja z usługą odbywa się w zakresie transakcji, powodując, że jest ona traktowana jako jednostka niepodzielna, w której wszystkie komunikaty kończą się powodzeniem lub niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="fc25c-145">Communication with the service takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="fc25c-146">Transakcja jest zatwierdzona przez wywołanie `Complete` zakresu transakcji.</span><span class="sxs-lookup"><span data-stu-id="fc25c-146">The transaction is committed by calling `Complete` on the transaction scope.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))
{
    // Open the ServiceHostBase to create listeners and start listening
    // for order status messages.
    serviceHost.Open();

    // Create a proxy with given client endpoint configuration
    OrderProcessorClient client = new OrderProcessorClient();

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
    using (TransactionScope scope = new
        TransactionScope(TransactionScopeOption.Required))
    {
        // Make a queued call to submit the purchase order
        client.SubmitPurchaseOrder(po,
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");
        // Complete the transaction.
        scope.Complete();
    }

    //Closing the client gracefully closes the connection and cleans up
    //resources
    client.Close();

    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();

    // Close the ServiceHostBase to shutdown the service.
    serviceHost.Close();
    }
```

<span data-ttu-id="fc25c-147">Kod klienta implementuje kontrakt, `IOrderStatus` Aby otrzymać stan zamówienia z usługi.</span><span class="sxs-lookup"><span data-stu-id="fc25c-147">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="fc25c-148">W takim przypadku drukuje stan zamówienia.</span><span class="sxs-lookup"><span data-stu-id="fc25c-148">In this case, it prints out the order status.</span></span>

```csharp
[ServiceBehavior]
public class OrderStatusService : IOrderStatus
{
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]
    public void OrderStatus(string poNumber, string status)
    {
        Console.WriteLine("Status of order {0}:{1} ",
                                         poNumber , status);
    }
}
```

<span data-ttu-id="fc25c-149">Kolejka stanu zamówienia jest tworzona w `Main` metodzie.</span><span class="sxs-lookup"><span data-stu-id="fc25c-149">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="fc25c-150">Konfiguracja klienta zawiera konfigurację usługi stanu zamówienia do hostowania usługi stanu zamówienia, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="fc25c-150">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <!-- use appSetting to configure MSMQ queue name -->
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />
  </appSettings>

<system.serviceModel>

    <services>
      <service
         name="Microsoft.ServiceModel.Samples.OrderStatusService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
    </client>

  </system.serviceModel>
```

<span data-ttu-id="fc25c-151">Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie Windows, jak i w konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="fc25c-151">When you run the sample, the client and service activities are displayed in both the server and client console windows.</span></span> <span data-ttu-id="fc25c-152">Można zobaczyć, że serwer odbiera komunikaty od klienta.</span><span class="sxs-lookup"><span data-stu-id="fc25c-152">You can see the server receive messages from the client.</span></span> <span data-ttu-id="fc25c-153">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć serwer i klienta.</span><span class="sxs-lookup"><span data-stu-id="fc25c-153">Press ENTER in each console window to shut down the server and client.</span></span>

<span data-ttu-id="fc25c-154">Klient wyświetla informacje o stanie zamówienia wysyłane przez serwer:</span><span class="sxs-lookup"><span data-stu-id="fc25c-154">The client displays the order status information sent by the server:</span></span>

```console
Press <ENTER> to terminate client.
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fc25c-155">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="fc25c-155">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="fc25c-156">Upewnij się, że usługi IIS 7,0 są zainstalowane, ponieważ są wymagane do aktywacji.</span><span class="sxs-lookup"><span data-stu-id="fc25c-156">Ensure that IIS 7.0 is installed, as it is required for WAS activation.</span></span>

2. <span data-ttu-id="fc25c-157">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fc25c-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span> <span data-ttu-id="fc25c-158">Ponadto należy zainstalować składniki aktywacji inne niż HTTP programu WCF:</span><span class="sxs-lookup"><span data-stu-id="fc25c-158">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="fc25c-159">Z menu **Start** wybierz pozycję **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="fc25c-159">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="fc25c-160">Wybierz **programy i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="fc25c-160">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="fc25c-161">Kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="fc25c-161">Click **Turn Windows Features on or off**.</span></span>

    4. <span data-ttu-id="fc25c-162">W obszarze **Podsumowanie funkcji**kliknij pozycję **Dodaj funkcje**.</span><span class="sxs-lookup"><span data-stu-id="fc25c-162">Under **Features Summary**, click **Add Features**.</span></span>

    5. <span data-ttu-id="fc25c-163">Rozwiń węzeł **Microsoft .NET Framework 3,0** i Sprawdź funkcję **aktywacji Windows Communication Foundation niehttp** .</span><span class="sxs-lookup"><span data-stu-id="fc25c-163">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="fc25c-164">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fc25c-164">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="fc25c-165">Uruchom klienta programu, wykonując polecenie Client. exe z okna polecenia.</span><span class="sxs-lookup"><span data-stu-id="fc25c-165">Run the client by executing client.exe from a command window.</span></span> <span data-ttu-id="fc25c-166">Spowoduje to utworzenie kolejki i wysłanie do niej komunikatu.</span><span class="sxs-lookup"><span data-stu-id="fc25c-166">This creates the queue and sends a message to it.</span></span> <span data-ttu-id="fc25c-167">Pozostaw uruchomiony klient, aby zobaczyć wynik usługi odczytującej komunikat</span><span class="sxs-lookup"><span data-stu-id="fc25c-167">Leave the client running to see the result of the service reading the message</span></span>

5. <span data-ttu-id="fc25c-168">Domyślnie usługa aktywacji usługi MSMQ działa jako usługa sieciowa.</span><span class="sxs-lookup"><span data-stu-id="fc25c-168">The MSMQ activation service runs as Network Service by default.</span></span> <span data-ttu-id="fc25c-169">W związku z tym Kolejka służąca do aktywowania aplikacji musi mieć uprawnienia do odbierania i wglądu w usługę sieciową.</span><span class="sxs-lookup"><span data-stu-id="fc25c-169">Therefore, the queue that is used to activate the application must have receive and peek permissions for Network Service.</span></span> <span data-ttu-id="fc25c-170">Można to dodać przy użyciu programu MMC usługi kolejkowania komunikatów:</span><span class="sxs-lookup"><span data-stu-id="fc25c-170">This can be added by using the Message Queuing MMC:</span></span>

    1. <span data-ttu-id="fc25c-171">W menu **Start** kliknij polecenie **Uruchom**, a następnie wpisz `Compmgmt.msc` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="fc25c-171">From the **Start** menu, click **Run**, then type `Compmgmt.msc` and press ENTER.</span></span>

    2. <span data-ttu-id="fc25c-172">W obszarze **usługi i aplikacje**rozwiń węzeł **kolejkowanie komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="fc25c-172">Under **Services and Applications**, expand **Message Queuing**.</span></span>

    3. <span data-ttu-id="fc25c-173">Kliknij pozycję **kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="fc25c-173">Click **Private Queues**.</span></span>

    4. <span data-ttu-id="fc25c-174">Kliknij prawym przyciskiem myszy kolejkę (ServiceModelSamples/Service. svc) i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fc25c-174">Right-click the queue (servicemodelsamples/Service.svc) and choose **Properties**.</span></span>

    5. <span data-ttu-id="fc25c-175">Na karcie **zabezpieczenia** kliknij pozycję **Dodaj** i Udziel uprawnień wglądu i Odbierz do usługi sieciowej.</span><span class="sxs-lookup"><span data-stu-id="fc25c-175">On the **Security** tab, click **Add** and give peek and receive permissions to Network Service.</span></span>

6. <span data-ttu-id="fc25c-176">Skonfiguruj usługę aktywacji procesów systemu Windows (WAS) do obsługi aktywacji usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fc25c-176">Configure the Windows Process Activation Service (WAS) to support MSMQ activation.</span></span>

    <span data-ttu-id="fc25c-177">Jako wygoda, następujące kroki są zaimplementowane w pliku wsadowym o nazwie AddMsmqSiteBinding. cmd znajdującym się w katalogu przykładowym.</span><span class="sxs-lookup"><span data-stu-id="fc25c-177">As a convenience, the following steps are implemented in a batch file called AddMsmqSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="fc25c-178">Aby można było obsługiwać aktywację net. MSMQ, domyślna witryna sieci Web musi być najpierw powiązana z protokołem net. MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fc25c-178">To support net.msmq activation, the default Web site must first be bound to the net.msmq protocol.</span></span> <span data-ttu-id="fc25c-179">Można to zrobić za pomocą programu Appcmd. exe, który jest instalowany przy użyciu zestawu narzędzi do zarządzania usługami IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="fc25c-179">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="fc25c-180">W wierszu polecenia z podwyższonym poziomem uprawnień (Administrator) Uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="fc25c-180">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="fc25c-181">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="fc25c-181">This command is a single line of text.</span></span>

        <span data-ttu-id="fc25c-182">To polecenie dodaje powiązanie witryny net. MSMQ do domyślnej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="fc25c-182">This command adds a net.msmq site binding to the default Web site.</span></span>

    2. <span data-ttu-id="fc25c-183">Mimo że wszystkie aplikacje w lokacji współdzielą wspólne powiązanie net. MSMQ, każda aplikacja może włączyć obsługę usługi net. MSMQ osobno.</span><span class="sxs-lookup"><span data-stu-id="fc25c-183">Although all applications within a site share a common net.msmq binding, each application can enable net.msmq support individually.</span></span> <span data-ttu-id="fc25c-184">Aby włączyć usługę net. msmq dla aplikacji/servicemodelsamples, uruchom następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="fc25c-184">To enable net.msmq for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq
        ```

        > [!NOTE]
        > <span data-ttu-id="fc25c-185">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="fc25c-185">This command is a single line of text.</span></span>

        <span data-ttu-id="fc25c-186">To polecenie umożliwia dostęp do aplikacji/servicemodelsamples przy użyciu `http://localhost/servicemodelsamples` i `net.msmq://localhost/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="fc25c-186">This command enables the /servicemodelsamples application to be accessed using `http://localhost/servicemodelsamples` and `net.msmq://localhost/servicemodelsamples`.</span></span>

7. <span data-ttu-id="fc25c-187">Jeśli nie zostało to wcześniej zrobione, upewnij się, że usługa aktywacji MSMQ jest włączona.</span><span class="sxs-lookup"><span data-stu-id="fc25c-187">If you have not done so previously, ensure that the MSMQ activation service is enabled.</span></span> <span data-ttu-id="fc25c-188">W menu **Start** kliknij polecenie **Uruchom**, a następnie wpisz `Services.msc` .</span><span class="sxs-lookup"><span data-stu-id="fc25c-188">From the **Start** menu, click **Run**, and type `Services.msc`.</span></span> <span data-ttu-id="fc25c-189">Przeszukaj listę usług dla **karty odbiornika NET. MSMQ**.</span><span class="sxs-lookup"><span data-stu-id="fc25c-189">Search the list of services for the **Net.Msmq Listener Adapter**.</span></span> <span data-ttu-id="fc25c-190">Kliknij prawym przyciskiem myszy i wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fc25c-190">Right-click and select **Properties**.</span></span> <span data-ttu-id="fc25c-191">Ustaw **Typ uruchamiania** na **automatyczny**, kliknij przycisk **Zastosuj** , a następnie kliknij przycisk **Uruchom** .</span><span class="sxs-lookup"><span data-stu-id="fc25c-191">Set the **Startup Type** to **Automatic**, click **Apply** and click the **Start** button.</span></span> <span data-ttu-id="fc25c-192">Ten krok należy wykonać tylko raz przed pierwszym użyciem usługi adaptera odbiornika NET. MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fc25c-192">This step must only be done once prior to the first usage of the Net.Msmq Listener Adapter service.</span></span>

8. <span data-ttu-id="fc25c-193">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fc25c-193">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="fc25c-194">Ponadto należy zmienić kod na kliencie, który przesyła zamówienie zakupu w celu odzwierciedlenia nazwy komputera w identyfikatorze URI kolejki podczas przesyłania zamówienia zakupu.</span><span class="sxs-lookup"><span data-stu-id="fc25c-194">Additionally, change the code on the client that submits the purchase order to reflect the computer name in the URI of the queue when submitting the purchase order.</span></span> <span data-ttu-id="fc25c-195">Użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="fc25c-195">Use the following code:</span></span>

    ```csharp
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");
    ```

9. <span data-ttu-id="fc25c-196">Usuń powiązanie witryny net. MSMQ dodane do tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="fc25c-196">Remove the net.msmq site binding you added for this sample.</span></span>

    <span data-ttu-id="fc25c-197">Jako wygoda, następujące kroki są zaimplementowane w pliku wsadowym o nazwie RemoveMsmqSiteBinding. cmd, który znajduje się w przykładowym katalogu:</span><span class="sxs-lookup"><span data-stu-id="fc25c-197">As a convenience, the following steps are implemented in a batch file called RemoveMsmqSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="fc25c-198">Usuń usługę net. MSMQ z listy włączonych protokołów, uruchamiając następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="fc25c-198">Remove net.msmq from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="fc25c-199">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="fc25c-199">This command is a single line of text.</span></span>

    2. <span data-ttu-id="fc25c-200">Usuń powiązanie witryny net. MSMQ, uruchamiając następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="fc25c-200">Remove the net.msmq site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="fc25c-201">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="fc25c-201">This command is a single line of text.</span></span>

    > [!WARNING]
    > <span data-ttu-id="fc25c-202">Uruchomienie pliku wsadowego spowoduje zresetowanie tej opcji do uruchamiania przy użyciu .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="fc25c-202">Running the batch file will reset the DefaultAppPool to run using .NET Framework version 2.0.</span></span>

<span data-ttu-id="fc25c-203">Domyślnie w przypadku `netMsmqBinding` transportu powiązań jest włączone zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="fc25c-203">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="fc25c-204">Dwie właściwości, `MsmqAuthenticationMode` a `MsmqProtectionLevel` także określają typ zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="fc25c-204">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="fc25c-205">Domyślnie tryb uwierzytelniania jest ustawiony na `Windows` , a poziom ochrony jest ustawiony na `Sign` .</span><span class="sxs-lookup"><span data-stu-id="fc25c-205">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="fc25c-206">Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny.</span><span class="sxs-lookup"><span data-stu-id="fc25c-206">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="fc25c-207">Jeśli ten przykład zostanie uruchomiony na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący komunikat o błędzie: "wewnętrzny certyfikat usługi kolejkowania komunikatów użytkownika nie istnieje".</span><span class="sxs-lookup"><span data-stu-id="fc25c-207">If you run this sample on a computer that is not part of a domain, the following error is received: "User's internal message queuing certificate does not exist".</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="fc25c-208">Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej</span><span class="sxs-lookup"><span data-stu-id="fc25c-208">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="fc25c-209">Jeśli komputer nie jest częścią domeny, Wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom ochrony na brak, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="fc25c-209">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to none as shown in the following sample configuration.</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding configurationName="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

2. <span data-ttu-id="fc25c-210">Przed uruchomieniem przykładu Zmień konfigurację na serwerze i kliencie.</span><span class="sxs-lookup"><span data-stu-id="fc25c-210">Change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fc25c-211">Ustawienie `security mode` odpowiada `None` ustawieniu `MsmqAuthenticationMode` `MsmqProtectionLevel` i `Message` zabezpieczenia na `None` .</span><span class="sxs-lookup"><span data-stu-id="fc25c-211">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

3. <span data-ttu-id="fc25c-212">Aby włączyć aktywację na komputerze przyłączonym do grupy roboczej, należy uruchomić zarówno usługę aktywacji, jak i proces roboczy przy użyciu określonego konta użytkownika (musi być taka sama dla obu), a kolejka musi mieć listy ACL dla określonego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fc25c-212">To enable activation in a computer joined to a workgroup, both the activation service and the worker process must be run with a specific user account (must be same for both) and the queue must have ACLs for the specific user account.</span></span>

     <span data-ttu-id="fc25c-213">Aby zmienić tożsamość, w której uruchamiany jest proces roboczy:</span><span class="sxs-lookup"><span data-stu-id="fc25c-213">To change the identity that the worker process runs under:</span></span>

    1. <span data-ttu-id="fc25c-214">Uruchom plik inetmgr. exe.</span><span class="sxs-lookup"><span data-stu-id="fc25c-214">Run Inetmgr.exe.</span></span>

    2. <span data-ttu-id="fc25c-215">W obszarze **Pule aplikacji**kliknij prawym przyciskiem myszy pozycję **puli aplikacji** (zazwyczaj **Domyślna pula**aplikacji), a następnie wybierz pozycję **Ustaw wartości domyślne puli.**</span><span class="sxs-lookup"><span data-stu-id="fc25c-215">Under **Application Pools**, right-click the **AppPool** (typically **DefaultAppPool**) and choose **Set Application Pool Defaults…**.</span></span>

    3. <span data-ttu-id="fc25c-216">Zmień właściwości tożsamości, aby użyć określonego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fc25c-216">Change the Identity properties to use the specific user account.</span></span>

     <span data-ttu-id="fc25c-217">Aby zmienić tożsamość, w której działa usługa aktywacji:</span><span class="sxs-lookup"><span data-stu-id="fc25c-217">To change the identity that the Activation Service runs under:</span></span>

    1. <span data-ttu-id="fc25c-218">Uruchom Services. msc.</span><span class="sxs-lookup"><span data-stu-id="fc25c-218">Run Services.msc.</span></span>

    2. <span data-ttu-id="fc25c-219">Kliknij prawym przyciskiem myszy **kartę net. MsmqListener**, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fc25c-219">Right-click the **Net.MsmqListener Adapter**, and choose **Properties**.</span></span>

4. <span data-ttu-id="fc25c-220">Zmień konto na karcie **Logowanie** .</span><span class="sxs-lookup"><span data-stu-id="fc25c-220">Change the account in the **LogOn** tab.</span></span>

5. <span data-ttu-id="fc25c-221">W grupie roboczej usługa musi również działać przy użyciu nieograniczonego tokenu.</span><span class="sxs-lookup"><span data-stu-id="fc25c-221">In workgroup, the service must also run using an unrestricted token.</span></span> <span data-ttu-id="fc25c-222">Aby to zrobić, uruchom następujące polecenie w oknie polecenia:</span><span class="sxs-lookup"><span data-stu-id="fc25c-222">To do this, run the following in a command window:</span></span>

    ```console
    sc sidtype netmsmqactivator unrestricted
    ```

## <a name="see-also"></a><span data-ttu-id="fc25c-223">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc25c-223">See also</span></span>

- <span data-ttu-id="fc25c-224">[Przykłady hostingu i trwałości usługi AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="fc25c-224">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
