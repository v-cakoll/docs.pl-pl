---
title: "Obsługa wsadowa w ramach transakcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87d8e3e09618b214dcafb7afd82970dde54fc4fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transacted-batching"></a>Obsługa wsadowa w ramach transakcji
W tym przykładzie pokazano, jak partii odczyty transakcyjne przy użyciu usługi kolejkowania komunikatów (MSMQ). Wsadowe transakcyjne jest funkcja optymalizacji wydajności dla odczytów transakcyjnych w kolejce komunikacji.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W kolejce komunikacji klient komunikuje się z usługą przy użyciu kolejki. Mówiąc ściślej klient wysyła wiadomości do kolejki. Usługa odbiera komunikaty z kolejki. Usługi i klienta w związku z tym ma być uruchomiona, w tym samym czasie do komunikowania się przy użyciu kolejki.  
  
 W tym przykładzie przedstawiono transakcyjnego przetwarzania wsadowego. Transakcyjnego przetwarzania wsadowego jest to zachowanie, która umożliwia korzystanie z jednej transakcji podczas odczytywania wiele wiadomości w kolejce i przetwarzanie ich.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Jeśli usługa jest uruchamiana pierwszy, sprawdza, upewnij się, że kolejka jest obecny. Jeśli kolejka nie jest obecny, będzie utworzyć usługę. Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub można go utworzyć za pomocą Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.  
  
    1.  Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozwiń węzeł **funkcje** kartę.  
  
    3.  Kliknij prawym przyciskiem myszy **kolejki wiadomości prywatne**i wybierz **nowy**, **kolejki prywatnej**.  
  
    4.  Sprawdź **transakcyjna** pole.  
  
    5.  Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.  
  
    > [!NOTE]
    >  W tym przykładzie klient wysyła setki wiadomości jako część partii. Jest zjawiskiem aplikacji usługi do trochę potrwać zostać przetworzone.  
  
3.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Aby uruchomić na komputerze, na przykład dołączona do grupy roboczej lub bez integracji z usługą active directory  
  
1.  Domyślnie z <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczeń transportu jest włączona. Istnieją dwa odpowiednie właściwości dla zabezpieczeń transportu MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` domyślnie tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`. Dla usługi MSMQ w celu zapewnienia uwierzytelniania oraz podpisywania funkcji musi być częścią domeny, a opcja integracji usługi active directory dla usługi MSMQ musi być zainstalowany. Jeśli w tym przykładzie jest uruchomiony na komputerze, który nie spełnia te kryteria, wystąpi błąd.  
  
2.  Jeśli komputer nie jest częścią domeny lub nie ma zainstalowanych integracji usługi active directory, należy wyłączyć zabezpieczeń transportu przez ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższych Przykładowa konfiguracja:  
  
    ```xml  
    <system.serviceModel>  
      <behaviors>  
        <serviceBehaviors>  
          <behavior name="ThrottlingBehavior">  
            <serviceMetadata httpGetEnabled="true"/>  
            <serviceThrottling maxConcurrentCalls="5"/>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="BatchingBehavior">  
            <transactedBatching maxBatchSize="100"/>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <services>  
        <service   
            behaviorConfiguration="ThrottlingBehavior"   
            name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                    binding="netMsmqBinding"  
                    bindingConfiguration="Binding1"   
                    behaviorConfiguration="BatchingBehavior"   
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
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
  
    </system.serviceModel>  
    ```  
  
3.  Sprawdź, czy zmian konfiguracji na serwerze i kliencie, przed uruchomieniem próbki.  
  
    > [!NOTE]
    >  Ustawienie `security``mode` do `None` jest odpowiednikiem ustawienia <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, i `Message` zabezpieczeń do `None`.  
  
4.  Aby uruchomić bazy danych na komputerze zdalnym, Zmień parametry połączenia, aby wskazywały na komputerze, na którym znajdują się bazy danych.  
  
## <a name="requirements"></a>Wymagania  
 Aby uruchomić ten przykład, muszą zostać zainstalowane usługi MSMQ i bazy danych SQL lub programu SQL Express jest wymagany.  
  
## <a name="demonstrates"></a>Demonstracje  
 W przykładzie pokazano transakcyjnego łączenia we wsady zachowanie. Transakcyjnego przetwarzania wsadowego jest funkcja optymalizacji wydajności dostarczane z usługi MSMQ w kolejce transportu.  
  
 Jeśli transakcje są używane do wysyłania i odbierania wiadomości są faktycznie 2 oddzielne transakcji. Gdy klient wysyła komunikaty w zakresie transakcji, transakcja jest lokalne klient i klient menedżera kolejek. Gdy usługa odbiera komunikaty w zakresie transakcji, transakcja jest lokalnego do usługi i odbierającego menedżera kolejek. Jest bardzo ważne, aby należy pamiętać, że klient i usługa nie uczestniczą w tej samej transakcji; zamiast używają różnych transakcji podczas wykonywania ich działania (takie jak wysyłanie i odbieranie) z kolejką.  
  
 W przykładzie używamy pojedynczej transakcji do wykonania wielu operacji usługi. To jest używany tylko jako funkcja optymalizacji wydajności i nie ma wpływu na semantykę aplikacji. Próbki jest oparta na [nietransakcyjnego powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
## <a name="comments"></a>Komentarze  
 W tym przykładzie klient wysyła komunikaty zbiorczo do usługi z zakresu transakcji. Aby wyświetlić optymalizacji wydajności, możemy wysyłać dużej liczby wiadomości. w takim przypadku maksymalnie 2500 wiadomości.  
  
 Komunikaty wysłane do kolejki następnie są odbierane przez usługę w zakresie transakcji, określonym przez usługę. Bez partii, powoduje to 2500 transakcji dla każdego wywołania operacji usługi. Ma to wpływ na wydajność systemu. Ponieważ obejmuje dwa menedżerowie zasobów - kolejki usługi MSMQ i `Orders` bazy danych — każdego tych transakcji jest transakcji usługi DTC. Zoptymalizowana to przy użyciu znacznie mniejszą liczbę transakcji przez zapewnienie im to zrobić partii komunikatów i wywołania operacji usługi w ramach jednej transakcji.  
  
 Możemy użyć funkcji łączenia we wsady przez:  
  
-   Określanie transakcyjnego łączenia we wsady zachowanie w konfiguracji.  
  
-   Określanie rozmiar partii pod względem liczby wiadomości odczytywane przy użyciu pojedynczej transakcji.  
  
-   Określająca maksymalną liczbę równoczesnych partie do uruchomienia.  
  
 W tym przykładzie zostanie przedstawiony wydajność dzięki zmniejszeniu liczby transakcji przez zapewnienie, że 100 operacje usług są wywoływane w ramach jednej transakcji przed zatwierdzeniem transakcji.  
  
 Zachowanie usługi definiuje zachowanie operacji z `TransactionScopeRequired` ustawioną `true`. Dzięki temu, że tego samego zakresu transakcji, który służy do pobierania wiadomości z kolejki jest używana przez Menedżera zasobów, wszystkie dostępne metody. W tym przykładzie używamy podstawowej bazy danych do przechowywania informacji o zamówienia zakupu, które zostały zawarte w wiadomości. Zakresu transakcji gwarantuje również, że jeśli metoda zgłosi wyjątek, wiadomość jest zwracana do kolejki. Bez ustawienia zachowania tej operacji, kolejkowanym kanale tworzy transakcji, aby odczytać wiadomość z kolejki i zatwierdza ją automatycznie, zanim wywoływane jest tak, aby w przypadku niepowodzenia operacji wiadomości utraconych. Najbardziej typowym scenariuszem jest dla operacji usługi zarejestrować się w transakcji, który jest używany do odczytu komunikatu z kolejki, jak pokazano w poniższym kodzie.  
  
 Należy pamiętać, że `ReleaseServiceInstanceOnTransactionComplete` ma ustawioną wartość `false`. Jest to ważne potrzeby przetwarzania wsadowego. Właściwość `ReleaseServiceInstanceOnTransactionComplete` na `ServiceBehaviorAttribute` wskazuje, co należy zrobić po zakończeniu transakcji wystąpienia usługi. Domyślnie wystąpienie usługi jest publikowany po zakończeniu transakcji. Aspekt core do przetwarzania wsadowego jest wykorzystanie pojedynczej transakcji do odczytywania i wysyłania wielu wiadomości w kolejce. W związku z tym wydanie wystąpienia usługi kończy się wykonanie transakcji przedwcześnie Negacja bardzo stosowania przetwarzania wsadowego. Jeśli ta właściwość jest ustawiona na `true` i transakcyjnego łączenia we wsady zachowanie jest dodawany do punktu końcowego, przetwarzanie wsadowe zachowanie weryfikacji zgłasza wyjątek.  
  
```  
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(ReleaseServiceInstanceOnTransactionComplete=false,   
TransactionIsolationLevel=  
System.Transactions.IsolationLevel.Serializable, ConcurrencyMode=ConcurrencyMode.Multiple)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                       TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
    …  
}  
```  
  
 `Orders` Klasa hermetyzuje przetwarzania zamówienia. W przykładzie aktualizuje bazę danych z informacji o zamówieniu zakupu.  
  
```  
// Order Processing Logic  
public class Orders  
{  
    public static void Add(PurchaseOrder po)  
    {  
        // Insert purchase order.  
        SqlCommand insertPurchaseOrderCommand =   
        new SqlCommand(  
        "insert into PurchaseOrders(poNumber, customerId)   
                               values(@poNumber, @customerId)");  
        insertPurchaseOrderCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        insertPurchaseOrderCommand.Parameters.Add("@customerId",   
                                         SqlDbType.VarChar, 50);  
  
        // Insert product line item.  
        SqlCommand insertProductLineItemCommand =   
             new SqlCommand("insert into ProductLineItems(productId,   
                    unitCost, quantity, poNumber) values(@productId,   
                    @unitCost, @quantity, @poNumber)");  
        insertProductLineItemCommand.Parameters.Add("@productId",   
                                           SqlDbType.VarChar, 50);  
        insertProductLineItemCommand.Parameters.Add("@unitCost",   
                                                  SqlDbType.Float);  
        insertProductLineItemCommand.Parameters.Add("@quantity",   
                                                     SqlDbType.Int);  
        insertProductLineItemCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        int rowsAffected = 0;  
        using (TransactionScope scope =   
              new TransactionScope(TransactionScopeOption.Required))  
        {  
             using (SqlConnection conn = new   
                 SqlConnection(  
                 ConfigurationManager.AppSettings["connectionString"]))  
             {  
                 conn.Open();  
  
                // Insert into purchase order table.  
               insertPurchaseOrderCommand.Connection = conn;  
               insertPurchaseOrderCommand.Parameters["@poNumber"].Value   
                                                       = po.PONumber;  
             insertPurchaseOrderCommand.Parameters["@customerId"].Value   
                                                    =po.CustomerId;  
             insertPurchaseOrderCommand.ExecuteNonQuery();  
  
            // Insert into product line item table.  
            insertProductLineItemCommand.Connection = conn;  
            foreach (PurchaseOrderLineItem orderLineItem in   
                                        po.orderLineItems) {  
            insertProductLineItemCommand.Parameters["@poNumber"].Value   
                                                          =po.PONumber;  
            insertProductLineItemCommand.Parameters["@productId"].Value   
                                             = orderLineItem.ProductId;  
            insertProductLineItemCommand.Parameters["@unitCost"].Value   
                                             = orderLineItem.UnitCost;  
            insertProductLineItemCommand.Parameters["@quantity"].Value   
                                             = orderLineItem.Quantity;  
            rowsAffected +=   
            insertProductLineItemCommand.ExecuteNonQuery();  
            }  
            scope.Complete();  
        }  
     }  
     Console.WriteLine(  
     "Updated database with {0} product line items  for purchase order   
                                     {1} ", rowsAffected, po.PONumber);  
    }  
}  
```  
  
 Przetwarzanie wsadowe zachowania i jego konfiguracja są określone w konfiguracji aplikacji usługi.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName"   
     value=".\private$\ServiceModelSamplesTransactedBatching" />  
    <add key="baseAddress"   
     value=  
     "http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
    <add key="connectionString" value="Data Source=.\SQLEXPRESS;AttachDbFilename=|DataDirectory|orders.mdf;Integrated Security=True;User Instance=True;" />  
  </appSettings>  
  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ThrottlingBehavior">  
          <serviceThrottling maxConcurrentCalls="5"/>  
        </behavior>  
      </serviceBehaviors>  
  
      <endpointBehaviors>  
        <behavior name="BatchingBehavior">  
          <transactedBatching maxBatchSize="100"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service   
          behaviorConfiguration="ThrottlingBehavior"   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address=  
"net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                  binding="netMsmqBinding"  
                  behaviorConfiguration="BatchingBehavior"   
                  contract=  
                    "Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  Rozmiar partii to wskazówkę systemu. Na przykład jeśli określisz rozmiar partii, 20, następnie 20 komunikatów będą odczytywane i wysłane przy użyciu pojedynczej transakcji i następnie transakcja została przekazana. Istnieją przypadki, w którym może zatwierdzić transakcji partii przed osiągnięciem rozmiar partii.  
>   
>  Skojarzone z każdej transakcji jest limit czasu, która rozpoczyna się zaznaczenie po utworzeniu transakcji. Transakcja została przerwana, po upływie tego czasu. Istnieje możliwość tego limitu czasu wygaśnięcia nawet przed osiągnięciem rozmiaru partii. Aby uniknąć ponownego pracy partii z powodu przerwania, `TransactedBatchingBehavior` sprawdza, ile czasu pozostało w transakcji. Jeśli wykorzystane 80% czasu transakcji transakcja została przekazana.  
>   
>  Jeśli nie ma żadnych więcej wiadomości w kolejce, a następnie zamiast oczekiwania na realizację rozmiar partii <xref:System.ServiceModel.Description.TransactedBatchingBehavior> zatwierdza transakcji.  
>   
>  Wybór rozmiar partii jest zależny od aplikacji. Jeśli rozmiar partii jest za mały, nie może pobrać żądaną wydajność. Z drugiej strony, jeśli rozmiar partii jest zbyt duży, może pogarszać wydajność. Na przykład transakcji można już na żywo i przytrzymaj blokady bazy danych lub transakcji może stać się martwych zablokowana, które mogłyby powodować partii pobrać wycofana i wykonaj ponownie pracy.  
  
 Klient tworzy zakresu transakcji. Komunikacja z kolejki odbywa się w zakresie transakcji, co powoduje traktowane jako Atomowej jednostki, w którym wszystkie komunikaty są wysyłane do kolejki lub brak komunikaty są wysyłane do kolejki. Transakcja zostaje zatwierdzona przez wywołanie metody <xref:System.Transactions.TransactionScope.Complete%2A> w zakresie transakcji.  
  
```  
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        Random randomGen = new Random();  
        for (int i = 0; i < 2500; i++)  
        {  
            // Create a client with given client endpoint configuration.  
            OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
            // Create the purchase order.  
            PurchaseOrder po = new PurchaseOrder();  
            po.CustomerId = "somecustomer" + i + ".com";  
            po.PONumber = Guid.NewGuid().ToString();  
  
            PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
            lineItem1.ProductId = "Blue Widget";  
            lineItem1.Quantity = randomGen.Next(1, 100);  
            lineItem1.UnitCost = (float)randomGen.NextDouble() * 10;  
  
            PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
            lineItem2.ProductId = "Red Widget";  
            lineItem2.Quantity = 890;  
            lineItem2.UnitCost = 45.89F;  
  
            po.orderLineItems = new PurchaseOrderLineItem[2];  
            po.orderLineItems[0] = lineItem1;  
            po.orderLineItems[1] = lineItem2;  
  
            //Create a transaction scope.  
            using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
            {  
                // Make a queued call to submit the purchase order.  
                client.SubmitPurchaseOrder(po);  
                // Complete the transaction.  
                scope.Complete();  
            }  
  
            client.Close();  
        }  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```  
  
 Po uruchomieniu próbki działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Można wyświetlić wiadomości receive usługi z klienta. Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta. Należy zauważyć, że usługi kolejkowania wiadomości jest w użyciu, klient i usługa nie być uruchomiona w tym samym czasie. Możesz z klientem, zamknij go, a następnie uruchom usługi i nadal otrzymuje jej wiadomości. Widać stopniowego dane wyjściowe jako odczytana w partii i przetwarzania komunikatów.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Updated database with 2 product line items for purchase order 493ac832-d216-4e94-b2a5-d7f492fb5e39  
Processing Purchase Order: 8b567f5b-0661-4662-aae2-6cef1bd6d278  
        Customer: somecustomer849.com  
        OrderDetails  
               Order LineItem: 80 of Blue Widget @unit price: $9.751623  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41622.23  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 41130b95-4ea8-40a9-91c3-2e129117fcb8  
Processing Purchase Order: 5ce2699d-9a31-4cc2-a8c5-64cda614b3c7  
        Customer: somecustomer850.com  
        OrderDetails  
               Order LineItem: 89 of Blue Widget @unit price: $6.369128  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41408.95  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 8b567f5b-0661-4662-aae2-6cef1bd6d278  
Processing Purchase Order: ea94486b-7c86-4309-a42d-2f06c00656cd  
        Customer: somecustomer851.com  
        OrderDetails  
             Order LineItem: 47 of Blue Widget @unit price: $0.9391424  
             Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $40886.24  
        Order status: Pending  
```  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a>Zobacz też
