---
title: Komunikacja dwukierunkowa
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 56f789fe185cb2885c215e9512e82ae2fbb64a36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143762"
---
# <a name="two-way-communication"></a>Komunikacja dwukierunkowa
W tym przykładzie pokazano, jak wykonać transacted dwukierunkowej komunikacji w kolejce za sprawą usługi MSMQ. W tym przykładzie użyto `netMsmqBinding` powiązania. W takim przypadku usługa jest samodzielną aplikacją konsoli, która umożliwia obserwowanie usługi odbierającej wiadomości w kolejce.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład jest oparty na [powiązaniu Z MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)transakcji .  
  
 W komunikacji w kolejce klient komunikuje się z usługą przy użyciu kolejki. Klient wysyła wiadomości do kolejki, a usługa odbiera wiadomości z kolejki. W związku z tym usługi i klienta, nie muszą być uruchomione w tym samym czasie do komunikowania się przy użyciu kolejki.  
  
 W tym przykładzie pokazano komunikacji dwukierunkowej przy użyciu kolejek. Klient wysyła zamówienia zakupu do kolejki z zakresu transakcji. Usługa odbiera zamówienia, przetwarza zamówienie, a następnie odwołuje klienta ze stanem zamówienia z kolejki w zakresie transakcji. Aby ułatwić komunikację dwukierunkową, klient i usługa używają kolejek do umieszczania w kolejce zamówień zakupu i stanu zamówienia.  
  
 Umowa serwisowa `IOrderProcessor` definiuje jednokierunkowe operacje serwisowe, które odpowiadają użyciu kolejkowania. Operacja usługi obejmuje punkt końcowy odpowiedzi, który służy do wysyłania stanów zamówienia. Punkt końcowy odpowiedzi jest identyfikatorem URI kolejki, aby wysłać stan zamówienia z powrotem do klienta. Aplikacja do przetwarzania zamówień implementuje tę umowę.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 Kontrakt odpowiedzi do wysłania stanu zamówienia jest określony przez klienta. Klient implementuje kontrakt o stanie zamówienia. Usługa używa wygenerowanego serwera proxy tej umowy, aby wysłać stan zamówienia z powrotem do klienta.  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 Operacja serwisowa przetwarza przesłane zamówienie zakupu. Jest <xref:System.ServiceModel.OperationBehaviorAttribute> stosowany do operacji usługi, aby określić automatyczne rejestrowanie w transakcji, która jest używana do odbierania wiadomości z kolejki i automatycznego zakończenia transakcji po zakończeniu operacji usługi. Klasa `Orders` hermetyzuje funkcje przetwarzania zamówień. W takim przypadku dodaje zamówienie zakupu do słownika. Transakcja, w którą zarejestrowano operację usługi, jest `Orders` dostępna dla operacji w klasie.  
  
 Operacja usługi, oprócz przetwarzania przesłanego zamówienia zakupu, odpowiada klientowi na stan zamówienia.  

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

 Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji. Punkt końcowy usługi jest zdefiniowany w sekcji System.ServiceModel pliku konfiguracyjnego.  
  
> [!NOTE]
> Nazwa kolejki usługi MSMQ i adres punktu końcowego używają nieco innych konwencji adresowania. Nazwa kolejki usługi MSMQ używa kropki (.) dla komputera lokalnego i separatorów ukośnika odwrotnego w jego ścieżce. Adres punktu końcowego Programu Komunikacji systemu Windows (WCF) określa schemat net.msmq: używa "localhost" dla komputera lokalnego i używa ukośników do przodu w swojej ścieżce. Aby odczytać z kolejki hostowanej na komputerze zdalnym, należy zastąpić "." i "localhost" nazwą komputera zdalnego.  
  
 Usługa jest hostowana samodzielnie. Podczas korzystania z transportu usługi MSMQ używana kolejka musi zostać utworzona z wyprzedzeniem. Można to zrobić ręcznie lub za pomocą kodu. W tym przykładzie usługa sprawdza istnienie kolejki i tworzy go, jeśli to konieczne. Nazwa kolejki jest odczytywana z pliku konfiguracji. Adres podstawowy jest używany przez [narzędzie narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania serwera proxy do usługi.  

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

 Klient tworzy transakcję. Komunikacja z kolejką odbywa się w zakresie transakcji, powodując, że jest traktowana jako jednostka niepodzielna, w której wszystkie wiadomości powiodą się lub nie powiedzie się.  

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

 Kod klienta implementuje `IOrderStatus` kontrakt, aby otrzymać stan zamówienia z usługi. W takim przypadku drukuje stan zamówienia.  

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

 Kolejka stanu zamówienia jest `Main` tworzona w metodzie. Konfiguracja klienta zawiera konfigurację usługi stanu zamówienia do obsługi usługi stanu zamówienia, jak pokazano w poniższej konfiguracji przykładowej.  
  
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
  
 Po uruchomieniu przykładu działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Możesz zobaczyć, że usługa odbiera wiadomości od klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
 Usługa wyświetla informacje o zamówieniu zakupu i wskazuje, że wysyła stan zamówienia z powrotem do kolejki stanu zamówienia.  
  
```console  
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
  
 Klient wyświetla informacje o stanie zamówienia wysyłane przez usługę.  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Jeśli używasz Svcutil.exe do ponownego wygenerowania konfiguracji dla tego przykładu, należy zmodyfikować nazwy punktów końcowych w konfiguracji klienta, aby dopasować kod klienta.  
  
 Domyślnie z <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczenia transportu jest włączona. Istnieją dwie odpowiednie właściwości zabezpieczeń transportu usługi <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` MSMQ, a domyślnie `Windows` jest ustawiony na `Sign`tryb uwierzytelniania, a poziom ochrony jest ustawiony na . Aby usługa MSMQ udostępniała funkcję uwierzytelniania i podpisywania, musi ona być częścią domeny, a opcja integracji usługi Active Directory dla usługi MSMQ musi być zainstalowana. Jeśli uruchomisz ten przykład na komputerze, który nie spełnia tych kryteriów, zostanie wyświetlony błąd.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej lub bez integracji z usługą Active Directory  
  
1. Jeśli komputer nie należy do domeny lub nie ma zainstalowanej integracji z aktywną funkcją `None` katalogową, wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom ochrony na pokazano w poniższej przykładowej konfiguracji:  
  
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
  
2. Wyłączenie zabezpieczeń dla konfiguracji klienta generuje następujące elementy:  
  
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
  
3. Usługa dla tego przykładu tworzy `OrderProcessorService`powiązanie w . Dodaj wiersz kodu po utworzeniu wystąpienia powiązania, aby `None`ustawić tryb zabezpieczeń na .  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. Przed uruchomieniem przykładu upewnij się, że konfiguracja jest zmieniana zarówno na serwerze, jak i na kliencie.  
  
    > [!NOTE]
    > Ustawienie `security mode` `None` jest równoważne <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> z `Message` ustawieniem lub zabezpieczeniem `None`.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
