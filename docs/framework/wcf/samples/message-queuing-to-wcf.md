---
title: Obsługa kolejek komunikatów programu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 983fd2ef7338e24c67e3556849e73c2feaf97a60
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525701"
---
# <a name="message-queuing-to-windows-communication-foundation"></a>Obsługa kolejek komunikatów programu Windows Communication Foundation
Niniejszy przykład pokazuje, jak aplikacja usługi kolejkowania komunikatów (MSMQ) można wysłać wiadomości usługi MSMQ do usługi Windows Communication Foundation (WCF). Usługa jest aplikacji konsoli Self-Hosted umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.  
  
 Umowa serwisowa jest `IOrderProcessor`, definiujący usługi jednokierunkowej, który jest odpowiedni do użytku z kolejki. Wiadomości usługi MSMQ nie ma nagłówek akcji, więc nie jest możliwe do mapowania różnych wiadomości usługi MSMQ kontrakty operacji automatycznie. W związku z tym może istnieć tylko jedno operacji kontraktu. Jeśli chcesz zdefiniować więcej niż jeden kontrakt operacji dla usługi, aplikacja musi udostępniać informacje, które nagłówka wiadomości usługi MSMQ (na przykład etykiety lub correlationID) może służyć do określania, który kontrakt operacji wysłania. Jest to zaprezentowane w [niestandardowe demultipleksowanie](../../../../docs/framework/wcf/samples/custom-demux.md).  
  
 Wiadomości usługi MSMQ nie zawiera informacje, które nagłówki są zamapowane na różne parametry kontrakt operacji. Parametr jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), który zawiera podstawowe wiadomości usługi MSMQ. Typ "T" w elemencie <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) klasa reprezentuje dane, które jest serializowana w treści wiadomości usługi MSMQ. W tym przykładzie `PurchaseOrder` typ jest serializowana w treści wiadomości usługi MSMQ.  
  
 Następujący przykładowy kod przedstawia kontrakt usługi Usługa przetwarzania zamówień.  

```csharp
// Define a service contract.  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```

 Usługa jest samodzielnie hostowana. Podczas korzystania z usługi MSMQ kolejki używanej musi zostać utworzona wcześniej. Można to zrobić ręcznie lub za pomocą kodu. W tym przykładzie usługa sprawdza istnienie kolejki i utworzy go, jeśli jest to wymagane. Nazwa kolejki jest do odczytu z pliku konfiguracji.  

```csharp
public static void Main()  
{  
    // Get the MSMQ queue name from the application settings in   
    // configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
    // Create the MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
    …  
}  
```

 Usługa tworzy i otwiera <xref:System.ServiceModel.ServiceHost> dla `OrderProcessorService`, jak pokazano w poniższym przykładowym kodzie.  

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
{  
    serviceHost.Open();  
    Console.WriteLine("The service is ready.");  
    Console.WriteLine("Press <ENTER> to terminate service.");  
    Console.ReadLine();  
    serviceHost.Close();  
}  
```

 Nazwa kolejki usługi MSMQ jest określony w sekcji appSettings pliku konfiguracji, jak pokazano w poniższym Przykładowa konfiguracja.  
  
> [!NOTE]
>  Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnik odwrotny w ścieżce. Adres punktu końcowego WCF Określa schemat msmq.formatname i używane host_lokalny na komputerze lokalnym. Adres kolejki dla każdej nazwy formatu MSMQ adresowania wytycznych jest zgodna schematu msmq.formatname.  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 Aplikacja kliencka jest aplikacja usługi MSMQ, która używa <xref:System.Messaging.MessageQueue.Send%2A> metodę, aby wysłać wiadomość trwały i transakcyjnych w kolejce, jak pokazano w poniższym przykładowym kodzie.  

```csharp
//Connect to the queue.  
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);  
  
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
  
// Submit the purchase order.  
Message msg = new Message();  
msg.Body = po;  
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
  
    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);  
    // Complete the transaction.  
    scope.Complete();  
  
}  
Console.WriteLine("Placed the order:{0}", po);  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```

 Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Możesz zobaczyć komunikaty odbierania usługi z klienta. Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta. Należy zauważyć, że ponieważ kolejkowania wiadomości jest używany, klient i usługa musi być uruchomiona w tym samym czasie. Na przykład można uruchomić klienta, zamknij go, a następnie uruchom usługi i nadal będzie ona otrzymywać jego wiadomości.  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a>Zobacz też  
 [Kolejki programu WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Usługa kolejkowania komunikatów](https://go.microsoft.com/fwlink/?LinkId=94968)
