---
title: Sesje i kolejki
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: ce8cdd08f9bc34d03a014b253024a2b756d4c82a
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728451"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="3fd77-102">Sesje i kolejki</span><span class="sxs-lookup"><span data-stu-id="3fd77-102">Sessions and queues</span></span>

<span data-ttu-id="3fd77-103">Ten przykład pokazuje, jak wysyłać i odbierać zestaw powiązanych komunikatów w kolejce komunikacji za pośrednictwem transportu usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="3fd77-103">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="3fd77-104">Ten przykład używa `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="3fd77-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="3fd77-105">Usługa to samodzielna aplikacja konsolowa, która umożliwia obserwowanie usługi do odebrania komunikatów znajdujących się w kolejce.</span><span class="sxs-lookup"><span data-stu-id="3fd77-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3fd77-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="3fd77-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3fd77-107">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3fd77-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3fd77-108">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="3fd77-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3fd77-109">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="3fd77-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3fd77-110">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3fd77-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="3fd77-111">W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="3fd77-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="3fd77-112">Dokładniej, klient wysyła komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="3fd77-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="3fd77-113">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="3fd77-113">The service receives messages from the queue.</span></span> <span data-ttu-id="3fd77-114">W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="3fd77-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="3fd77-115">Czasami klient wysyła zestaw komunikatów, które są powiązane ze sobą w grupie.</span><span class="sxs-lookup"><span data-stu-id="3fd77-115">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="3fd77-116">Gdy wiadomości muszą być przetwarzane razem lub w określonej kolejności, można użyć kolejki w celu pogrupowania ich razem w celu przetworzenia przez pojedynczą aplikację otrzymującą.</span><span class="sxs-lookup"><span data-stu-id="3fd77-116">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="3fd77-117">Jest to szczególnie ważne w przypadku, gdy w grupie serwerów istnieje kilka aplikacji do odebrania, a konieczne jest upewnienie się, że grupa komunikatów jest przetwarzana przez tę samą aplikację otrzymującą.</span><span class="sxs-lookup"><span data-stu-id="3fd77-117">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="3fd77-118">Sesje w kolejce są mechanizmem używanym do wysyłania i odbierania powiązanego zestawu komunikatów, które muszą zostać przetworzone jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="3fd77-118">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="3fd77-119">Sesje w kolejce wymagają transakcji, aby wymusić ten wzorzec.</span><span class="sxs-lookup"><span data-stu-id="3fd77-119">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="3fd77-120">W przykładzie klient wysyła do usługi wiele komunikatów w ramach sesji w ramach jednego z zakresów pojedynczej transakcji.</span><span class="sxs-lookup"><span data-stu-id="3fd77-120">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="3fd77-121">Kontrakt usługi to `IOrderTaker`, który definiuje usługę jednokierunkową, która jest odpowiednia do użycia z kolejkami.</span><span class="sxs-lookup"><span data-stu-id="3fd77-121">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="3fd77-122"><xref:System.ServiceModel.SessionMode> Użycie w umowie pokazanej w następującym przykładowym kodzie wskazuje, że komunikaty są częścią sesji.</span><span class="sxs-lookup"><span data-stu-id="3fd77-122">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

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

 <span data-ttu-id="3fd77-123">Usługa definiuje operacje usługi w taki sposób, że pierwsza operacja jest rejestrowana w transakcji, ale nie powoduje automatycznego wykonania transakcji.</span><span class="sxs-lookup"><span data-stu-id="3fd77-123">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="3fd77-124">Kolejne operacje są rejestrowane również w tej samej transakcji, ale nie są automatycznie uzupełniane.</span><span class="sxs-lookup"><span data-stu-id="3fd77-124">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="3fd77-125">Ostatnia operacja w sesji automatycznie kończy transakcję.</span><span class="sxs-lookup"><span data-stu-id="3fd77-125">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="3fd77-126">W ten sam sposób jest używana w przypadku kilku wywołań operacji w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="3fd77-126">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="3fd77-127">Jeśli jakakolwiek z operacji zgłasza wyjątek, transakcja zostanie wycofana, a sesja zostanie umieszczona w kolejce.</span><span class="sxs-lookup"><span data-stu-id="3fd77-127">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="3fd77-128">Po pomyślnym zakończeniu ostatniej operacji transakcja zostanie zatwierdzona.</span><span class="sxs-lookup"><span data-stu-id="3fd77-128">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="3fd77-129">Usługa używa `PerSession` jako <xref:System.ServiceModel.InstanceContextMode> do odbierania wszystkich komunikatów w sesji w tym samym wystąpieniu usługi.</span><span class="sxs-lookup"><span data-stu-id="3fd77-129">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

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

 <span data-ttu-id="3fd77-130">Usługa jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="3fd77-130">The service is self hosted.</span></span> <span data-ttu-id="3fd77-131">W przypadku korzystania z transportu usługi MSMQ użyta Kolejka musi zostać utworzona z góry.</span><span class="sxs-lookup"><span data-stu-id="3fd77-131">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="3fd77-132">Można to zrobić ręcznie lub przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="3fd77-132">This can be done manually or through code.</span></span> <span data-ttu-id="3fd77-133">W tym przykładzie usługa zawiera <xref:System.Messaging> kod służący do sprawdzania istnienia kolejki i w razie potrzeby tworzy ją.</span><span class="sxs-lookup"><span data-stu-id="3fd77-133">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="3fd77-134">Nazwa kolejki jest odczytywana z pliku konfiguracji przy użyciu <xref:System.Configuration.ConfigurationManager.AppSettings%2A> klasy.</span><span class="sxs-lookup"><span data-stu-id="3fd77-134">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

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

 <span data-ttu-id="3fd77-135">Nazwa kolejki MSMQ jest określona w sekcji appSettings w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3fd77-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="3fd77-136">Punkt końcowy usługi jest zdefiniowany w sekcji System. serviceModel w pliku konfiguracji i określa `netMsmqBinding` powiązanie.</span><span class="sxs-lookup"><span data-stu-id="3fd77-136">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
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
</system.serviceModel>  
```  
  
 <span data-ttu-id="3fd77-137">Klient tworzy zakres transakcji.</span><span class="sxs-lookup"><span data-stu-id="3fd77-137">The client creates a transaction scope.</span></span> <span data-ttu-id="3fd77-138">Wszystkie komunikaty w sesji są wysyłane do kolejki w zakresie transakcji, co sprawia, że może być traktowana jako jednostka niepodzielna, w której wszystkie komunikaty kończą się powodzeniem lub niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3fd77-138">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="3fd77-139">Transakcja jest zatwierdzona przez wywołanie <xref:System.Transactions.TransactionScope.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="3fd77-139">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

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
> <span data-ttu-id="3fd77-140">Można użyć tylko jednej transakcji dla wszystkich komunikatów w sesji i wszystkie komunikaty w sesji muszą być wysyłane przed zatwierdzeniem transakcji.</span><span class="sxs-lookup"><span data-stu-id="3fd77-140">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="3fd77-141">Zamknięcie klienta powoduje zamknięcie sesji programu.</span><span class="sxs-lookup"><span data-stu-id="3fd77-141">Closing the client closes the session.</span></span> <span data-ttu-id="3fd77-142">W związku z tym przed ukończeniem transakcji należy zamknąć klienta w celu wysłania wszystkich komunikatów w sesji do kolejki.</span><span class="sxs-lookup"><span data-stu-id="3fd77-142">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="3fd77-143">Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="3fd77-143">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="3fd77-144">Możesz zobaczyć, że usługa odbiera komunikaty od klienta.</span><span class="sxs-lookup"><span data-stu-id="3fd77-144">You can see the service receive messages from the client.</span></span> <span data-ttu-id="3fd77-145">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="3fd77-145">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="3fd77-146">Ponieważ kolejkowanie jest w użyciu, klient i usługa nie muszą działać w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="3fd77-146">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="3fd77-147">Można uruchomić klienta programu, zamknąć go, a następnie uruchomić usługę i nadal otrzymywać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3fd77-147">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="3fd77-148">Na kliencie programu.</span><span class="sxs-lookup"><span data-stu-id="3fd77-148">On the client.</span></span>  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="3fd77-149">W usłudze.</span><span class="sxs-lookup"><span data-stu-id="3fd77-149">On the service.</span></span>  
  
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
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="3fd77-150">Konfigurowanie, kompilowanie i uruchamianie przykładu</span><span class="sxs-lookup"><span data-stu-id="3fd77-150">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3fd77-151">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fd77-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3fd77-152">Aby skompilować wersję rozwiązania dla języka C#, C++ lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fd77-152">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3fd77-153">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fd77-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="3fd77-154">Domyślnie z opcją <xref:System.ServiceModel.NetMsmqBinding>jest włączona funkcja zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="3fd77-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="3fd77-155">Istnieją <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> dwie istotne właściwości zabezpieczenia transportu usługi MSMQ, a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` mianowicie tryb uwierzytelniania jest ustawiony na `Windows` , a poziom ochrony jest ustawiony na. `Sign`</span><span class="sxs-lookup"><span data-stu-id="3fd77-155">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="3fd77-156">Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny, a dla usługi MSMQ należy zainstalować opcję Integracja z usługą Active Directory.</span><span class="sxs-lookup"><span data-stu-id="3fd77-156">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="3fd77-157">Jeśli ten przykład zostanie uruchomiony na komputerze, który nie spełnia tych kryteriów, zostanie wyświetlony komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="3fd77-157">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>  
  
### <a name="run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="3fd77-158">Uruchom przykład na komputerze przyłączonym do grupy roboczej</span><span class="sxs-lookup"><span data-stu-id="3fd77-158">Run the sample on a computer joined to a workgroup</span></span>  
  
1. <span data-ttu-id="3fd77-159">Jeśli komputer nie jest częścią domeny lub nie zainstalowano integracji z usługą Active Directory, Wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom ochrony `None` tak jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="3fd77-159">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
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
  
2. <span data-ttu-id="3fd77-160">Przed uruchomieniem przykładu należy zmienić konfigurację na serwerze i kliencie programu.</span><span class="sxs-lookup"><span data-stu-id="3fd77-160">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3fd77-161">Ustawienie trybu zabezpieczeń `None` jest równoważne ustawieniu <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>i `Message` zabezpieczenia z. `None`</span><span class="sxs-lookup"><span data-stu-id="3fd77-161">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
