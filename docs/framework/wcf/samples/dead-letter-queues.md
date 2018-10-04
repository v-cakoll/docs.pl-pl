---
title: Kolejki utraconych komunikatów
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: c6b3f059f1a1b11825b595346ed47f6a498078f1
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582609"
---
# <a name="dead-letter-queues"></a>Kolejki utraconych komunikatów
W tym przykładzie pokazano, jak obsługiwać i przetwarzać komunikaty, które dostarczania nie powiodło się. Jest on oparty na [dokonana transakcja powiązania usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) próbki. W tym przykładzie użyto `netMsmqBinding` powiązania. Usługa jest aplikacji konsoli Self-Hosted umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.

> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.

> [!NOTE]
>  W tym przykładzie przedstawiono kolejkę z utraconymi każdej aplikacji, która jest dostępna tylko na [!INCLUDE[wv](../../../../includes/wv-md.md)]. Przykład można zmodyfikować, aby użyć domyślnej kolejki systemowe dla usługi MSMQ 3.0 na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].

 W komunikacie w kolejce klient komunikuje się z usługą przy użyciu kolejki. Mówiąc ściślej klient wysyła komunikaty do kolejki. Usługa odbiera komunikaty z kolejki. Usługi i klienta w związku z tym, nie musi być uruchomiona w tym samym czasie do komunikowania się za pomocą kolejki.

 Ponieważ komunikacja umieszczonych w kolejce może obejmować określoną ilość spoczynku, można skojarzyć wartości czasu wygaśnięcia na komunikat, aby zapewnić, że komunikat nie uzyskać dostarczane do aplikacji, gdy stała się późniejsza niż godzina. Istnieją przypadki, gdzie aplikacja należy poinformować, czy komunikat zakończyło się niepowodzeniem dostarczania. We wszystkich przypadkach takich jak time-to-live w komunikacie wygasła lub komunikat dostarczania nie powiodło się, komunikat jest umieszczany w kolejce utraconych wiadomości. Aplikacji wysyłającej można odczytywać wiadomości z kolejki utraconych wiadomości i podejmuj akcje naprawcze, z zakresu od żadnych działań do poprawiania przyczyn dostawy nie powiodło się i ponowne wysyłanie wiadomości.

 Kolejki utraconych wiadomości w `NetMsmqBinding` wiązanie danych jest wyrażona w następujących właściwościach:

-   <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> Właściwość wyrażenia rodzaju kolejki utraconych wiadomości wymagane przez klienta. To wyliczenie ma następujące wartości:

-   `None`: Brak kolejki utraconych wiadomości jest wymagane przez klienta.

-   `System`Kolejki utraconych wiadomości system służy do przechowywania utracone wiadomości. Kolejka utraconych wiadomości systemu jest współużytkowana przez wszystkie aplikacje uruchomione na komputerze.

-   `Custom`Niestandardowe kolejki utraconych wiadomości, które są określone za pomocą <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> właściwość jest używana do przechowywania utracone wiadomości. Ta funkcja jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)]. Służy to, gdy aplikacja musi używać własnej kolejki utraconych wiadomości zamiast udostępnianie innym aplikacjom działającym na tym samym komputerze.

-   <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> Właściwość do określonej kolejki do użycia jako kolejki utraconych wiadomości express. Ta opcja jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)].

 W tym przykładzie klient wysyła komunikaty zbiorczo do usługi z zakresu transakcji i określa arbitralnie niska wartość "time-to-live" dla tych wiadomości (około 2 sekund). Klient określa również niestandardowych kolejki utraconych wiadomości do użycia można umieścić w kolejce komunikatów, które wygasły.

 Aplikacja kliencka może odczytywać wiadomości z kolejki utraconych wiadomości i albo ponownych prób wysyłania komunikatu lub naprawić błąd, który spowodował oryginalna wiadomość ma zostać umieszczone w kolejce utraconych wiadomości, a następnie wysłać wiadomość. W tym przykładzie klient jest wyświetlany komunikat o błędzie.

 Umowa serwisowa jest `IOrderProcessor`, jak pokazano w poniższym przykładowym kodzie.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Kod usługi, w przykładzie jest [dokonana transakcja powiązania usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).

 Komunikacja z usługą odbywa się w zakresie transakcji. Usługa odczytuje komunikaty z kolejki, wykonuje operację, a następnie wyświetla wyniki operacji. Aplikacja tworzy również kolejka utraconych wiadomości utraconych wiadomości.

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

 Konfiguracja klienta określa krótki czas trwania komunikatu w celu dotarcia do usługi. Jeśli komunikat nie mogą być przekazywane w trakcie trwania określone, komunikat wygaśnie i zostanie przeniesiona do kolejki utraconych wiadomości.

> [!NOTE]
>  Istnieje możliwość dla klienta w celu dostarczenia komunikatu do kolejki usługi w określonym czasie. Aby wyświetlić usługę wiadomości utraconych w akcji, należy uruchomić przed uruchomieniem usługi klienta. Komunikat upłynie limit czasu i jest dostarczana z usługą utraconych wiadomości.

 Aplikacja musi definiować której kolejki do użycia jako swojej kolejki utraconych wiadomości. Jeśli kolejka nie zostanie określony, domyślna systemowe transakcyjnej kolejki utraconych wiadomości jest używany do kolejki martwych wiadomości. W tym przykładzie aplikacja kliencka określa własnej kolejki utraconych wiadomości dla aplikacji.

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

 Usługa wiadomości utraconych odczytuje komunikaty z kolejki utraconych wiadomości. Implementuje usługi wiadomości utraconych `IOrderProcessor` kontraktu. Jego implementacja nie jest jednak aby przetwarzać zamówienia. Usługa utraconych wiadomości usługi klienta i nie ma możliwości przetwarzania zamówień.

> [!NOTE]
>  Kolejki utraconych wiadomości jest kolejką klienta i lokalny Menedżer kolejki klienta.

 Sprawdza implementacji usługi wiadomości utraconych z powodu komunikatu nie powiodła się, dostarczanie i środki naprawcze przyjmuje. Przyczyną niepowodzenia wiadomości są przechwytywane w dwóch wyliczenia <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> i <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>. Możesz pobrać <xref:System.ServiceModel.Channels.MsmqMessageProperty> z <xref:System.ServiceModel.OperationContext> jak pokazano w poniższym przykładowym kodzie:

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

 Wiadomości w kolejce wiadomości utraconych to komunikaty, które są kierowane do usługi, która przetwarza wiadomości. W związku z tym gdy usługa wiadomości utraconych odczytuje komunikaty z kolejki, warstwy kanału usługi Windows Communication Foundation (WCF) umożliwia znalezienie niezgodność punktów końcowych i nie wysyła komunikat. W takich przypadkach komunikat jest skierowana do Usługa przetwarzania zamówień, ale są odbierane przez usługę utraconych wiadomości. Aby otrzymywać wiadomość, która jest skierowana do innego punktu końcowego, filtr adresów, aby dopasować dowolny adres jest określony w `ServiceBehavior`. Jest to wymagane, aby pomyślnie przetwarzania komunikatów, które są odczytywane z kolejki utraconych wiadomości.

 W tym przykładzie Usługa utraconych wiadomości umożliwia ponowne wysłanie wiadomości Jeśli przyczyna niepowodzenia jest fakt, że komunikat upłynął limit czasu. Z innych przyczyn wyświetla błąd dostarczania, jak pokazano w poniższym przykładowym kodzie:

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

 Poniższy przykład przedstawia konfigurację dla wiadomości utraconych wiadomości:

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

 W działa aplikacja przykładowa, istnieją 3 pliki wykonywalne uruchomić, aby zobaczyć, jak działa kolejki utraconych wiadomości dla każdej aplikacji; Klient usługi i usługi utraconych wiadomości, odczytuje z kolejki utraconych wiadomości dla każdej aplikacji, która umożliwia ponowne wysłanie wiadomości w usłudze. Wszystkie są aplikacje konsoli z danych wyjściowych okna konsoli.

> [!NOTE]
>  Ponieważ usługi kolejkowania wiadomości jest używany, klient i usługa ma być uruchomiona w tym samym czasie. Można uruchomić klienta, zamknij go, a następnie uruchom usługi i wciąż otrzymuje jego wiadomości. Należy uruchomić usługę i zamknij go, tak że można utworzyć kolejki.

 Podczas uruchamiania klienta, klient jest wyświetlany komunikat:

```
Press <ENTER> to terminate client.
```

 Klient próbował wysłać wiadomość, ale z krótki limit czasu, wiadomość wygasł i jest obecnie w kolejce kolejki utraconych wiadomości dla każdej aplikacji.

 Następnie uruchom usługę utraconych wiadomości, która odczytuje komunikat i wyświetla kod błędu: umożliwia ponowne wysłanie wiadomości do usługi.

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

 Uruchamiania i następnie odczytuje komunikat wysłane ponownie i przetwarza je.

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

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny. Jeśli kolejka nie jest obecny, będzie utworzyć usługę. Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.

    1.  Otwórz Menedżera serwera w programie Visual Studio 2012.

    2.  Rozwiń **funkcji** kartę.

    3.  Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.

    4.  Sprawdź **transakcyjna** pole.

    5.  Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.

3.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4.  Do uruchomienia przykładu w kolejce zmiany konfiguracji komputera jednego lub wielu nazw odpowiednio zastępowanie localhost z pełną nazwę komputera i postępuj zgodnie z instrukcjami w [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Do uruchomienia przykładu na komputer przyłączony do grupy roboczej

1.  Jeśli komputer nie jest częścią domeny, należy wyłączyć zabezpieczenia transportu, ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższym Przykładowa konfiguracja:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Upewnij się, punkt końcowy jest skojarzony z powiązaniem przez ustawienie punktu końcowego `bindingConfiguration` atrybutu.

2.  Upewnij się, zmień konfigurację na DeadLetterService, serwera i klienta, przed uruchomieniem przykładu.

    > [!NOTE]
    >  Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia `MsmqAuthenticationMode`, `MsmqProtectionLevel` i `Message` security `None`.

## <a name="comments"></a>Komentarze
 Domyślnie `netMsmqBinding` powiązania transportu, zabezpieczeń jest włączone. Dwie właściwości `MsmqAuthenticationMode` i `MsmqProtectionLevel`, wspólnie określić typ zabezpieczeń transportu. Domyślny tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`. Dla usługi MSMQ zapewniać uwierzytelnianie i funkcji podpisywania należy do domeny. Po uruchomieniu tego przykładu na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "Wiadomość użytkownika wewnętrzny certyfikat usługi kolejkowania nie istnieje".

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
  
## <a name="see-also"></a>Zobacz też
