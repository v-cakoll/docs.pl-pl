---
title: Niestandardowe demultipleksowanie
ms.date: 03/30/2017
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
ms.openlocfilehash: 1542743a6e1658bad162d7ee9ca73e6b9b0444e2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43803424"
---
# <a name="custom-demux"></a><span data-ttu-id="359ce-102">Niestandardowe demultipleksowanie</span><span class="sxs-lookup"><span data-stu-id="359ce-102">Custom Demux</span></span>
<span data-ttu-id="359ce-103">Niniejszy przykład pokazuje, jak nagłówków wiadomości usługi MSMQ mogą być mapowane na operacje innej usługi, aby Windows Communication Foundation (WCF) usługi używające <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nie są ograniczone do przy użyciu jednej operacji usługi, jak pokazano w [ Wiadomości usługi MSMQ programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) i [Windows Communication Foundation do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) przykładów.</span><span class="sxs-lookup"><span data-stu-id="359ce-103">This sample demonstrates how MSMQ message headers can be mapped to different service operations so that Windows Communication Foundation (WCF) services that use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> are not limited to using one service operation as demonstrated in the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) and [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) samples.</span></span>  
  
 <span data-ttu-id="359ce-104">Usługi w tym przykładzie to aplikacja konsoli Self-Hosted umożliwiające zaobserwować, że usługa, która odbiera wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="359ce-104">The service in this sample is a self-hosted console application to enable you to observe the service that receives queued messages.</span></span>  
  
 <span data-ttu-id="359ce-105">Umowa serwisowa jest `IOrderProcessor`i umożliwia zdefiniowanie usługi jednokierunkowej, który jest odpowiedni do użytku z kolejki.</span><span class="sxs-lookup"><span data-stu-id="359ce-105">The service contract is `IOrderProcessor`, and defines a one-way service that is suitable for use with queues.</span></span>  

```csharp
[ServiceContract]  
[KnownType(typeof(PurchaseOrder))]  
[KnownType(typeof(String))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Name = "SubmitPurchaseOrder")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
  
    [OperationContract(IsOneWay = true, Name = "CancelPurchaseOrder")]  
    void CancelPurchaseOrder(MsmqMessage<string> ponumber);  
}  
```

 <span data-ttu-id="359ce-106">Wiadomości usługi MSMQ nie ma nagłówek akcji.</span><span class="sxs-lookup"><span data-stu-id="359ce-106">An MSMQ message does not have an Action header.</span></span> <span data-ttu-id="359ce-107">Nie jest możliwe do mapowania różnych wiadomości usługi MSMQ kontrakty operacji automatycznie.</span><span class="sxs-lookup"><span data-stu-id="359ce-107">It is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="359ce-108">W związku z tym może istnieć tylko jedno operacji kontraktu.</span><span class="sxs-lookup"><span data-stu-id="359ce-108">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="359ce-109">To ograniczenie implementuje usługi <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> metody <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="359ce-109">To overcome this limitation, the service implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method of the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface.</span></span> <span data-ttu-id="359ce-110"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> Metoda umożliwia usłudze mapy dany nagłówek komunikatu do operacji określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="359ce-110">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method enables the service to map a given header of the message to a particular service operation.</span></span> <span data-ttu-id="359ce-111">W tym przykładzie nagłówek Etykieta wiadomości jest mapowany do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="359ce-111">In this sample, the message's label header is mapped to the service operations.</span></span> <span data-ttu-id="359ce-112">`Name` Parametr kontrakt operacji określa operacji usługi, które muszą być wysyłane etykiety podanym komunikatem.</span><span class="sxs-lookup"><span data-stu-id="359ce-112">The `Name` parameter of the operation contract determines which service operation must be dispatched for a given message label.</span></span> <span data-ttu-id="359ce-113">Na przykład jeśli nagłówek Etykieta wiadomości zawiera "SubmitPurchaseOrder", "SubmitPurchaseOrder" Operacja usługi zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="359ce-113">For example, if the message's label header contains "SubmitPurchaseOrder", the "SubmitPurchaseOrder" service operation is invoked.</span></span>  

```csharp
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```

 <span data-ttu-id="359ce-114">Usługa musi implementować <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> metody <xref:System.ServiceModel.Description.IContractBehavior> interfejsu, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="359ce-114">The service must implement the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> method of the <xref:System.ServiceModel.Description.IContractBehavior> interface as shown in the following sample code.</span></span> <span data-ttu-id="359ce-115">Dotyczy to niestandardowa `OperationSelector` do środowiska uruchomieniowego usługi framework wysyłania.</span><span class="sxs-lookup"><span data-stu-id="359ce-115">This applies the custom `OperationSelector` to the service framework dispatch runtime.</span></span>  

```csharp
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```

 <span data-ttu-id="359ce-116">Wiadomość musi przechodzić przez dyspozytora <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> przed przejściem do parametr OperationSelector.</span><span class="sxs-lookup"><span data-stu-id="359ce-116">A message must pass through the dispatcher's <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> before getting to the OperationSelector.</span></span> <span data-ttu-id="359ce-117">Domyślnie wiadomość zostanie odrzucone, jeśli nie można odnaleźć swoje działania na żadną umową implementowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="359ce-117">By default a message is rejected if its action cannot be found on any contract implemented by the service.</span></span> <span data-ttu-id="359ce-118">Aby uniknąć tego wyboru, firma Microsoft zaimplementowania <xref:System.ServiceModel.Description.IEndpointBehavior> o nazwie `MatchAllFilterBehavior`, dzięki czemu każdy komunikat do przekazywania `ContractFilter` , stosując <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="359ce-118">To avoid this check, we implement an <xref:System.ServiceModel.Description.IEndpointBehavior> named `MatchAllFilterBehavior`, which allows any message to pass through the `ContractFilter` by applying the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> as follows.</span></span>  

```csharp
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```
  
 <span data-ttu-id="359ce-119">Gdy wiadomość zostaje odebrana przez usługę, wywoływane jest operacja odpowiednią usługę, korzystając z informacji podanych w nagłówku etykiety.</span><span class="sxs-lookup"><span data-stu-id="359ce-119">When a message is received by the service, the appropriate service operation is dispatched using the information provided by the label header.</span></span> <span data-ttu-id="359ce-120">Treść komunikatu jest przeprowadzona deserializacja `PurchaseOrder` obiektu, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="359ce-120">The body of the message is deserialized into a `PurchaseOrder` object, as shown in the following sample code.</span></span>  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```

 <span data-ttu-id="359ce-121">Usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="359ce-121">The service is self-hosted.</span></span> <span data-ttu-id="359ce-122">Korzystając z usługi MSMQ, kolejki, która jest używana musi zostać utworzona wcześniej.</span><span class="sxs-lookup"><span data-stu-id="359ce-122">When using the MSMQ, the queue that is used must be created in advance.</span></span> <span data-ttu-id="359ce-123">Można to zrobić ręcznie lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="359ce-123">This can be done manually or through code.</span></span> <span data-ttu-id="359ce-124">W tym przykładzie Usługa zawiera kod, aby sprawdzić, czy istnienie kolejki i utworzy go, jeśli kolejka nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="359ce-124">In this sample, the service contains code to check for the existence of the queue and creates it if the queue does not exist.</span></span> <span data-ttu-id="359ce-125">Nazwa kolejki jest do odczytu z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="359ce-125">The queue name is read from the configuration file.</span></span>  

```csharp
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration  
    string queueName = ConfigurationManager.AppSettings["orderQueueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {                 
        ServiceEndpoint endpoint = serviceHost.Description.Endpoints[0];  
        endpoint.Behaviors.Add(new MatchAllFilterBehavior());  
  
        //Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();  
    }  
}  
```

 <span data-ttu-id="359ce-126">Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="359ce-126">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="359ce-127">Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnik odwrotny w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="359ce-127">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="359ce-128">Adres punktu końcowego WCF Określa schemat msmq.formatname i używane host_lokalny na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="359ce-128">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="359ce-129">Poniżej schemat jest adresem prawidłowo sformatowaną kolejki według nazwy formatu MSMQ adresowania wytycznych.</span><span class="sxs-lookup"><span data-stu-id="359ce-129">What follows the scheme is a properly formatted queue address according to the MSMQ Format name addressing guidelines.</span></span>  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="359ce-130">Ten przykładowy skrypt wymaga instalacji [usługi kolejkowania komunikatów](https://go.microsoft.com/fwlink/?LinkId=95143).</span><span class="sxs-lookup"><span data-stu-id="359ce-130">This sample requires the installation of [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=95143).</span></span>  
  
 <span data-ttu-id="359ce-131">Uruchom usługę i uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="359ce-131">Start the service and run the client.</span></span>  
  
 <span data-ttu-id="359ce-132">Następujące dane wyjściowe pojawia się na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="359ce-132">The following output is seen on the client.</span></span>  
  
```  
Placed the order:Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
Canceled the Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="359ce-133">Następujące dane wyjściowe muszą być widoczne w usługę.</span><span class="sxs-lookup"><span data-stu-id="359ce-133">The following output must be seen on the service.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
Processing Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Shipped  
Purchase Order 28fc457a-1a56-4fe0-9dde-156965c21ed6 is canceled  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="359ce-134">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="359ce-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="359ce-135">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="359ce-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="359ce-136">Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny.</span><span class="sxs-lookup"><span data-stu-id="359ce-136">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="359ce-137">Jeśli kolejka nie jest obecny, będzie utworzyć usługę.</span><span class="sxs-lookup"><span data-stu-id="359ce-137">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="359ce-138">Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="359ce-138">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="359ce-139">Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="359ce-139">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="359ce-140">Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="359ce-140">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="359ce-141">Rozwiń **funkcji** kartę.</span><span class="sxs-lookup"><span data-stu-id="359ce-141">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="359ce-142">Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="359ce-142">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="359ce-143">Sprawdź **transakcyjna** pole.</span><span class="sxs-lookup"><span data-stu-id="359ce-143">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="359ce-144">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="359ce-144">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="359ce-145">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="359ce-145">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="359ce-146">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="359ce-146">To run the sample in a single- or cross- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="359ce-147">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="359ce-147">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="359ce-148">Skopiuj pliki programu usługi z folderu \service\bin\ w folderze specyficzny dla języka na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="359ce-148">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="359ce-149">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="359ce-149">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="359ce-150">W pliku Client.exe.config zmienić orderQueueName do określenia nazwy komputera usługi zamiast ".".</span><span class="sxs-lookup"><span data-stu-id="359ce-150">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="359ce-151">Na komputerze usługi Service.exe należy uruchomić z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="359ce-151">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="359ce-152">Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="359ce-152">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="359ce-153">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="359ce-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="359ce-154">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="359ce-154">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="359ce-155">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="359ce-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="359ce-156">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="359ce-156">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a><span data-ttu-id="359ce-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="359ce-157">See Also</span></span>  
 [<span data-ttu-id="359ce-158">Tworzenie kolejek w programie WCF</span><span class="sxs-lookup"><span data-stu-id="359ce-158">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="359ce-159">Usługa kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="359ce-159">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=95143)
