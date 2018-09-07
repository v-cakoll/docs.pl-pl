---
title: Komunikacja za pomocą nietrwałych kolejek
ms.date: 03/30/2017
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
ms.openlocfilehash: 55c2b695cdc672216ef6a76bef55bc0d427336a0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44065826"
---
# <a name="volatile-queued-communication"></a>Komunikacja za pomocą nietrwałych kolejek
Niniejszy przykład pokazuje sposób wykonywania volatile komunikatu w kolejce za pomocą transportu usługi kolejkowania komunikatów (MSMQ). W tym przykładzie użyto <xref:System.ServiceModel.NetMsmqBinding>. Usługa jest w tym przypadku aplikacji konsoli Self-Hosted umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W komunikacie w kolejce klient komunikuje się z usługą przy użyciu kolejki. Mówiąc ściślej klient wysyła komunikaty do kolejki. Usługa odbiera komunikaty z kolejki. Usługi i klienta w związku z tym, nie musi być uruchomiona w tym samym czasie do komunikowania się za pomocą kolejki.  
  
 Podczas wysyłania wiadomości z żadnych zapewnień, MSMQ tylko sprawia, że najlepszy nakład pracy na dostarczenie wiadomości, w przeciwieństwie do dokładnie jeden raz gwarancji gdzie MSMQ gwarantuje, że komunikat pobiera dostarczane lub jeśli nie można dostarczyć, informuje o tym, że nie można dostarczyć wiadomości.  
  
 W niektórych scenariuszach może chcesz wysłać wiadomość volatile z żadnych zapewnień, za pośrednictwem kolejki, gdy terminowe dostarczanie jest ważniejsza niż utraty wiadomości. Volatile komunikaty nie są unieważniane awarii menedżera kolejki. Dlatego jeśli Menedżer kolejki ulegnie awarii, przeżyje nietransakcyjnej kolejki, używane do przechowywania wiadomości lotnych, ale komunikaty się czy nie, ponieważ komunikaty nie są przechowywane na dysku.  
  
> [!NOTE]
>  Nie można wysyłać volatile wiadomości nie gwarancji w zakresie transakcji za pomocą usługi MSMQ. Ponadto należy utworzyć nietransakcyjnej kolejkę do wysyłania wiadomości lotnych.  
  
 Kontrakt usługi, w tym przykładzie jest `IStockTicker` definiujący usługi jednokierunkowe, które są najbardziej odpowiednie do użycia z usługą kolejkowania wiadomości.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IStockTicker  
{  
    [OperationContract(IsOneWay = true)]  
    void StockTick(string symbol, float price);  
}  
```

 Operacja usługi wyświetla symbol giełdowych i ceny, jak pokazano w poniższym przykładowym kodzie:  
  
```csharp
public class StockTickerService : IStockTicker  
{  
    public void StockTick(string symbol, float price)  
    {  
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);  
     }  
     …  
}  
```  
  
 Usługa jest samodzielnie hostowana. Za pomocą transportu MSMQ, kolejki, używane musi zostać utworzona wcześniej. Można to zrobić ręcznie lub za pomocą kodu. W tym przykładzie Usługa zawiera kod, aby sprawdzić istnienia kolejki i go utworzyć, jeśli jest to wymagane. Nazwa kolejki jest do odczytu z pliku konfiguracji. Adres podstawowy jest używany przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania serwera proxy dla usługi.  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName);  
  
    // Create a ServiceHost for the StockTickerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))  
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

 Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji. Punkt końcowy usługi jest zdefiniowany w sekcji system.serviceModel pliku konfiguracji i określa `netMsmqBinding` powiązania.  
  
> [!NOTE]
>  Nazwa kolejki używa pojedynczego znaku kropki (.) dla lokalnego separatory maszyny i ukośnika odwrotnego w ścieżce podczas tworzenia kolejki przy użyciu <xref:System.Messaging>. Adres punktu końcowego usługi Windows Communication Foundation (WCF) określa net.msmq: schemat, używa "localhost" dla komputera lokalnego i ukośników w ścieżce.  
  
 Zabezpieczenia i trwałości lub zmienności komunikatów także są określone w konfiguracji.  
  
```xml  
<appSettings>  
  <!-- use appSetting to configure MSMQ queue name -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"  
                binding="netMsmqBinding"  
                bindingConfiguration="volatileBinding"   
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />  
    ...  
    </service>  
  </services>  
  
  <bindings>  
    <netMsmqBinding>  
      <binding name="volatileBinding"   
             durable="false"  
           exactlyOnce="false"/>  
    </netMsmqBinding>  
  </bindings>  
  ...  
</system.serviceModel>  
```  
  
 Ponieważ próbki wysyła wiadomości w kolejce przy użyciu kolejki nietransakcyjnej, komunikaty transakcyjne nie można wysłać do kolejki.  

```csharp
// Create a client.  
Random r = new Random(137);  
  
StockTickerClient client = new StockTickerClient();  
  
float price = 43.23F;  
for (int i = 0; i < 10; i++)  
{  
    float increment = 0.01f * (r.Next(10));  
    client.StockTick("zzz" + i, price + increment);  
}  
  
//Closing the client gracefully cleans up resources.  
client.Close();  
```

 Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Możesz zobaczyć komunikaty odbierania usługi z klienta. Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta. Należy zauważyć, że ponieważ kolejkowania wiadomości jest używany, klient i usługa musi być uruchomiona w tym samym czasie. Można uruchomić klienta, zamknij go, a następnie uruchom usługi i wciąż otrzymuje jego wiadomości.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Stock Tick zzz0:43.25  
Stock Tick zzz1:43.23  
Stock Tick zzz2:43.28  
Stock Tick zzz3:43.3  
Stock Tick zzz4:43.23  
Stock Tick zzz5:43.25  
Stock Tick zzz6:43.25  
Stock Tick zzz7:43.24  
Stock Tick zzz8:43.32  
Stock Tick zzz9:43.3  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Domyślnie <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczenia transportu jest włączona. Istnieją dwie właściwości istotnych dla zabezpieczeń transportu usługi MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` domyślny tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`. Dla usługi MSMQ zapewniać uwierzytelnianie i podpisywania funkcji musi być częścią domeny i musi być zainstalowany opcji integracji usługi active directory dla usługi MSMQ. Jeśli w tym przykładzie jest uruchomiony na komputerze, który nie spełnia tych kryteriów otrzymasz komunikat o błędzie.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Do uruchomienia przykładu na komputer przyłączony do grupy roboczej lub bez integracji usługi active directory  
  
1.  Jeśli komputer nie jest częścią domeny lub nie ma zainstalowaną integracją usługi active directory, należy wyłączyć zabezpieczenia transportu, ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższym kodzie przykładowej konfiguracji:  
  
    ```xml  
    <system.serviceModel>  
        <services>  
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"  
                   behaviorConfiguration="StockTickerServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="volatileBinding"   
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />  
            <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="volatileBinding"   
                  durable="false"  
                  exactlyOnce="false">  
              <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="StockTickerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  Upewnij się, zmień konfigurację serwera i klienta, przed uruchomieniem przykładu.  
  
    > [!NOTE]
    >  Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, i `Message` security `None`.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`  
  
## <a name="see-also"></a>Zobacz też
