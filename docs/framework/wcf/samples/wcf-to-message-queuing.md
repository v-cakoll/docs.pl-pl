---
title: Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: ea0723d178b37b1ff2581981f8f49a6953c913cc
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521547"
---
# <a name="windows-communication-foundation-to-message-queuing"></a>Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów
Niniejszy przykład pokazuje, jak aplikacja Windows Communication Foundation (WCF) może także wysłać komunikat do aplikacji usługi kolejkowania komunikatów (MSMQ). Usługa jest aplikacji konsoli Self-Hosted umożliwia obserwowanie usługi odbieranie wiadomości w kolejce. Usługa i klient nie musi być uruchomiona w tym samym czasie.  
  
 Ta usługa odbiera komunikaty z kolejki i przetwarza zamówienia. Usługa tworzy kolejkę transakcyjną i konfiguruje program obsługi komunikatów odebranego komunikatu, jak pokazano w poniższym przykładowym kodzie.  

```csharp
static void Main(string[] args)  
{  
    if (!MessageQueue.Exists(  
              ConfigurationManager.AppSettings["queueName"]))  
       MessageQueue.Create(  
           ConfigurationManager.AppSettings["queueName"], true);  
        //Connect to the queue  
        MessageQueue Queue = new   
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);  
    Queue.ReceiveCompleted +=   
                 new ReceiveCompletedEventHandler(ProcessOrder);  
    Queue.BeginReceive();  
    Console.WriteLine("Order Service is running");  
    Console.ReadLine();  
}  
```

 Gdy wiadomość zostaje odebrana w kolejce, program obsługi komunikatów `ProcessOrder` zostanie wywołana.  

```csharp
public static void ProcessOrder(Object source,  
    ReceiveCompletedEventArgs asyncResult)  
{  
    try  
    {  
        // Connect to the queue.  
        MessageQueue Queue = (MessageQueue)source;  
        // End the asynchronous receive operation.  
        System.Messaging.Message msg =   
                     Queue.EndReceive(asyncResult.AsyncResult);  
        msg.Formatter = new System.Messaging.XmlMessageFormatter(  
                                new Type[] { typeof(PurchaseOrder) });  
        PurchaseOrder po = (PurchaseOrder) msg.Body;  
        Random statusIndexer = new Random();  
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
        Console.WriteLine("Processing {0} ", po);  
        Queue.BeginReceive();  
    }  
    catch (System.Exception ex)  
    {  
        Console.WriteLine(ex.Message);  
    }  
  
}  
```

 Wyodrębnia usługi `ProcessOrder` treść komunikatu z usługi MSMQ i przetworzy to zamówienie.  
  
 Nazwa kolejki usługi MSMQ jest określony w sekcji appSettings pliku konfiguracji, jak pokazano w poniższym Przykładowa konfiguracja.  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnik odwrotny w ścieżce.  
  
 Klient tworzy zamówienie zakupu i przesyła zamówienia zakupu w zakresie transakcji, jak pokazano w poniższym przykładowym kodzie.  

```csharp
// Create the purchase order  
PurchaseOrder po = new PurchaseOrder();  
// Fill in the details  
...  
  
OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");  
  
MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    client.SubmitPurchaseOrder(ordermsg);  
    scope.Complete();  
}  
Console.WriteLine("Order has been submitted:{0}", po);  
  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```

 Klient używa niestandardowego klienta w prawidłowej kolejności do wysyłania wiadomości usługi MSMQ do kolejki. Ponieważ aplikacja, która odbiera i przetwarza komunikat jest aplikacją usługi MSMQ, a nie aplikacji WCF, istnieje nie niejawne Umowa serwisowa między dwiema aplikacjami. Dlatego nie można utworzyć serwera proxy, korzystając z narzędzia Svcutil.exe w tym scenariuszu.  
  
 Klient niestandardowy jest zasadniczo taki sam dla wszystkich aplikacji WCF, które używają `MsmqIntegration` powiązania do wysyłania wiadomości. W odróżnieniu od innych klientów nie obejmuje szereg operacji usługi. Jest tylko operacja komunikatu przesyłania.  

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor  
{  
    public OrderProcessorClient(){}  
  
    public OrderProcessorClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SubmitPurchaseOrder(msg);  
    }  
}  
```

 Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Możesz zobaczyć komunikaty odbierania usługi z klienta. Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta. Należy zauważyć, że ponieważ kolejkowania wiadomości jest używany, klient i usługa musi być uruchomiona w tym samym czasie. Na przykład można uruchomić klienta, zamknij go, a następnie uruchom usługi i nadal będzie ona otrzymywać jego wiadomości.  
  
> [!NOTE]
>  Ten przykładowy skrypt wymaga instalacji usługi kolejkowania komunikatów. Zapoznaj się z instrukcjami instalacji w [usługi kolejkowania komunikatów](https://go.microsoft.com/fwlink/?LinkId=94968).  
  
### <a name="to-setup-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny. Jeśli kolejka nie jest obecny, będzie utworzyć usługę. Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.  
  
    1.  Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozwiń **funkcji** kartę.  
  
    3.  Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.  
  
    4.  Sprawdź **transakcyjna** pole.  
  
    5.  Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.  
  
3.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym komputerze, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1.  Skopiuj pliki programu usługi z folderu \service\bin\ w folderze specyficzny dla języka na komputerze usługi.  
  
2.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.  
  
3.  W pliku Client.exe.config, Zmień adres punktu końcowego klienta do określania nazwy komputera usługi, a nie ".".  
  
4.  Na komputerze usługi Service.exe należy uruchomić z wiersza polecenia.  
  
5.  Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Usługa kolejkowania komunikatów](https://go.microsoft.com/fwlink/?LinkId=94968)
