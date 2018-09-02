---
title: Obsługa wsadowa w ramach transakcji
ms.date: 03/30/2017
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
ms.openlocfilehash: abada9aaf5fac8f05599467f385e708e1898832f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416651"
---
# <a name="transacted-batching"></a>Obsługa wsadowa w ramach transakcji
Niniejszy przykład pokazuje jak dzielić na partie transakcyjne operacje odczytu za pomocą usługi kolejkowania komunikatów (MSMQ). Transakcyjne przetwarzania wsadowego jest funkcja optymalizacji wydajności dla odczytów transakcyjne w komunikacie w kolejce.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W komunikacie w kolejce klient komunikuje się z usługą przy użyciu kolejki. Mówiąc ściślej klient wysyła komunikaty do kolejki. Usługa odbiera komunikaty z kolejki. Usługi i klienta w związku z tym, nie musi być uruchomiona w tym samym czasie do komunikowania się za pomocą kolejki.  
  
 Niniejszy przykład pokazuje transakcyjnego przetwarzania wsadowego. Transakcyjnego przetwarzania wsadowego jest zachowanie, które umożliwia korzystanie z pojedynczą transakcję, podczas odczytywania wiele komunikatów w kolejce i ich przetworzeniu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny. Jeśli kolejka nie jest obecny, będzie utworzyć usługę. Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.  
  
    1.  Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozwiń **funkcji** kartę.  
  
    3.  Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.  
  
    4.  Sprawdź **transakcyjna** pole.  
  
    5.  Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.  
  
    > [!NOTE]
    >  W tym przykładzie klient wysyła setki komunikatów w ramach usługi batch. Jest to normalny aplikacji usługi w celu zająć trochę czasu, można je przetworzyć.  
  
3.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Do uruchomienia przykładu na komputer przyłączony do grupy roboczej lub bez integracji usługi active directory  
  
1.  Domyślnie <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczenia transportu jest włączona. Istnieją dwie właściwości istotnych dla zabezpieczeń transportu usługi MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` domyślny tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`. Dla usługi MSMQ zapewniać uwierzytelnianie i podpisywania funkcji musi być częścią domeny i musi być zainstalowany opcji integracji usługi active directory dla usługi MSMQ. Jeśli w tym przykładzie jest uruchomiony na komputerze, który nie spełnia tych kryteriów otrzymasz komunikat o błędzie.  
  
2.  Jeśli komputer nie jest częścią domeny lub nie ma zainstalowaną integracją usługi active directory, należy wyłączyć zabezpieczenia transportu, ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższym Przykładowa konfiguracja:  
  
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
  
3.  Upewnij się, zmień konfigurację serwera i klienta, przed uruchomieniem przykładu.  
  
    > [!NOTE]
    >  Ustawienie `security``mode` do `None` jest odpowiednikiem ustawienia <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, i `Message` security `None`.  
  
4.  Aby uruchomić bazy danych na komputerze zdalnym, należy zmienić parametry połączenia, aby wskazywała na komputerze, na którym znajduje się baza danych.  
  
## <a name="requirements"></a>Wymagania  
 Aby uruchomić ten przykład, należy zainstalować usługi MSMQ i bazy danych SQL lub programu SQL Express jest wymagana.  
  
## <a name="demonstrates"></a>Demonstracje  
 W przykładzie pokazano transakcyjnych zachowanie przetwarzania wsadowego. Przetwarzanie wsadowe transakcyjne jest funkcja optymalizacji wydajności, wyposażone w usłudze MSMQ w kolejce transportu.  
  
 Gdy transakcji są używane do wysyłania i odbierania komunikatów, które są rzeczywiście 2 oddzielne transakcji. Gdy klient wysyła komunikaty w zakresie transakcji, transakcja jest lokalny dla klienta i Menedżer kolejki klienta. Gdy usługa odbiera komunikaty w zakresie transakcji, transakcja jest lokalnego do usługi i odbieranie Menedżer kolejki. Jest bardzo ważne, należy pamiętać, że klient i usługa nie uczestniczą w tej samej transakcji; zamiast używają różnych transakcji podczas ich działania (takie jak wysyłanie i odbieranie) z kolejką.  
  
 W przykładzie służy do wykonywania wielu operacji usługi pojedynczej transakcji. To jest używana tylko jako funkcja optymalizacji wydajności i nie ma wpływu na semantykę aplikacji. Przykład jest oparty na [dokonana transakcja powiązania usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
## <a name="comments"></a>Komentarze  
 W tym przykładzie klient wysyła komunikaty zbiorczo do usługi z zakresu transakcji. Aby wyświetlić optymalizacji wydajności, wyślemy dużej liczby wiadomości. w tym przypadku maksymalnie 2500 wiadomości.  
  
 Komunikaty wysyłane do kolejki następnie są odbierane przez usługę w zakresie transakcji, zdefiniowane przez usługę. Bez dzielenia na partie, powoduje to 2500 transakcji dla każdego wywołania operacji usługi. Ma to wpływ na wydajność systemu. Ponieważ dwie menedżerów zasobów są zaangażowani — Kolejka usługi MSMQ i `Orders` bazy danych — każdej takiej transakcji jest transakcji usługi DTC. Możemy to zoptymalizować za pomocą znacznie mniejszej liczby transakcji, zapewniając, że partię komunikatów i wywołania operacji usługi odbywa się w jednej transakcji.  
  
 Firma Microsoft funkcja przetwarzania wsadowego przez:  
  
-   Określanie zachowania łączenia we wsady transakcyjne w konfiguracji.  
  
-   Określanie rozmiar partii pod względem liczby wiadomości, które mają być odczytywany za pomocą jednej transakcji.  
  
-   Określająca maksymalną liczbę równoczesnych partii zadań do uruchomienia.  
  
 W tym przykładzie przedstawiono zwiększenie wydajności dzięki zmniejszeniu liczby transakcji, zapewniając, że 100 operacji usługi są wywoływane w ramach jednej transakcji przed zatwierdzeniem transakcji.  
  
 Zachowanie usługi definiuje zachowanie operacji za pomocą `TransactionScopeRequired` równa `true`. Gwarantuje to, że ten sam zakres transakcji, który służy do pobierania komunikatu z kolejki jest używany przez wszystkie menedżerów zasobów uzyskiwał dostęp do metody. W tym przykładzie używamy podstawowej bazy danych do przechowywania informacji o zamówienia zakupu, które zostały zawarte w komunikacie. Zakres transakcji gwarantuje również, że jeśli metoda zgłasza wyjątek, zwracany jest komunikat do kolejki. Bez ustawienia tego zachowania operacji, kanał umieszczonych w kolejce tworzy transakcji, aby odczytać wiadomość z kolejki i zatwierdzeń go automatycznie, zanim wywoływane jest tak, aby w przypadku niepowodzenia operacji, komunikat zostanie utracony. Najbardziej typowym scenariuszem jest dla operacji usługi można zarejestrować w transakcji, która służy do odczytywania komunikatów z kolejki, jak pokazano w poniższym kodzie.  
  
 Należy pamiętać, że `ReleaseServiceInstanceOnTransactionComplete` ustawiono `false`. Jest to ważne wymagania dotyczące dzielenia na partie. Właściwość `ReleaseServiceInstanceOnTransactionComplete` na `ServiceBehaviorAttribute` wskazuje, co należy zrobić z wystąpieniem usługi po zakończeniu transakcji. Domyślnie wystąpienie usługi jest zwalniany, po zakończeniu transakcji. Aspekt core do dzielenia na partie polega na użyciu pojedynczą transakcję do odczytywania i wysyła wiele komunikatów w kolejce. W związku z tym przy zwalnianiu wystąpienie usługi będą istnieć realizowanie transakcji przedwcześnie Negacja bardzo korzystanie z dzielenia na partie. Jeśli ta właściwość jest ustawiona `true` i transakcyjnych zachowanie łączenia we wsady jest dodawany do punktu końcowego przetwarzania wsadowego zachowanie walidacji zgłasza wyjątek.  

```csharp
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

 `Orders` Klasa hermetyzuje przetwarzania zamówienia. W tym przykładzie powoduje zaktualizowanie bazy danych przy użyciu informacji o zamówieniu zakupu.  

```csharp
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

 Zachowanie przetwarzania wsadowego i jego konfiguracji są określone w konfiguracji aplikacji usługi.  
  
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
>  Rozmiar partii jest to wskazówka do systemu. Na przykład jeśli określisz rozmiar partii, 20, następnie 20 wiadomości zostaną wczytane i wysyłane przy użyciu pojedynczej transakcji i następnie transakcja została zatwierdzona. Jednak istnieją przypadki, gdzie może zatwierdzić transakcji partii przed osiągnięciem rozmiar partii.  
>   
>  Skojarzone z każdej transakcji jest limit czasu, który rozpoczyna się, jak należy po utworzeniu transakcji. Po upływie tego czasu transakcja została przerwana. Istnieje możliwość dla tego limitu czasu wygaśnięcia, nawet w przypadku, zanim osiągnie rozmiar partii. Aby uniknąć ponownego pracy usługi batch z powodu przerwania, `TransactedBatchingBehavior` sprawdza, ile czasu pozostało w transakcji. Jeśli wyczerpaniu 80% czasu transakcji, transakcja została zatwierdzona.  
>   
>  W przypadku dalszych komunikatów w kolejce, a następnie zamiast oczekiwania na realizację rozmiar partii <xref:System.ServiceModel.Description.TransactedBatchingBehavior> zatwierdzeń transakcji.  
>   
>  Wybór rozmiaru partii jest zależny od aplikacji. Jeśli rozmiar partii jest zbyt mała, może nie pobrać żądaną wydajność. Z drugiej strony Jeśli rozmiar partii jest zbyt duży, może pogarszać wydajność. Na przykład transakcji można już na żywo i przytrzymaj blokady w bazie danych lub transakcji może stać się dead zablokowane, która może spowodować, że usługi batch, Pobierz wycofana i wykonaj ponownie pracy.  
  
 Klient tworzy zakres transakcji. Komunikacja z kolejką odbywa się w zakresie transakcji, co powoduje powinien być traktowany jako pojedynczej Atomowej jednostki, w którym wszystkie komunikaty są wysyłane do kolejki lub żadne komunikaty są wysyłane do kolejki. Transakcja została zatwierdzona przez wywołanie metody <xref:System.Transactions.TransactionScope.Complete%2A> w zakresie transakcji.  

```csharp
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

 Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Możesz zobaczyć komunikaty odbierania usługi z klienta. Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta. Należy zauważyć, że ponieważ kolejkowania wiadomości jest używany, klient i usługa musi być uruchomiona w tym samym czasie. Można uruchomić klienta, zamknij go, a następnie uruchom usługi i wciąż otrzymuje jego wiadomości. Można wyświetlić stopniowe danych wyjściowych, jak komunikaty są odczytywane w zadaniu wsadowym i przetwarzane.  
  
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
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a>Zobacz też
