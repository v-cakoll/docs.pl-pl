---
title: Kolejki utraconych komunikatów
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 489de5d8147edd58d90be01975ddbc9927e29902
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045625"
---
# <a name="dead-letter-queues"></a>Kolejki utraconych komunikatów
Ten przykład pokazuje, jak obsługiwać i przetwarzać komunikaty, których dostarczenie nie powiodło się. Jest on oparty na przykładowym [wiązaniem usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) . Ten przykład używa `netMsmqBinding` powiązania. Usługa to samodzielna aplikacja konsolowa, która umożliwia obserwowanie usługi do odebrania komunikatów znajdujących się w kolejce.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

> [!NOTE]
> Ten przykład pokazuje każdą kolejkę utraconych wiadomości aplikacji, która jest [!INCLUDE[wv](../../../../includes/wv-md.md)]dostępna tylko w systemie. Przykład można zmodyfikować w taki sposób, aby korzystał z domyślnych kolejek cały system dla usługi [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] MSMQ [!INCLUDE[wxp](../../../../includes/wxp-md.md)]3,0 w systemach i.

 W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki. Dokładniej, klient wysyła komunikaty do kolejki. Usługa odbiera komunikaty z kolejki. W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.

 Ponieważ komunikacja w kolejce może potrwać określoną ilość dormancy, możesz chcieć skojarzyć wartość czasu wygaśnięcia w komunikacie, aby upewnić się, że wiadomość nie zostanie dostarczona do aplikacji w przypadku jej wcześniejszego przekroczenia. Istnieją również przypadki, w których aplikacja musi być poinformowana, czy dostarczenie komunikatu nie powiodło się. We wszystkich tych przypadkach, na przykład gdy czas wygaśnięcia komunikatu wygasł lub dostarczenie komunikatu nie powiodło się, komunikat zostanie umieszczony w kolejce utraconych wiadomości. Aplikacja wysyłająca może następnie odczytywać komunikaty w kolejce utraconych wiadomości i podejmować działania naprawcze, które nie są wynikiem działania, aby skorygować przyczyny niepowodzenia dostawy i ponownie wysłać wiadomość.

 Kolejka utraconych wiadomości w `NetMsmqBinding` powiązaniu jest wyrażona w następujących właściwościach:

- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>Właściwość w celu wyrażenia rodzaju kolejki utraconych wiadomości, która jest wymagana przez klienta. To wyliczenie ma następujące wartości:

- `None`: Klient nie wymaga kolejki utraconych wiadomości.

- `System`: Kolejka utraconych wiadomości systemowych służy do przechowywania wiadomości utraconych. Kolejka utraconych wiadomości systemowych jest udostępniana przez wszystkie aplikacje uruchomione na komputerze.

- `Custom`: Niestandardowa Kolejka utraconych wiadomości określona <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> przy użyciu właściwości jest używana do przechowywania wiadomości utraconych. Ta funkcja jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)]systemie. Jest on używany, gdy aplikacja musi używać własnej kolejki utraconych wiadomości zamiast udostępniać ją innym aplikacjom uruchomionym na tym samym komputerze.

- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>Właściwość do wyrażenia określonej kolejki, która ma być używana jako kolejka utraconych wiadomości. Jest to możliwe tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)]programie.

 W tym przykładzie klient wysyła partię komunikatów do usługi z zakresu transakcji i określa arbitralnie niską wartość "czas wygaśnięcia" dla tych komunikatów (około 2 sekund). Klient określa również niestandardową kolejkę utraconych wiadomości, która ma być używana do kolejkowania komunikatów, które wygasły.

 Aplikacja kliencka może odczytać komunikaty w kolejce utraconych wiadomości i ponowić próbę wysłania komunikatu albo rozwiązać błąd, który spowodował umieszczenie oryginalnego komunikatu w kolejce utraconych wiadomości i wysłanie komunikatu. W przykładzie klient wyświetli komunikat o błędzie.

 Kontrakt usługi jest `IOrderProcessor`, jak pokazano w poniższym przykładowym kodzie.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Kod usługi w przykładzie jest tym, że [transakcyjne powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).

 Komunikacja z usługą odbywa się w zakresie transakcji. Usługa odczytuje komunikaty z kolejki, wykonuje operację, a następnie wyświetla wyniki operacji. Aplikacja tworzy również kolejkę utraconych wiadomości dla komunikatów utraconych.

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

 Konfiguracja klienta określa krótki czas trwania wiadomości w celu uzyskania dostępu do usługi. Jeśli nie można przesłać komunikatu w określonym czasie trwania, komunikat wygaśnie i zostanie przeniesiony do kolejki utraconych wiadomości.

> [!NOTE]
> Klient może dostarczyć komunikat do kolejki usług w określonym czasie. Aby upewnić się, że usługa utraconych wiadomości zostanie wyświetlona, należy uruchomić klienta programu przed uruchomieniem usługi. Komunikat przekracza limit czasu i jest dostarczany do usługi utraconych wiadomości.

 Aplikacja musi zdefiniować, która kolejka ma być używana jako jej Kolejka utraconych wiadomości. Jeśli kolejka nie jest określona, domyślna kolejka utraconych wiadomości transakcyjnych w całej systemie jest używana do kolejkowania martwych komunikatów. W tym przykładzie aplikacja kliencka określa własną kolejkę utraconych wiadomości aplikacji.

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

 Usługa komunikatów utraconych odczytuje komunikaty z kolejki utraconych wiadomości. Usługa wiadomości utraconych zawiera implementację `IOrderProcessor` kontraktu. Jego implementacja nie przetwarza jednak zamówień. Usługa wiadomości utraconych jest usługą klienta i nie ma możliwości przetwarzania zamówień.

> [!NOTE]
> Kolejka utraconych wiadomości jest kolejką klienta i jest lokalna dla Menedżera kolejki klienta.

 Implementacja usługi komunikatów utraconych wiadomości sprawdza, czy nie powiodło się dostarczenie komunikatu i podejmuje środki naprawcze. Przyczyna niepowodzenia komunikatu jest przechwytywana w dwóch wyliczeniach <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> i. <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A> Możesz pobrać <xref:System.ServiceModel.Channels.MsmqMessageProperty> <xref:System.ServiceModel.OperationContext> z programu, tak jak pokazano w poniższym przykładowym kodzie:

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succeed ", po);
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

 Komunikaty w kolejce utraconych wiadomości to komunikaty, które są rozkierowane do usługi, która przetwarza komunikat. W związku z tym, gdy usługa wiadomości utraconych odczytuje komunikaty z kolejki, warstwa kanału Windows Communication Foundation (WCF) znajdzie niezgodność w punktach końcowych i nie wyśle komunikatu. W takim przypadku komunikat jest kierowany do usługi przetwarzania zamówień, ale jest odbierany przez usługę wiadomości utraconych. Aby odebrać komunikat, który jest rozkierowany do innego punktu końcowego, filtr adresów w celu dopasowania do dowolnego adresu jest określony `ServiceBehavior`w. Jest to wymagane do pomyślnego przetworzenia komunikatów, które są odczytywane z kolejki utraconych wiadomości.

 W tym przykładzie usługa wiadomości utraconych wysyła komunikat, jeśli przyczyną niepowodzenia jest komunikat z limitem czasu. Ze względu na to, że wyświetla błąd dostarczania, jak pokazano w poniższym przykładowym kodzie:

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

 Poniższy przykład pokazuje konfigurację wiadomości utraconej:

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

 W trakcie uruchamiania przykładu dostępne są 3 pliki wykonywalne, aby zobaczyć, jak Kolejka utraconych komunikatów działa dla każdej aplikacji; Klient, usługa i utracona usługa, która odczytuje z kolejki utraconych wiadomości dla każdej aplikacji i ponownie wysyła komunikat do usługi. Wszystkie są aplikacjami konsolowymi z danymi wyjściowymi w oknach konsoli.

> [!NOTE]
> Ponieważ kolejkowanie jest w użyciu, klient i usługa nie muszą działać w tym samym czasie. Można uruchomić klienta programu, zamknąć go, a następnie uruchomić usługę i nadal otrzymywać wiadomości. Należy uruchomić usługę i zamknąć ją, aby można było utworzyć kolejkę.

 W przypadku uruchamiania klienta klient wyświetla komunikat:

```
Press <ENTER> to terminate client.
```

 Klient podjął próbę wysłania komunikatu, ale z krótkim limitem czasu, wiadomość wygasła i została teraz umieszczona w kolejce do kolejki utraconych wiadomości dla każdej aplikacji.

 Następnie uruchamiasz usługę utraconych wiadomości, która odczytuje komunikat i wyświetla kod błędu i ponownie wysyła komunikat z powrotem do usługi.

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

 Usługa uruchamia się, a następnie odczytuje ponownie wysłaną wiadomość i przetwarza ją.

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

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Jeśli usługa jest uruchamiana po raz pierwszy, sprawdzi, czy kolejka jest obecna. Jeśli kolejka nie istnieje, usługa utworzy ją. Aby utworzyć kolejkę, można najpierw uruchomić tę usługę lub utworzyć ją za pośrednictwem Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.

    1. Otwórz Menedżer serwera w programie Visual Studio 2012.

    2. Rozwiń kartę **funkcje** .

    3. Kliknij prawym przyciskiem myszy pozycję **prywatne kolejki komunikatów**, a następnie wybierz kolejno pozycje **Nowa**i **prywatne**.

    4. Zaznacz pole **transakcyjne** .

    5. Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.

3. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Aby uruchomić przykład w odpowiedniej nazwie kolejki zmian konfiguracji na jednym lub wielu komputerach, zastępując localhost pełną nazwą komputera i postępuj zgodnie z instrukcjami w temacie [uruchamianie Windows Communication Foundation przykładów](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej

1. Jeśli komputer nie jest częścią domeny, Wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom `None` ochrony tak jak pokazano w poniższej konfiguracji przykładowej:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Upewnij się, że punkt końcowy jest skojarzony z powiązaniem przez ustawienie `bindingConfiguration` atrybutu punktu końcowego.

2. Przed uruchomieniem przykładu należy zmienić konfigurację na DeadLetterService, serwerze i kliencie.

    > [!NOTE]
    > `security mode` Ustawienieodpowiada`MsmqProtectionLevel` ustawieniu i`MsmqAuthenticationMode` zabezpieczeniana`None`. `None` `Message`

## <a name="comments"></a>Komentarze
 Domyślnie w przypadku `netMsmqBinding` transportu powiązań jest włączone zabezpieczenia. Dwie właściwości, `MsmqAuthenticationMode` a `MsmqProtectionLevel`także określają typ zabezpieczenia transportu. Domyślnie tryb uwierzytelniania jest ustawiony na `Windows` , a poziom ochrony jest ustawiony na. `Sign` Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny. Jeśli ten przykład zostanie uruchomiony na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "Wewnętrzny certyfikat usługi kolejkowania komunikatów użytkownika nie istnieje".

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
