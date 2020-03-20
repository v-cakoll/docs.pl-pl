---
title: Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 4b662094923c85e825edcc9025a73f1a1b42cb9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144243"
---
# <a name="poison-message-handling-in-msmq-40"></a>Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0
W tym przykładzie pokazano, jak wykonać trujące obsługi wiadomości w usłudze. Ten przykład jest oparty na próbce [wiązania transacted MSMQ.](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) W tym przykładzie użyto pliku `netMsmqBinding`. Usługa jest samodzielną aplikacją konsoli, która umożliwia obserwowanie usługi odbierającej wiadomości w kolejce.

 W komunikacji w kolejce klient komunikuje się z usługą przy użyciu kolejki. Dokładniej, klient wysyła wiadomości do kolejki. Usługa odbiera wiadomości z kolejki. W związku z tym usługi i klienta, nie muszą być uruchomione w tym samym czasie do komunikowania się przy użyciu kolejki.

 Trująca wiadomość to wiadomość, która jest wielokrotnie odczytywana z kolejki, gdy usługa odczytywana wiadomości nie może przetworzyć wiadomości i w związku z tym kończy transakcję, w ramach której jest odczytywana wiadomość. W takich przypadkach wiadomość zostanie ponownie ponowiona. Teoretycznie może to trwać wiecznie, jeśli pojawi się problem z przesłaniem. Może to nastąpić tylko wtedy, gdy używasz transakcji do odczytu z kolejki i wywołania operacji usługi.

 Na podstawie wersji usługi MSMQ NetMsmqBinding obsługuje ograniczone wykrywanie do pełnego wykrywania wiadomości poison. Po wykryciu wiadomości jako zatrutej, można ją obsłużyć na kilka sposobów. Ponownie, na podstawie wersji usługi MSMQ, NetMsmqBinding obsługuje ograniczoną obsługę do pełnej obsługi wiadomości trujących.

 W tym przykładzie przedstawiono ograniczone udogodnienia dotyczące trucizn na platformie Windows Server 2003 i Windows XP oraz pełne udogodnienia dotyczące trucizny dostępne w systemie Windows Vista. W obu przykładach celem jest przeniesienie trującej wiadomości z kolejki do innej kolejki. Ta kolejka może być następnie obsługiwana przez usługę trująca wiadomość.

## <a name="msmq-v40-poison-handling-sample"></a>Msmq v4.0 Próbka obsługi trucizny
 W systemie Windows Vista usługa MSMQ udostępnia zatrutą zajemkę, która może służyć do przechowywania wiadomości o truciznach. W tym przykładzie przedstawiono najlepsze praktyki radzenia sobie z trującymi wiadomościami przy użyciu systemu Windows Vista.

 Wykrywanie trujących komunikatów w systemie Windows Vista jest zaawansowane. Istnieją 3 właściwości, które pomagają w wykrywaniu. Jest <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> liczba razy dana wiadomość jest ponownie odczytywany z kolejki i wysyłane do aplikacji do przetwarzania. Komunikat jest ponownie odczytywany z kolejki, gdy jest odłożony z powrotem do kolejki, ponieważ nie można wysłać wiadomości do aplikacji lub aplikacja wycofuje transakcję w operacji usługi. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>to liczba przenoszona wiadomości do kolejki ponownych prób. Po <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> osiągnięciu wiadomości zostanie przeniesiona do kolejki ponownych prób. Właściwość <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> jest opóźnieniem czasowym, po którym wiadomość jest przenoszona z kolejki ponawiania próby z powrotem do kolejki głównej. Jest <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> resetowany do 0. Wiadomość zostanie ponownie wypróbowana. Jeśli wszystkie próby odczytania wiadomości nie powiodły się, wiadomość jest oznaczona jako zatruta.

 Gdy wiadomość jest oznaczona jako zatruta, wiadomość jest rozpatrywana zgodnie z ustawieniami w <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> wyliczeniu. Aby powtórzyć możliwe wartości:

- Błąd (domyślnie): Aby zaćterować odbiornika, a także hosta usługi.

- Upuść: Aby usunąć wiadomość.

- Przenieś: Aby przenieść wiadomość do podzasady zatrutej. Ta wartość jest dostępna tylko w systemie Windows Vista.

- Odrzucić: Aby odrzucić wiadomość, wysyłając wiadomość z powrotem do kolejki utraconych wiadomości nadawcy. Ta wartość jest dostępna tylko w systemie Windows Vista.

 Próbka pokazuje przy `Move` użyciu dyspozycji dla wiadomości trucizny. `Move`powoduje, że wiadomość, aby przejść do podkiełki trucizny.

 Umowa serwisowa `IOrderProcessor`jest , która definiuje usługę jednokierunkową, która nadaje się do użytku z kolejkami.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Operacja usługi wyświetla komunikat informujący, że przetwarza zamówienie. Aby zademonstrować funkcję trująca `SubmitPurchaseOrder` wiadomość, operacja usługi zgłasza wyjątek, aby wycofać transakcję przy losowym wywołaniu usługi. Powoduje to, że wiadomość ma zostać odłożona z powrotem w kolejce. Ostatecznie wiadomość jest oznaczona jako trucizna. Konfiguracja jest ustawiona na przeniesienie wiadomości o trucinie do podkiełka trucizny.

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

 Konfiguracja usługi zawiera następujące właściwości `receiveRetryCount`trującego komunikatu: , `maxRetryCycles` `retryCycleDelay`, i `receiveErrorHandling` jak pokazano w następującym pliku konfiguracyjnym.

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

## <a name="processing-messages-from-the-poison-message-queue"></a>Przetwarzanie wiadomości z kolejki trujących komunikatów
 Usługa trująca wiadomość odczytuje wiadomości z kolejki ostatecznej trującej wiadomości i przetwarza je.

 Wiadomości w kolejce trujących komunikatów są wiadomościami, które są adresowane do usługi, która przetwarza wiadomość, która może się różnić od punktu końcowego usługi trująca wiadomość. W związku z tym gdy usługa trująca wiadomość odczytuje wiadomości z kolejki, warstwa kanału WCF znajduje niezgodność w punktach końcowych i nie wysyła wiadomości. W takim przypadku wiadomość jest adresowany do usługi przetwarzania zamówień, ale jest odbierany przez usługę trująca wiadomość. Aby nadal odbierać wiadomość, nawet jeśli wiadomość jest adresowany do `ServiceBehavior` innego punktu końcowego, musimy dodać do filtru adresy, gdzie kryterium dopasowania jest zgodne z dowolnym punktem końcowym usługi, do którego jest zaadresowany. Jest to wymagane do pomyślnego przetwarzania wiadomości odczytywanych z kolejki trujących komunikatów.

 Sama implementacja usługi trująca wiadomość jest bardzo podobna do implementacji usługi. Realizuje kontrakt i przetwarza zamówienia. Przykład kodu jest następujący.

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

 W przeciwieństwie do usługi przetwarzania zamówień, która odczytuje wiadomości z kolejki zamówień, usługa trująca wiadomość odczytuje wiadomości z podokazji trucizny. Kolejka trucizny jest podk. Aby uzyskać do niego dostęp, podaj nazwę kolejki głównej, po której następuje ";" i nazwa podoka, w tym przypadku -"poison", jak pokazano w poniższej konfiguracji przykładowej.

> [!NOTE]
> W przykładzie dla usługi MSMQ w wersji 3.0 nazwa kolejki trucicieli nie jest kolejką podrzędną, a kolejką, do których przenieśliśmy wiadomość.

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

 Po uruchomieniu przykładu działania usługi klienta, usługi i trucić komunikatów są wyświetlane w oknach konsoli. Możesz zobaczyć, że usługa odbiera wiadomości od klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby wyłączyć usługi.

 Usługa rozpoczyna działanie, przetwarzanie zamówień i losowo rozpoczyna przetwarzanie. Jeśli komunikat wskazuje, że przetworzył zamówienie, można uruchomić klienta ponownie, aby wysłać inną wiadomość, dopóki nie zobaczysz, że usługa faktycznie zakończyła wiadomość. Na podstawie skonfigurowanych ustawień trucizny, komunikat jest próbowany raz do przetworzenia przed przeniesieniem go do ostatecznej kolejki trucizny.

```console
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

 Uruchom usługę trująca wiadomość, aby odczytać zatrutą wiadomość z kolejki trucizny. W tym przykładzie usługa trująca wiadomość odczytuje komunikat i przetwarza ją. Można zobaczyć, że zamówienie zakupu, które zostało zakończone i zatrute jest odczytywane przez usługę trująca wiadomość.

```console
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

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę

1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Jeśli usługa jest uruchamiana jako pierwsza, sprawdzi, czy kolejka jest obecna. Jeśli kolejka nie jest obecny, usługa utworzy jeden. Usługę można uruchomić najpierw, aby utworzyć kolejkę, lub utworzyć ją za pośrednictwem Menedżera kolejek usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.

    1. Otwórz Menedżera serwera w programie Visual Studio 2012.

    2. Rozwiń kartę **Funkcje.**

    3. Kliknij prawym przyciskiem myszy **pozycję Kolejki wiadomości prywatnych**i wybierz polecenie **Nowa**, **Kolejka prywatna**.

    4. Zaznacz pole **Transakcyjne.**

    5. Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.

3. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Aby uruchomić przykład w konfiguracji jedno- lub międzykomputerowej, zmień nazwy kolejki, aby odzwierciedlić rzeczywistą nazwa hosta zamiast localhost i postępuj zgodnie z instrukcjami w [uruchomionych przykładach fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).

 Domyślnie z `netMsmqBinding` transportu powiązania zabezpieczeń jest włączona. Dwie właściwości `MsmqAuthenticationMode` i `MsmqProtectionLevel`, razem określić typ zabezpieczeń transportu. Domyślnie tryb uwierzytelniania jest `Windows` ustawiony, a poziom `Sign`ochrony jest ustawiony na . Aby usługa MSMQ udostępniała funkcję uwierzytelniania i podpisywania, musi ona być częścią domeny. Po uruchomieniu tego przykładu na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "Certyfikat kolejkowania wiadomości wewnętrznych użytkownika nie istnieje".

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej

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

     Upewnij się, że punkt końcowy jest skojarzony z powiązaniem, ustawiając atrybut powiązania punktu końcowegoKonfiguracja.

2. Przed uruchomieniem przykładu upewnij się, że konfiguracja na serwerze PoisonMessageServer, serwerze i kliencie została zmieniona.

    > [!NOTE]
    > Ustawienie `security mode` `None` jest równoważne `MsmqAuthenticationMode` `MsmqProtectionLevel`z `Message` ustawieniem `None`i zabezpieczeniami .  
  
3. Aby meta data exchange działała, rejestrujemy adres URL za pomocą powiązania http. Wymaga to, aby usługa została uruchomiony w oknie polecenia z podwyższonym poziomem uprawnień. W przeciwnym razie zostanie zgłoszony `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`wyjątek, taki jak: .  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
