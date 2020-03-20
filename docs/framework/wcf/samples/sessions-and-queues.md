---
title: Sesje i kolejki
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 8a342b185c7965e9ee0ff9941a09e00fc392ad4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144102"
---
# <a name="sessions-and-queues"></a>Sesje i kolejki
W tym przykładzie pokazano, jak wysyłać i odbierać zestaw powiązanych wiadomości w komunikacji w kolejce za przejmując usługi kolejkowania wiadomości (MSMQ). W tym przykładzie użyto `netMsmqBinding` powiązania. Usługa jest samodzielną aplikacją konsoli, która umożliwia obserwowanie usługi odbierającej wiadomości w kolejce.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 W komunikacji w kolejce klient komunikuje się z usługą przy użyciu kolejki. Dokładniej, klient wysyła wiadomości do kolejki. Usługa odbiera wiadomości z kolejki. W związku z tym usługi i klienta, nie muszą być uruchomione w tym samym czasie do komunikowania się przy użyciu kolejki.  
  
 Czasami klient wysyła zestaw wiadomości, które są ze sobą powiązane w grupie. Gdy wiadomości muszą być przetwarzane razem lub w określonej kolejności, kolejka może służyć do grupowania ich razem, do przetwarzania przez jedną aplikację odbierającą. Jest to szczególnie ważne, gdy istnieje kilka aplikacji odbierających na grupie serwerów i jest konieczne, aby upewnić się, że grupa wiadomości jest przetwarzana przez tę samą aplikację odbierającą. Sesje w kolejce to mechanizm używany do wysyłania i odbierania powiązanego zestawu wiadomości, które muszą zostać przetworzone jednocześnie. Sesje w kolejce wymagają transakcji do wykazania tego wzorca.  
  
 W przykładzie klient wysyła kilka komunikatów do usługi w ramach sesji w zakresie pojedynczej transakcji.  
  
 Umowa serwisowa `IOrderTaker`jest , która definiuje usługę jednokierunkową, która nadaje się do użytku z kolejkami. Używane <xref:System.ServiceModel.SessionMode> w umowie pokazane w poniższym przykładowym kodzie wskazuje, że wiadomości są częścią sesji.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 Usługa definiuje operacje usługi w taki sposób, że pierwsza operacja rejestruje się w transakcji, ale nie automatycznie zakończyć transakcję. Kolejne operacje również zarejestrować w tej samej transakcji, ale nie automatycznie zakończyć. Ostatnia operacja w sesji automatycznie kończy transakcję. W związku z tym ta sama transakcja jest używana dla kilku wywołań operacji w umowie serwisowej. Jeśli którakolwiek z operacji zgłosić wyjątek, a następnie transakcja wycofuje i sesji jest odłożony z powrotem do kolejki. Po pomyślnym zakończeniu ostatniej operacji transakcja jest zatwierdzana. Usługa używa `PerSession` jako <xref:System.ServiceModel.InstanceContextMode> do odbierania wszystkich wiadomości w sesji w tym samym wystąpieniu usługi.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 Usługa jest hostowana samodzielnie. Podczas korzystania z transportu usługi MSMQ używana kolejka musi zostać utworzona z wyprzedzeniem. Można to zrobić ręcznie lub za pomocą kodu. W tym przykładzie <xref:System.Messaging> usługa zawiera kod, aby sprawdzić istnienie kolejki i tworzy go, jeśli to konieczne. Nazwa kolejki jest odczytywana z <xref:System.Configuration.ConfigurationManager.AppSettings%2A> pliku konfiguracji przy użyciu klasy.  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();
    }  
}  
```

 Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji. Punkt końcowy usługi jest zdefiniowany w sekcji system.serviceModel pliku konfiguracji `netMsmqBinding` i określa powiązanie.  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
<system.serviceModel>  
```  
  
 Klient tworzy zakres transakcji. Wszystkie wiadomości w sesji są wysyłane do kolejki w zakresie transakcji, co powoduje, że są traktowane jako jednostki atomowej, gdzie wszystkie wiadomości zakończyć się powodzeniem lub niepowodzeniem. Transakcja jest zatwierdzana <xref:System.Transactions.TransactionScope.Complete%2A>przez wywołanie .  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
> Można użyć tylko jednej transakcji dla wszystkich wiadomości w sesji i wszystkie wiadomości w sesji muszą być wysyłane przed zatwierdzeniem transakcji. Zamknięcie klienta zamyka sesję. W związku z tym klient musi zostać zamknięty przed zakończeniem transakcji, aby wysłać wszystkie wiadomości w sesji do kolejki.  
  
 Po uruchomieniu przykładu działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Możesz zobaczyć, że usługa odbiera wiadomości od klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta. Należy zauważyć, że ponieważ kolejkowanie jest w użyciu, klient i usługa nie muszą być uruchomione w tym samym czasie. Można uruchomić klienta, zamknąć go, a następnie uruchomić usługę i nadal odbiera swoje komunikaty.  
  
 Na kliencie.  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 W serwisie.  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C#, C++ lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Domyślnie z <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczenia transportu jest włączona. Istnieją dwie odpowiednie właściwości zabezpieczeń transportu usługi MSMQ <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a mianowicie i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` Domyślnie tryb uwierzytelniania jest `Windows` ustawiony, a poziom ochrony jest ustawiony na `Sign`. Aby usługa MSMQ udostępniała funkcję uwierzytelniania i podpisywania, musi ona być częścią domeny, a opcja integracji usługi Active Directory dla usługi MSMQ musi być zainstalowana. Jeśli uruchomisz ten przykład na komputerze, który nie spełnia tych kryteriów, zostanie wyświetlony błąd.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej lub bez integracji z usługą Active Directory  
  
1. Jeśli komputer nie należy do domeny lub nie ma zainstalowanej integracji z aktywną funkcją `None` katalogową, wyłącz zabezpieczenia transportu, ustawiając na poziomie trybu uwierzytelniania i ochrony, jak pokazano w poniższej przykładowej konfiguracji.  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2. Przed uruchomieniem przykładu upewnij się, że konfiguracja jest zmieniana zarówno na serwerze, jak i na kliencie.  
  
    > [!NOTE]
    > Ustawienie trybu `None` zabezpieczeń na <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>równoważne `Message` z `None`ustawieniem <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, i zabezpieczeń do .  
