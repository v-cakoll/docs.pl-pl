---
title: Sesje i kolejki
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 425135b533b898cbc75464f50ce8a5e8f6550755
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584171"
---
# <a name="sessions-and-queues"></a>Sesje i kolejki

Ten przykład pokazuje, jak wysyłać i odbierać zestaw powiązanych komunikatów w kolejce komunikacji za pośrednictwem transportu usługi kolejkowania komunikatów (MSMQ). Ten przykład używa `netMsmqBinding` powiązania. Usługa to samodzielna aplikacja konsolowa, która umożliwia obserwowanie usługi do odebrania komunikatów znajdujących się w kolejce.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki. Dokładniej, klient wysyła komunikaty do kolejki. Usługa odbiera komunikaty z kolejki. W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.  
  
 Czasami klient wysyła zestaw komunikatów, które są powiązane ze sobą w grupie. Gdy wiadomości muszą być przetwarzane razem lub w określonej kolejności, można użyć kolejki w celu pogrupowania ich razem w celu przetworzenia przez pojedynczą aplikację otrzymującą. Jest to szczególnie ważne w przypadku, gdy w grupie serwerów istnieje kilka aplikacji do odebrania, a konieczne jest upewnienie się, że grupa komunikatów jest przetwarzana przez tę samą aplikację otrzymującą. Sesje w kolejce są mechanizmem używanym do wysyłania i odbierania powiązanego zestawu komunikatów, które muszą zostać przetworzone jednocześnie. Sesje w kolejce wymagają transakcji, aby wymusić ten wzorzec.  
  
 W przykładzie klient wysyła do usługi wiele komunikatów w ramach sesji w ramach jednego z zakresów pojedynczej transakcji.  
  
 Kontrakt usługi to `IOrderTaker` , który definiuje usługę jednokierunkową, która jest odpowiednia do użycia z kolejkami. <xref:System.ServiceModel.SessionMode>Użycie w umowie pokazanej w następującym przykładowym kodzie wskazuje, że komunikaty są częścią sesji.  

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

 Usługa definiuje operacje usługi w taki sposób, że pierwsza operacja jest rejestrowana w transakcji, ale nie powoduje automatycznego wykonania transakcji. Kolejne operacje są rejestrowane również w tej samej transakcji, ale nie są automatycznie uzupełniane. Ostatnia operacja w sesji automatycznie kończy transakcję. W ten sam sposób jest używana w przypadku kilku wywołań operacji w kontrakcie usługi. Jeśli jakakolwiek z operacji zgłasza wyjątek, transakcja zostanie wycofana, a sesja zostanie umieszczona w kolejce. Po pomyślnym zakończeniu ostatniej operacji transakcja zostanie zatwierdzona. Usługa używa `PerSession` jako <xref:System.ServiceModel.InstanceContextMode> do odbierania wszystkich komunikatów w sesji w tym samym wystąpieniu usługi.  

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

 Usługa jest samodzielna. W przypadku korzystania z transportu usługi MSMQ użyta Kolejka musi zostać utworzona z góry. Można to zrobić ręcznie lub przy użyciu kodu. W tym przykładzie usługa zawiera <xref:System.Messaging> kod służący do sprawdzania istnienia kolejki i w razie potrzeby tworzy ją. Nazwa kolejki jest odczytywana z pliku konfiguracji przy użyciu <xref:System.Configuration.ConfigurationManager.AppSettings%2A> klasy.  

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

 Nazwa kolejki MSMQ jest określona w sekcji appSettings w pliku konfiguracji. Punkt końcowy usługi jest zdefiniowany w sekcji System. serviceModel w pliku konfiguracji i określa `netMsmqBinding` powiązanie.  
  
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
</system.serviceModel>  
```  
  
 Klient tworzy zakres transakcji. Wszystkie komunikaty w sesji są wysyłane do kolejki w zakresie transakcji, co sprawia, że może być traktowana jako jednostka niepodzielna, w której wszystkie komunikaty kończą się powodzeniem lub niepowodzeniem. Transakcja jest zatwierdzona przez wywołanie <xref:System.Transactions.TransactionScope.Complete%2A> .  

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
> Można użyć tylko jednej transakcji dla wszystkich komunikatów w sesji i wszystkie komunikaty w sesji muszą być wysyłane przed zatwierdzeniem transakcji. Zamknięcie klienta powoduje zamknięcie sesji programu. W związku z tym przed ukończeniem transakcji należy zamknąć klienta w celu wysłania wszystkich komunikatów w sesji do kolejki.  
  
 Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta. Możesz zobaczyć, że usługa odbiera komunikaty od klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta. Ponieważ kolejkowanie jest w użyciu, klient i usługa nie muszą działać w tym samym czasie. Można uruchomić klienta programu, zamknąć go, a następnie uruchomić usługę i nadal otrzymywać wiadomości.  
  
 Na kliencie programu.  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 W usłudze.  
  
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
  
### <a name="set-up-build-and-run-the-sample"></a>Konfigurowanie, kompilowanie i uruchamianie przykładu  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania dla języka C#, C++ lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
 Domyślnie z opcją <xref:System.ServiceModel.NetMsmqBinding> jest włączona funkcja zabezpieczenia transportu. Istnieją dwie istotne właściwości zabezpieczenia transportu usługi MSMQ, a mianowicie <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` tryb uwierzytelniania jest ustawiony na, `Windows` a poziom ochrony jest ustawiony na `Sign` . Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny, a dla usługi MSMQ należy zainstalować opcję Integracja z usługą Active Directory. Jeśli ten przykład zostanie uruchomiony na komputerze, który nie spełnia tych kryteriów, zostanie wyświetlony komunikat o błędzie.  
  
### <a name="run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Uruchom przykład na komputerze przyłączonym do grupy roboczej  
  
1. Jeśli komputer nie jest częścią domeny lub nie zainstalowano integracji z usługą Active Directory, Wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom ochrony `None` tak jak pokazano w poniższej konfiguracji przykładowej.  
  
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
  
2. Przed uruchomieniem przykładu należy zmienić konfigurację na serwerze i kliencie programu.  
  
    > [!NOTE]
    > Ustawienie trybu zabezpieczeń `None` jest równoważne ustawieniu <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> , <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> i `Message` zabezpieczenia z `None` .  
