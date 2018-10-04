---
title: Aktywacja usługi MSMQ
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: a179fca70a97b4fd9c7b21bdf548afdda59dda91
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780157"
---
# <a name="msmq-activation"></a><span data-ttu-id="7a6e5-102">Aktywacja usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="7a6e5-102">MSMQ Activation</span></span>
<span data-ttu-id="7a6e5-103">Niniejszy przykład pokazuje, jak hostować aplikacje w Windows Process Activation Service (WAS), które są odczytywane z kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-103">This sample demonstrates how to host applications in Windows Process Activation Service (WAS) that are read from a message queue.</span></span> <span data-ttu-id="7a6e5-104">W tym przykładzie użyto `netMsmqBinding` i opiera się na [komunikacji dwustronny](../../../../docs/framework/wcf/samples/two-way-communication.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-104">This sample uses the `netMsmqBinding` and is based on the [Two-Way Communication](../../../../docs/framework/wcf/samples/two-way-communication.md) sample.</span></span> <span data-ttu-id="7a6e5-105">Usługa jest w tym przypadku aplikacji hostowanej w sieci Web w języku klienta i jest samodzielnie hostowana w konsoli, aby obserwować stan zamówienia zakupu przesłane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-105">The service in this case is a Web-hosted application and the client is self-hosted and outputs to the console to observe the status of purchase orders submitted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a6e5-106">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a6e5-107">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7a6e5-108">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7a6e5-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  <span data-ttu-id="7a6e5-109">\<InstallDrive>:\WF_WCF_Samples</span><span class="sxs-lookup"><span data-stu-id="7a6e5-109">\<InstallDrive>:\WF_WCF_Samples</span></span>  
>   
>  <span data-ttu-id="7a6e5-110">Jeśli ten katalog nie istnieje, przejdź do Windows Communication Foundation (WCF) HYPERLINK "https://go.microsoft.com/fwlink/?LinkId=150780"\t"\_puste" i przykłady Windows Workflow Foundation (WF) dotyczące [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] do pobierania wszystkich usług WCF i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-110">If this directory does not exist, go to Windows Communication Foundation (WCF) HYPERLINK "https://go.microsoft.com/fwlink/?LinkId=150780" \t "\_blank"  and Windows Workflow Foundation (WF) Samples for [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] to download all WCF and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7a6e5-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-111">This sample is located in the following directory.</span></span>  
>   
>  <span data-ttu-id="7a6e5-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span></span>  
  
 <span data-ttu-id="7a6e5-113">Windows Process Activation Service (WAS), przy użyciu nowego procesu aktywacji mechanizmu [!INCLUDE[lserver](../../../../includes/lserver-md.md)], zapewnia funkcje podobne do usług IIS, które były wcześniej dostępne tylko dla aplikacji opartych na protokole HTTP dla aplikacji, które używają protokołów innych niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-113">Windows Process Activation Service (WAS), the new process activation mechanism for [!INCLUDE[lserver](../../../../includes/lserver-md.md)], provides IIS-like features that were previously only available to HTTP-based applications to applications that use non-HTTP protocols.</span></span> <span data-ttu-id="7a6e5-114">Windows Communication Foundation (WCF) używa interfejsu karty odbiornika do komunikowania się żądania aktywacji, które są odbierane za pośrednictwem protokołów innych niż HTTP obsługiwane przez architekturę WCF, takie jak TCP, potoków nazwanych i usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-114">Windows Communication Foundation (WCF) uses the Listener Adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, Named Pipes, and MSMQ.</span></span> <span data-ttu-id="7a6e5-115">Funkcje do odbierania żądań za pośrednictwem protokołów innych niż HTTP jest hostowana przez zarządzane usługi Windows SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-115">The functionality for receiving requests over non-HTTP protocols is hosted by managed Windows services running in SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="7a6e5-116">Usługa Net.Msmq odbiornika Adapter (NetMsmqActivator) aktywuje umieszczonych w kolejce aplikacje oparte na komunikaty w kolejce.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-116">The Net.Msmq Listener Adapter service (NetMsmqActivator) activates queued applications based on messages in the queue.</span></span>  
  
 <span data-ttu-id="7a6e5-117">Klient wysyła zamówienia zakupu usługi z zakresu transakcji.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-117">The client sends purchase orders to the service from within the scope of a transaction.</span></span> <span data-ttu-id="7a6e5-118">Ta usługa odbiera zamówień w ramach transakcji i przetwarza je.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-118">The service receives the orders in a transaction and processes them.</span></span> <span data-ttu-id="7a6e5-119">Usługa następnie ponownie wywołuje klienta z stan zamówienia.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-119">The service then calls back the client with the status of the order.</span></span> <span data-ttu-id="7a6e5-120">Ułatwianie dwukierunkowej komunikacji klienta i usługi użyj kolejki, aby umieścić zakupów i stanu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-120">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="7a6e5-121">Kontrakt usługi `IOrderProcessor` definiuje operacje usługi jednokierunkowej, współpracujących z usługi kolejkowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-121">The service contract `IOrderProcessor` defines the one-way service operations that work with queuing.</span></span> <span data-ttu-id="7a6e5-122">Operacja usługi używa odpowiedzi punktu końcowego do wysyłania stanów zlecenia do klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-122">The service operation uses the reply endpoint to send order statuses to the client.</span></span> <span data-ttu-id="7a6e5-123">Adres punktu końcowego odpowiedzi jest identyfikatorem URI, kolejki, używane do wysyłania stan zamówienia klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-123">The reply endpoint's address is the URI of the queue used to send the order status back to the client.</span></span> <span data-ttu-id="7a6e5-124">Kolejność przetwarzania aplikacji implementuje ten kontrakt.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-124">The order processing application implements this contract.</span></span>  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 <span data-ttu-id="7a6e5-125">Kontrakt odpowiedź do wysłania raportowanie stanu zamówienia jest określony przez klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-125">The reply contract to send order status to is specified by the client.</span></span> <span data-ttu-id="7a6e5-126">Klient implementuje ten kontrakt stan zamówienia.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-126">The client implements the order status contract.</span></span> <span data-ttu-id="7a6e5-127">Usługa używa wygenerowanego klienta ten kontrakt do odesłania stan zamówienia do klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-127">The service uses the generated client of this contract to send order status back to the client.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 <span data-ttu-id="7a6e5-128">Operacja usługi przetworzy to zamówienie zakupu przesłane.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-128">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="7a6e5-129"><xref:System.ServiceModel.OperationBehaviorAttribute> Jest stosowany do operacji usługi, aby określić automatycznej rejestracji w transakcji, która jest używana do odbierania wiadomości z kolejki i automatycznego uzupełniania transakcji po zakończeniu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-129">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in the transaction that is used to receive the message from the queue and automatic completion of the transaction on completion of the service operation.</span></span> <span data-ttu-id="7a6e5-130">`Orders` Klasa hermetyzuje funkcjonalność przetwarzania zamówienia.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-130">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="7a6e5-131">W tym przypadku dodaje zamówienia zakupu w słowniku.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-131">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="7a6e5-132">Operacja usługi zarejestrowany w transakcji jest dostępna dla operacji w `Orders` klasy.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-132">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="7a6e5-133">Operacja usługi, oprócz przetwarzania zamówienia zakupu przesłanych odpowiedzi do klienta o stanie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-133">The service operation, in addition to processing the submitted purchase order, replies back to the client about the status of the order.</span></span>  
  
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
  
 <span data-ttu-id="7a6e5-134">Klient powiązania do użycia jest określony, przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-134">The client binding to use is specified using a configuration file.</span></span>  
  
 <span data-ttu-id="7a6e5-135">Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="7a6e5-136">Punkt końcowy usługi jest zdefiniowany w sekcji System.serviceModel pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-136">The endpoint for the service is defined in the System.serviceModel section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a6e5-137">Adres nazwy i punkt końcowy kolejki usługi MSMQ Użyj nieco Konwencji adresowania.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-137">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="7a6e5-138">Nazwa kolejki usługi MSMQ używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnik odwrotny w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-138">The MSMQ queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="7a6e5-139">Adres punktu końcowego WCF określa net.msmq: schemat, używane "localhost" na komputerze lokalnym i korzysta z ukośników w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-139">The WCF endpoint address specifies a net.msmq: scheme, uses "localhost" for the local computer, and uses forward slashes in its path.</span></span> <span data-ttu-id="7a6e5-140">Aby zapoznać się z kolejki znajdującej się na komputerze zdalnym, zastąp "." i "localhost" do nazwy komputera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-140">To read from a queue that is hosted on the remote computer, replace the "." and "localhost" to the remote computer name.</span></span>  
  
 <span data-ttu-id="7a6e5-141">Plik .svc o nazwie klasy jest używana do hostowania kodu usługi WAS.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-141">A .svc file with the name of the class is used to host the service code in WAS.</span></span>  
  
 <span data-ttu-id="7a6e5-142">Sam plik Service.svc zawiera dyrektywy do tworzenia `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-142">The Service.svc file itself contains a directive to create the `OrderProcessorService`.</span></span>  
  
```xml  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 <span data-ttu-id="7a6e5-143">Plik Service.svc zawiera również dyrektywę zestawu, aby upewnić się, że System.Transactions.dll zostanie załadowana.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-143">The Service.svc file also contains an assembly directive to ensure that System.Transactions.dll is loaded.</span></span>  
  
```xml  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 <span data-ttu-id="7a6e5-144">Klient tworzy zakres transakcji.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-144">The client creates a transaction scope.</span></span> <span data-ttu-id="7a6e5-145">Komunikacja z usługą odbywa się w zakresie transakcji, co powoduje powinien być traktowany jako pojedynczej Atomowej jednostki, której wszystkie komunikaty sukces lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-145">Communication with the service takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="7a6e5-146">Transakcja została zatwierdzona przez wywołanie metody `Complete` w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-146">The transaction is committed by calling `Complete` on the transaction scope.</span></span>  
  
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
  
 <span data-ttu-id="7a6e5-147">Kod klienta implementuje `IOrderStatus` umowę odbierać stan zamówienia z usługi.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-147">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="7a6e5-148">W tym przypadku wyświetla się stan zamówienia.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-148">In this case, it prints out the order status.</span></span>  
  
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
  
 <span data-ttu-id="7a6e5-149">Kolejkę stanu zamówienia jest tworzony w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-149">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="7a6e5-150">Konfiguracja klienta obejmuje konfigurację usługi stanu zamówienia do hostowania usługi stanu zamówienia, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-150">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="7a6e5-151">Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w serwera i klienta okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-151">When you run the sample, the client and service activities are displayed in both the server and client console windows.</span></span> <span data-ttu-id="7a6e5-152">Możesz zobaczyć serwer odbiera komunikaty z klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-152">You can see the server receive messages from the client.</span></span> <span data-ttu-id="7a6e5-153">Naciśnij klawisz ENTER w oknie konsoli, każdej do zamykania serwera i klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-153">Press ENTER in each console window to shut down the server and client.</span></span>  
  
 <span data-ttu-id="7a6e5-154">Klient Wyświetla informacje o stanie zamówienia, które zostały przesłane przez serwer:</span><span class="sxs-lookup"><span data-stu-id="7a6e5-154">The client displays the order status information sent by the server:</span></span>  
  
```Output  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7a6e5-155">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="7a6e5-155">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7a6e5-156">Upewnij się, że [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jest zainstalowany, ponieważ jest on wymagany do aktywacji WAS.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-156">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed, as it is required for WAS activation.</span></span>  
  
2.  <span data-ttu-id="7a6e5-157">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a6e5-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span> <span data-ttu-id="7a6e5-158">Ponadto należy zainstalować składniki Aktywacja bez HTTP programu WCF:</span><span class="sxs-lookup"><span data-stu-id="7a6e5-158">In addition, you must install the WCF non-HTTP activation components:</span></span>  
  
    1.  <span data-ttu-id="7a6e5-159">Z **Start** menu, wybierz **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-159">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="7a6e5-160">Wybierz **programy i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-160">Select **Programs and Features**.</span></span>  
  
    3.  <span data-ttu-id="7a6e5-161">Kliknij przycisk **Włącz lub wyłącz funkcje Windows**.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-161">Click **Turn Windows Features on or off**.</span></span>  
  
    4.  <span data-ttu-id="7a6e5-162">W obszarze **Podsumowanie funkcji**, kliknij przycisk **Dodaj funkcje**.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-162">Under **Features Summary**, click **Add Features**.</span></span>  
  
    5.  <span data-ttu-id="7a6e5-163">Rozwiń **Microsoft .NET Framework 3.0** węzła i wyboru **Aktywacja bez HTTP programu Windows Communication Foundation** funkcji.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-163">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3.  <span data-ttu-id="7a6e5-164">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a6e5-164">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="7a6e5-165">Uruchom klienta, wykonując client.exe z okna poleceń.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-165">Run the client by executing client.exe from a command window.</span></span> <span data-ttu-id="7a6e5-166">To tworzy kolejkę i wysyła komunikat do niego.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-166">This creates the queue and sends a message to it.</span></span> <span data-ttu-id="7a6e5-167">Pozostaw kliencie z uruchomioną Aby sprawdzić działanie usługi, odczytywanie wiadomości</span><span class="sxs-lookup"><span data-stu-id="7a6e5-167">Leave the client running to see the result of the service reading the message</span></span>  
  
5.  <span data-ttu-id="7a6e5-168">Domyślnie usługę Aktywacja usługi MSMQ jest uruchamiana jako usługa sieciowa.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-168">The MSMQ activation service runs as Network Service by default.</span></span> <span data-ttu-id="7a6e5-169">W związku z tym, kolejki, która jest używana do aktywowania aplikacji musi mieć odbieranie i Wybieranie uprawnień dla usługi sieci.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-169">Therefore, the queue that is used to activate the application must have receive and peek permissions for Network Service.</span></span> <span data-ttu-id="7a6e5-170">To można dodać za pomocą programu MMC usługi kolejkowania komunikatów:</span><span class="sxs-lookup"><span data-stu-id="7a6e5-170">This can be added by using the Message Queuing MMC:</span></span>  
  
    1.  <span data-ttu-id="7a6e5-171">Z **Start** menu, kliknij przycisk **Uruchom**, a następnie wpisz `Compmgmt.msc` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-171">From the **Start** menu, click **Run**, then type `Compmgmt.msc` and press ENTER.</span></span>  
  
    2.  <span data-ttu-id="7a6e5-172">W obszarze **usługi i aplikacje**, rozwiń węzeł **usługi kolejkowania komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-172">Under **Services and Applications**, expand **Message Queuing**.</span></span>  
  
    3.  <span data-ttu-id="7a6e5-173">Kliknij przycisk **kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-173">Click **Private Queues**.</span></span>  
  
    4.  <span data-ttu-id="7a6e5-174">Kliknij prawym przyciskiem myszy kolejki (servicemodelsamples/Service.svc), a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-174">Right-click the queue (servicemodelsamples/Service.svc) and choose **Properties**.</span></span>  
  
    5.  <span data-ttu-id="7a6e5-175">Na **zabezpieczeń** kliknij pozycję **Dodaj** zapewniają wgląd i otrzymać uprawnienie do usługi sieciowej.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-175">On the **Security** tab, click **Add** and give peek and receive permissions to Network Service.</span></span>  
  
6.  <span data-ttu-id="7a6e5-176">Skonfiguruj Windows Process Activation Service (WAS) do obsługi aktywacji usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-176">Configure the Windows Process Activation Service (WAS) to support MSMQ activation.</span></span>  
  
     <span data-ttu-id="7a6e5-177">Dla wygody poniższe kroki są implementowane w pliku wsadowym, o nazwie AddMsmqSiteBinding.cmd znajduje się w katalogu próbki.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-177">As a convenience, the following steps are implemented in a batch file called AddMsmqSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="7a6e5-178">Aby zapewnić obsługę aktywacji net.msmq, domyślna witryna sieci Web musi zostać powiązana z protokołem net.msmq.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-178">To support net.msmq activation, the default Web site must first be bound to the net.msmq protocol.</span></span> <span data-ttu-id="7a6e5-179">Można to zrobić za pomocą appcmd.exe, który został zainstalowany przy użyciu [!INCLUDE[iisver](../../../../includes/iisver-md.md)] zestaw narzędzi do zarządzania.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-179">This can be done using appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="7a6e5-180">Z wiersza polecenia o podniesionych uprawnień (administrator) uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-180">From an elevated (administrator) command prompt, run the following command.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="7a6e5-181">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-181">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="7a6e5-182">To polecenie dodaje powiązanie witryny net.msmq do domyślnej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-182">This command adds a net.msmq site binding to the default Web site.</span></span>  
  
    2.  <span data-ttu-id="7a6e5-183">Mimo że wszystkie aplikacje w ramach lokacji mają wspólne powiązanie net.msmq, każdej aplikacji można włączyć obsługę net.msmq indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-183">Although all applications within a site share a common net.msmq binding, each application can enable net.msmq support individually.</span></span> <span data-ttu-id="7a6e5-184">Aby włączyć net.msmq aplikacji /servicemodelsamples, uruchom następujące polecenie z wiersza polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-184">To enable net.msmq for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="7a6e5-185">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-185">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="7a6e5-186">To polecenie włącza aplikację /servicemodelsamples można uzyskać za pomocą `http://localhost/servicemodelsamples` i `net.msmq://localhost/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-186">This command enables the /servicemodelsamples application to be accessed using `http://localhost/servicemodelsamples` and `net.msmq://localhost/servicemodelsamples`.</span></span>
  
7.  <span data-ttu-id="7a6e5-187">Jeśli użytkownik nie zostało zrobione wcześniej, upewnij się, że włączono usługę Aktywacja usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-187">If you have not done so previously, ensure that the MSMQ activation service is enabled.</span></span> <span data-ttu-id="7a6e5-188">Z **Start** menu, kliknij przycisk **Uruchom**i wpisz `Services.msc`.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-188">From the **Start** menu, click **Run**, and type `Services.msc`.</span></span> <span data-ttu-id="7a6e5-189">Wyszukaj listę usług dla **Net.Msmq nasłuchujący**.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-189">Search the list of services for the **Net.Msmq Listener Adapter**.</span></span> <span data-ttu-id="7a6e5-190">Kliknij prawym przyciskiem myszy i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-190">Right-click and select **Properties**.</span></span> <span data-ttu-id="7a6e5-191">Ustaw **uruchamiana** do **automatyczne**, kliknij przycisk **Zastosuj** i kliknij przycisk **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-191">Set the **Startup Type** to **Automatic**, click **Apply** and click the **Start** button.</span></span> <span data-ttu-id="7a6e5-192">Ten krok tylko musi odbywać się jeden raz przed pierwsze użycie usługi Net.Msmq nasłuchujący.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-192">This step must only be done once prior to the first usage of the Net.Msmq Listener Adapter service.</span></span>  
  
8.  <span data-ttu-id="7a6e5-193">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a6e5-193">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="7a6e5-194">Ponadto można zmienić kodu na komputerze klienckim, który przesyła zamówienia zakupu w celu odzwierciedlenia nazwy komputera w identyfikatorze URI kolejki podczas przesyłania zamówienia zakupu.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-194">Additionally, change the code on the client that submits the purchase order to reflect the computer name in the URI of the queue when submitting the purchase order.</span></span> <span data-ttu-id="7a6e5-195">Użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="7a6e5-195">Use the following code:</span></span>  
  
    ```  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. <span data-ttu-id="7a6e5-196">Usuń powiązanie witryny net.msmq, dodane dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-196">Remove the net.msmq site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="7a6e5-197">Dla wygody poniższe kroki są implementowane w pliku wsadowym, o nazwie RemoveMsmqSiteBinding.cmd znajduje się w katalogu próbki:</span><span class="sxs-lookup"><span data-stu-id="7a6e5-197">As a convenience, the following steps are implemented in a batch file called RemoveMsmqSiteBinding.cmd located in the sample directory:</span></span>  
  
    1.  <span data-ttu-id="7a6e5-198">Usuń net.msmq z listy włączone protokoły, uruchamiając następujące polecenie z wiersza polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-198">Remove net.msmq from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="7a6e5-199">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-199">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="7a6e5-200">Usuń powiązanie witryny net.msmq, uruchamiając następujące polecenie z wiersza polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-200">Remove the net.msmq site binding by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="7a6e5-201">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-201">This command is a single line of text.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="7a6e5-202">Uruchamianie pliku wsadowego spowoduje zresetowanie domyślna pula aplikacji do uruchamiania przy użyciu platformy .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-202">Running the batch file will reset the DefaultAppPool to run using .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="7a6e5-203">Domyślnie `netMsmqBinding` powiązania transportu, zabezpieczeń jest włączone.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-203">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="7a6e5-204">Dwie właściwości `MsmqAuthenticationMode` i `MsmqProtectionLevel`, wspólnie określić typ zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-204">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="7a6e5-205">Domyślny tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-205">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="7a6e5-206">Dla usługi MSMQ zapewniać uwierzytelnianie i funkcji podpisywania należy do domeny.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-206">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="7a6e5-207">Po uruchomieniu tego przykładu na komputerze, który nie jest częścią domeny odebraniu następujący błąd: "Wiadomość użytkownika wewnętrzny certyfikat usługi kolejkowania nie istnieje".</span><span class="sxs-lookup"><span data-stu-id="7a6e5-207">If you run this sample on a computer that is not part of a domain, the following error is received: "User's internal message queuing certificate does not exist".</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="7a6e5-208">Do uruchomienia przykładu na komputer przyłączony do grupy roboczej</span><span class="sxs-lookup"><span data-stu-id="7a6e5-208">To run the sample on a computer joined to a workgroup</span></span>  
  
1.  <span data-ttu-id="7a6e5-209">Jeśli komputer nie jest częścią domeny, należy wyłączyć zabezpieczenia transportu przez ustawienie poziomu uwierzytelniania w trybie i ochrony None, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-209">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to none as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2.  <span data-ttu-id="7a6e5-210">Przed uruchomieniem próbki, należy zmienić konfigurację serwera i klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-210">Change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a6e5-211">Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia `MsmqAuthenticationMode`, `MsmqProtectionLevel` i `Message` security `None`.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-211">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>  
  
3.  <span data-ttu-id="7a6e5-212">Aby włączyć aktywacji na komputerze, który został przyłączony do grupy roboczej, zarówno usługa aktywacji, jak i proces roboczy musi być uruchamiane z określonego konta użytkownika (musi być takie same dla obu) i kolejki musi mieć listy kontroli dostępu dla konta określonego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-212">To enable activation in a computer joined to a workgroup, both the activation service and the worker process must be run with a specific user account (must be same for both) and the queue must have ACLs for the specific user account.</span></span>  
  
     <span data-ttu-id="7a6e5-213">Aby zmienić tożsamość, która działa procesu roboczego:</span><span class="sxs-lookup"><span data-stu-id="7a6e5-213">To change the identity that the worker process runs under:</span></span>  
  
    1.  <span data-ttu-id="7a6e5-214">Uruchom Inetmgr.exe.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-214">Run Inetmgr.exe.</span></span>  
  
    2.  <span data-ttu-id="7a6e5-215">W obszarze **pul aplikacji**, kliknij prawym przyciskiem myszy **puli AppPool** (zazwyczaj **DefaultAppPool**) i wybierz polecenie **ustawienia domyślne puli aplikacji...** .</span><span class="sxs-lookup"><span data-stu-id="7a6e5-215">Under **Application Pools**, right-click the **AppPool** (typically **DefaultAppPool**) and choose **Set Application Pool Defaults…**.</span></span>  
  
    3.  <span data-ttu-id="7a6e5-216">Zmień właściwości tożsamości do używania konta określonego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-216">Change the Identity properties to use the specific user account.</span></span>  
  
     <span data-ttu-id="7a6e5-217">Aby zmienić tożsamość, która jest uruchamiana usługa aktywacji:</span><span class="sxs-lookup"><span data-stu-id="7a6e5-217">To change the identity that the Activation Service runs under:</span></span>  
  
    1.  <span data-ttu-id="7a6e5-218">Uruchom aplikację Services.msc.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-218">Run Services.msc.</span></span>  
  
    2.  <span data-ttu-id="7a6e5-219">Kliknij prawym przyciskiem myszy **karty Net.MsmqListener**i wybierz polecenie **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-219">Right-click the **Net.MsmqListener Adapter**, and choose **Properties**.</span></span>  
  
4.  <span data-ttu-id="7a6e5-220">Zmień konto w **logowania** kartę.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-220">Change the account in the **LogOn** tab.</span></span>  
  
5.  <span data-ttu-id="7a6e5-221">W grupie roboczej należy również uruchomić usługę przy użyciu tokenu bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="7a6e5-221">In workgroup, the service must also run using an unrestricted token.</span></span> <span data-ttu-id="7a6e5-222">Aby to zrobić, uruchom następujące polecenie w oknie polecenia:</span><span class="sxs-lookup"><span data-stu-id="7a6e5-222">To do this, run the following in a command window:</span></span>  
  
    ```  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7a6e5-223">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a6e5-223">See Also</span></span>  
 [<span data-ttu-id="7a6e5-224">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="7a6e5-224">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
