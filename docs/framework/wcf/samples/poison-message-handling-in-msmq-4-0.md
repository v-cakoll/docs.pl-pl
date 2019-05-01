---
title: Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: b4711d344a6ce08adc6e993c19f2c3d97f56e7b4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052095"
---
# <a name="poison-message-handling-in-msmq-40"></a>Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0
Niniejszy przykład pokazuje sposób wykonywania skażonych komunikatów w usłudze. Ten przykład jest oparty na [dokonana transakcja powiązania usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) próbki. W tym przykładzie użyto `netMsmqBinding`. Usługa jest aplikacji konsoli Self-Hosted umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.

 W komunikacie w kolejce klient komunikuje się z usługą przy użyciu kolejki. Mówiąc ściślej klient wysyła komunikaty do kolejki. Usługa odbiera komunikaty z kolejki. Usługi i klienta w związku z tym, nie musi być uruchomiona w tym samym czasie do komunikowania się za pomocą kolejki.

 Zarządzanie skażonymi komunikatami jest komunikat, który jest regularnie odczytany z kolejki, gdy usługa odczytanie komunikatu o nie może przetworzyć komunikatu i w związku z tym kończy się transakcji, w którym komunikat został odczytany. W takich przypadkach komunikat zostanie ponowiony ponownie. To może teoretycznie Przejdź w nieskończoność w przypadku problemu z komunikatem. Należy pamiętać, że to można tylko wówczas, gdy użycie transakcji do odczytu z kolejki i wywoływanie operacji usługi.

 Na podstawie wersji usługi MSMQ, NetMsmqBinding obsługuje ograniczone wykrywania pełne wykrywanie skażonych komunikatów. Po komunikat został wykryty jako intoksykowane, a następnie mogą być obsługiwane na kilka sposobów. Ponownie na podstawie wersji usługi MSMQ, NetMsmqBinding obsługuje ograniczoną obsługę pełnej obsługi wiadomości.

 W tym przykładzie pokazano ograniczone instrumenty skażone na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platformy i pełne zarządzanie skażonymi urządzeń, dostępnym na [!INCLUDE[wv](../../../../includes/wv-md.md)]. W obu przykładach celem jest Przenieś skażonych komunikatów z kolejki do innej kolejki, które następnie mogą być obsługiwane przez usługę, zarządzanie skażonymi komunikatami.

## <a name="msmq-v40-poison-handling-sample"></a>Usługi MSMQ 4.0 Poison obsługi próbki
 W [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ zapewnia funkcji skażone kolejki podrzędnej, który może służyć do przechowywania skażonych komunikatów. W tym przykładzie przedstawiono najlepsze rozwiązanie polegające na obsłudze skażonych komunikatów za pomocą [!INCLUDE[wv](../../../../includes/wv-md.md)].

 Wykrywanie skażonych komunikatów w [!INCLUDE[wv](../../../../includes/wv-md.md)] jest dość złożone. Istnieją 3 właściwości, które pomagają wykrywania. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Razy danej komunikatów jest ponownie odczytany z kolejki i wysłane do aplikacji w celu przetworzenia. Komunikat został odczytany z kolejki ponownie, gdy zostanie ono przełączone powrót do kolejki ponieważ nie można wysłać wiadomości do aplikacji lub aplikacji powoduje wycofanie transakcji w ramach operacji usługi. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> jest to liczba przypadków, gdy wiadomość zostaje przeniesiona do kolejki ponownych prób. Gdy <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> jest osiągnięty, wiadomość zostanie przeniesiona do kolejki ponownych prób. Właściwość <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> jest czas opóźnienia, po upływie którego wiadomość zostanie przeniesiona z kolejki ponawiania powrót do kolejki głównej. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Zostaje zresetowana do 0. Komunikat zostanie podjęta próba ponownie. Jeśli wszystkie próby Przeczytaj komunikat nie powiodły się, komunikat jest oznaczony jako intoksykowane.

 Gdy komunikat jest oznaczony jako intoksykowane, wiadomość została omówiona zgodnie z ustawieniami <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> wyliczenia. Zgodnie z możliwe wartości:

- Odporność (ustawienie domyślne): Aby błędów odbiornik, a także hosta usługi.

- Upuść: Można usunąć wiadomości.

- Przenieś: Przenoszenie wiadomości do podrzędnej kolejki Zarządzanie skażonymi komunikatami. Ta wartość jest dostępna tylko na [!INCLUDE[wv](../../../../includes/wv-md.md)].

- Odrzuć: Aby odrzucić wiadomości, wysyła komunikat do kolejki utraconych wiadomości przez nadawcę. Ta wartość jest dostępna tylko na [!INCLUDE[wv](../../../../includes/wv-md.md)].

 Przykład demonstruje użycie `Move` dyspozycja dla Zarządzanie skażonymi komunikatami. `Move` powoduje, że komunikat, aby przejść do skażone kolejki podrzędnej.

 Umowa serwisowa jest `IOrderProcessor`, definiujący usługi jednokierunkowej, który jest odpowiedni do użytku z kolejki.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Operacja usługi wyświetla komunikat informujący, że kolejność przetwarzania. Aby zademonstrować funkcje zarządzanie skażonymi komunikatami `SubmitPurchaseOrder` operacji usługi występuje wyjątek, można wycofać transakcji w losowych wywołania usługi. Powoduje to komunikatu powinna być umieszczona w kolejce. Po pewnym czasie komunikat jest oznaczana poison. Aby przenieść Zarządzanie skażonymi komunikatami skażone kolejki podrzędnej ustawieniu konfiguracji.

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

 Konfiguracja usługi zawiera następujące właściwości Zarządzanie skażonymi komunikatami: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, i `receiveErrorHandling` jak pokazano w następującym pliku konfiguracji.

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

## <a name="processing-messages-from-the-poison-message-queue"></a>Przetwarzanie komunikatów z kolejki Zarządzanie skażonymi komunikatami
 Usługa Zarządzanie skażonymi komunikatami odczytuje komunikaty z kolejki końcowego skażone wiadomości i przetwarza je.

 Komunikaty w kolejce Zarządzanie skażonymi komunikatami to komunikaty, które są kierowane do usługi, która przetwarza komunikat, który może być inny niż punkt końcowy usługi Zarządzanie skażonymi komunikatami. W związku z tym gdy usługa Zarządzanie skażonymi komunikatami odczytuje komunikaty z kolejki, warstwy kanału WCF umożliwia znalezienie niezgodność punktów końcowych, a nie wysyła komunikat. W takich przypadkach komunikat jest skierowana do Usługa przetwarzania zamówień, ale są odbierane przez usługę Zarządzanie skażonymi komunikatami. Aby nadal odbierać wiadomości, nawet wtedy, gdy komunikat jest skierowana do innego punktu końcowego, należy można dodać `ServiceBehavior` adresy filtr, gdzie kryterium dopasowywania ma zgodny komunikat jest skierowana do dowolnego punktu końcowego usługi. Jest to wymagane do pomyślnie przetwarzania komunikatów, które odczytany z kolejki Zarządzanie skażonymi komunikatami.

 Implementacji usługi Zarządzanie skażonymi komunikatami, sama jest bardzo podobny do implementacji usługi. On implementuje ten kontrakt i przetwarza zamówienia. Przykład kodu jest w następujący sposób.

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

 W odróżnieniu od kolejności, usługa, która odczytuje komunikaty z kolejki kolejności przetwarzania Zarządzanie skażonymi komunikatami usługi odczytuje komunikaty z poison kolejki podrzędnej. Skażone kolejki jest kolejką podrzędnych kolejki głównej, nosi nazwę "poison" i jest generowany automatycznie przez usługę MSMQ. Aby uzyskać do niego dostęp, należy podać nazwę kolejki głównej, a następnie ";" i podrzędny nazwę kolejki, w tym przypadku — "skażone", jak pokazano w poniższym Przykładowa konfiguracja.

> [!NOTE]
>  W tym przykładzie dla usługi MSMQ w wersji 3.0 Nazwa kolejki skażone nie jest kolejką podrzędnych zamiast przenieśliśmy komunikat do kolejki.

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

 Po uruchomieniu przykładu klienta, usług i zarządzanie skażonymi komunikatami usługi działań są wyświetlane w konsoli systemu windows. Możesz zobaczyć komunikaty odbierania usługi z klienta. Naciśnij klawisz ENTER w oknie konsoli, każdy zamknięcia usługi.

 Usługa rozpoczyna się systemem, przetwarzania zamówień i losowo rozpoczyna się o zakończeniu przetwarzania. Jeśli komunikat wskazuje, że został przetworzony, kolejność, można uruchomić klienta ponownie, aby wysłać kolejną wiadomość, aż zobaczysz, że usługa rzeczywiście został zakończony wiadomość. Na podstawie skonfigurowanych ustawień skażone wiadomości zostanie podjęta próba raz do przetwarzania przed jego przeniesieniem do końcowego skażone kolejki.

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

 Uruchom usługę Zarządzanie skażonymi komunikatami, można odczytać uszkodzone kolejką komunikatu z kolejki skażone. W tym przykładzie Usługa Zarządzanie skażonymi komunikatami odczytuje komunikat i przetwarza je. Można zobaczyć, czy zamówienie zakupu, które zostały zakończone, a następnie intoksykowane jest odczytywany przez usługę Zarządzanie skażonymi komunikatami.

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

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny. Jeśli kolejka nie jest obecny, będzie utworzyć usługę. Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.

    1. Otwórz Menedżera serwera w programie Visual Studio 2012.

    2. Rozwiń **funkcji** kartę.

    3. Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.

    4. Sprawdź **transakcyjna** pole.

    5. Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.

3. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Do uruchomienia przykładu w konfiguracji o jednym lub wielu komputera, należy zmienić nazwy kolejki, aby odzwierciedlić rzeczywiste nazwy hosta zamiast nazwy localhost i postępuj zgodnie z instrukcjami w [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

 Domyślnie `netMsmqBinding` powiązania transportu, zabezpieczeń jest włączone. Dwie właściwości `MsmqAuthenticationMode` i `MsmqProtectionLevel`, wspólnie określić typ zabezpieczeń transportu. Domyślnie, tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`. Dla usługi MSMQ zapewniać uwierzytelnianie i funkcji podpisywania należy do domeny. Po uruchomieniu tego przykładu na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "Użytkownika wewnętrznego kolejkowania certyfikatu nie istnieje".

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Do uruchomienia przykładu na komputer przyłączony do grupy roboczej

1. Jeśli komputer nie jest częścią domeny, należy wyłączyć zabezpieczenia transportu, ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższym Przykładowa konfiguracja:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Upewnij się, że punkt końcowy jest skojarzony z powiązaniem przez ustawienie atrybutu bindingConfiguration punktu końcowego.

2. Upewnij się, zmień konfigurację na PoisonMessageServer, serwera i klienta, przed uruchomieniem przykładu.

    > [!NOTE]
    >  Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia `MsmqAuthenticationMode`, `MsmqProtectionLevel`, i `Message` security `None`.  
  
3. Aby Meta wymiany danych do pracy zarejestrujemy adres URL dla wiązania http. Wymaga to, że usługa jest uruchomiona w oknie wiersza polecenia z podwyższonym poziomem uprawnień. W przeciwnym razie użytkownik uzyska wyjątek, takich jak: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
