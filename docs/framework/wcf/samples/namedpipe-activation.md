---
title: Aktywowanie elementu NamedPipe
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 3e6084e8334eddc16b115cc1199819c6ab637666
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051848"
---
# <a name="namedpipe-activation"></a>Aktywowanie elementu NamedPipe

Niniejszy przykład pokazuje usługi, używającej Windows Process Activation Service (WAS), aby aktywować usługę, która komunikuje się za pośrednictwem potoków nazwy hosta. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i wymaga [!INCLUDE[wv](../../../../includes/wv-md.md)] do uruchomienia.

> [!NOTE]
> Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.

> [!IMPORTANT]
> Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a>Przykład szczegółów

Przykład składa się z konsoli program kliencki (.exe) i usługi biblioteki (.dll), hostowana w procesie roboczym aktywowany przez Windows Process Activation usług (WAS). Aktywność klienta jest widoczna w oknie konsoli.

Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź". Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (dodawania, odejmowania, mnożenia i dzielenia,) jak pokazano w poniższym przykładowym kodzie.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

Klient wysyła żądań synchronicznych operacji matematycznych danego i implementacji usługi oblicza i zwraca odpowiedni wynik.

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

W przykładzie użyto zmodyfikowane `netNamedPipeBinding` powiązania z żadnych zabezpieczeń. Powiązanie jest określona w plikach konfiguracji klienta i usługi. Typ powiązania usługi jest określona w elemencie punktu końcowego `binding` atrybutu, jak pokazano w poniższym Przykładowa konfiguracja.

Jeśli chcesz użyć powiązania zabezpieczonej nazwany potok, zmianę trybu zabezpieczeń serwera z ustawieniem pożądanych zabezpieczeń i ponownie uruchom svcutil.exe na kliencie, aby uzyskać zaktualizowanego klienta z pliku konfiguracji.

```xml
<system.serviceModel>
        <services>
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">

        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->
        <endpoint address=""
                  binding="netNamedPipeBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexNamedPipeBinding"
                  contract="IMetadataExchange" />
      </service>
        </services>
        <bindings>
            <netNamedPipeBinding>
                <binding name="Binding1" >
                    <security mode = "None">
                    </security>
                </binding >
            </netNamedPipeBinding>
        </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

Informacje o punkcie końcowym klienta jest skonfigurowany, jak pokazano w poniższym przykładowym kodzie.

```xml
<system.serviceModel>

    <client>
      <endpoint name=""
                          address="net.pipe://localhost/servicemodelsamples/service.svc"
                          binding="netNamedPipeBinding"
                          bindingConfiguration="Binding1"
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>

    <bindings>

      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.
            Each property is configured with the default value. -->

      <netNamedPipeBinding>
        <binding name="Binding1"
                         maxBufferSize="65536"
                         maxConnections="10">
          <security mode = "None">
          </security>
        </binding >

      </netNamedPipeBinding>
    </bindings>

  </system.serviceModel>
```

Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1. Upewnij się, że [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jest zainstalowany. [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jest wymagany do aktywacji WAS.

2. Upewnij się, kiedy została wykonana [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

    Ponadto należy zainstalować składniki Aktywacja bez HTTP programu WCF:

    1. Z **Start** menu, wybierz **Panelu sterowania**.

    2. Wybierz **programy i funkcje**.

    3. Kliknij przycisk **włączyć składników Windows lub wyłączyć**.

    4. Rozwiń **Microsoft .NET Framework 3.0** węzła i wyboru **Aktywacja bez HTTP programu Windows Communication Foundation** funkcji.

3. Skonfiguruj Windows Process Activation Service (WAS) do obsługi aktywacji nazwanego potoku.

    Dla wygody następujące dwa kroki są implementowane w pliku wsadowym, o nazwie AddNetPipeSiteBinding.cmd znajduje się w katalogu próbki.

    1. Aby zapewnić obsługę aktywacji net.pipe, domyślna witryna sieci Web musi zostać powiązana z protokołem net.pipe. Można to zrobić za pomocą appcmd.exe, który jest instalowany z zestawem narzędzi zarządzania usług IIS 7.0. Z wiersza polecenia o podniesionych uprawnień (administrator) uruchom następujące polecenie.

        ```
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > To polecenie jest pojedynczy wiersz tekstu.

        To polecenie dodaje powiązanie witryny net.pipe do domyślnej witryny sieci Web.

    2. Mimo że wszystkie aplikacje w ramach lokacji mają wspólne powiązanie net.pipe, każdej aplikacji można włączyć obsługę net.pipe indywidualnie. Aby włączyć net.pipe aplikacji /servicemodelsamples, uruchom następujące polecenie z wiersza polecenia z podwyższonym poziomem uprawnień.

        ```
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > To polecenie jest pojedynczy wiersz tekstu.

        To polecenie włącza aplikację /servicemodelsamples można uzyskać za pomocą zarówno `http://localhost/servicemodelsamples` i `net.tcp://localhost/servicemodelsamples`.

4. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

5. Usuń powiązanie witryny net.pipe, dodane dla tego przykładu.

    Dla wygody następujące dwa kroki są implementowane w pliku wsadowym, o nazwie RemoveNetPipeSiteBinding.cmd znajduje się w katalogu próbki:

    1. Usuń net.tcp z listy włączone protokoły, uruchamiając następujące polecenie z wiersza polecenia z podwyższonym poziomem uprawnień.

        ```
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > To polecenie muszą zostać wprowadzone jako pojedynczy wiersz tekstu.

    2. Usuń powiązanie witryny net.tcp, uruchamiając następujące polecenie z wiersza polecenia z podwyższonym poziomem uprawnień.

        ```
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > To polecenie musi być wpisana w jako pojedynczy wiersz tekstu.

## <a name="see-also"></a>Zobacz także

- [Przykłady trwałości i hostingu AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
