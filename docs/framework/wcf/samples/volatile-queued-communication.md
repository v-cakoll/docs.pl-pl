---
title: Komunikacja za pomocą nietrwałych kolejek
ms.date: 03/30/2017
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
ms.openlocfilehash: a9f7e8a96fd293c7f87cc19846a42a42f28de288
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602349"
---
# <a name="volatile-queued-communication"></a>Komunikacja za pomocą nietrwałych kolejek

W tym przykładzie pokazano, jak wykonać nietrwałą komunikację w kolejce za pośrednictwem transportu kolejkowania komunikatów (MSMQ). Ten przykład używa <xref:System.ServiceModel.NetMsmqBinding> . Usługa w tym przypadku jest samoobsługową aplikacją konsolową, która umożliwia obserwowanie usługi do odebrania komunikatów znajdujących się w kolejce.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki. Dokładniej, klient wysyła komunikaty do kolejki. Usługa odbiera komunikaty z kolejki. W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.

W przypadku wysłania wiadomości bez żadnych gwarancji usługa MSMQ najlepiej sprawdza się tylko w celu dostarczenia komunikatu, w przeciwieństwie do tego, że jest to możliwe tylko wtedy, gdy usługa MSMQ zagwarantuje, że wiadomość zostanie dostarczona lub, jeśli nie zostanie dostarczona, informuje o tym, że nie można dostarczyć wiadomości.

W niektórych scenariuszach możesz chcieć wysłać nietrwały komunikat bez gwarancji dla kolejki, gdy czas dostarczania jest ważniejszy niż utrata komunikatów. Komunikaty nietrwałe nie przeżyły do awarii Menedżera kolejki. W związku z tym w przypadku awarii Menedżera kolejki nietransakcyjnej kolejki używanej do przechowywania nietransakcyjnych komunikatów, ale same wiadomości nie są przechowywane na dysku.

> [!NOTE]
> Nie można wysyłać nietrwałych komunikatów bez gwarancji w zakresie transakcji przy użyciu usługi MSMQ. Należy również utworzyć kolejkę nietransakcyjną do wysyłania komunikatów nietransakcyjnych.

Kontrakt usługi w tym przykładzie `IStockTicker` definiuje usługi jednokierunkowe, które najlepiej nadają się do użycia z kolejkami.

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void StockTick(string symbol, float price);
}
```

Operacja usługi wyświetla symbol i cenę znacznika giełdowego, jak pokazano w poniższym przykładowym kodzie:

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

Usługa jest samodzielna. W przypadku korzystania z transportu usługi MSMQ użyta Kolejka musi zostać utworzona z góry. Można to zrobić ręcznie lub przy użyciu kodu. W tym przykładzie usługa zawiera kod, aby sprawdzić istnienie kolejki i utworzyć ją, jeśli jest to wymagane. Nazwa kolejki jest odczytywana z pliku konfiguracji. Adres podstawowy jest używany przez narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania serwera proxy dla usługi.

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

Nazwa kolejki MSMQ jest określona w sekcji appSettings w pliku konfiguracji. Punkt końcowy usługi jest zdefiniowany w sekcji System. serviceModel w pliku konfiguracji i określa `netMsmqBinding` powiązanie.

> [!NOTE]
> Nazwa kolejki używa kropki (.) dla komputera lokalnego i separatorów ukośników odwrotnych w ścieżce podczas tworzenia kolejki przy użyciu <xref:System.Messaging> . Adres punktu końcowego Windows Communication Foundation (WCF) określa schemat net. MSMQ:, używa "localhost" dla komputera lokalnego i ukośników w swojej ścieżce.

Gwarancje i trwałość lub lotność komunikatów są również określone w konfiguracji.

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

Ponieważ przykład wysyła wiadomości w kolejce przy użyciu kolejki nietransakcyjnej, wiadomości transakcyjne nie mogą być wysyłane do kolejki.

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

Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta. Możesz zobaczyć, że usługa odbiera komunikaty od klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta. Należy pamiętać, że ponieważ usługa kolejkowania jest w użyciu, klient i usługi nie muszą działać w tym samym czasie. Można uruchomić klienta programu, zamknąć go, a następnie uruchomić usługę i nadal otrzymywać wiadomości.

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

Domyślnie z opcją <xref:System.ServiceModel.NetMsmqBinding> jest włączona funkcja zabezpieczenia transportu. Istnieją dwie odpowiednie właściwości zabezpieczenia transportu usługi MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` tryb uwierzytelniania jest ustawiony na wartość, `Windows` a poziom ochrony jest ustawiony na `Sign` . Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny, a dla usługi MSMQ należy zainstalować opcję Integracja z usługą Active Directory. Jeśli ten przykład zostanie uruchomiony na komputerze, który nie spełnia tych kryteriów, wystąpi błąd.

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej lub bez integracji z usługą Active Directory

1. Jeśli komputer nie jest częścią domeny lub nie zainstalowano integracji z usługą Active Directory, Wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom ochrony `None` tak, jak pokazano w poniższym przykładowym kodzie konfiguracji:

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
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
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

2. Przed uruchomieniem przykładu należy zmienić konfigurację na serwerze i kliencie programu.

    > [!NOTE]
    > Ustawienie `security mode` odpowiada `None` ustawieniu <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> , <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> i `Message` zabezpieczenia na `None` .

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`
