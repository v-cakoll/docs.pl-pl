---
title: "Transakcyjne powiązanie MSMQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
caps.latest.revision: "50"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 247627cdf52f7e08490cc95d88b4dd4ab539d97e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="transacted-msmq-binding"></a>Transakcyjne powiązanie MSMQ
W tym przykładzie pokazano, jak wykonać transakcyjnych w kolejce komunikacji przy użyciu usługi kolejkowania komunikatów (MSMQ).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W kolejce komunikacji klient komunikuje się z usługą przy użyciu kolejki. Mówiąc ściślej klient wysyła wiadomości do kolejki. Usługa odbiera komunikaty z kolejki. Usługi i klienta, w związku z tym ma być uruchomiona, w tym samym czasie do komunikowania się przy użyciu kolejki.  
  
 Gdy transakcje są używane do wysyłania i odbierania wiadomości, istnieją faktycznie dwóch oddzielnych transakcji. Gdy klient wysyła komunikaty w zakresie transakcji, transakcja jest lokalne klient i klient menedżera kolejek. Gdy usługa odbiera komunikaty w zakresie transakcji, transakcja jest lokalnego do usługi i odbierającego menedżera kolejek. Jest bardzo ważne, aby należy pamiętać, że klient i usługa nie uczestniczą w tej samej transakcji; zamiast używają różnych transakcji podczas wykonywania ich działania (takie jak wysyłanie i odbieranie) z kolejką.  
  
 W tym przykładzie klient wysyła komunikaty zbiorczo do usługi z zakresu transakcji. Komunikaty wysłane do kolejki następnie są odbierane przez usługę w zakresie transakcji, określonym przez usługę.  
  
 Kontrakt usługi jest `IOrderProcessor`, jak pokazano w poniższym kodzie próbki. Interfejs definiuje jednokierunkowe usługa, która jest odpowiednia do użycia w przypadku kolejek.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 Zachowanie usługi definiuje zachowanie operacji z `TransactionScopeRequired` ustawioną `true`. Dzięki temu, że tego samego zakresu transakcji, który służy do pobierania wiadomości z kolejki jest używana przez Menedżera zasobów, wszystkie dostępne metody. Gwarantuje również, że jeśli metoda zgłosi wyjątek, wiadomość jest zwracana do kolejki. Bez ustawienia zachowania tej operacji, kolejkowanym kanale tworzy transakcji, aby odczytać wiadomość z kolejki i zatwierdza on automatycznie przed wysyłką taki sposób, że jeśli operacja nie powiedzie się, komunikat zostaną utracone. Najbardziej typowym scenariuszem jest dla operacji usługi zarejestrować się w transakcji, która służy do odczytywania wiadomości z kolejki, jak pokazano w poniższym kodzie.  
  
```  
 // This service class that implements the service contract.  
 // This added code writes output to the console window.  
 public class OrderProcessorService : IOrderProcessor  
 {  
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
     public void SubmitPurchaseOrder(PurchaseOrder po)  
     {  
         Orders.Add(po);  
         Console.WriteLine("Processing {0} ", po);  
     }  
  …  
}  
```  
  
 Usługa jest samodzielnie hostowana. Za pomocą transportu MSMQ, kolejki używane musi zostać utworzona z wyprzedzeniem. Można to zrobić ręcznie lub za pomocą kodu. W tym przykładzie Usługa zawiera kod, aby sprawdzić obecność kolejki i utworzyć kolejkę, jeśli nie istnieje. Nazwa kolejki jest do odczytu z pliku konfiguracji. Adres podstawowy jest używany przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania serwera proxy do usługi.  
  
```  
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get the MSMQ queue name from appSettings in configuration.  
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
  
        // Close the ServiceHost to shut down the service.  
        serviceHost.Close();  
    }  
}  
```  
  
 Nazwa kolejki usługi MSMQ określono w sekcji appSettings pliku konfiguracji, jak pokazano w poniższych Przykładowa konfiguracja.  
  
```xml  
<appSettings>  
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />  
</appSettings>  
```  
  
> [!NOTE]
>  Nazwa kolejki używa pojedynczego znaku kropki (.) dla komputera lokalnego i separatorów ukośnika w jego ścieżki, podczas tworzenia kolejki, przy użyciu <xref:System.Messaging>. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Punktu końcowego używa adres kolejki z Schemat net.msmq, używa "localhost", określający komputera lokalnego i używa przekazywania ukośniki w swojej ścieżce.  
  
 Klient tworzy zakresu transakcji. Komunikacja z kolejki odbywa się w zakresie transakcji, co powoduje traktowane jako Atomowej jednostki, w którym wszystkie komunikaty są wysyłane do kolejki lub brak komunikaty są wysyłane do kolejki. Transakcja zostaje zatwierdzona przez wywołanie metody <xref:System.Transactions.TransactionScope.Complete%2A> w zakresie transakcji.  
  
```  
// Create a client.  
OrderProcessorClient client = new OrderProcessorClient();  
  
// Create the purchase order.  
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
  
// Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Make a queued call to submit the purchase order.  
    client.SubmitPurchaseOrder(po);  
    // Complete the transaction.  
    scope.Complete();  
}  
  
// Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 Aby sprawdzić, czy działają transakcji, zmodyfikować klienta komentowania zasięg transakcji, jak pokazano w poniższym kodzie próbki, ponownie skompiluj rozwiązanie i klientem.  
  
```  
//scope.Complete();  
```  
  
 Ponieważ transakcja nie jest ukończona, nie są wysyłane wiadomości do kolejki.  
  
 Po uruchomieniu próbki działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Można wyświetlić wiadomości receive usługi z klienta. Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta. Należy zauważyć, że usługi kolejkowania wiadomości jest w użyciu, klient i usługa nie być uruchomiona w tym samym czasie. Możesz z klientem, zamknij go, a następnie uruchom usługi i nadal odbiera komunikaty.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Jeśli usługa jest uruchamiana pierwszy, sprawdza, upewnij się, że kolejka jest obecny. Jeśli kolejka nie jest obecny, będzie utworzyć usługę. Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub można go utworzyć za pomocą Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.  
  
    1.  Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozwiń węzeł **funkcje** kartę.  
  
    3.  Kliknij prawym przyciskiem myszy **kolejki wiadomości prywatne**i wybierz **nowy**, **kolejki prywatnej**.  
  
    4.  Sprawdź **transakcyjna** pole.  
  
    5.  Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.  
  
3.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Domyślnie z <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczeń transportu jest włączona. Istnieją dwa odpowiednie właściwości dla zabezpieczeń transportu MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>. Domyślnie tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`. Dla usługi MSMQ w celu zapewnienia uwierzytelniania oraz podpisywania funkcji musi być częścią domeny, a opcja integracji usługi Active Directory dla usługi MSMQ musi być zainstalowany. Jeśli w tym przykładzie zostanie uruchomiony na komputerze, który nie spełnia te kryteria, wystąpi błąd.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Aby uruchomić na komputerze, na przykład dołączona do grupy roboczej lub bez integracji usługi Active Directory  
  
1.  Jeśli komputer nie jest częścią domeny lub nie ma zainstalowanych integracji usługi Active Directory, należy wyłączyć zabezpieczeń transportu przez ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższym kodzie próbki w konfiguracji.  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"  
                 behaviorConfiguration="OrderProcessorServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint. -->  
          <endpoint  
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <!-- The mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
            <behavior name="OrderProcessorServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  Sprawdź, czy zmian konfiguracji na serwerze i kliencie, przed uruchomieniem próbki.  
  
    > [!NOTE]
    >  Ustawienie `security``mode` do `None` jest odpowiednikiem ustawienia <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, i `Message` zabezpieczeń do `None`.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`  
  
## <a name="see-also"></a>Zobacz też
