---
title: "Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 910ebf0952d4a2399447de7442046eb0fe90060e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="poison-message-handling-in-msmq-40"></a>Obsługa zanieczyszczonych komunikatów w usłudze MSMQ 4.0
W tym przykładzie pokazano, jak wykonać Trująca wiadomość została obsługa w usłudze. Ten przykład jest oparty na [nietransakcyjnego powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) próbki. W przykładzie użyto `netMsmqBinding`. Usługa jest aplikacji konsoli siebie umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.  
  
 W kolejce komunikacji klient komunikuje się z usługą przy użyciu kolejki. Mówiąc ściślej klient wysyła wiadomości do kolejki. Usługa odbiera komunikaty z kolejki. Usługi i klienta w związku z tym ma być uruchomiona, w tym samym czasie do komunikowania się przy użyciu kolejki.  
  
 Trująca wiadomość jest komunikat, który jest wielokrotnie odczytany z kolejki, gdy usługa, odczytywanie wiadomości nie może przetworzyć komunikatu i w związku z tym kończy transakcji, pod którym komunikat został odczytany. W takich przypadkach komunikat zostanie ponowiony ponownie. To może teoretycznie Przejdź w nieskończoność w przypadku problemu z wiadomością. Należy pamiętać, że to można tylko wówczas, gdy używasz transakcji do odczytu z kolejki i wywołania operacji usługi.  
  
 Na podstawie wersji usługi MSMQ, NetMsmqBinding obsługuje wykrywanie ograniczone do pełnego wykrywania skażone wiadomości. Po komunikat wykryto jako intoksykowane, a następnie mogą być obsługiwane na kilka sposobów. Ponownie na podstawie wersji usługi MSMQ, NetMsmqBinding obsługuje obsługa ograniczona do pełnej obsługi wiadomości.  
  
 W tym przykładzie przedstawiono ograniczone skażone urządzeń na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platformy i pełnej skażone urządzenia, na [!INCLUDE[wv](../../../../includes/wv-md.md)]. W obu próbek celem jest Przenieś Trująca wiadomość kolejki do innej kolejki, który następnie może być obsługiwany przez usługę Trująca wiadomość.  
  
## <a name="msmq-v40-poison-handling-sample"></a>Obsługa próbki Poison v4.0 usługi MSMQ  
 W [!INCLUDE[wv](../../../../includes/wv-md.md)], usługa MSMQ oferuje funkcje skażone kolejki podrzędne, który może służyć do przechowywania wiadomości. W tym przykładzie pokazano, najlepszym rozwiązaniem dotyczącym skażone wiadomości przy użyciu [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 Wykrywanie Trująca wiadomość w [!INCLUDE[wv](../../../../includes/wv-md.md)] jest bardzo zaawansowane. Istnieją 3 właściwości, które pomagają w wykrywania. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Razy danej wiadomości jest ponownie odczytany z kolejki i wysłane do aplikacji do przetwarzania. Komunikat jest ponownie do odczytu z kolejki przy przekazywaniu wstecz do kolejki, ponieważ nie można wysłać wiadomości do aplikacji lub aplikacji wycofuje transakcji w operacji usługi. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>jest to liczba razy wiadomość zostanie przeniesiona do kolejki ponawiania. Gdy <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> jest osiągnięty, wiadomość zostanie przeniesiona do kolejki ponawiania. Właściwość <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> jest czas opóźnienia, po którym wiadomość zostanie przeniesiona z kolejki ponawiania wstecz do kolejki głównej. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Zostanie zresetowana do 0. Wiadomość zostanie podjęta próba ponownie. Jeśli wszystkie Przeczytaj komunikat prób, wiadomość jest oznaczony jako intoksykowane.  
  
 Gdy komunikat jest oznaczony jako intoksykowane, wiadomość została omówiona zgodnie z ustawieniami <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> wyliczenia. Aby przywołują możliwe wartości:  
  
-   Błąd (domyślnie): do odbiornika, a także hosta usługi.  
  
-   Upuść: Można usunąć wiadomości.  
  
-   Przenieś: Na przenoszenie wiadomości do kolejki podrzędne Trująca wiadomość. Ta wartość jest dostępna tylko na [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
-   Odrzuć: Aby odrzucić wiadomości, wysyłanie komunikatu do nadawcy na utraconych kolejki. Ta wartość jest dostępna tylko na [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 W przykładzie pokazano, przy użyciu `Move` dyspozycji skażone wiadomości. `Move`powoduje, że komunikat, aby przejść do skażone kolejki podrzędne.  
  
 Kontrakt usługi jest `IOrderProcessor`, który definiuje jednokierunkowe usługa, która jest odpowiednia do użycia w przypadku kolejek.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 Operacja usługi wyświetla komunikat informujący, że kolejność przetwarzania. Aby zademonstrować funkcje Trująca wiadomość `SubmitPurchaseOrder` operacji usługi zgłasza wyjątek można wycofać transakcji na losowe wywołania usługi. Powoduje to, że wiadomości powinna być umieszczona w kolejce. Po pewnym czasie wiadomość jest oznaczona jako poison. Konfiguracja została ustawiona na przenoszenie Trująca wiadomość do kolejki podrzędne skażone.  
  
```  
// Service class that implements the service contract.  
// Added code to write output to the console window.  
public class OrderProcessorService : IOrderProcessor  
{  
    static Random r = new Random(137);  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
  
        int randomNumber = r.Next(10);  
  
        if (randomNumber % 2 == 0)  
        {  
            Orders.Add(po);  
            Console.WriteLine("Processing {0} ", po);  
        }  
        else  
        {  
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);  
            Console.WriteLine();  
            throw new Exception("Cannot process purchase order: " + po.PONumber);  
        }  
    }  
  
    public static void OnServiceFaulted(object sender, EventArgs e)   
    {  
        Console.WriteLine("Service Faulted");  
    }  
  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Get MSMQ queue name from app settings in configuration.  
        string queueName = ConfigurationManager.AppSettings["queueName"];  
  
        // Create the transacted MSMQ queue if necessary.  
        if (!System.Messaging.MessageQueue.Exists(queueName))  
            System.Messaging.MessageQueue.Create(queueName, true);  
  
        // Get the base address that is used to listen for WS-MetaDataExchange requests.  
        // This is useful to generate a proxy for the client.  
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];  
  
        // Create a ServiceHost for the OrderProcessorService type.  
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));  
  
        // Hook on to the service host faulted events.  
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);  
  
        // Open the ServiceHostBase to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        if(serviceHost.State != CommunicationState.Faulted) {  
            serviceHost.Close();  
        }  
  
    }  
}  
```  
  
 Konfiguracja usługi zawiera następujące właściwości Trująca wiadomość została: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, i `receiveErrorHandling` jak pokazano w następującym pliku konfiguracji.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />  
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>  
  </appSettings>  
  <system.serviceModel>  
    <services>  
      <service   
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="PoisonBinding"   
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="PoisonBinding"   
                 receiveRetryCount="0"  
                 maxRetryCycles="1"  
                 retryCycleDelay="00:00:05"                        
                 receiveErrorHandling="Move">  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="processing-messages-from-the-poison-message-queue"></a>Przetwarzanie komunikatów z kolejki Trująca wiadomość  
 Trująca wiadomość usługi odczytuje wiadomości z kolejki końcowego Trująca wiadomość i przetwarza je.  
  
 Wiadomości w kolejce Trująca wiadomość są komunikaty adresowane do usługi, który przetwarza wiadomości, która może się różnić od punktu końcowego usługi Trująca wiadomość. W związku z tym, kiedy usługi Trująca wiadomość została odczytuje wiadomości z kolejki, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] warstwy kanału znajduje niezgodność w punktów końcowych i wysyła wiadomość. W takim przypadku wiadomość jest skierowana do kolejność przetwarzania usługi, ale są odbierane przez usługę Trująca wiadomość. Aby przejść do komunikatu, nawet jeśli komunikat jest skierowana do innego punktu końcowego, możemy dodać `ServiceBehavior` adresy filtr przypadku kryterium dopasowywania do dopasowania wiadomość jest skierowana do dowolnego punktu końcowego usługi. Jest to wymagane do pomyślnie przetwarzania komunikatów odczytujących z kolejki Trująca wiadomość.  
  
 Trująca wiadomość implementacji usługi sam jest bardzo podobny do implementacji usługi. Ją implementuje kontrakt i przetwarza zamówienia. Przykładowy kod ma następującą składnię.  
  
```  
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
  
    public static void OnServiceFaulted(object sender, EventArgs e)   
    {  
        Console.WriteLine("Service Faulted...exiting app");  
        Environment.Exit(1);  
    }  
  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
  
        // Create a ServiceHost for the OrderProcessorService type.  
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));  
  
        // Hook on to the service host faulted events.  
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);  
  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The poison message service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHostBase to shutdown the service.  
        if(serviceHost.State != CommunicationState.Faulted)  
        {  
            serviceHost.Close();  
        }  
    }  
```  
  
 W odróżnieniu od kolejność przetwarzania usługi, która odczytuje wiadomości z kolejki kolejności usługi Trująca wiadomość została odczytuje wiadomości z kolejki podrzędne skażone. Trująca kolejki jest kolejką podrzędnej kolejki głównej, nosi nazwę "poison" i jest generowana automatycznie przez usługę MSMQ. Aby do niego dostęp, należy podać nazwę kolejki głównej, a następnie ";" i podrzędne nazwę kolejki, w tym przypadku-"skażone", jak pokazano w poniższych Przykładowa konfiguracja.  
  
> [!NOTE]
>  W przykładowym dla usługi MSMQ w wersji 3.0 Nazwa skażone kolejki nie jest kolejkę podrzędną raczej przenieśliśmy komunikat do kolejki.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"  
                  binding="netMsmqBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >  
        </endpoint>  
      </service>  
    </services>  
  
  </system.serviceModel>  
</configuration>  
```  
  
 Po uruchomieniu próbki klienta, usługi i działania usługi Trująca wiadomość są wyświetlane w konsoli systemu windows. Można wyświetlić wiadomości receive usługi z klienta. Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługi.  
  
 Usługa uruchamia uruchomiony, przetwarzanie zamówień i losowo rozpoczyna się o zakończeniu przetwarzania. Komunikat oznacza, że został on przetworzony kolejności, po uruchomieniu klienta ponownie, aby wysłać kolejną wiadomość, aż zobaczysz, że usługa faktycznie został zakończony wiadomości. Na podstawie skonfigurowanego skażone ustawień, komunikat zostanie podjęta próba raz dla przetwarzania przed jego przeniesieniem do końcowego skażone kolejki.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89  
```  
  
 Uruchom usługi Trująca wiadomość odczytać skażone wiadomości z kolejki skażone. W tym przykładzie Usługa Trująca wiadomość odczytuje komunikat i przetwarza je. Można zauważyć, że zamówienia zakupu, który został zakończony i intoksykowane jest odczytywany przez usługę Trująca wiadomość.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Jeśli usługa jest uruchamiana pierwszy, sprawdza, upewnij się, że kolejka jest obecny. Jeśli kolejka nie jest obecny, będzie utworzyć usługę. Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub można go utworzyć za pomocą Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.  
  
    1.  Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozwiń węzeł **funkcje** kartę.  
  
    3.  Kliknij prawym przyciskiem myszy **kolejki wiadomości prywatne**i wybierz **nowy**, **kolejki prywatnej**.  
  
    4.  Sprawdź **transakcyjna** pole.  
  
    5.  Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.  
  
3.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, Zmień nazwy kolejki, aby odzwierciedlić rzeczywistej nazwy hosta zamiast localhost i postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Domyślnie z `netMsmqBinding` powiązania transportu, zabezpieczeń jest włączone. Dwie właściwości `MsmqAuthenticationMode` i `MsmqProtectionLevel`, wspólnie określić typ zabezpieczeń transportu. Domyślnie tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`. MSMQ zapewnić uwierzytelnianie i funkcji podpisywania musi być częścią domeny. Jeśli w tym przykładzie zostanie uruchomiony na komputerze, który nie jest częścią domeny, zostanie wyświetlony następujący błąd: "Komunikat użytkownika wewnętrzny certyfikat usługi kolejkowania wiadomości nie istnieje".  
  
#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Aby uruchomić na komputerze, na przykład przyłączony do grupy roboczej  
  
1.  Jeśli komputer nie jest częścią domeny, należy wyłączyć zabezpieczeń transportu przez ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższych Przykładowa konfiguracja:  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding name="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
     Upewnij się, że punkt końcowy jest skojarzony z powiązaniem przez ustawienie atrybutu bindingConfiguration punktu końcowego.  
  
2.  Upewnij się, zmiany konfiguracji na PoisonMessageServer, serwera i klienta, przed uruchomieniem próbki.  
  
    > [!NOTE]
    >  Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia `MsmqAuthenticationMode`, `MsmqProtectionLevel`, i `Message` zabezpieczeń do `None`.  
  
3.  Aby Meta wymiany danych do pracy możemy zarejestrować adresu URL wiązania http. Wymaga to, czy usługi są uruchamiane w oknie polecenia z podwyższonym poziomem uprawnień. W przeciwnym razie otrzymasz wyjątek takich jak: nieobsługiwany wyjątek: System.ServiceModel.AddressAccessDeniedException: HTTP nie może zarejestrować adresu URL http://+:8000/ServiceModelSamples/service/. Proces nie ma praw dostępu do tej przestrzeni nazw (zobacz http://go.microsoft.com/fwlink/?LinkId=70353). ---> System.Net.HttpListenerException: odmowa dostępu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`  
  
## <a name="see-also"></a>Zobacz też
