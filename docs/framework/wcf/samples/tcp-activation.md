---
title: Aktywacja TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 0fa737adbdc7acc51511557877799c89849149bc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598661"
---
# <a name="tcp-activation"></a>Aktywacja TCP

Ten przykład pokazuje hosting usługi, która korzysta z usług aktywacji procesów systemu Windows (WAS) w celu aktywowania usługi, która komunikuje się za pośrednictwem protokołu net. TCP. Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md).

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

Przykład składa się z programu konsolowego klienta (exe) i biblioteki usług (. dll) hostowanej w procesie roboczym aktywowanym przez program. Aktywność klienta jest widoczna w oknie konsoli.

Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź. Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie), jak pokazano w poniższym przykładowym kodzie:

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

Implementacja usługi oblicza i zwraca odpowiedni wynik:

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

W przykładzie zastosowano wariant powiązania net. TCP z włączonym udostępnianiem portów TCP i wyłączonym zabezpieczeniami. Jeśli chcesz użyć bezpiecznego powiązania TCP, Zmień tryb zabezpieczeń serwera na żądane ustawienie i ponownie uruchom program Svcutil. exe na kliencie, aby wygenerować plik konfiguracji klienta aktualizacji.

Poniższy przykład pokazuje konfigurację usługi:

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netTcpBinding>
        <binding name="PortSharingBinding" portSharingEnabled="true">
          <security mode="None" />
        </binding>
      </netTcpBinding>
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

Punkt końcowy klienta jest skonfigurowany tak, jak pokazano w następującym przykładowym kodzie:

```xml
<system.serviceModel>
    <bindings>
        <netTcpBinding>
          <binding name="NetTcpBinding_ICalculator">
            <security mode="None"/>
          </binding>
        </netTcpBinding>
    </bindings>
    <client>
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />
    </client>
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

2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

    Ponadto należy zainstalować składniki aktywacji inne niż HTTP programu WCF:

    1. Z menu **Start** wybierz pozycję **Panel sterowania**.

    2. Wybierz **programy i funkcje**.

    3. Kliknij pozycję **Włącz lub Wyłącz składniki systemu Windows**.

    4. Rozwiń węzeł **Microsoft .NET Framework 3,0** i Sprawdź funkcję **aktywacji Windows Communication Foundation niehttp** .

3. Konfiguracja programu miała obsługiwać aktywację protokołu TCP.

    Jako wygoda, następujące dwa kroki są zaimplementowane w pliku wsadowym o nazwie AddNetTcpSiteBinding. cmd znajdującym się w przykładowym katalogu.

    1. Aby można było obsługiwać aktywację net. TCP, domyślną witryną sieci Web należy najpierw powiązać z portem net. TCP. Można to zrobić za pomocą programu Appcmd. exe, który jest instalowany przy użyciu zestawu narzędzi do zarządzania Internet Information Services 7,0 (IIS). W wierszu polecenia na poziomie administratora uruchom następujące polecenie:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > To polecenie jest pojedynczym wierszem tekstu. To polecenie dodaje powiązanie witryny net. TCP do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 z dowolną nazwą hosta.

    2. Mimo że wszystkie aplikacje w lokacji współdzielą wspólne powiązanie net. TCP, każda aplikacja może włączać pojedynczą obsługę protokołu net. TCP. Aby włączyć usługę net. TCP dla aplikacji/servicemodelsamples, uruchom następujące polecenie w wierszu polecenia administratora:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > To polecenie jest pojedynczym wierszem tekstu. To polecenie umożliwia dostęp do aplikacji/servicemodelsamples przy użyciu obu `http://localhost/servicemodelsamples` i `net.tcp://localhost/servicemodelsamples` .

4. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

5. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

    Usuń powiązanie witryny net. TCP dodane do tego przykładu.

    Jako wygoda, następujące dwa kroki są zaimplementowane w pliku wsadowym o nazwie RemoveNetTcpSiteBinding. cmd znajdującym się w przykładowym katalogu.

    1. Usuń usługę net. TCP z listy włączonych protokołów, uruchamiając następujące polecenie w wierszu polecenia na poziomie administratora:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > To polecenie musi zostać wprowadzone jako pojedynczy wiersz tekstu.

    2. Usuń powiązanie witryny net. TCP, uruchamiając następujące polecenie w wierszu polecenia na poziomie administratora:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > To polecenie musi być wpisane jako pojedynczy wiersz tekstu.

## <a name="see-also"></a>Zobacz też

- [Przykłady hostingu i trwałości usługi AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
