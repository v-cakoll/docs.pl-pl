---
title: Aktywowanie elementu NamedPipe
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: a562ec51d35af08f49e89b652670e9a57b0f00c2
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837860"
---
# <a name="namedpipe-activation"></a>Aktywowanie elementu NamedPipe

W tym przykładzie pokazano, jak hostować usługę, która używa usługi aktywacji procesów systemu Windows (WAS) do aktywowania usługi, która komunikuje się z potokami nazw. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i wymaga uruchomienia systemu Windows Vista.

> [!NOTE]
> Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a>Przykładowe szczegóły

Przykład składa się z programu konsoli klienta (. exe) i biblioteki usług (. dll) hostowanej w procesie roboczym aktywowanym przez usługi aktywacji procesów systemu Windows (WAS). Aktywność klienta jest widoczna w oknie konsoli.

Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź. Umowa jest definiowana przez interfejs `ICalculator`, który uwidacznia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie), jak pokazano w poniższym przykładowym kodzie.

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

Klient wykonuje synchroniczne żądania do danej operacji matematycznej, a implementacja usługi oblicza i zwraca odpowiedni wynik.

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

Przykład używa zmodyfikowanego powiązania `netNamedPipeBinding` bez zabezpieczeń. Powiązanie jest określone w plikach konfiguracji klienta i usługi. Typ powiązania dla usługi jest określony w atrybucie `binding` elementu punktu końcowego, jak pokazano w poniższej konfiguracji przykładowej.

Jeśli chcesz użyć bezpiecznego powiązania nazwanego potoku, Zmień tryb zabezpieczeń serwera na żądane ustawienie zabezpieczeń i ponownie uruchom program Svcutil. exe na kliencie, aby uzyskać zaktualizowany plik konfiguracji klienta.

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

Informacje o punkcie końcowym klienta są konfigurowane, jak pokazano w poniższym przykładowym kodzie.

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

Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że usługi IIS 7,0 są zainstalowane. Do przeprowadzenia aktywacji wymagane są usługi IIS 7,0.

2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

    Ponadto należy zainstalować składniki aktywacji inne niż HTTP programu WCF:

    1. Z menu **Start** wybierz pozycję **Panel sterowania**.

    2. Wybierz **programy i funkcje**.

    3. Kliknij pozycję **Włącz lub Wyłącz składniki systemu Windows**.

    4. Rozwiń węzeł **Microsoft .NET Framework 3,0** i Sprawdź funkcję **aktywacji Windows Communication Foundation niehttp** .

3. Skonfiguruj usługę aktywacji procesów systemu Windows (WAS) do obsługi aktywacji potoków nazwanych.

    Jako wygoda, następujące dwa kroki są zaimplementowane w pliku wsadowym o nazwie AddNetPipeSiteBinding. cmd znajdującym się w przykładowym katalogu.

    1. Aby można było obsługiwać aktywację net. pipe, domyślna witryna sieci Web musi być najpierw powiązana z protokołem net. pipe. Można to zrobić za pomocą programu Appcmd. exe, który jest instalowany przy użyciu zestawu narzędzi do zarządzania usługami IIS 7,0. W wierszu polecenia z podwyższonym poziomem uprawnień (Administrator) Uruchom następujące polecenie.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > To polecenie jest pojedynczym wierszem tekstu.

        To polecenie dodaje powiązanie witryny net. pipe do domyślnej witryny sieci Web.

    2. Mimo że wszystkie aplikacje w lokacji współużytkują wspólne powiązanie net. pipe, każda aplikacja może włączyć obsługę sieci net. pipe pojedynczo. Aby włączyć usługę net. pipe dla aplikacji/servicemodelsamples, uruchom następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > To polecenie jest pojedynczym wierszem tekstu.

        To polecenie umożliwia dostęp do aplikacji/servicemodelsamples przy użyciu obu `http://localhost/servicemodelsamples` i `net.tcp://localhost/servicemodelsamples`.

4. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

5. Usuń powiązanie witryny net. pipe dodane do tego przykładu.

    Jako wygoda, następujące dwa kroki są zaimplementowane w pliku wsadowym o nazwie RemoveNetPipeSiteBinding. cmd, który znajduje się w przykładowym katalogu:

    1. Usuń usługę net. TCP z listy włączonych protokołów, uruchamiając następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > To polecenie musi zostać wprowadzone jako pojedynczy wiersz tekstu.

    2. Usuń powiązanie witryny net. TCP, uruchamiając następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > To polecenie musi być wpisane jako pojedynczy wiersz tekstu.

## <a name="see-also"></a>Zobacz także

- [Przykłady hostingu i trwałości usługi AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
