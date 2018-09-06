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
# <a name="custom-demux"></a>Niestandardowe demultipleksowanie
Niniejszy przykład pokazuje, jak nagłówków wiadomości usługi MSMQ mogą być mapowane na operacje innej usługi, aby Windows Communication Foundation (WCF) usługi używające <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nie są ograniczone do przy użyciu jednej operacji usługi, jak pokazano w [ Wiadomości usługi MSMQ programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) i [Windows Communication Foundation do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) przykładów.  
  
 Usługi w tym przykładzie to aplikacja konsoli Self-Hosted umożliwiające zaobserwować, że usługa, która odbiera wiadomości w kolejce.  
  
 Umowa serwisowa jest `IOrderProcessor`i umożliwia zdefiniowanie usługi jednokierunkowej, który jest odpowiedni do użytku z kolejki.  

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

 Wiadomości usługi MSMQ nie ma nagłówek akcji. Nie jest możliwe do mapowania różnych wiadomości usługi MSMQ kontrakty operacji automatycznie. W związku z tym może istnieć tylko jedno operacji kontraktu. To ograniczenie implementuje usługi <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> metody <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interfejsu. <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> Metoda umożliwia usłudze mapy dany nagłówek komunikatu do operacji określonej usługi. W tym przykładzie nagłówek Etykieta wiadomości jest mapowany do operacji usługi. `Name` Parametr kontrakt operacji określa operacji usługi, które muszą być wysyłane etykiety podanym komunikatem. Na przykład jeśli nagłówek Etykieta wiadomości zawiera "SubmitPurchaseOrder", "SubmitPurchaseOrder" Operacja usługi zostanie wywołana.  

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

 Usługa musi implementować <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> metody <xref:System.ServiceModel.Description.IContractBehavior> interfejsu, jak pokazano w poniższym przykładowym kodzie. Dotyczy to niestandardowa `OperationSelector` do środowiska uruchomieniowego usługi framework wysyłania.  

```csharp
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```

 Wiadomość musi przechodzić przez dyspozytora <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> przed przejściem do parametr OperationSelector. Domyślnie wiadomość zostanie odrzucone, jeśli nie można odnaleźć swoje działania na żadną umową implementowane przez usługę. Aby uniknąć tego wyboru, firma Microsoft zaimplementowania <xref:System.ServiceModel.Description.IEndpointBehavior> o nazwie `MatchAllFilterBehavior`, dzięki czemu każdy komunikat do przekazywania `ContractFilter` , stosując <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> w następujący sposób.  

```csharp
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```
  
 Gdy wiadomość zostaje odebrana przez usługę, wywoływane jest operacja odpowiednią usługę, korzystając z informacji podanych w nagłówku etykiety. Treść komunikatu jest przeprowadzona deserializacja `PurchaseOrder` obiektu, jak pokazano w poniższym przykładowym kodzie.  

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

 Usługa jest samodzielnie hostowana. Korzystając z usługi MSMQ, kolejki, która jest używana musi zostać utworzona wcześniej. Można to zrobić ręcznie lub za pomocą kodu. W tym przykładzie Usługa zawiera kod, aby sprawdzić, czy istnienie kolejki i utworzy go, jeśli kolejka nie istnieje. Nazwa kolejki jest do odczytu z pliku konfiguracji.  

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

 Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji.  
  
> [!NOTE]
>  Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnik odwrotny w ścieżce. Adres punktu końcowego WCF Określa schemat msmq.formatname i używane host_lokalny na komputerze lokalnym. Poniżej schemat jest adresem prawidłowo sformatowaną kolejki według nazwy formatu MSMQ adresowania wytycznych.  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  Ten przykładowy skrypt wymaga instalacji [usługi kolejkowania komunikatów](https://go.microsoft.com/fwlink/?LinkId=95143).  
  
 Uruchom usługę i uruchom klienta.  
  
 Następujące dane wyjściowe pojawia się na komputerze klienckim.  
  
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
  
 Następujące dane wyjściowe muszą być widoczne w usługę.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny. Jeśli kolejka nie jest obecny, będzie utworzyć usługę. Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.  
  
    1.  Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozwiń **funkcji** kartę.  
  
    3.  Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.  
  
    4.  Sprawdź **transakcyjna** pole.  
  
    5.  Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.  
  
3.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1.  Skopiuj pliki programu usługi z folderu \service\bin\ w folderze specyficzny dla języka na komputerze usługi.  
  
2.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.  
  
3.  W pliku Client.exe.config zmienić orderQueueName do określenia nazwy komputera usługi zamiast ".".  
  
4.  Na komputerze usługi Service.exe należy uruchomić z wiersza polecenia.  
  
5.  Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Usługa kolejkowania komunikatów](https://go.microsoft.com/fwlink/?LinkId=95143)
