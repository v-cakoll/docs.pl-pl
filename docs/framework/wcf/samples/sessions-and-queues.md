---
title: Sesje i kolejki
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 5e8cd975c27e5e7a833e53da7a03c06b10d14ca7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404496"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="9fbdb-102">Sesje i kolejki</span><span class="sxs-lookup"><span data-stu-id="9fbdb-102">Sessions and Queues</span></span>
<span data-ttu-id="9fbdb-103">W tym przykładzie pokazano, jak wysyłać i odbierać zbiór pokrewne wiadomości w komunikacie w kolejce za pomocą transportu usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="9fbdb-103">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="9fbdb-104">W tym przykładzie użyto `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="9fbdb-105">Usługa jest aplikacji konsoli Self-Hosted umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fbdb-106">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9fbdb-107">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9fbdb-108">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="9fbdb-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9fbdb-109">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9fbdb-110">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="9fbdb-111">W komunikacie w kolejce klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="9fbdb-112">Mówiąc ściślej klient wysyła komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="9fbdb-113">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-113">The service receives messages from the queue.</span></span> <span data-ttu-id="9fbdb-114">Usługi i klienta w związku z tym, nie musi być uruchomiona w tym samym czasie do komunikowania się za pomocą kolejki.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="9fbdb-115">Czasami klient wysyła zestaw komunikatów, które są powiązane ze sobą w grupie.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-115">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="9fbdb-116">Gdy muszą zostać przetworzone komunikaty, razem lub w określonej kolejności, kolejki można je pogrupować, do przetworzenia przez aplikację odbierającą jednego.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-116">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="9fbdb-117">Jest to szczególnie ważne w przypadku, gdy istnieje kilka aplikacje odbierające na grupy serwerów i jest zapewnienie, że grupę wiadomości jest przetwarzany przez samą aplikację odbierającą.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-117">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="9fbdb-118">Sesje umieszczonych w kolejce są mechanizmem używanym do wysyłania i odbierania powiązany zestaw komunikatów, które są przetwarzane wszystkie na raz.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-118">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="9fbdb-119">Sesje umieszczonych w kolejce wymagają transakcji wykazują tego wzorca.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-119">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="9fbdb-120">W tym przykładzie klient wysyła komunikaty do usługi w ramach sesji w zakresie pojedynczą transakcję.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-120">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="9fbdb-121">Umowa serwisowa jest `IOrderTaker`, definiujący usługi jednokierunkowej, który jest odpowiedni do użytku z kolejki.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-121">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="9fbdb-122"><xref:System.ServiceModel.SessionMode> Używane w kontrakcie pokazano w następującym przykładowym kodzie wskazuje, czy komunikaty są częścią sesji.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-122">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 <span data-ttu-id="9fbdb-123">Usługa zawiera definicję operacji usługi w taki sposób, rejestruje w ramach transakcji pierwszą operacją, ale nie zostanie automatycznie zakończone transakcji.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-123">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="9fbdb-124">Kolejne operacje również zarejestrować się w tej samej transakcji, ale nie zakończą się automatycznie.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-124">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="9fbdb-125">Ostatniej operacji w sesji są automatycznie wykonuje transakcję.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-125">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="9fbdb-126">W efekcie tej samej transakcji jest używany dla wielu wywołań operacji w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-126">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="9fbdb-127">Jeśli każdej operacji zgłosić wyjątek, wycofanie transakcji, a sesja jest ponownie umieszczone w kolejce.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-127">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="9fbdb-128">Po pomyślnym zakończeniu ostatniej operacji transakcja została zatwierdzona.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-128">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="9fbdb-129">Używa usługi `PerSession` jako <xref:System.ServiceModel.InstanceContextMode> odbierać wszystkie wiadomości w sesji na tym samym wystąpieniu usługi.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-129">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +   
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 <span data-ttu-id="9fbdb-130">Usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-130">The service is self hosted.</span></span> <span data-ttu-id="9fbdb-131">Za pomocą transportu MSMQ, kolejki, używane musi zostać utworzona wcześniej.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-131">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="9fbdb-132">Można to zrobić ręcznie lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-132">This can be done manually or through code.</span></span> <span data-ttu-id="9fbdb-133">W tym przykładzie Usługa zawiera <xref:System.Messaging> kodu pod kątem istnienia kolejki i utworzy go, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-133">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="9fbdb-134">Nazwa kolejki są odczytywane z pliku konfiguracji przy użyciu <xref:System.Configuration.ConfigurationManager.AppSettings%2A> klasy.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-134">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();   
    }  
}  
```

 <span data-ttu-id="9fbdb-135">Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="9fbdb-136">Punkt końcowy usługi jest zdefiniowany w sekcji system.serviceModel pliku konfiguracji i określa `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-136">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
<system.serviceModel>  
```  
  
 <span data-ttu-id="9fbdb-137">Klient tworzy zakres transakcji.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-137">The client creates a transaction scope.</span></span> <span data-ttu-id="9fbdb-138">Wszystkie komunikaty w sesji są wysyłane do kolejki w zakresie transakcji, co powoduje powinien być traktowany jako pojedynczej Atomowej jednostki, której wszystkie komunikaty sukces lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-138">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="9fbdb-139">Transakcja została zatwierdzona przez wywołanie metody <xref:System.Transactions.TransactionScope.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-139">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();                  
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
>  <span data-ttu-id="9fbdb-140">Można użyć tylko w ramach jednej transakcji dla wszystkich komunikatów w sesji, a wszystkie komunikaty w sesji muszą być wysyłane przed zatwierdzeniem transakcji.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-140">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="9fbdb-141">Zamykanie klient zamyka sesję.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-141">Closing the client closes the session.</span></span> <span data-ttu-id="9fbdb-142">W związku z tym klient musi być zamknięty ukończenia transakcji do wysłania wszystkie komunikaty w sesji do kolejki.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-142">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="9fbdb-143">Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-143">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="9fbdb-144">Możesz zobaczyć komunikaty odbierania usługi z klienta.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-144">You can see the service receive messages from the client.</span></span> <span data-ttu-id="9fbdb-145">Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-145">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="9fbdb-146">Należy zauważyć, że ponieważ kolejkowania wiadomości jest używany, klient i usługa musi być uruchomiona w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-146">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="9fbdb-147">Można uruchomić klienta, zamknij go, a następnie uruchom usługi i wciąż otrzymuje jego wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-147">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="9fbdb-148">Na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-148">On the client.</span></span>  
  
```  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="9fbdb-149">W usłudze.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-149">On the service.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9fbdb-150">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="9fbdb-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9fbdb-151">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9fbdb-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9fbdb-152">Aby kompilować rozwiązania w wersji języka C#, C++ lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9fbdb-152">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9fbdb-153">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9fbdb-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="9fbdb-154">Domyślnie <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczenia transportu jest włączona.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="9fbdb-155">Istnieją dwie właściwości istotnych dla zabezpieczeń transportu usługi MSMQ są <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` domyślny tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-155">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="9fbdb-156">Dla usługi MSMQ zapewniać uwierzytelnianie i podpisywania funkcji musi być częścią domeny i musi być zainstalowany opcji integracji usługi active directory dla usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-156">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="9fbdb-157">Jeśli w tym przykładzie jest uruchomiony na komputerze, który nie spełnia tych kryteriów otrzymasz komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-157">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="9fbdb-158">Do uruchomienia przykładu na komputer przyłączony do grupy roboczej lub bez integracji usługi active directory</span><span class="sxs-lookup"><span data-stu-id="9fbdb-158">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="9fbdb-159">Jeśli komputer nie jest częścią domeny lub nie ma zainstalowaną integracją usługi active directory, należy wyłączyć zabezpieczenia transportu, ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-159">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->      
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="9fbdb-160">Upewnij się, zmień konfigurację serwera i klienta, przed uruchomieniem przykładu.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-160">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9fbdb-161">Ustawianie trybu zabezpieczeń do `None` jest odpowiednikiem ustawienia <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, i `Message` security `None`.</span><span class="sxs-lookup"><span data-stu-id="9fbdb-161">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fbdb-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fbdb-162">See Also</span></span>
