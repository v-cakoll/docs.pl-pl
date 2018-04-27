---
title: Kolejki utraconych komunikatów
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
caps.latest.revision: 35
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9892579633103f1e7a6612c09865c91c559df34c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="dead-letter-queues"></a>Kolejki utraconych komunikatów
W tym przykładzie przedstawiono sposób obsługi i przetwarzania komunikatów, które nie powiodły dostarczania. Jest on oparty na [nietransakcyjnego powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) próbki. W przykładzie użyto `netMsmqBinding` powiązania. Usługa jest aplikacji konsoli siebie umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!NOTE]
>  W tym przykładzie pokazano każdej aplikacji kolejki utraconych wiadomości, która jest dostępna tylko na [!INCLUDE[wv](../../../../includes/wv-md.md)]. Przykład można zmodyfikować, aby użyć kolejki systemowe domyślny dla usługi MSMQ 3.0 na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 W kolejce komunikacji klient komunikuje się z usługą przy użyciu kolejki. Mówiąc ściślej klient wysyła wiadomości do kolejki. Usługa odbiera komunikaty z kolejki. Usługi i klienta w związku z tym ma być uruchomiona, w tym samym czasie do komunikowania się przy użyciu kolejki.  
  
 Ponieważ komunikacja umieszczonych w kolejce może wymagać pewnego spoczynku, można skojarzyć wartość czasu wygaśnięcia wiadomości, aby upewnić się, że komunikat nie pobrać dostarczany do aplikacji, jeśli stała się późniejsza niż godzina. Istnieją przypadki, gdzie aplikacja musi mieć świadomość, czy wiadomości nie powiodło się dostarczania. We wszystkich przypadkach takich jak wygasł czas wygaśnięcia wiadomości lub wiadomości nie powiodło się dostarczania, wiadomość zostanie umieszczona w kolejce wiadomości utraconych. Aplikacja wysyłająca można odczytywać wiadomości w kolejce wiadomości utraconych i podjęcia działań naprawczych, które należeć do zakresu od żadnej akcji na usunięciu przyczyny dostawy nie powiodło się i ponowne wysyłanie wiadomości.  
  
 Kolejki utraconych wiadomości w `NetMsmqBinding` powiązania jest wyrażona w następujących właściwości:  
  
-   <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> Właściwość do wyrażenia typu kolejki utraconych wiadomości wymagane przez klienta. To wyliczenie ma następujące wartości:  
  
-   `None`: Brak kolejki utraconych wiadomości jest wymagana przez klienta.  
  
-   `System`System kolejki utraconych wiadomości jest używany do przechowywania utracone wiadomości. System kolejki utraconych wiadomości jest współużytkowana przez wszystkie aplikacje uruchomione na komputerze.  
  
-   `Custom`Niestandardowej kolejki utraconych wiadomości określona za pomocą <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> właściwość jest używana do przechowywania komunikatów martwy. Ta funkcja jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)]. Służy to, gdy aplikacja musi używać kolejki utraconych wiadomości zamiast Udostępnianie innych aplikacji uruchomionych na tym samym komputerze.  
  
-   <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> Właściwość express określonej kolejki do użycia jako kolejki utraconych wiadomości. To jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 W tym przykładzie klient wysyła komunikaty zbiorczo do usługi z zakresu transakcji i określa arbitralnie niska wartość "time-to-live" dla tych wiadomości (około 2 sekundy). Klient określa również niestandardowej kolejki utraconych wiadomości do użycia można umieścić w kolejce wiadomości, które wygasły.  
  
 Aplikacja kliencka może odczytywać wiadomości w kolejce wiadomości utraconych i albo ponownych prób wysyłania wiadomości lub Popraw błąd, który spowodował oryginalnej wiadomości, które można umieścić w kolejce wiadomości utraconych i wysłać wiadomość. W przykładzie klient jest wyświetlany komunikat o błędzie.  
  
 Kontrakt usługi jest `IOrderProcessor`, jak pokazano w poniższym kodzie próbki.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 Kod usługi w próbce jest [nietransakcyjnego powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
 Komunikacja z usługą odbywa się w zakresie transakcji. Usługa odczytuje wiadomości z kolejki, wykonuje operację, a następnie wyświetli wyniki operacji. Aplikacja tworzy również kolejka utraconych wiadomości utraconych.  

```csharp
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        // Get MSMQ queue name from app settings in configuration  
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];  
  
        // Create the transacted MSMQ queue for storing dead message if necessary.  
        if (!MessageQueue.Exists(deadLetterQueueName))  
            MessageQueue.Create(deadLetterQueueName, true);  
  
        // Create a proxy with given client endpoint configuration  
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
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
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            // Make a queued call to submit the purchase order  
            client.SubmitPurchaseOrder(po);  
            // Complete the transaction.  
            scope.Complete();  
        }  
  
        client.Close();  
  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```

 Konfiguracja klienta określa krótki czas trwania komunikatu w celu dotarcia do usługi. Jeśli wiadomość nie może być przesyłany w czasie trwania określone, komunikat wygasa, a zostanie przeniesiona do kolejki utraconych wiadomości.  
  
> [!NOTE]
>  Istnieje możliwość dla klienta na dostarczenie wiadomości do kolejki usługi w określonym czasie. Aby upewnić się, zobacz usługi utraconych w akcji, należy uruchomić przed uruchomieniem usługi klienta. Komunikat upłynie limit czasu i jest dostarczany z usługą utraconych wiadomości.  
  
 Aplikacja musi definiować kolejki, które ma być używana jako kolejki utraconych wiadomości. Jeśli kolejka nie jest określony, domyślne systemowe transakcyjnej kolejki utraconych wiadomości jest używany utracone wiadomości w kolejce. W tym przykładzie aplikacja kliencka Określa kolejkę z utraconymi komunikatami własnej aplikacji.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->  
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>  
  </appSettings>  
  
  <system.serviceModel>  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"   
                binding="netMsmqBinding"   
                bindingConfiguration="PerAppDLQBinding"   
                contract="IOrderProcessor" />  
    </client>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="PerAppDLQBinding"  
                 deadLetterQueue="Custom"  
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"   
                 timeToLive="00:00:02"/>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Usługa wiadomości utraconych odczytuje wiadomości z kolejki utraconych wiadomości. Implementuje usługi wiadomości utraconych `IOrderProcessor` kontraktu. Jej implementacja nie jest jednak proces zleceń. Usługa utraconych wiadomości jest usługa klienta i nie ma możliwości przetwarzania zamówienia.  
  
> [!NOTE]
>  Kolejki utraconych wiadomości jest kolejką klienta i jest lokalny do menedżera kolejki klienta.  
  
 Sprawdza implementacji usługi utraconych komunikatów z powodu dostarczania i środki naprawcze przyjmuje wiadomości nie powiodło się. Przyczynę niepowodzenia wiadomości są przechwytywane w dwóch wyliczenia <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> i <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>. Możesz pobrać <xref:System.ServiceModel.Channels.MsmqMessageProperty> z <xref:System.ServiceModel.OperationContext> jak pokazano w poniższym kodzie próbki:  

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)  
{  
    Console.WriteLine("Submitting purchase order did not succed ", po);  
    MsmqMessageProperty mqProp =   
                  OperationContext.Current.IncomingMessageProperties[  
                  MsmqMessageProperty.Name] as MsmqMessageProperty;  
    Console.WriteLine("Message Delivery Status: {0} ",   
                                                mqProp.DeliveryStatus);  
    Console.WriteLine("Message Delivery Failure: {0}",   
                                               mqProp.DeliveryFailure);  
    Console.WriteLine();  
    …  
}
```

 Wiadomości w kolejce wiadomości utraconych są komunikaty adresowane do usługi, który przetwarza wiadomości. W związku z tym, gdy usługi utraconych wiadomości odczytuje wiadomości z kolejki, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] warstwy kanału znajduje niezgodność w punktów końcowych i wysyła wiadomość. W takim przypadku wiadomość jest skierowana do kolejność przetwarzania usługi, ale jest odbierane przez usługę utraconych wiadomości. Komunikat, która jest skierowana do innego punktu końcowego, filtr adresów, aby dopasować dowolnego adresu jest określona w `ServiceBehavior`. Jest to wymagane do pomyślnie przetwarzać komunikatów, które są odczytywane z kolejki utraconych wiadomości.  
  
 W tym przykładzie Usługa utraconych wiadomości ponownie wysyła komunikat Jeśli przyczyną błędu jest to, że komunikat został przekroczony. Z innych powodów wyświetla błąd dostarczania, jak pokazano w poniższym kodzie próbki:  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]  
public class PurchaseOrderDLQService : IOrderProcessor  
{  
    OrderProcessorClient orderProcessorService;  
    public PurchaseOrderDLQService()  
    {  
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Console.WriteLine("Submitting purchase order did not succeed ", po);  
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;  
  
        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);  
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);  
        Console.WriteLine();  
  
        // resend the message if timed out  
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||  
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)  
        {  
            // re-send  
            Console.WriteLine("Purchase order Time To Live expired");  
            Console.WriteLine("Trying to resend the message");  
  
            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue  
            orderProcessorService.SubmitPurchaseOrder(po);  
            Console.WriteLine("Purchase order resent");  
        }  
    }  
  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the PurchaseOrderDLQService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))  
        {  
            // Open the ServiceHostBase to create listeners and start listening for messages.  
            serviceHost.Open();  
  
            // The service can now be accessed.  
            Console.WriteLine("The dead letter service is ready.");  
            Console.WriteLine("Press <ENTER> to terminate service.");  
            Console.WriteLine();  
            Console.ReadLine();  
        }  
    }  
}   
```

 Poniższy przykład przedstawia konfigurację dla wiadomości utraconych:  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">  
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="DefaultBinding"   
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"   
                 binding="netMsmqBinding"   
                 bindingConfiguration="SystemDLQBinding"   
                 contract="IOrderProcessor" />  
    </client>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="DefaultBinding" />  
        <binding name="SystemDLQBinding"  
                 deadLetterQueue="System"/>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
 W uruchomienia przykładu, istnieją 3 pliki wykonywalne uruchomić, aby zobaczyć, jak działa kolejki utraconych wiadomości dla każdej aplikacji; Klient usługi i usługa utraconych wiadomości, która odczytuje z kolejki utraconych wiadomości dla każdej aplikacji i ponownie wysyła komunikat do usługi. Wszystkie są aplikacji konsoli, przy czym dane wyjściowe w oknach konsoli.  
  
> [!NOTE]
>  Ponieważ usługi kolejkowania wiadomości jest używany, klient i usługa ma być uruchomiona w tym samym czasie. Możesz z klientem, zamknij go, a następnie uruchom usługi i nadal otrzymuje jej wiadomości. Należy uruchomić usługę i zamknąć, dzięki czemu można utworzyć kolejki.  
  
 Podczas uruchamiania klienta, klient jest wyświetlany komunikat:  
  
```  
Press <ENTER> to terminate client.  
```  
  
 Klient próbował wysłać wiadomość, ale z limitem czasu krótkich, wiadomość wygasła i jest obecnie w kolejce kolejki utraconych wiadomości dla każdej aplikacji.  
  
 Następnie należy uruchomić usługę utraconych wiadomości, która odczytuje komunikat i wyświetla kod błędu i ponownie wysyła komunikat do usługi.  
  
```  
The dead letter service is ready.  
Press <ENTER> to terminate service.  
  
Submitting purchase order did not succeed  
Message Delivery Status: InDoubt  
Message Delivery Failure: ReachQueueTimeout  
  
Purchase order Time To Live expired  
Trying to resend the message  
Purchase order resent  
```  
  
 Usługa uruchamia odczytuje komunikat wysłane ponownie i przetwarza je.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
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
  
4.  Do uruchamiania próbki w kolejce zmiany konfiguracji jednego lub między komputerami nazwy, zastępując localhost pełną nazwę komputera i postępuj zgodnie z instrukcjami [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Aby uruchomić na komputerze, na przykład przyłączony do grupy roboczej  
  
1.  Jeśli komputer nie jest częścią domeny, należy wyłączyć zabezpieczeń transportu przez ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższych Przykładowa konfiguracja:  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding name="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
     Upewnij się punkt końcowy jest skojarzony z powiązaniem przez ustawienie punktu końcowego `bindingConfiguration` atrybutu.  
  
2.  Upewnij się, zmiany konfiguracji na DeadLetterService, serwera i klienta, przed uruchomieniem próbki.  
  
    > [!NOTE]
    >  Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia `MsmqAuthenticationMode`, `MsmqProtectionLevel` i `Message` zabezpieczeń do `None`.  
  
## <a name="comments"></a>Komentarze  
 Domyślnie z `netMsmqBinding` powiązania transportu, zabezpieczeń jest włączone. Dwie właściwości `MsmqAuthenticationMode` i `MsmqProtectionLevel`, wspólnie określić typ zabezpieczeń transportu. Domyślny tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`. MSMQ zapewnić uwierzytelnianie i funkcji podpisywania musi być częścią domeny. Jeśli w tym przykładzie zostanie uruchomiony na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "Komunikat użytkownika wewnętrzny certyfikat usługi kolejkowania wiadomości nie istnieje".  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
  
## <a name="see-also"></a>Zobacz też
