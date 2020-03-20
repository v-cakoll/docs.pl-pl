---
title: Kolejki utraconych komunikatów
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: eab1c52f4d0b3d0f82cf561a9478ea8233598e1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144951"
---
# <a name="dead-letter-queues"></a>Kolejki utraconych komunikatów
W tym przykładzie pokazano, jak obsługiwać i przetwarzać wiadomości, które nie powiodło się dostarczenie. Jest on oparty na próbce [wiązania transacted MSMQ.](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) W tym przykładzie użyto `netMsmqBinding` powiązania. Usługa jest samodzielną aplikacją konsoli, która umożliwia obserwowanie usługi odbierającej wiadomości w kolejce.

> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.

> [!NOTE]
> W tym przykładzie pokazano każdą kolejkę utraconych wiadomości aplikacji, która jest dostępna tylko w systemie Windows Vista. Przykład można zmodyfikować w celu użycia domyślnych kolejek systemowych dla usługi MSMQ 3.0 w systemach Windows Server 2003 i Windows XP.

 W komunikacji w kolejce klient komunikuje się z usługą przy użyciu kolejki. Dokładniej, klient wysyła wiadomości do kolejki. Usługa odbiera wiadomości z kolejki. W związku z tym usługi i klienta, nie muszą być uruchomione w tym samym czasie do komunikowania się przy użyciu kolejki.

 Ponieważ komunikacja w kolejce może obejmować pewną ilość spoczynku, można skojarzyć wartość czasu do żywo w wiadomości, aby upewnić się, że wiadomość nie zostanie dostarczona do aplikacji, jeśli minęła czas. Istnieją również przypadki, w których aplikacja musi być informowana, czy wiadomość nie powiodło się. We wszystkich tych przypadkach, takich jak po upływie czasu wygaśnięcia wiadomości lub wiadomość nie powiodło się, wiadomość jest umieszczana w kolejce utraconych wiadomości. Aplikacja wysyłająca może następnie odczytać wiadomości w kolejce utraconych wiadomości i podjąć działania naprawcze, które wahają się od braku akcji do korygowania przyczyn nieudanego dostarczania i ponownego wysyłania wiadomości.

 Kolejka utraconych wiadomości `NetMsmqBinding` w powiązaniu jest wyrażona w następujących właściwościach:

- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>właściwości, aby wyrazić rodzaj kolejki utraconych wiadomości wymaganych przez klienta. To wyliczenie ma następujące wartości:

- `None`: Klient nie wymaga kolejki utraconych wiadomości.

- `System`: Kolejka utraconych wiadomości systemu służy do przechowywania wiadomości utraconych. Kolejka utraconych wiadomości systemu jest współużytkowana przez wszystkie aplikacje uruchomione na komputerze.

- `Custom`: Niestandardowa kolejka utraconych <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> wiadomości określona przy użyciu właściwości służy do przechowywania wiadomości utraconych. Ta funkcja jest dostępna tylko w systemie Windows Vista. Jest to używane, gdy aplikacja musi używać własnej kolejki utraconych wiadomości zamiast udostępniania jej innym aplikacjom uruchomionym na tym samym komputerze.

- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>właściwość, aby wyrazić określoną kolejkę do użycia jako kolejki utraconych wiadomości. Jest to dostępne tylko w systemie Windows Vista.

 W tym przykładzie klient wysyła partii komunikatów do usługi z zakresu transakcji i określa dowolnie niską wartość dla "czas do żywo" dla tych wiadomości (około 2 sekund). Klient określa również niestandardową kolejkę utraconych wiadomości, która ma być używana do umieszczania w kolejce wiadomości, które wygasły.

 Aplikacja kliencka może odczytywać wiadomości w kolejce utraconych wiadomości i ponowić próbę wysłania wiadomości lub poprawić błąd, który spowodował umieszczenie oryginalnej wiadomości w kolejce utraconych wiadomości i wysłanie wiadomości. W przykładzie klient wyświetla komunikat o błędzie.

 Umowa serwisowa `IOrderProcessor`jest , jak pokazano w poniższym przykładowym kodzie.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Kod usługi w próbce jest to, że [transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).

 Komunikacja z usługą odbywa się w ramach transakcji. Usługa odczytuje komunikaty z kolejki, wykonuje operację, a następnie wyświetla wyniki operacji. Aplikacja tworzy również kolejkę utraconych wiadomości utraconych wiadomości.

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

 Konfiguracja klienta określa krótki czas trwania wiadomości, aby dotrzeć do usługi. Jeśli wiadomość nie może być przesłana w określonym czasie trwania, wiadomość wygasa i jest przenoszona do kolejki utraconych wiadomości.

> [!NOTE]
> Jest możliwe dla klienta do dostarczenia wiadomości do kolejki usługi w określonym czasie. Aby upewnić się, że widzisz dead-letter service w akcji, należy uruchomić klienta przed uruchomieniem usługi. Komunikat jest wyświetlany i jest dostarczany do usługi dead-letter.

 Aplikacja musi zdefiniować, która kolejka ma być używana jako kolejka utraconych wiadomości. Jeśli nie określono kolejki, domyślna transakcyjna kolejka utraconych wiadomości jest używana do kolejkowania utraconych wiadomości. W tym przykładzie aplikacja kliencka określa własną kolejkę utraconych wiadomości aplikacji.

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

 Usługa wiadomości utraconych odczytuje wiadomości z kolejki utraconych wiadomości. Usługa wiadomości utraconych wiadomości `IOrderProcessor` implementuje kontrakt. Jego realizacja nie polega jednak na przetwarzać zamówienia. Usługa wiadomości utraconych jest usługą klienta i nie ma możliwości przetwarzania zamówień.

> [!NOTE]
> Kolejka utraconych wiadomości jest kolejką klienta i jest lokalna dla menedżera kolejki klienta.

 Implementacja usługi wiadomości utraconych sprawdza, dlaczego wiadomość nie powiodło się i podejmuje środki naprawcze. Przyczyna niepowodzenia wiadomości jest przechwytywany w <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> dwóch <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>wyliczeń i . Można pobrać z <xref:System.ServiceModel.Channels.MsmqMessageProperty> <xref:System.ServiceModel.OperationContext> jak pokazano w poniższym przykładowym kodzie:

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

 Wiadomości w kolejce utraconych wiadomości są wiadomości, które są adresowane do usługi, która przetwarza komunikat. W związku z tym gdy usługa wiadomości utraconych odczytuje wiadomości z kolejki, warstwa kanału Windows Communication Foundation (WCF) znajduje niezgodność w punktach końcowych i nie wysyła wiadomości. W takim przypadku wiadomość jest adresowany do usługi przetwarzania zamówień, ale jest odbierana przez usługę wiadomości utraconych. Aby otrzymać wiadomość zaadresowaną do innego punktu końcowego, filtr `ServiceBehavior`adresu pasujący do dowolnego adresu jest określony w pliku . Jest to wymagane do pomyślnego przetwarzania wiadomości, które są odczytywane z kolejki utraconych wiadomości.

 W tym przykładzie usługa wiadomości utraconych wiadomości ponownie wysyła wiadomość, jeśli przyczyną niepowodzenia jest upłynięcie czasu wiadomości. Ze wszystkich innych powodów wyświetla błąd dostawy, jak pokazano w poniższym przykładowym kodzie:

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

 W poniższym przykładzie przedstawiono konfigurację wiadomości utraconej:

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

 W uruchomieniu próbki istnieją 3 pliki wykonywalne do uruchomienia, aby zobaczyć, jak działa kolejka utraconych wiadomości dla każdej aplikacji; klient, usługa i usługa utraconych wiadomości, która odczytuje z kolejki utraconych wiadomości dla każdej aplikacji i ponownie wysyła wiadomość do usługi. Wszystkie są aplikacjami konsolowymi z wyjściem w oknach konsoli.

> [!NOTE]
> Ponieważ kolejkowanie jest w użyciu, klient i usługa nie muszą być uruchomione w tym samym czasie. Można uruchomić klienta, zamknąć go, a następnie uruchomić usługę i nadal odbiera swoje komunikaty. Należy uruchomić usługę i zamknąć ją, aby można było utworzyć kolejkę.

 Podczas uruchamiania klienta klient wyświetla komunikat:

```console
Press <ENTER> to terminate client.
```

 Klient próbował wysłać wiadomość, ale z krótkim limitem czasu wiadomość wygasła i jest teraz w kolejce utraconych wiadomości dla każdej aplikacji.

 Następnie uruchom usługę utraconej wiadomości, która odczytuje komunikat i wyświetla kod błędu i ponownie wysyła wiadomość z powrotem do usługi.

```console
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 Usługa zostanie uruchomiony, a następnie odczytuje komunikat resent i przetwarza go.

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę

1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Jeśli usługa jest uruchamiana jako pierwsza, sprawdzi, czy kolejka jest obecna. Jeśli kolejka nie jest obecny, usługa utworzy jeden. Usługę można uruchomić najpierw, aby utworzyć kolejkę, lub utworzyć ją za pośrednictwem Menedżera kolejek usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.

    1. Otwórz Menedżera serwera w programie Visual Studio 2012.

    2. Rozwiń kartę **Funkcje.**

    3. Kliknij prawym przyciskiem myszy **pozycję Kolejki wiadomości prywatnych**i wybierz polecenie **Nowa**, **Kolejka prywatna**.

    4. Zaznacz pole **Transakcyjne.**

    5. Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.

3. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Aby uruchomić przykład w konfiguracji jedno- lub międzykomputerowej odpowiednio zmienić nazwy kolejki, zastępując localhost z pełną nazwą komputera i postępuj zgodnie z instrukcjami w [Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej

1. Jeśli komputer nie należy do domeny, wyłącz zabezpieczenia transportu, ustawiając `None` tryb uwierzytelniania i poziom ochrony na pokazano w poniższej przykładowej konfiguracji:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Upewnij się, że punkt końcowy jest skojarzony z `bindingConfiguration` powiązaniem, ustawiając atrybut punktu końcowego.

2. Przed uruchomieniem przykładu należy zmienić konfigurację na serwerze, serwerze i kliencie.

    > [!NOTE]
    > Ustawienie `security mode` `None` jest równoważne `MsmqAuthenticationMode` `MsmqProtectionLevel` z `Message` ustawieniem i zabezpieczeniami `None`.

## <a name="comments"></a>Komentarze
 Domyślnie z `netMsmqBinding` transportu powiązania zabezpieczeń jest włączona. Dwie właściwości `MsmqAuthenticationMode` i `MsmqProtectionLevel`, razem określić typ zabezpieczeń transportu. Domyślnie jest ustawiony tryb `Windows` uwierzytelniania, a `Sign`poziom ochrony jest ustawiony na . Aby usługa MSMQ udostępniała funkcję uwierzytelniania i podpisywania, musi ona być częścią domeny. Po uruchomieniu tego przykładu na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "Certyfikat kolejkowania wiadomości wewnętrznych użytkownika nie istnieje".

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
