---
title: Element BasicBinding z elementem Transport Security
ms.date: 03/30/2017
ms.assetid: f49b1de6-0254-4362-8ef2-fccd8ff9688b
ms.openlocfilehash: 822a7dcb20c6559a70ba77719b6e7a62633bb31c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575670"
---
# <a name="basicbinding-with-transport-security"></a>Element BasicBinding z elementem Transport Security

Ten przykład ilustruje użycie zabezpieczeń transportu SSL z powiązaniem podstawowym. Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md) , który implementuje usługę kalkulatora.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\TransportSecurity`

## <a name="sample-details"></a>Przykładowe szczegóły

Domyślnie podstawowe powiązanie obsługuje komunikację HTTP. W przykładzie pokazano, jak włączyć zabezpieczenia transportu dla podstawowego powiązania. Przed uruchomieniem przykładu należy utworzyć certyfikat i przypisać go przy użyciu kreatora certyfikatu serwera sieci Web.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Kod programu w przykładzie jest taki sam jak w przypadku usługi [wprowadzenie](getting-started-sample.md) . Definicja punktu końcowego i definicja powiązania w ustawieniach pliku konfiguracji są modyfikowane w celu włączenia bezpiecznej komunikacji, jak pokazano w poniższej konfiguracji przykładowej.

```xml
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
   </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"/>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```

Ponieważ certyfikat używany w tym przykładzie jest certyfikatem testowym utworzonym przy użyciu programu Makecert. exe, podczas próby uzyskania dostępu do adresu HTTPS w przeglądarce jest wyświetlany alert zabezpieczeń, na przykład `https://localhost/servicemodelsamples/service.svc` . Aby zezwolić klientowi Windows Communication Foundation (WCF) na współdziałanie z certyfikatem testowym, do klienta zostaje dodany dodatkowy kod, aby pominąć alert zabezpieczeń. Ten kod i Klasa towarzysząca nie są konieczne w przypadku używania prawdziwych certyfikatów.

```csharp
// This code is required only for test certificates such as those
// created by Makecert.exe.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```

Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Zainstaluj program ASP.NET 4,0 przy użyciu następującego polecenia:

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

3. Upewnij się, że wykonano [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](iis-server-certificate-installation-instructions.md).

4. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

5. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).
