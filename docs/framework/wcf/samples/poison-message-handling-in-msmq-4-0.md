---
title: Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: f20f7cec29574746edc84d45171cfa63a5682337
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039088"
---
# <a name="poison-message-handling-in-msmq-40"></a>Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0
Ten przykład pokazuje, jak przeprowadzić obsługę skażonych komunikatów w usłudze. Ten przykład jest oparty na przykładowym [wiązaniem usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) . Ten przykład używa `netMsmqBinding`. Usługa to samodzielna aplikacja konsolowa, która umożliwia obserwowanie usługi do odebrania komunikatów znajdujących się w kolejce.

 W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki. Dokładniej, klient wysyła komunikaty do kolejki. Usługa odbiera komunikaty z kolejki. W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.

 Trująca wiadomość jest komunikatem, który jest wielokrotnie odczytywany z kolejki, gdy usługa odczytująca wiadomość nie może przetworzyć komunikatu i w związku z tym kończy transakcję, w ramach której wiadomość jest odczytywana. W takich przypadkach komunikat zostanie ponowiony ponownie. Może to teoretycznie potrwać w razie wystąpienia problemu z komunikatem. Należy zauważyć, że może się to zdarzyć tylko w przypadku używania transakcji do odczytu z kolejki i wywołania operacji usługi.

 Na podstawie wersji usługi MSMQ, usługa msmqbinding obsługuje ograniczone wykrywanie do pełnego wykrywania skażonych komunikatów. Po wykryciu komunikatu jako trującego można go obsłużyć na kilka sposobów. Ponownie na podstawie wersji usługi MSMQ, usługa msmqbinding obsługuje ograniczoną obsługę do pełnej obsługi skażonych komunikatów.

 Ten przykład ilustruje ograniczoną liczbę skażonych obiektów, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] które [!INCLUDE[wxp](../../../../includes/wxp-md.md)] są dostępne dla i na platformie i [!INCLUDE[wv](../../../../includes/wv-md.md)]pełnych trujących obiektów. W obu przykładach celem jest przeniesienie skażonego komunikatu z kolejki do innej kolejki, która następnie może być serwisowana przez trującą usługę komunikatów.

## <a name="msmq-v40-poison-handling-sample"></a>Przykład obsługi trującej usługi MSMQ v 4.0
 W [!INCLUDE[wv](../../../../includes/wv-md.md)]programie usługa MSMQ udostępnia funkcję podkolejki trującej, która może być używana do przechowywania skażonych komunikatów. Ten przykład pokazuje najlepsze rozwiązanie dotyczące postępowania z trującymi komunikatami [!INCLUDE[wv](../../../../includes/wv-md.md)]przy użyciu.

 Wykrywanie skażonych komunikatów w [!INCLUDE[wv](../../../../includes/wv-md.md)] programie jest dość zaawansowane. Istnieją 3 właściwości, które pomagają w wykrywaniu. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Jest to liczba przypadków, w których dany komunikat jest ponownie odczytywany z kolejki i wysyłany do aplikacji w celu przetworzenia. Komunikat jest ponownie odczytywany z kolejki, gdy zostanie przywrócony do kolejki, ponieważ nie można wysłać komunikatu do aplikacji lub aplikacja Wycofuje transakcję w operacji usługi. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>jest to liczba przenoszonych wiadomości do kolejki ponownych prób. Gdy <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> zostanie osiągnięty, wiadomość zostanie przeniesiona do kolejki ponownych prób. Właściwość <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> jest opóźnieniem, po którym komunikat jest przenoszony z kolejki ponownych prób z powrotem do kolejki głównej. Wartość <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> zostanie zresetowana do 0. Wiadomość zostanie ponowiona. Jeśli wszystkie próby odczytu komunikatu zakończyły się niepowodzeniem, komunikat jest oznaczony jako trujący.

 Gdy wiadomość zostanie oznaczona jako trująca, komunikat jest rozpatrywany zgodnie z ustawieniami <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> wyliczenia. Aby ponownie powtórzyć możliwe wartości:

- Błąd (domyślnie): Aby wypróbować odbiornik, a także hosta usługi.

- Listy rozwijanej , Aby usunąć komunikat.

- Przenieś Aby przenieść komunikat do podkolejki trujących komunikatów. Ta wartość jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)]systemie.

- Oznacza Aby odrzucić komunikat, należy wysłać wiadomość z powrotem do kolejki utraconych wiadomości nadawcy. Ta wartość jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)]systemie.

 Przykład ilustruje użycie `Move` dyspozycji dla trującej wiadomości. `Move`powoduje, że komunikat jest przenoszony do podkolejki trującej.

 Kontrakt usługi to `IOrderProcessor`, który definiuje usługę jednokierunkową, która jest odpowiednia do użycia z kolejkami.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Operacja usługi wyświetla komunikat informujący o przetwarzaniu zamówienia. Aby zademonstrować działanie trującej wiadomości `SubmitPurchaseOrder` , operacja usługi zgłasza wyjątek, aby wycofać transakcję w losowym wywołaniu usługi. Powoduje to, że komunikat zostanie umieszczony w kolejce. Ostatecznie wiadomość jest oznaczona jako trująca. Konfiguracja jest ustawiona tak, aby przenieść skażony komunikat do podkolejki trującej.

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    static Random r = new Random(137);

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {

        int randomNumber = r.Next(10);

        if (randomNumber % 2 == 0)
        {
            Orders.Add(po);
            Console.WriteLine("Processing {0} ", po);
        }
        else
        {
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);
            Console.WriteLine();
            throw new Exception("Cannot process purchase order: " + po.PONumber);
        }
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted");
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Get MSMQ queue name from app settings in configuration.
        string queueName = ConfigurationManager.AppSettings["queueName"];

        // Create the transacted MSMQ queue if necessary.
        if (!System.Messaging.MessageQueue.Exists(queueName))
            System.Messaging.MessageQueue.Create(queueName, true);

        // Get the base address that is used to listen for WS-MetaDataExchange requests.
        // This is useful to generate a proxy for the client.
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        // Open the ServiceHostBase to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        if(serviceHost.State != CommunicationState.Faulted) {
            serviceHost.Close();
        }

    }
}
```

 Konfiguracja usługi zawiera następujące `receiveRetryCount`właściwości trujących komunikatów:, `maxRetryCycles`, `retryCycleDelay`i `receiveErrorHandling` , jak pokazano w następującym pliku konfiguracyjnym.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>
  </appSettings>
  <system.serviceModel>
    <services>
      <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"
                  binding="netMsmqBinding"
                  bindingConfiguration="PoisonBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <bindings>
      <netMsmqBinding>
        <binding name="PoisonBinding"
                 receiveRetryCount="0"
                 maxRetryCycles="1"
                 retryCycleDelay="00:00:05"
                 receiveErrorHandling="Move">
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="processing-messages-from-the-poison-message-queue"></a>Przetwarzanie komunikatów z kolejki skażonych komunikatów
 Usługa Trująca wiadomość odczytuje komunikaty z kolejki skażonych komunikatów i przetwarza je.

 Wiadomości w kolejce trujących komunikatów to komunikaty, które są rozkierowane do usługi przetwarzającej komunikat, co może się różnić od punktu końcowego trującej usługi komunikatów. W związku z tym, gdy usługa Trująca wiadomość odczytuje komunikaty z kolejki, warstwa kanału WCF znajdzie niezgodność w punktach końcowych i nie wysyła komunikatu. W takim przypadku komunikat jest kierowany do usługi przetwarzania zamówień, ale jest odbierany przez usługę trujących komunikatów. Aby nadal otrzymywać komunikat nawet wtedy, gdy wiadomość jest zakierowane do innego punktu końcowego, należy dodać `ServiceBehavior` do filtru, gdzie kryterium dopasowywania jest zgodne z dowolnymi punktami końcowymi, do których odnosi się komunikat. Jest to wymagane do pomyślnego przetworzenia komunikatów odczytywanych z kolejki skażonych komunikatów.

 Sama implementacja usługi trującej wiadomości jest podobna do implementacji usługi. Implementuje kontrakt i przetwarza zamówienia. Przykładowy kod jest następujący.

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted...exiting app");
        Environment.Exit(1);
    }

    // Host the service within this EXE console application.
    public static void Main()
    {

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The poison message service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHostBase to shutdown the service.
        if(serviceHost.State != CommunicationState.Faulted)
        {
            serviceHost.Close();
        }
    }
```

 W przeciwieństwie do usługi przetwarzania zamówień, która odczytuje komunikaty z kolejki kolejności, usługa Trująca wiadomość odczytuje komunikaty z podkolejki trującej. Kolejka Trująca jest podkolejki kolejki głównej, nosi nazwę "Trująca" i jest generowana automatycznie przez usługę MSMQ. Aby uzyskać do niego dostęp, podaj nazwę kolejki głównej, po której następuje ";" i nazwę kolejki podrzędnej, w tym przypadku "trujące", jak pokazano w poniższej konfiguracji przykładowej.

> [!NOTE]
> W przykładzie dla MSMQ v 3.0 nazwa kolejki trującej nie jest kolejką podrzędną, a nie kolejkę, do której przeniesiono komunikat.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >
        </endpoint>
      </service>
    </services>

  </system.serviceModel>
</configuration>
```

 Po uruchomieniu przykładu działania usług Klient, usługa i Trująca wiadomość są wyświetlane w oknach konsoli. Możesz zobaczyć, że usługa odbiera komunikaty od klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługi.

 Usługa uruchamia się, przetwarza zamówienia i losowo rozpoczyna przetwarzanie. Jeśli komunikat wskazuje, że przetworzył zamówienie, można ponownie uruchomić klienta, aby wysłać kolejny komunikat, dopóki usługa nie zakończyła się komunikatem. W oparciu o skonfigurowane ustawienia trujące komunikat jest podejmowany raz na potrzeby przetwarzania przed przeniesieniem go do końcowej kolejki trującej.

```
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
```

 Uruchom usługę trującej wiadomości, aby odczytać trującą wiadomość z kolejki trującej. W tym przykładzie usługa Trująca wiadomość odczytuje komunikat i przetwarza go. Można zobaczyć, że zamówienie zakupu, które zostało zakończone i trujące jest odczytywane przez trującą usługę komunikatów.

```
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Jeśli usługa jest uruchamiana po raz pierwszy, sprawdzi, czy kolejka jest obecna. Jeśli kolejka nie istnieje, usługa utworzy ją. Aby utworzyć kolejkę, można najpierw uruchomić tę usługę lub utworzyć ją za pośrednictwem Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.

    1. Otwórz Menedżer serwera w programie Visual Studio 2012.

    2. Rozwiń kartę **funkcje** .

    3. Kliknij prawym przyciskiem myszy pozycję **prywatne kolejki komunikatów**, a następnie wybierz kolejno pozycje **Nowa**i **prywatne**.

    4. Zaznacz pole **transakcyjne** .

    5. Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.

3. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, należy zmienić nazwy kolejek, aby odzwierciedlały rzeczywistą nazwę hosta zamiast hosta lokalnego i postępować zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

 Domyślnie w przypadku `netMsmqBinding` transportu powiązań jest włączone zabezpieczenia. Dwie właściwości, `MsmqAuthenticationMode` a `MsmqProtectionLevel`także określają typ zabezpieczenia transportu. Domyślnie tryb uwierzytelniania jest ustawiony na `Windows` , a poziom ochrony jest ustawiony na. `Sign` Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny. Jeśli ten przykład zostanie uruchomiony na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "Wewnętrzny certyfikat usługi kolejkowania komunikatów użytkownika nie istnieje".

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej

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

     Upewnij się, że punkt końcowy jest skojarzony z powiązaniem, ustawiając atrybut bindingConfiguration punktu końcowego.

2. Przed uruchomieniem przykładu należy zmienić konfigurację na PoisonMessageServer, serwerze i kliencie.

    > [!NOTE]
    > `security mode` Ustawienieodpowiada`MsmqAuthenticationMode`ustawieniu ,`MsmqProtectionLevel` i`None`zabezpieczenia na. `Message` `None`  
  
3. Aby wymiana metadanych działała, rejestrujemy adres URL z powiązaniem HTTP. Wymaga to uruchomienia usługi w oknie polecenia z podwyższonym poziomem uprawnień. W przeciwnym razie zostanie wyświetlony wyjątek, taki jak `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`:.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
