---
title: Niestandardowe demultipleksowanie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
caps.latest.revision: "41"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d4a460adfb8076f5d2c0fe273511e6de80be4ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-demux"></a>Niestandardowe demultipleksowanie
W przykładzie pokazano, jak nagłówki wiadomości usługi MSMQ mogą być mapowane do operacji innej usługi, aby [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi używające <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nie są ograniczone do przy użyciu jednej operacji usługi, jak pokazano w [usługi kolejkowania komunikatów Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) i [Windows Communication Foundation, do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) próbek.  
  
 Usługi w tym przykładzie jest aplikacji konsoli siebie umożliwiają przyjrzeć się, że usługa, która odbiera wiadomości w kolejce.  
  
 Kontrakt usługi jest `IOrderProcessor`i definiuje usługę jednokierunkowe, które są odpowiednie do użycia w przypadku kolejek.  
  
```  
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
  
 Wiadomości MSMQ nie ma nagłówka Action. Nie jest możliwe do mapowania różnych wiadomości usługi MSMQ kontrakty operacji automatycznie. W związku z tym może istnieć tylko jeden kontrakt operacji. Aby obejść to ograniczenie implementuje usługi <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> metody <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interfejsu. <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> — Metoda włącza usługę zamapować określony nagłówek komunikatu z operacją określonej usługi. W tym przykładzie nagłówek Etykieta wiadomości jest mapowany do operacji usługi. `Name` Parametr kontrakt operacji określa operacji usługi, które muszą być wysyłane etykiety podanym komunikatem. Na przykład jeśli nagłówek Etykieta wiadomości zawiera "SubmitPurchaseOrder", "SubmitPurchaseOrder" usługi wywołaniu operacji.  
  
```  
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```  
  
 Usługa musi implementować <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> metody <xref:System.ServiceModel.Description.IContractBehavior> interfejsu, jak pokazano w poniższym kodzie próbki. Dotyczy to niestandardowa `OperationSelector` do środowiska uruchomieniowego wysyłania framework usługi.  
  
```  
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```  
  
 Wiadomość musi przechodzić przez dyspozytora <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> przed przejściem do parametr OperationSelector. Domyślnie komunikat zostanie odrzucony, jeżeli nie można odnaleźć swoje działania na żadną umową zaimplementowanych przez usługę. Aby uniknąć tego wyboru, wdrożymy <xref:System.ServiceModel.Description.IEndpointBehavior> o nazwie `MatchAllFilterBehavior`, dzięki czemu wszystkie wiadomości do przekazywania `ContractFilter` przez zastosowanie <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> w następujący sposób.  
  
```  
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```  
  
 Po odebraniu komunikatu przez usługę wywoływane jest operacja odpowiednią usługę, korzystając z informacji podanych w nagłówku etykiety. Deserializacji treści komunikatu do `PurchaseOrder` obiektów, jak pokazano w poniższym kodzie próbki.  
  
```  
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```  
  
 Usługa jest samodzielnie hostowana. Przy użyciu usługi MSMQ, kolejki, która jest używana musi zostać utworzona z wyprzedzeniem. Można to zrobić ręcznie lub za pomocą kodu. W tym przykładzie Usługa zawiera kod, aby sprawdzić obecność kolejki i tworzy go, jeśli kolejka nie istnieje. Nazwa kolejki jest do odczytu z pliku konfiguracji.  
  
```  
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
>  Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnika w jego ścieżki. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Adres punktu końcowego określa schematu postać msmq.formatname i korzysta z hosta lokalnego na komputerze lokalnym. Poniżej schemat jest adresem kolejki poprawnie sformatowana zgodnie z nazwy formatu MSMQ adresowania wytyczne.  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  W tym przykładzie wymaga zainstalowania [usługi kolejkowania komunikatów](http://go.microsoft.com/fwlink/?LinkId=95143).  
  
 Uruchom usługę i uruchom klienta.  
  
 Następujące dane wyjściowe jest widoczna na kliencie.  
  
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
  
 Następujące dane wyjściowe muszą być widoczne w usłudze.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Jeśli usługa jest uruchamiana pierwszy, sprawdza, upewnij się, że kolejka jest obecny. Jeśli kolejka nie jest obecny, będzie utworzyć usługę. Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub można go utworzyć za pomocą Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.  
  
    1.  Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozwiń węzeł **funkcje** kartę.  
  
    3.  Kliknij prawym przyciskiem myszy **kolejki wiadomości prywatne**i wybierz **nowy**, **kolejki prywatnej**.  
  
    4.  Sprawdź **transakcyjna** pole.  
  
    5.  Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.  
  
3.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na komputerach  
  
1.  Skopiuj pliki programu usługi z folderu \service\bin\ w folderze danego języka na komputerze usługi.  
  
2.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka na komputerze klienckim.  
  
3.  W pliku Client.exe.config zmienić orderQueueName do określenia nazwy komputera usługi zamiast ".".  
  
4.  Na komputerze, usługi uruchom Service.exe z wiersza polecenia.  
  
5.  Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi kolejkowania wiadomości w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Usługi kolejkowania komunikatów](http://go.microsoft.com/fwlink/?LinkId=95143)
