---
title: Komunikacja dwukierunkowa
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 319b63ff1eefdab4c23932294c3f1970f204601e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519863"
---
# <a name="two-way-communication"></a>Komunikacja dwukierunkowa
Niniejszy przykład pokazuje sposób wykonywania transakcyjne dwukierunkowej komunikacji w kolejce za pośrednictwem usługi MSMQ. W tym przykładzie użyto `netMsmqBinding` powiązania. W tym przypadku usługa jest aplikacja konsolowa samodzielnie hostowanej która pozwala obserwować usługę otrzymywania wiadomości w kolejce.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Ten przykład jest oparty na [dokonana transakcja powiązania usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
 W komunikacie w kolejce klient komunikuje się z usługą przy użyciu kolejki. Klient wysyła komunikaty do kolejki, a usługa odbiera komunikaty z kolejki. Usługi i klienta w związku z tym, nie musi być uruchomiona w tym samym czasie do komunikowania się za pomocą kolejki.  
  
 Niniejszy przykład pokazuje sposób 2 komunikacji przy użyciu funkcji kolejek. Klient wysyła zamówienia zakupu w kolejce z zakresu transakcji. Usługa odbiera zamówienia, przetworzy to zamówienie, a następnie wywołuje ponownie klienta z stan zamówienia z kolejki w zakresie transakcji. Ułatwianie dwukierunkowej komunikacji klienta i usługi użyj kolejki, aby umieścić zakupów i stanu zamówienia.  
  
 Kontrakt usługi `IOrderProcessor` definiuje operacje usługi jednokierunkowej, spełniające użycie usługi kolejkowania wiadomości. Operacja usługi zawiera punkt końcowy odpowiedź do wysłania stanów zlecenia do. Punkt końcowy odpowiedzi jest identyfikator URI kolejki wysyłania stan zamówienia do klienta. Kolejność przetwarzania aplikacji implementuje ten kontrakt.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}
```
  
 Kontrakt odpowiedź do wysłania stan zamówienia jest określony przez klienta. Klient implementuje ten kontrakt stan zamówienia. Usługa używa wygenerowany serwer proxy niniejszej Umowy do odesłania stan zamówienia do klienta.  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 Operacja usługi przetworzy to zamówienie zakupu przesłane. <xref:System.ServiceModel.OperationBehaviorAttribute> Jest stosowany do operacji usługi, aby określić automatycznej rejestracji w transakcji, która umożliwia odbieranie wiadomości z kolejki i automatycznego uzupełniania transakcji po zakończeniu operacji usługi. `Orders` Klasa hermetyzuje funkcjonalność przetwarzania zamówienia. W tym przypadku dodaje zamówienia zakupu w słowniku. Operacja usługi zarejestrowany w transakcji jest dostępna dla operacji w `Orders` klasy.  
  
 Operacja usługi, oprócz przetwarzania zamówienia zakupu przesłanych odpowiedzi do klienta na stan zamówienia.  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
{  
    Orders.Add(po);  
    Console.WriteLine("Processing {0} ", po);  
    Console.WriteLine("Sending back order status information");  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding("ClientCallbackBinding");  
    OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
  
    // Please note that the same transaction that is used to dequeue the purchase order is used  
    // to send back order status.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        client.OrderStatus(po.PONumber, po.Status);  
        scope.Complete();  
    }  
    //Close the client.  
    client.Close();  
}  
```

 Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji. Punkt końcowy usługi jest zdefiniowany w sekcji System.ServiceModel pliku konfiguracji.  
  
> [!NOTE]
>  Adres nazwy i punkt końcowy kolejki usługi MSMQ Użyj nieco Konwencji adresowania. Nazwa kolejki usługi MSMQ używa pojedynczego znaku kropki (.) dla lokalnego separatory maszyny i ukośnika odwrotnego w ścieżce. Adres punktu końcowego usługi Windows Communication Foundation (WCF) określa net.msmq: schemat, używa "localhost" dla komputera lokalnego i korzysta z ukośników w ścieżce. Aby odczytać z kolejki, która znajduje się na komputerze zdalnym, zastąp "." i "localhost", aby nazwy maszyny zdalnej.  
  
 Usługa jest samodzielnie hostowana. Za pomocą transportu MSMQ, kolejki, używane musi zostać utworzona wcześniej. Można to zrobić ręcznie lub za pomocą kodu. W tym przykładzie usługa sprawdza istnienie kolejki i utworzy go, jeśli to konieczne. Nazwa kolejki jest do odczytu z pliku konfiguracji. Adres podstawowy jest używany przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania serwera proxy do usługi.  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from appSettings in configuration.  
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
    }  
}  
```

 Klient tworzy transakcji. Komunikacja z kolejką odbywa się w zakresie transakcji, co powoduje powinien być traktowany jako pojedynczej Atomowej jednostki, której wszystkie komunikaty sukces lub niepowodzenie.  

```csharp
// Create a ServiceHost for the OrderStatus service type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
  
    // Open the ServiceHostBase to create listeners and start listening for order status messages.  
    serviceHost.Open();  
  
    // Create the purchase order.  
    ...  
  
    // Create a client with given client endpoint configuration.  
    OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        string hostName = Dns.GetHostName();  
  
        // Make a queued call to submit the purchase order.  
        client.SubmitPurchaseOrder(po, "net.msmq://" + hostName + "/private/ServiceModelSamplesTwo-way/OrderStatus");  
  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Close down the client.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHost to shutdown the service.  
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
        Console.WriteLine("Status of order {0}:{1} ", poNumber ,   
                                                           status);  
    }  
}  
```

 Kolejkę stanu zamówienia jest tworzony w `Main` metody. Konfiguracja klienta obejmuje konfigurację usługi stanu zamówienia do hostowania usługi stanu zamówienia, jak pokazano w poniższym Przykładowa konfiguracja.  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
</appSettings>  
  
<system.serviceModel>  
  
  <services>  
    <service   
       name="Microsoft.ServiceModel.Samples.OrderStatusService">  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
    </service>  
  </services>  
  
  <client>  
    <!-- Define NetMsmqEndpoint -->  
    <endpoint name="OrderProcessorEndpoint"  
              address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"   
              binding="netMsmqBinding"   
              contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
  </client>  
  
</system.serviceModel>  
```  
  
 Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Możesz zobaczyć komunikaty odbierania usługi z klienta. Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.  
  
 Usługa Wyświetla informacje o zamówieniu zakupu i wskazuje, że wysyła ponownie stan zamówienia w kolejce stan zamówienia.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 124a1f69-3699-4b16-9bcc-43147a8756fc  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Sending back order status information  
```  
  
 Klient Wyświetla informacje o stanie zamówienia, które zostały wysłane przez usługę.  
  
```  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwy punktów końcowych w konfiguracji klienta, aby dopasować kod klienta.  
  
 Domyślnie <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczenia transportu jest włączona. Istnieją dwie właściwości istotnych dla zabezpieczeń transportu usługi MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` domyślny tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`. Dla usługi MSMQ zapewniać uwierzytelnianie i podpisywania funkcji musi być częścią domeny i musi być zainstalowany opcji integracji usługi active directory dla usługi MSMQ. Jeśli w tym przykładzie jest uruchomiony na komputerze, który nie spełnia tych kryteriów otrzymasz komunikat o błędzie.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Do uruchomienia przykładu na komputer przyłączony do grupy roboczej lub bez integracji usługi active directory  
  
1.  Jeśli komputer nie jest częścią domeny lub nie ma zainstalowaną integracją usługi active directory, należy wyłączyć zabezpieczenia transportu, ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższym Przykładowa konfiguracja:  
  
    ```xml  
    <configuration>  
  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderProcessor" />  
      </appSettings>  
  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding"   
                      contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
2.  Wyłączenie zabezpieczeń dla konfiguracji klienta generuje następujące czynności:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
      </appSettings>  
  
      <system.serviceModel>  
  
        <services>  
          <service   
             name="Microsoft.ServiceModel.Samples.OrderStatusService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding" contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
          </service>  
        </services>  
  
        <client>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint name="OrderProcessorEndpoint"  
                    address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"   
                    binding="netMsmqBinding"   
                    bindingConfiguration="TransactedBinding"  
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        </client>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
3.  Usługi w tym przykładzie tworzy powiązanie w `OrderProcessorService`. Dodaj wiersz kodu po wiązanie zostanie uruchomiony, aby ustawić tryb zabezpieczeń `None`.  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4.  Upewnij się, zmień konfigurację serwera i klienta, przed uruchomieniem przykładu.  
  
    > [!NOTE]
    >  Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> lub `Message` security `None`.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
  
## <a name="see-also"></a>Zobacz też
