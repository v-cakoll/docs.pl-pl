---
title: Sesje i kolejki
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 8a342b185c7965e9ee0ff9941a09e00fc392ad4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144102"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="6f02b-102">Sesje i kolejki</span><span class="sxs-lookup"><span data-stu-id="6f02b-102">Sessions and Queues</span></span>
<span data-ttu-id="6f02b-103">W tym przykładzie pokazano, jak wysyłać i odbierać zestaw powiązanych wiadomości w komunikacji w kolejce za przejmując usługi kolejkowania wiadomości (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="6f02b-103">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="6f02b-104">W tym przykładzie użyto `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="6f02b-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="6f02b-105">Usługa jest samodzielną aplikacją konsoli, która umożliwia obserwowanie usługi odbierającej wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="6f02b-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f02b-106">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="6f02b-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6f02b-107">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6f02b-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6f02b-108">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="6f02b-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6f02b-109">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="6f02b-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6f02b-110">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6f02b-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="6f02b-111">W komunikacji w kolejce klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="6f02b-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="6f02b-112">Dokładniej, klient wysyła wiadomości do kolejki.</span><span class="sxs-lookup"><span data-stu-id="6f02b-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="6f02b-113">Usługa odbiera wiadomości z kolejki.</span><span class="sxs-lookup"><span data-stu-id="6f02b-113">The service receives messages from the queue.</span></span> <span data-ttu-id="6f02b-114">W związku z tym usługi i klienta, nie muszą być uruchomione w tym samym czasie do komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="6f02b-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="6f02b-115">Czasami klient wysyła zestaw wiadomości, które są ze sobą powiązane w grupie.</span><span class="sxs-lookup"><span data-stu-id="6f02b-115">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="6f02b-116">Gdy wiadomości muszą być przetwarzane razem lub w określonej kolejności, kolejka może służyć do grupowania ich razem, do przetwarzania przez jedną aplikację odbierającą.</span><span class="sxs-lookup"><span data-stu-id="6f02b-116">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="6f02b-117">Jest to szczególnie ważne, gdy istnieje kilka aplikacji odbierających na grupie serwerów i jest konieczne, aby upewnić się, że grupa wiadomości jest przetwarzana przez tę samą aplikację odbierającą.</span><span class="sxs-lookup"><span data-stu-id="6f02b-117">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="6f02b-118">Sesje w kolejce to mechanizm używany do wysyłania i odbierania powiązanego zestawu wiadomości, które muszą zostać przetworzone jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="6f02b-118">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="6f02b-119">Sesje w kolejce wymagają transakcji do wykazania tego wzorca.</span><span class="sxs-lookup"><span data-stu-id="6f02b-119">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="6f02b-120">W przykładzie klient wysyła kilka komunikatów do usługi w ramach sesji w zakresie pojedynczej transakcji.</span><span class="sxs-lookup"><span data-stu-id="6f02b-120">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="6f02b-121">Umowa serwisowa `IOrderTaker`jest , która definiuje usługę jednokierunkową, która nadaje się do użytku z kolejkami.</span><span class="sxs-lookup"><span data-stu-id="6f02b-121">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="6f02b-122">Używane <xref:System.ServiceModel.SessionMode> w umowie pokazane w poniższym przykładowym kodzie wskazuje, że wiadomości są częścią sesji.</span><span class="sxs-lookup"><span data-stu-id="6f02b-122">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

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

 <span data-ttu-id="6f02b-123">Usługa definiuje operacje usługi w taki sposób, że pierwsza operacja rejestruje się w transakcji, ale nie automatycznie zakończyć transakcję.</span><span class="sxs-lookup"><span data-stu-id="6f02b-123">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="6f02b-124">Kolejne operacje również zarejestrować w tej samej transakcji, ale nie automatycznie zakończyć.</span><span class="sxs-lookup"><span data-stu-id="6f02b-124">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="6f02b-125">Ostatnia operacja w sesji automatycznie kończy transakcję.</span><span class="sxs-lookup"><span data-stu-id="6f02b-125">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="6f02b-126">W związku z tym ta sama transakcja jest używana dla kilku wywołań operacji w umowie serwisowej.</span><span class="sxs-lookup"><span data-stu-id="6f02b-126">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="6f02b-127">Jeśli którakolwiek z operacji zgłosić wyjątek, a następnie transakcja wycofuje i sesji jest odłożony z powrotem do kolejki.</span><span class="sxs-lookup"><span data-stu-id="6f02b-127">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="6f02b-128">Po pomyślnym zakończeniu ostatniej operacji transakcja jest zatwierdzana.</span><span class="sxs-lookup"><span data-stu-id="6f02b-128">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="6f02b-129">Usługa używa `PerSession` jako <xref:System.ServiceModel.InstanceContextMode> do odbierania wszystkich wiadomości w sesji w tym samym wystąpieniu usługi.</span><span class="sxs-lookup"><span data-stu-id="6f02b-129">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

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

 <span data-ttu-id="6f02b-130">Usługa jest hostowana samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="6f02b-130">The service is self hosted.</span></span> <span data-ttu-id="6f02b-131">Podczas korzystania z transportu usługi MSMQ używana kolejka musi zostać utworzona z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="6f02b-131">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="6f02b-132">Można to zrobić ręcznie lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="6f02b-132">This can be done manually or through code.</span></span> <span data-ttu-id="6f02b-133">W tym przykładzie <xref:System.Messaging> usługa zawiera kod, aby sprawdzić istnienie kolejki i tworzy go, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="6f02b-133">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="6f02b-134">Nazwa kolejki jest odczytywana z <xref:System.Configuration.ConfigurationManager.AppSettings%2A> pliku konfiguracji przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="6f02b-134">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

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

 <span data-ttu-id="6f02b-135">Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6f02b-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="6f02b-136">Punkt końcowy usługi jest zdefiniowany w sekcji system.serviceModel pliku konfiguracji `netMsmqBinding` i określa powiązanie.</span><span class="sxs-lookup"><span data-stu-id="6f02b-136">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
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
  
 <span data-ttu-id="6f02b-137">Klient tworzy zakres transakcji.</span><span class="sxs-lookup"><span data-stu-id="6f02b-137">The client creates a transaction scope.</span></span> <span data-ttu-id="6f02b-138">Wszystkie wiadomości w sesji są wysyłane do kolejki w zakresie transakcji, co powoduje, że są traktowane jako jednostki atomowej, gdzie wszystkie wiadomości zakończyć się powodzeniem lub niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6f02b-138">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="6f02b-139">Transakcja jest zatwierdzana <xref:System.Transactions.TransactionScope.Complete%2A>przez wywołanie .</span><span class="sxs-lookup"><span data-stu-id="6f02b-139">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

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
> <span data-ttu-id="6f02b-140">Można użyć tylko jednej transakcji dla wszystkich wiadomości w sesji i wszystkie wiadomości w sesji muszą być wysyłane przed zatwierdzeniem transakcji.</span><span class="sxs-lookup"><span data-stu-id="6f02b-140">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="6f02b-141">Zamknięcie klienta zamyka sesję.</span><span class="sxs-lookup"><span data-stu-id="6f02b-141">Closing the client closes the session.</span></span> <span data-ttu-id="6f02b-142">W związku z tym klient musi zostać zamknięty przed zakończeniem transakcji, aby wysłać wszystkie wiadomości w sesji do kolejki.</span><span class="sxs-lookup"><span data-stu-id="6f02b-142">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="6f02b-143">Po uruchomieniu przykładu działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="6f02b-143">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="6f02b-144">Możesz zobaczyć, że usługa odbiera wiadomości od klienta.</span><span class="sxs-lookup"><span data-stu-id="6f02b-144">You can see the service receive messages from the client.</span></span> <span data-ttu-id="6f02b-145">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="6f02b-145">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="6f02b-146">Należy zauważyć, że ponieważ kolejkowanie jest w użyciu, klient i usługa nie muszą być uruchomione w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="6f02b-146">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="6f02b-147">Można uruchomić klienta, zamknąć go, a następnie uruchomić usługę i nadal odbiera swoje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="6f02b-147">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="6f02b-148">Na kliencie.</span><span class="sxs-lookup"><span data-stu-id="6f02b-148">On the client.</span></span>  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="6f02b-149">W serwisie.</span><span class="sxs-lookup"><span data-stu-id="6f02b-149">On the service.</span></span>  
  
```console  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6f02b-150">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="6f02b-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6f02b-151">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6f02b-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6f02b-152">Aby utworzyć wersję C#, C++ lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6f02b-152">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6f02b-153">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6f02b-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="6f02b-154">Domyślnie z <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczenia transportu jest włączona.</span><span class="sxs-lookup"><span data-stu-id="6f02b-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="6f02b-155">Istnieją dwie odpowiednie właściwości zabezpieczeń transportu usługi MSMQ <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a mianowicie i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` Domyślnie tryb uwierzytelniania jest `Windows` ustawiony, a poziom ochrony jest ustawiony na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="6f02b-155">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="6f02b-156">Aby usługa MSMQ udostępniała funkcję uwierzytelniania i podpisywania, musi ona być częścią domeny, a opcja integracji usługi Active Directory dla usługi MSMQ musi być zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="6f02b-156">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="6f02b-157">Jeśli uruchomisz ten przykład na komputerze, który nie spełnia tych kryteriów, zostanie wyświetlony błąd.</span><span class="sxs-lookup"><span data-stu-id="6f02b-157">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="6f02b-158">Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej lub bez integracji z usługą Active Directory</span><span class="sxs-lookup"><span data-stu-id="6f02b-158">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="6f02b-159">Jeśli komputer nie należy do domeny lub nie ma zainstalowanej integracji z aktywną funkcją `None` katalogową, wyłącz zabezpieczenia transportu, ustawiając na poziomie trybu uwierzytelniania i ochrony, jak pokazano w poniższej przykładowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6f02b-159">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
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
  
2. <span data-ttu-id="6f02b-160">Przed uruchomieniem przykładu upewnij się, że konfiguracja jest zmieniana zarówno na serwerze, jak i na kliencie.</span><span class="sxs-lookup"><span data-stu-id="6f02b-160">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6f02b-161">Ustawienie trybu `None` zabezpieczeń na <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>równoważne `Message` z `None`ustawieniem <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, i zabezpieczeń do .</span><span class="sxs-lookup"><span data-stu-id="6f02b-161">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
