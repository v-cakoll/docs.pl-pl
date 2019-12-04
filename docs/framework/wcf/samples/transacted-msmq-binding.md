---
title: Transakcyjne powiązanie MSMQ
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: a3592195f853dd97bf8e4351526bf0fff9ce78fd
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715631"
---
# <a name="transacted-msmq-binding"></a>Transakcyjne powiązanie MSMQ

Ten przykład pokazuje, jak przeprowadzić komunikację z kolejką w kolejce przy użyciu usługi kolejkowania komunikatów (MSMQ).

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki. Dokładniej, klient wysyła komunikaty do kolejki. Usługa odbiera komunikaty z kolejki. W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.

Gdy transakcje są używane do wysyłania i odbierania wiadomości, istnieją w rzeczywistości dwie osobne transakcje. Gdy klient wysyła komunikaty w zakresie transakcji, transakcja jest lokalna dla klienta i Menedżera kolejki klienta. Gdy usługa odbiera komunikaty w zakresie transakcji, transakcja jest lokalna dla usługi i Menedżera kolejki odbierającej. Bardzo ważne jest, aby pamiętać, że klient i usługa nie uczestniczą w tej samej transakcji. Zamiast tego korzystają z różnych transakcji podczas wykonywania operacji (takich jak wysyłanie i odbieranie) z kolejką.

W tym przykładzie klient wysyła partię komunikatów do usługi z zakresu transakcji. Komunikaty wysyłane do kolejki są następnie odbierane przez usługę w zakresie transakcji zdefiniowanym przez usługę.

Kontrakt usługi jest `IOrderProcessor`, jak pokazano w poniższym przykładowym kodzie. Interfejs definiuje jednokierunkową usługę, która jest odpowiednia do użycia z kolejkami.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

Zachowanie usługi definiuje zachowanie operacji z `TransactionScopeRequired`m ustawionym na `true`. Gwarantuje to, że ten sam zakres transakcji, który jest używany do pobierania wiadomości z kolejki jest używany przez menedżerów zasobów, do których uzyskuje dostęp Metoda. Gwarantuje również, że jeśli metoda zgłasza wyjątek, komunikat jest zwracany do kolejki. Bez ustawiania tego zachowania, kanał umieszczony w kolejce tworzy transakcję odczytu wiadomości z kolejki i zatwierdza ją automatycznie przed wysłaniem, jeśli operacja nie powiedzie się, komunikat zostanie utracony. Najbardziej typowym scenariuszem jest to, że operacje usługi mogą być rejestrowane w transakcji, która jest używana do odczytywania wiadomości z kolejki, jak pokazano w poniższym kodzie.

```csharp
 // This service class that implements the service contract.
 // This added code writes output to the console window.
 public class OrderProcessorService : IOrderProcessor
 {
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
     public void SubmitPurchaseOrder(PurchaseOrder po)
     {
         Orders.Add(po);
         Console.WriteLine("Processing {0} ", po);
     }
  …
}
```

Usługa jest samodzielna. W przypadku korzystania z transportu usługi MSMQ użyta Kolejka musi zostać utworzona z góry. Można to zrobić ręcznie lub przy użyciu kodu. W tym przykładzie usługa zawiera kod służący do sprawdzania istnienia kolejki i tworzenia kolejki, jeśli nie istnieje. Nazwa kolejki jest odczytywana z pliku konfiguracji. Adres podstawowy jest używany przez narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania serwera proxy w usłudze.

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get the MSMQ queue name from appSettings in configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];

    // Create the transacted MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);

    // Create a ServiceHost for the OrderProcessorService type.
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
    {
        // Open the ServiceHost to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHost to shut down the service.
        serviceHost.Close();
    }
}
```

Nazwa kolejki MSMQ jest określona w sekcji appSettings w pliku konfiguracji, jak pokazano w poniższej konfiguracji przykładowej.

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
> Nazwa kolejki używa kropki (.) dla komputera lokalnego i separatorów ukośników odwrotnych w ścieżce podczas tworzenia kolejki przy użyciu <xref:System.Messaging>. Punkt końcowy Windows Communication Foundation (WCF) używa adresu kolejki w schemacie net. MSMQ, używa "localhost" do określenia komputera lokalnego i używa ukośników w ścieżce.

Klient tworzy zakres transakcji. Komunikacja z kolejką odbywa się w zakresie transakcji, co sprawia, że jest ona traktowana jako jednostka niepodzielna, w której wszystkie komunikaty są wysyłane do kolejki lub żaden z komunikatów nie jest wysyłany do kolejki. Transakcja jest zatwierdzana przez wywołanie <xref:System.Transactions.TransactionScope.Complete%2A> w zakresie transakcji.

```csharp
// Create a client.
OrderProcessorClient client = new OrderProcessorClient();

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

// Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    // Make a queued call to submit the purchase order.
    client.SubmitPurchaseOrder(po);
    // Complete the transaction.
    scope.Complete();
}

// Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

Aby sprawdzić, czy transakcje działają, zmodyfikuj klienta, dodając komentarz do zakresu transakcji, jak pokazano w poniższym przykładowym kodzie, Skompiluj ponownie rozwiązanie i uruchom klienta.

```csharp
//scope.Complete();
```

Ponieważ transakcja nie została ukończona, wiadomości nie są wysyłane do kolejki.

Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta. Możesz zobaczyć, że usługa odbiera komunikaty od klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta. Należy pamiętać, że ponieważ usługa kolejkowania jest w użyciu, klient i usługi nie muszą działać w tym samym czasie. Można uruchomić klienta programu, zamknąć go, a następnie uruchomić usługę i nadal otrzymuje komunikaty.

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd
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

4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

Domyślnie przy <xref:System.ServiceModel.NetMsmqBinding>włączono zabezpieczenia transportu. Istnieją dwie istotne właściwości zabezpieczeń transportu usługi MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>. Domyślnie tryb uwierzytelniania jest ustawiony na `Windows`, a poziom ochrony jest ustawiony na `Sign`. Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny i należy zainstalować opcję integracji Active Directory dla usługi MSMQ. Jeśli ten przykład zostanie uruchomiony na komputerze, który nie spełnia tych kryteriów, zostanie wyświetlony komunikat o błędzie.

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej lub bez integracji z Active Directory

1. Jeśli komputer nie jest częścią domeny lub nie ma zainstalowanej integracji Active Directory, Wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom ochrony na `None`, jak pokazano w poniższym przykładowym kodzie konfiguracyjnym.

    ```xml
    <system.serviceModel>
      <services>
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"
                 behaviorConfiguration="OrderProcessorServiceBehavior">
          <host>
            <baseAddresses>
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
            </baseAddresses>
          </host>
          <!-- Define NetMsmqEndpoint. -->
          <endpoint
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"
              binding="netMsmqBinding"
              bindingConfiguration="Binding1"
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
          <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
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
            <behavior name="OrderProcessorServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. Przed uruchomieniem przykładu należy zmienić konfigurację na serwerze i kliencie programu.

    > [!NOTE]
    > Ustawienie `security mode` `None` jest równoznaczne z ustawieniem <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>i `Message` zabezpieczenia `None`.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`
