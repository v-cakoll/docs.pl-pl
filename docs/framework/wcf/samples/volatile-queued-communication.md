---
title: "Komunikacja za pomocą nietrwałych kolejek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d7af5e29faf000fe3fe86463cb4eca9dc1e5c567
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="volatile-queued-communication"></a>Komunikacja za pomocą nietrwałych kolejek
W tym przykładzie pokazano, jak wykonać volatile komunikatu w kolejce przez transportu usługi kolejkowania komunikatów (MSMQ). W przykładzie użyto <xref:System.ServiceModel.NetMsmqBinding>. Usługa jest w tym przypadku aplikacji konsoli siebie umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W kolejce komunikacji klient komunikuje się z usługą przy użyciu kolejki. Mówiąc ściślej klient wysyła wiadomości do kolejki. Usługa odbiera komunikaty z kolejki. Usługi i klienta w związku z tym ma być uruchomiona, w tym samym czasie do komunikowania się przy użyciu kolejki.  
  
 Podczas wysyłania wiadomości nie gwarancji, MSMQ tylko sprawia, że optymalnego na dostarczenie wiadomości, w przeciwieństwie do dokładnie raz gwarancji gdzie MSMQ zapewnia czy komunikat pobiera wydana lub, jeśli nie można dostarczyć, pozwala dowiedzieć się, że nie można dostarczyć wiadomości.  
  
 W niektórych scenariuszach można wysłać wiadomość volatile nie gwarancji za pośrednictwem kolejki, gdy czas dostawy ma większe znaczenie niż utraty wiadomości. Volatile wiadomości po awarii menedżera kolejki. Dlatego jeśli wystąpiła awaria menedżera kolejek, nietransakcyjnej kolejki używane do przechowywania wiadomości volatile przeżyje, ale komunikaty się czy nie, ponieważ komunikaty nie są przechowywane na dysku.  
  
> [!NOTE]
>  Nie można wysłać wiadomości volatile nie gwarancji w zakresie transakcji za pomocą usługi MSMQ. Należy także utworzyć nietransakcyjnej kolejkę do wysyłania wiadomości volatile.  
  
 Kontrakt usługi, w tym przykładzie jest `IStockTicker` definiuje usługi jednokierunkowe, które są najbardziej odpowiednie do użycia z usługi kolejkowania wiadomości.  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IStockTicker  
{  
    [OperationContract(IsOneWay = true)]  
    void StockTick(string symbol, float price);  
}  
```  
  
 Operacja usługi wyświetla symbol giełdowych i cen, jak pokazano w poniższym kodzie próbki:  
  
```  
public class StockTickerService : IStockTicker  
{  
    public void StockTick(string symbol, float price)  
    {  
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);  
     }  
     …  
}  
```  
  
 Usługa jest samodzielnie hostowana. Za pomocą transportu MSMQ, kolejki używane musi zostać utworzona z wyprzedzeniem. Można to zrobić ręcznie lub za pomocą kodu. W tym przykładzie Usługa zawiera kod, aby sprawdzić obecność kolejki i go utworzyć, jeśli jest to wymagane. Nazwa kolejki jest do odczytu z pliku konfiguracji. Adres podstawowy jest używany przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania serwera proxy dla usługi.  
  
```  
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
>  Nazwa kolejki używa pojedynczego znaku kropki (.) lokalnego separatory maszyny i ukośnika w jego ścieżki, podczas tworzenia kolejki przy użyciu <xref:System.Messaging>. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Net.msmq Określa adres punktu końcowego: schemat, używa "localhost" dla komputera lokalnego i ukośniki pod jego ścieżki.  
  
 Gwarancje i trwałości lub zmienności wiadomości są również określona w konfiguracji.  
  
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
  
 Ponieważ próbki wysyła wiadomości z kolejki przy użyciu kolejki nietransakcyjnej, wiadomości transakcyjne nie można wysłać do kolejki.  
  
```  
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
  
 Po uruchomieniu próbki działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Można wyświetlić wiadomości receive usługi z klienta. Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta. Należy zauważyć, że usługi kolejkowania wiadomości jest w użyciu, klient i usługa nie być uruchomiona w tym samym czasie. Możesz z klientem, zamknij go, a następnie uruchom usługi i nadal otrzymuje jej wiadomości.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Domyślnie z <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczeń transportu jest włączona. Istnieją dwa odpowiednie właściwości zabezpieczeń transportu MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` domyślnie tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`. Dla usługi MSMQ w celu zapewnienia uwierzytelniania oraz podpisywania funkcji musi być częścią domeny, a opcja integracji usługi active directory dla usługi MSMQ musi być zainstalowany. Jeśli w tym przykładzie jest uruchomiony na komputerze, który nie spełnia te kryteria, wystąpi błąd.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Aby uruchomić na komputerze, na przykład dołączona do grupy roboczej lub bez integracji z usługą active directory  
  
1.  Jeśli komputer nie jest częścią domeny lub nie ma zainstalowanych integracji usługi active directory, należy wyłączyć zabezpieczeń transportu przez ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższym kodzie próbki w konfiguracji:  
  
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
  
2.  Sprawdź, czy zmian konfiguracji na serwerze i kliencie, przed uruchomieniem próbki.  
  
    > [!NOTE]
    >  Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, i `Message` zabezpieczeń do `None`.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`  
  
## <a name="see-also"></a>Zobacz też
