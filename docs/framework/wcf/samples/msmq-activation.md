---
title: Aktywacja usługi MSMQ
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 4dc8cc2a3c6d9178f6507c87ae512a8929bd1380
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808133"
---
# <a name="msmq-activation"></a>Aktywacja usługi MSMQ
W tym przykładzie pokazano, jak udostępniać aplikacje w usługi aktywacji procesów systemu Windows (WAS), które są odczytywane z kolejki komunikatów. W przykładzie użyto `netMsmqBinding` i opierają się na [komunikacji dwustronny](../../../../docs/framework/wcf/samples/two-way-communication.md) próbki. Usługa jest w tym przypadku aplikacji sieci Web hostowanych klienta i jest samodzielnie hostowana konsoli obserwować stan zakupów przesłane dane wyjściowe.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!NOTE]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  \<InstallDrive>:\WF_WCF_Samples  
>   
>  Jeśli ten katalog nie istnieje, przejdź do systemu Windows Communication Foundation (WCF) HYPERLINK "http://go.microsoft.com/fwlink/?LinkId=150780" \t "_blank" i przykłady Windows Workflow Foundation (WF) dotyczące [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] do pobrania wszystkich WCF i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  \<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.  
  
 Windows Process Activation Service (WAS), nowy proces aktywacji mechanizm [!INCLUDE[lserver](../../../../includes/lserver-md.md)], zapewnia funkcje podobne usług IIS, które były wcześniej dostępne tylko do aplikacji HTTP dla aplikacji, które używają protokołów innych niż HTTP. Windows Communication Foundation (WCF) używa interfejsu Adapter odbiornika do komunikowania się żądania aktywacji, które są otrzymywane za pośrednictwem protokołów innych niż HTTP obsługiwane przez usługi WCF, takie jak protokół TCP, potoków nazwanych i usługi MSMQ. Funkcja odbierania żądań za pośrednictwem protokołów innych niż HTTP jest hostowana przez zarządzanych usług systemu Windows działa w SMSvcHost.exe.  
  
 Adapter odbiornika Net.Msmq usługi (NetMsmqActivator) aktywuje umieszczonych w kolejce aplikacje oparte na wiadomości w kolejce.  
  
 Klient wysyła zakupów do usługi z zakresu transakcji. Usługa odbiera zamówienia w transakcji i przetwarza je. Usługa następnie wywołuje klienta z stan zlecenia. Aby ułatwić dwukierunkowej komunikacji klienta i usługi użyj kolejki, aby umieścić w kolejce zakupów i stanu zlecenia.  
  
 Kontrakt usługi `IOrderProcessor` definiuje operacje usługi jednokierunkowej współpracujących z usługi kolejkowania wiadomości. Operacja usługi wysyła stanów zleceń do klienta przy użyciu punktu końcowego odpowiedzi. Adres punktu końcowego odpowiedzi jest identyfikatorem URI kolejki używanej do odesłania do klienta stan zlecenia. Kolejność przetwarzania aplikacji implementuje tego kontraktu.  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 Kontrakt odpowiedź do wysłania stanu zlecenia jest określony przez klienta. Klient implementuje kontraktu stan zlecenia. Usługa używa wygenerowanego klienta tego kontraktu do odesłania do klienta stan zlecenia.  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 Operacja usługi przetwarza zamówienia zakupu zostało przesłane. <xref:System.ServiceModel.OperationBehaviorAttribute> Jest stosowany do operacji usługi, aby określić automatycznej rejestracji w transakcji, która służy do odbierania wiadomości z kolejki i automatyczne uzupełnianie transakcji po zakończeniu operacji usługi. `Orders` Klasa hermetyzuje funkcjonalność przetwarzania zamówienia. W takim przypadku dodaje zamówienie do słownika. Operacja usługi jest zarejestrowana w transakcji jest dostępny do operacji w `Orders` klasy.  
  
 Operacji usługi, oprócz przetwarzania zamówienia zakupu przesłanych odpowiedzi do klienta o stan zlecenia.  
  
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
```  
  
 Powiązanie do użycia klienta zostanie określona przy użyciu pliku konfiguracji.  
  
 Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji. Punkt końcowy usługi jest zdefiniowany w sekcji System.serviceModel pliku konfiguracji.  
  
> [!NOTE]
>  Adres nazwy i punktu końcowego kolejki usługi MSMQ Użyj konwencji adresowania nieco inne. Nazwa kolejki usługi MSMQ używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatory ukośnika w jego ścieżki. Adres punktu końcowego WCF określa net.msmq: schemat, korzysta "localhost" na komputerze lokalnym, a ukośniki w swojej ścieżce. Aby odczytać z kolejki znajdującej się na komputerze zdalnym, zastąp "." i "localhost" do nazwy komputera zdalnego.  
  
 Plik .svc o nazwie klasy jest używana do hostowania kodu usługi WAS.  
  
 Sam plik Service.svc zawiera dyrektywy, aby utworzyć `OrderProcessorService`.  
  
```xml  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 Plik Service.svc zawiera także dyrektywa zestawu, aby upewnić się, że zostanie załadowana biblioteka System.Transactions.dll.  
  
```xml  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 Klient tworzy zakresu transakcji. Komunikacja z usługą odbywa się w zakresie transakcji, co powoduje traktowane jako Atomowej jednostki, w którym wszystkie komunikaty powodzenie lub niepowodzenie. Transakcja zostaje zatwierdzona przez wywołanie metody `Complete` w zakresie transakcji.  
  
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
  
 Kod klienta implementuje `IOrderStatus` kontraktu do odbierania stanu zlecenia z usługi. W takim przypadku wyświetla się stan zlecenia.  
  
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
  
 Kolejność kolejkę stanu jest tworzony w `Main` metody. Konfiguracja klienta obejmuje konfiguracji kolejności stanu usługi do obsługi usługi stanu kolejności, jak pokazano w poniższych Przykładowa konfiguracja.  
  
```csharp  
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
  
 Po uruchomieniu próbki działania klienta i usługi są wyświetlane w serwera i klienta systemu windows z konsoli. Serwer odbiera komunikaty z klienta jest widoczny. Naciśnij klawisz ENTER w każdym okna konsoli do zamykania serwera i klienta.  
  
 Klient jest wyświetlany kolejności informacje o stanie wysyłane przez serwer:  
  
```Output  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że [!INCLUDE[iisver](../../../../includes/iisver-md.md)] zainstalowano, zgodnie z wymaganiami aktywacji WAS.  
  
2.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md). Ponadto należy zainstalować składniki Aktywacja bez HTTP usług WCF:  
  
    1.  Z **Start** menu, wybierz **Panelu sterowania**.  
  
    2.  Wybierz **programy i funkcje**.  
  
    3.  Kliknij przycisk **Włącz lub wyłącz funkcje systemu Windows**.  
  
    4.  W obszarze **Podsumowanie funkcji**, kliknij przycisk **Dodaj funkcje**.  
  
    5.  Rozwiń węzeł **Microsoft .NET Framework 3.0** węzeł i wyboru **Aktywacja bez HTTP programu systemu Windows Communication Foundation** funkcji.  
  
3.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Uruchom klienta, wykonując client.exe z okna poleceń. To tworzy kolejkę i wysyła komunikat do niego. Pozostaw klienta uruchamiania, aby sprawdzić działanie usługi, odczytywanie wiadomości  
  
5.  Domyślnie usługi MSMQ activation service jest uruchamiana jako usługa sieciowa. W związku z tym kolejki, która jest używana do aktywowania aplikacji musi mieć odbierają i wgląd uprawnień dla usługi sieciowej. Mogą to być dodawane za pomocą programu MMC usługi kolejkowania komunikatów:  
  
    1.  Z **Start** menu, kliknij przycisk **Uruchom**, wpisz `Compmgmt.msc` i naciśnij klawisz ENTER.  
  
    2.  W obszarze **usługi i aplikacje**, rozwiń węzeł **usługi kolejkowania komunikatów**.  
  
    3.  Kliknij przycisk **kolejki prywatne**.  
  
    4.  Kliknij prawym przyciskiem myszy kolejki (servicemodelsamples/Service.svc) i wybierz polecenie **właściwości**.  
  
    5.  Na **zabezpieczeń** , kliknij pozycję **Dodaj** i przypisz wglądu i uzyskują uprawnienia do usługi sieciowej.  
  
6.  Skonfiguruj Windows Process Activation Service (WAS) do obsługi aktywacji usługi MSMQ.  
  
     Dla wygody poniższe kroki są implementowane w pliku wsadowym o nazwie AddMsmqSiteBinding.cmd znajduje się w katalogu próbki.  
  
    1.  Do obsługi aktywacji net.msmq, domyślnej witryny sieci Web musi zostać powiązana z protokołem net.msmq. Można to zrobić przy użyciu appcmd.exe, który jest instalowany z [!INCLUDE[iisver](../../../../includes/iisver-md.md)] narzędzi zarządzania. Z wiersza polecenia z podniesionymi uprawnieniami (administrator) uruchom następujące polecenie.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu.  
  
         To polecenie dodaje powiązania witryny net.msmq do domyślnej witryny sieci Web.  
  
    2.  Mimo że wszystkie aplikacje w obrębie lokacji korzystają wspólnej powiązanie net.msmq, każdej aplikacji można włączyć obsługę net.msmq pojedynczo. Aby włączyć net.msmq aplikacji /servicemodelsamples, uruchom następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu.  
  
         To polecenie umożliwia uzyskać dostęp za pomocą aplikacji /servicemodelsamples http://localhost/servicemodelsamples i net.msmq://localhost/servicemodelsamples.  
  
7.  Jeśli użytkownik nie zostało zrobione wcześniej, upewnij się, czy włączono usługi MSMQ activation service. Z **Start** menu, kliknij przycisk **Uruchom**i wpisz `Services.msc`. Wyszukaj na liście usług dla **Adapter odbiornika Net.Msmq**. Kliknij prawym przyciskiem myszy i wybierz **właściwości**. Ustaw **uruchamiana** do **automatyczne**, kliknij przycisk **Zastosuj** i kliknij przycisk **Start** przycisku. Ten krok należy przeprowadzić tylko raz przed pierwsze użycie usługi Adapter odbiornika Net.Msmq.  
  
8.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Ponadto zmianę kodu na komputerze klienckim, który przesyła zamówienia zakupu w celu odzwierciedlenia nazwy komputera w identyfikatorze URI kolejki podczas przesyłania zamówienia zakupu. Użyj następującego kodu:  
  
    ```  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. Usuń powiązanie witryny net.msmq, dodane dla tego przykładu.  
  
     Dla wygody następujące czynności są wykonywane w pliku wsadowym o nazwie RemoveMsmqSiteBinding.cmd znajduje się w katalogu próbki:  
  
    1.  Usuń net.msmq z listy włączonych protokołów, uruchamiając następujące polecenie z wiersza polecenia o podniesionych uprawnieniach.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu.  
  
    2.  Usuń powiązanie witryny net.msmq, uruchamiając następujące polecenie z wiersza polecenia o podniesionych uprawnieniach.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu.  
  
    > [!WARNING]
    >  Uruchamiania pliku wsadowego spowoduje zresetowanie domyślna pula aplikacji do uruchamiania przy użyciu platformy .NET Framework w wersji 2.0.  
  
 Domyślnie z `netMsmqBinding` powiązania transportu, zabezpieczeń jest włączone. Dwie właściwości `MsmqAuthenticationMode` i `MsmqProtectionLevel`, wspólnie określić typ zabezpieczeń transportu. Domyślny tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`. MSMQ zapewnić uwierzytelnianie i funkcji podpisywania musi być częścią domeny. Jeśli w tym przykładzie zostanie uruchomiony na komputerze, który nie jest częścią domeny, jest Odebrano następujący błąd: "Komunikat użytkownika wewnętrzny certyfikat usługi kolejkowania wiadomości nie istnieje".  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Aby uruchomić na komputerze, na przykład przyłączony do grupy roboczej  
  
1.  Jeśli komputer nie jest częścią domeny, należy wyłączyć zabezpieczeń transportu przez ustawienie poziomu uwierzytelniania w trybie i ochrony None, jak pokazano w poniższych Przykładowa konfiguracja.  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2.  Przed uruchomieniem próbki, należy zmienić konfigurację na serwerze i kliencie.  
  
    > [!NOTE]
    >  Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia `MsmqAuthenticationMode`, `MsmqProtectionLevel` i `Message` zabezpieczeń do `None`.  
  
3.  Aby włączyć aktywacji w komputer, który należy do grupy roboczej, zarówno z usługą aktywacji i proces roboczy musi być uruchamiane z określonego konta użytkownika (musi być taka sama dla obu) i kolejki musi mieć listy kontroli dostępu dla konta użytkownika.  
  
     Aby zmienić tożsamość działającą procesu roboczego:  
  
    1.  Uruchom Inetmgr.exe.  
  
    2.  W obszarze **pul aplikacji**, kliknij prawym przyciskiem myszy **AppPool** (zazwyczaj **DefaultAppPool**) i wybierz polecenie **ustawienia domyślne puli aplikacji...** .  
  
    3.  Zmień właściwości tożsamości pod kątem używania konta określonego użytkownika.  
  
     Aby zmienić tożsamość, która jest uruchamiana usługa aktywacji:  
  
    1.  Uruchom aplikację Services.msc.  
  
    2.  Kliknij prawym przyciskiem myszy **karty Net.MsmqListener**i wybierz polecenie **właściwości**.  
  
4.  Zmień konto w **logowania** kartę.  
  
5.  W grupie roboczej należy także uruchomić usługę przy użyciu tokenu bez ograniczeń. Aby to zrobić, uruchom następujące polecenie w oknie poleceń:  
  
    ```  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
