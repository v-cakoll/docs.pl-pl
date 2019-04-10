---
title: Aktywacja usługi MSMQ
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: d83759f321abe7fa7e39202daadd4ceda82d8f23
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295682"
---
# <a name="msmq-activation"></a>Aktywacja usługi MSMQ
Niniejszy przykład pokazuje, jak hostować aplikacje w Windows Process Activation Service (WAS), które są odczytywane z kolejki komunikatów. W tym przykładzie użyto `netMsmqBinding` i opiera się na [komunikacji dwustronny](../../../../docs/framework/wcf/samples/two-way-communication.md) próbki. Usługa jest w tym przypadku aplikacji hostowanej w sieci Web w języku klienta i jest samodzielnie hostowana w konsoli, aby obserwować stan zamówienia zakupu przesłane dane wyjściowe.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
> [!NOTE]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  \<InstallDrive>:\WF_WCF_Samples  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich usług WCF i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  \<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.  
  
 Windows Process Activation Service (WAS), przy użyciu nowego procesu aktywacji mechanizmu [!INCLUDE[lserver](../../../../includes/lserver-md.md)], zapewnia funkcje podobne do usług IIS, które były wcześniej dostępne tylko dla aplikacji opartych na protokole HTTP dla aplikacji, które używają protokołów innych niż HTTP. Windows Communication Foundation (WCF) używa interfejsu karty odbiornika do komunikowania się żądania aktywacji, które są odbierane za pośrednictwem protokołów innych niż HTTP obsługiwane przez architekturę WCF, takie jak TCP, potoków nazwanych i usługi MSMQ. Funkcje do odbierania żądań za pośrednictwem protokołów innych niż HTTP jest hostowana przez zarządzane usługi Windows SMSvcHost.exe.  
  
 Usługa Net.Msmq odbiornika Adapter (NetMsmqActivator) aktywuje umieszczonych w kolejce aplikacje oparte na komunikaty w kolejce.  
  
 Klient wysyła zamówienia zakupu usługi z zakresu transakcji. Ta usługa odbiera zamówień w ramach transakcji i przetwarza je. Usługa następnie ponownie wywołuje klienta z stan zamówienia. Ułatwianie dwukierunkowej komunikacji klienta i usługi użyj kolejki, aby umieścić zakupów i stanu zamówienia.  
  
 Kontrakt usługi `IOrderProcessor` definiuje operacje usługi jednokierunkowej, współpracujących z usługi kolejkowania wiadomości. Operacja usługi używa odpowiedzi punktu końcowego do wysyłania stanów zlecenia do klienta. Adres punktu końcowego odpowiedzi jest identyfikatorem URI, kolejki, używane do wysyłania stan zamówienia klienta. Kolejność przetwarzania aplikacji implementuje ten kontrakt.  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 Kontrakt odpowiedź do wysłania raportowanie stanu zamówienia jest określony przez klienta. Klient implementuje ten kontrakt stan zamówienia. Usługa używa wygenerowanego klienta ten kontrakt do odesłania stan zamówienia do klienta.  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 Operacja usługi przetworzy to zamówienie zakupu przesłane. <xref:System.ServiceModel.OperationBehaviorAttribute> Jest stosowany do operacji usługi, aby określić automatycznej rejestracji w transakcji, która jest używana do odbierania wiadomości z kolejki i automatycznego uzupełniania transakcji po zakończeniu operacji usługi. `Orders` Klasa hermetyzuje funkcjonalność przetwarzania zamówienia. W tym przypadku dodaje zamówienia zakupu w słowniku. Operacja usługi zarejestrowany w transakcji jest dostępna dla operacji w `Orders` klasy.  
  
 Operacja usługi, oprócz przetwarzania zamówienia zakupu przesłanych odpowiedzi do klienta o stanie zamówienia.  
  
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
  
 Klient powiązania do użycia jest określony, przy użyciu pliku konfiguracji.  
  
 Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji. Punkt końcowy usługi jest zdefiniowany w sekcji System.serviceModel pliku konfiguracji.  
  
> [!NOTE]
>  Adres nazwy i punkt końcowy kolejki usługi MSMQ Użyj nieco Konwencji adresowania. Nazwa kolejki usługi MSMQ używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnik odwrotny w ścieżce. Adres punktu końcowego WCF określa net.msmq: schemat, używane "localhost" na komputerze lokalnym i korzysta z ukośników w ścieżce. Aby zapoznać się z kolejki znajdującej się na komputerze zdalnym, zastąp "." i "localhost" do nazwy komputera zdalnego.  
  
 Plik .svc o nazwie klasy jest używana do hostowania kodu usługi WAS.  
  
 Sam plik Service.svc zawiera dyrektywy do tworzenia `OrderProcessorService`.  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 Plik Service.svc zawiera również dyrektywę zestawu, aby upewnić się, że System.Transactions.dll zostanie załadowana.  
  
```svc  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 Klient tworzy zakres transakcji. Komunikacja z usługą odbywa się w zakresie transakcji, co powoduje powinien być traktowany jako pojedynczej Atomowej jednostki, której wszystkie komunikaty sukces lub niepowodzenie. Transakcja została zatwierdzona przez wywołanie metody `Complete` w zakresie transakcji.  
  
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
  
 Kod klienta implementuje `IOrderStatus` umowę odbierać stan zamówienia z usługi. W tym przypadku wyświetla się stan zamówienia.  
  
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
  
 Kolejkę stanu zamówienia jest tworzony w `Main` metody. Konfiguracja klienta obejmuje konfigurację usługi stanu zamówienia do hostowania usługi stanu zamówienia, jak pokazano w poniższym Przykładowa konfiguracja.  
  
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
  
 Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w serwera i klienta okna konsoli. Możesz zobaczyć serwer odbiera komunikaty z klienta. Naciśnij klawisz ENTER w oknie konsoli, każdej do zamykania serwera i klienta.  
  
 Klient Wyświetla informacje o stanie zamówienia, które zostały przesłane przez serwer:  
  
```console  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jest zainstalowany, ponieważ jest on wymagany do aktywacji WAS.  
  
2. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md). Ponadto należy zainstalować składniki Aktywacja bez HTTP programu WCF:  
  
    1.  Z **Start** menu, wybierz **Panelu sterowania**.  
  
    2.  Wybierz **programy i funkcje**.  
  
    3.  Kliknij przycisk **Włącz lub wyłącz funkcje Windows**.  
  
    4.  W obszarze **Podsumowanie funkcji**, kliknij przycisk **Dodaj funkcje**.  
  
    5.  Rozwiń **Microsoft .NET Framework 3.0** węzła i wyboru **Aktywacja bez HTTP programu Windows Communication Foundation** funkcji.  
  
3. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Uruchom klienta, wykonując client.exe z okna poleceń. To tworzy kolejkę i wysyła komunikat do niego. Pozostaw kliencie z uruchomioną Aby sprawdzić działanie usługi, odczytywanie wiadomości  
  
5. Domyślnie usługę Aktywacja usługi MSMQ jest uruchamiana jako usługa sieciowa. W związku z tym, kolejki, która jest używana do aktywowania aplikacji musi mieć odbieranie i Wybieranie uprawnień dla usługi sieci. To można dodać za pomocą programu MMC usługi kolejkowania komunikatów:  
  
    1.  Z **Start** menu, kliknij przycisk **Uruchom**, a następnie wpisz `Compmgmt.msc` i naciśnij klawisz ENTER.  
  
    2.  W obszarze **usługi i aplikacje**, rozwiń węzeł **usługi kolejkowania komunikatów**.  
  
    3.  Kliknij przycisk **kolejki prywatne**.  
  
    4.  Kliknij prawym przyciskiem myszy kolejki (servicemodelsamples/Service.svc), a następnie wybierz **właściwości**.  
  
    5.  Na **zabezpieczeń** kliknij pozycję **Dodaj** zapewniają wgląd i otrzymać uprawnienie do usługi sieciowej.  
  
6. Skonfiguruj Windows Process Activation Service (WAS) do obsługi aktywacji usługi MSMQ.  
  
     Dla wygody poniższe kroki są implementowane w pliku wsadowym, o nazwie AddMsmqSiteBinding.cmd znajduje się w katalogu próbki.  
  
    1.  Aby zapewnić obsługę aktywacji net.msmq, domyślna witryna sieci Web musi zostać powiązana z protokołem net.msmq. Można to zrobić za pomocą appcmd.exe, który został zainstalowany przy użyciu [!INCLUDE[iisver](../../../../includes/iisver-md.md)] zestaw narzędzi do zarządzania. Z wiersza polecenia o podniesionych uprawnień (administrator) uruchom następujące polecenie.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu.  
  
         To polecenie dodaje powiązanie witryny net.msmq do domyślnej witryny sieci Web.  
  
    2.  Mimo że wszystkie aplikacje w ramach lokacji mają wspólne powiązanie net.msmq, każdej aplikacji można włączyć obsługę net.msmq indywidualnie. Aby włączyć net.msmq aplikacji /servicemodelsamples, uruchom następujące polecenie z wiersza polecenia z podwyższonym poziomem uprawnień.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu.  
  
         To polecenie włącza aplikację /servicemodelsamples można uzyskać za pomocą `http://localhost/servicemodelsamples` i `net.msmq://localhost/servicemodelsamples`.
  
7. Jeśli użytkownik nie zostało zrobione wcześniej, upewnij się, że włączono usługę Aktywacja usługi MSMQ. Z **Start** menu, kliknij przycisk **Uruchom**i wpisz `Services.msc`. Wyszukaj listę usług dla **Net.Msmq nasłuchujący**. Kliknij prawym przyciskiem myszy i wybierz **właściwości**. Ustaw **uruchamiana** do **automatyczne**, kliknij przycisk **Zastosuj** i kliknij przycisk **Start** przycisku. Ten krok tylko musi odbywać się jeden raz przed pierwsze użycie usługi Net.Msmq nasłuchujący.  
  
8. Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Ponadto można zmienić kodu na komputerze klienckim, który przesyła zamówienia zakupu w celu odzwierciedlenia nazwy komputera w identyfikatorze URI kolejki podczas przesyłania zamówienia zakupu. Użyj następującego kodu:  
  
    ```csharp  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. Usuń powiązanie witryny net.msmq, dodane dla tego przykładu.  
  
     Dla wygody poniższe kroki są implementowane w pliku wsadowym, o nazwie RemoveMsmqSiteBinding.cmd znajduje się w katalogu próbki:  
  
    1.  Usuń net.msmq z listy włączone protokoły, uruchamiając następujące polecenie z wiersza polecenia z podwyższonym poziomem uprawnień.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu.  
  
    2.  Usuń powiązanie witryny net.msmq, uruchamiając następujące polecenie z wiersza polecenia z podwyższonym poziomem uprawnień.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu.  
  
    > [!WARNING]
    >  Uruchamianie pliku wsadowego spowoduje zresetowanie domyślna pula aplikacji do uruchamiania przy użyciu platformy .NET Framework w wersji 2.0.  
  
 Domyślnie `netMsmqBinding` powiązania transportu, zabezpieczeń jest włączone. Dwie właściwości `MsmqAuthenticationMode` i `MsmqProtectionLevel`, wspólnie określić typ zabezpieczeń transportu. Domyślny tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`. Dla usługi MSMQ zapewniać uwierzytelnianie i funkcji podpisywania należy do domeny. Po uruchomieniu tego przykładu na komputerze, który nie jest częścią domeny jest Odebrano następujący błąd: "Użytkownika wewnętrznego kolejkowania certyfikatu nie istnieje".  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Do uruchomienia przykładu na komputer przyłączony do grupy roboczej  
  
1. Jeśli komputer nie jest częścią domeny, należy wyłączyć zabezpieczenia transportu przez ustawienie poziomu uwierzytelniania w trybie i ochrony None, jak pokazano w poniższym Przykładowa konfiguracja.  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2. Przed uruchomieniem próbki, należy zmienić konfigurację serwera i klienta.  
  
    > [!NOTE]
    >  Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia `MsmqAuthenticationMode`, `MsmqProtectionLevel` i `Message` security `None`.  
  
3. Aby włączyć aktywacji na komputerze, który został przyłączony do grupy roboczej, zarówno usługa aktywacji, jak i proces roboczy musi być uruchamiane z określonego konta użytkownika (musi być takie same dla obu) i kolejki musi mieć listy kontroli dostępu dla konta określonego użytkownika.  
  
     Aby zmienić tożsamość, która działa procesu roboczego:  
  
    1.  Uruchom Inetmgr.exe.  
  
    2.  W obszarze **pul aplikacji**, kliknij prawym przyciskiem myszy **puli AppPool** (zazwyczaj **DefaultAppPool**) i wybierz polecenie **ustawienia domyślne puli aplikacji...** .  
  
    3.  Zmień właściwości tożsamości do używania konta określonego użytkownika.  
  
     Aby zmienić tożsamość, która jest uruchamiana usługa aktywacji:  
  
    1.  Uruchom aplikację Services.msc.  
  
    2.  Kliknij prawym przyciskiem myszy **karty Net.MsmqListener**i wybierz polecenie **właściwości**.  
  
4. Zmień konto w **logowania** kartę.  
  
5. W grupie roboczej należy również uruchomić usługę przy użyciu tokenu bez ograniczeń. Aby to zrobić, uruchom następujące polecenie w oknie polecenia:  
  
    ```console  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
