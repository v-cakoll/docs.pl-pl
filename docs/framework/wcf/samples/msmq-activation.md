---
title: Aktywacja usługi MSMQ
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 0dbd24a612d56c0fe88066f625be2a8369b7df5b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602545"
---
# <a name="msmq-activation"></a>Aktywacja usługi MSMQ

Ten przykład pokazuje, jak hostować aplikacje w usłudze aktywacji procesów systemu Windows (WAS) odczytywane z kolejki komunikatów. Ten przykład używa `netMsmqBinding` i jest oparty na [dwukierunkowej](two-way-communication.md) próbce komunikacji. Usługa w tym przypadku jest aplikacją hostowaną w sieci Web, a klient jest samoobsługowy i wyprowadza do konsoli, aby obserwować stan przesłanych zamówień zakupu.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

> [!NOTE]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> \<InstallDrive>: \ WF_WCF_Samples
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie WCF i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> \<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.

Usługa aktywacji procesów systemu Windows (WAS), nowy mechanizm aktywacji procesu dla systemu Windows Server 2008, zapewnia funkcje podobne do usług IIS, które były wcześniej dostępne tylko dla aplikacji opartych na protokole HTTP, do aplikacji korzystających z protokołów innych niż HTTP. Windows Communication Foundation (WCF) używa interfejsu adaptera odbiornika do przekazywania żądań aktywacji odbieranych za pośrednictwem protokołów innych niż HTTP obsługiwanych przez funkcję WCF, takich jak TCP, nazwane potoki i MSMQ. Funkcja otrzymywania żądań za pośrednictwem protokołów innych niż HTTP jest hostowana przez zarządzane usługi systemu Windows działające w SMSvcHost. exe.

Usługa adaptera odbiornika NET. msmq (NetMsmqActivator) aktywuje aplikacje znajdujące się w kolejce na podstawie komunikatów w kolejce.

Klient wysyła zamówienia zakupu do usługi z zakresu transakcji. Usługa otrzymuje zamówienia w transakcji i przetwarza je. Następnie usługa wywołuje klienta przy użyciu stanu zamówienia. Aby ułatwić komunikację dwukierunkową, klient i usługa używają kolejek do dodawania do kolejki zamówień zakupu i stanu zamówienia.

Kontrakt usługi `IOrderProcessor` definiuje jednokierunkowe operacje usługi, które działają z kolejkowanie. Operacja usługi używa punktu końcowego odpowiedzi do wysyłania do klienta stanu zamówienia. Adres punktu końcowego odpowiedzi to identyfikator URI kolejki użytej do wysłania stanu zamówienia z powrotem do klienta. Aplikacja do przetwarzania zamówień implementuje ten kontrakt.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po,
                                           string reportOrderStatusTo);
}
```

Kontrakt odpowiedzi, do którego ma zostać wysłana stan zamówienia, jest określany przez klienta. Klient implementuje kontrakt stanu zamówienia. Usługa używa wygenerowanego klienta tego kontraktu do wysyłania stanu zamówienia z powrotem do klienta.

```csharp
[ServiceContract]
public interface IOrderStatus
{
    [OperationContract(IsOneWay = true)]
    void OrderStatus(string poNumber, string status);
}
```

Operacja usługi przetwarza przesłane zamówienie zakupu. <xref:System.ServiceModel.OperationBehaviorAttribute>Jest stosowana do operacji usługi, aby określić automatyczną rejestrację w transakcji, która jest używana do odbierania komunikatu z kolejki i automatycznego uzupełniania transakcji po zakończeniu operacji usługi. `Orders`Klasa hermetyzuje funkcje przetwarzania zamówień. W takim przypadku dodaje zamówienie zakupu do słownika. Transakcja, w której rejestrowana jest operacja usługi, jest dostępna dla operacji w `Orders` klasie.

Operacja usługi, oprócz przetwarzania przesłanego zamówienia zakupu, odpowiada klientowi na informacje o stanie zamówienia.

```csharp
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
        Console.WriteLine("Sending back order status information");
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));
        // please note that the same transaction that is used to dequeue purchase order is used
        // to send back order status
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.OrderStatus(po.PONumber, po.Status);
            scope.Complete();
        }
    }
}
```

Powiązanie klienta do użycia jest określone przy użyciu pliku konfiguracji.

Nazwa kolejki MSMQ jest określona w sekcji appSettings w pliku konfiguracji. Punkt końcowy usługi jest zdefiniowany w sekcji System. serviceModel w pliku konfiguracji.

> [!NOTE]
> Nazwa kolejki MSMQ i adres punktu końcowego używają nieco różnych konwencji adresowania. Nazwa kolejki MSMQ używa kropki (.) dla komputera lokalnego i separatorów ukośników odwrotnych. Adres punktu końcowego programu WCF określa obiekt net. MSMQ: schemat, używa "localhost" dla komputera lokalnego i używa ukośników w ścieżce. Aby odczytać z kolejki hostowanej na komputerze zdalnym, Zastąp ciąg "." i "localhost" nazwą komputera zdalnego.

Plik. svc o nazwie klasy jest używany do hostowania kodu usługi w programie.

Sam plik Service. svc zawiera dyrektywę służącą do utworzenia `OrderProcessorService` .

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>`

Plik Service. svc zawiera także dyrektywę zestawu, aby upewnić się, że system. Transactions. dll jest załadowany.

`<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>`

Klient tworzy zakres transakcji. Komunikacja z usługą odbywa się w zakresie transakcji, powodując, że jest ona traktowana jako jednostka niepodzielna, w której wszystkie komunikaty kończą się powodzeniem lub niepowodzeniem. Transakcja jest zatwierdzona przez wywołanie `Complete` zakresu transakcji.

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))
{
    // Open the ServiceHostBase to create listeners and start listening
    // for order status messages.
    serviceHost.Open();

    // Create a proxy with given client endpoint configuration
    OrderProcessorClient client = new OrderProcessorClient();

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
    using (TransactionScope scope = new
        TransactionScope(TransactionScopeOption.Required))
    {
        // Make a queued call to submit the purchase order
        client.SubmitPurchaseOrder(po,
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");
        // Complete the transaction.
        scope.Complete();
    }

    //Closing the client gracefully closes the connection and cleans up
    //resources
    client.Close();

    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();

    // Close the ServiceHostBase to shutdown the service.
    serviceHost.Close();
    }
```

Kod klienta implementuje kontrakt, `IOrderStatus` Aby otrzymać stan zamówienia z usługi. W takim przypadku drukuje stan zamówienia.

```csharp
[ServiceBehavior]
public class OrderStatusService : IOrderStatus
{
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]
    public void OrderStatus(string poNumber, string status)
    {
        Console.WriteLine("Status of order {0}:{1} ",
                                         poNumber , status);
    }
}
```

Kolejka stanu zamówienia jest tworzona w `Main` metodzie. Konfiguracja klienta zawiera konfigurację usługi stanu zamówienia do hostowania usługi stanu zamówienia, jak pokazano w poniższej konfiguracji przykładowej.

```xml
<appSettings>
    <!-- use appSetting to configure MSMQ queue name -->
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />
  </appSettings>

<system.serviceModel>

    <services>
      <service
         name="Microsoft.ServiceModel.Samples.OrderStatusService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
    </client>

  </system.serviceModel>
```

Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie Windows, jak i w konsoli klienta. Można zobaczyć, że serwer odbiera komunikaty od klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć serwer i klienta.

Klient wyświetla informacje o stanie zamówienia wysyłane przez serwer:

```console
Press <ENTER> to terminate client.
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że usługi IIS 7,0 są zainstalowane, ponieważ są wymagane do aktywacji.

2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md). Ponadto należy zainstalować składniki aktywacji inne niż HTTP programu WCF:

    1. Z menu **Start** wybierz pozycję **Panel sterowania**.

    2. Wybierz **programy i funkcje**.

    3. Kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows**.

    4. W obszarze **Podsumowanie funkcji**kliknij pozycję **Dodaj funkcje**.

    5. Rozwiń węzeł **Microsoft .NET Framework 3,0** i Sprawdź funkcję **aktywacji Windows Communication Foundation niehttp** .

3. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

4. Uruchom klienta programu, wykonując polecenie Client. exe z okna polecenia. Spowoduje to utworzenie kolejki i wysłanie do niej komunikatu. Pozostaw uruchomiony klient, aby zobaczyć wynik usługi odczytującej komunikat

5. Domyślnie usługa aktywacji usługi MSMQ działa jako usługa sieciowa. W związku z tym Kolejka służąca do aktywowania aplikacji musi mieć uprawnienia do odbierania i wglądu w usługę sieciową. Można to dodać przy użyciu programu MMC usługi kolejkowania komunikatów:

    1. W menu **Start** kliknij polecenie **Uruchom**, a następnie wpisz `Compmgmt.msc` i naciśnij klawisz ENTER.

    2. W obszarze **usługi i aplikacje**rozwiń węzeł **kolejkowanie komunikatów**.

    3. Kliknij pozycję **kolejki prywatne**.

    4. Kliknij prawym przyciskiem myszy kolejkę (ServiceModelSamples/Service. svc) i wybierz polecenie **Właściwości**.

    5. Na karcie **zabezpieczenia** kliknij pozycję **Dodaj** i Udziel uprawnień wglądu i Odbierz do usługi sieciowej.

6. Skonfiguruj usługę aktywacji procesów systemu Windows (WAS) do obsługi aktywacji usługi MSMQ.

    Jako wygoda, następujące kroki są zaimplementowane w pliku wsadowym o nazwie AddMsmqSiteBinding. cmd znajdującym się w katalogu przykładowym.

    1. Aby można było obsługiwać aktywację net. MSMQ, domyślna witryna sieci Web musi być najpierw powiązana z protokołem net. MSMQ. Można to zrobić za pomocą programu Appcmd. exe, który jest instalowany przy użyciu zestawu narzędzi do zarządzania usługami IIS 7,0. W wierszu polecenia z podwyższonym poziomem uprawnień (Administrator) Uruchom następujące polecenie.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > To polecenie jest pojedynczym wierszem tekstu.

        To polecenie dodaje powiązanie witryny net. MSMQ do domyślnej witryny sieci Web.

    2. Mimo że wszystkie aplikacje w lokacji współdzielą wspólne powiązanie net. MSMQ, każda aplikacja może włączyć obsługę usługi net. MSMQ osobno. Aby włączyć usługę net. msmq dla aplikacji/servicemodelsamples, uruchom następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq
        ```

        > [!NOTE]
        > To polecenie jest pojedynczym wierszem tekstu.

        To polecenie umożliwia dostęp do aplikacji/servicemodelsamples przy użyciu `http://localhost/servicemodelsamples` i `net.msmq://localhost/servicemodelsamples` .

7. Jeśli nie zostało to wcześniej zrobione, upewnij się, że usługa aktywacji MSMQ jest włączona. W menu **Start** kliknij polecenie **Uruchom**, a następnie wpisz `Services.msc` . Przeszukaj listę usług dla **karty odbiornika NET. MSMQ**. Kliknij prawym przyciskiem myszy i wybierz pozycję **Właściwości**. Ustaw **Typ uruchamiania** na **automatyczny**, kliknij przycisk **Zastosuj** , a następnie kliknij przycisk **Uruchom** . Ten krok należy wykonać tylko raz przed pierwszym użyciem usługi adaptera odbiornika NET. MSMQ.

8. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md). Ponadto należy zmienić kod na kliencie, który przesyła zamówienie zakupu w celu odzwierciedlenia nazwy komputera w identyfikatorze URI kolejki podczas przesyłania zamówienia zakupu. Użyj następującego kodu:

    ```csharp
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");
    ```

9. Usuń powiązanie witryny net. MSMQ dodane do tego przykładu.

    Jako wygoda, następujące kroki są zaimplementowane w pliku wsadowym o nazwie RemoveMsmqSiteBinding. cmd, który znajduje się w przykładowym katalogu:

    1. Usuń usługę net. MSMQ z listy włączonych protokołów, uruchamiając następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > To polecenie jest pojedynczym wierszem tekstu.

    2. Usuń powiązanie witryny net. MSMQ, uruchamiając następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > To polecenie jest pojedynczym wierszem tekstu.

    > [!WARNING]
    > Uruchomienie pliku wsadowego spowoduje zresetowanie tej opcji do uruchamiania przy użyciu .NET Framework w wersji 2,0.

Domyślnie w przypadku `netMsmqBinding` transportu powiązań jest włączone zabezpieczenia. Dwie właściwości, `MsmqAuthenticationMode` a `MsmqProtectionLevel` także określają typ zabezpieczenia transportu. Domyślnie tryb uwierzytelniania jest ustawiony na `Windows` , a poziom ochrony jest ustawiony na `Sign` . Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny. Jeśli ten przykład zostanie uruchomiony na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący komunikat o błędzie: "wewnętrzny certyfikat usługi kolejkowania komunikatów użytkownika nie istnieje".

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej

1. Jeśli komputer nie jest częścią domeny, Wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom ochrony na brak, jak pokazano w poniższej konfiguracji przykładowej.

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding configurationName="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

2. Przed uruchomieniem przykładu Zmień konfigurację na serwerze i kliencie.

    > [!NOTE]
    > Ustawienie `security mode` odpowiada `None` ustawieniu `MsmqAuthenticationMode` `MsmqProtectionLevel` i `Message` zabezpieczenia na `None` .

3. Aby włączyć aktywację na komputerze przyłączonym do grupy roboczej, należy uruchomić zarówno usługę aktywacji, jak i proces roboczy przy użyciu określonego konta użytkownika (musi być taka sama dla obu), a kolejka musi mieć listy ACL dla określonego konta użytkownika.

     Aby zmienić tożsamość, w której uruchamiany jest proces roboczy:

    1. Uruchom plik inetmgr. exe.

    2. W obszarze **Pule aplikacji**kliknij prawym przyciskiem myszy pozycję **puli aplikacji** (zazwyczaj **Domyślna pula**aplikacji), a następnie wybierz pozycję **Ustaw wartości domyślne puli.**

    3. Zmień właściwości tożsamości, aby użyć określonego konta użytkownika.

     Aby zmienić tożsamość, w której działa usługa aktywacji:

    1. Uruchom Services. msc.

    2. Kliknij prawym przyciskiem myszy **kartę net. MsmqListener**, a następnie wybierz polecenie **Właściwości**.

4. Zmień konto na karcie **Logowanie** .

5. W grupie roboczej usługa musi również działać przy użyciu nieograniczonego tokenu. Aby to zrobić, uruchom następujące polecenie w oknie polecenia:

    ```console
    sc sidtype netmsmqactivator unrestricted
    ```

## <a name="see-also"></a>Zobacz też

- [Przykłady hostingu i trwałości usługi AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
