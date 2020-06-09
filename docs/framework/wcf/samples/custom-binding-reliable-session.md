---
title: Sesja niezawodna powiązania niestandardowego
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: bd690f96eea885c4d414f9725125e1918fdffa23
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585146"
---
# <a name="custom-binding-reliable-session"></a>Sesja niezawodna powiązania niestandardowego

Niestandardowe powiązanie jest definiowane przez uporządkowaną listę elementów powiązania dyskretnego. Ten przykład pokazuje, jak skonfigurować powiązanie niestandardowe z różnymi elementami transportu i transportem komunikatów, szczególnie w przypadku włączania niezawodnych sesji.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`

## <a name="sample-details"></a>Przykładowe szczegóły

Niezawodne sesje zapewniają funkcje niezawodnej obsługi komunikatów i sesji. Niezawodna komunikacja w celu komunikacji przy niepowodzeń i pozwala na określenie gwarancji dostarczania, takich jak wysyłanie komunikatów. Sesje utrzymują stan dla klientów między wywołaniami. Przykład implementuje sesje do obsługi stanu klienta i określa gwarancje dostarczania w kolejności. Przykład jest oparty na [wprowadzenie](getting-started-sample.md) , który implementuje usługę kalkulatora. Funkcje niezawodnej sesji są włączane i konfigurowane w plikach konfiguracji aplikacji dla klienta i usługi.

> [!NOTE]
> Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Kolejność elementów powiązania jest istotna dla definiowania niestandardowego powiązania, ponieważ każdy reprezentuje warstwę w stosie kanału (zobacz [powiązania niestandardowe](../extending/custom-bindings.md)).

Konfiguracja usługi dla przykładu jest zdefiniowana, jak pokazano w poniższym przykładzie kodu.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                     requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"
                        hostNameComparisonMode="StrongWildcard"
                        proxyAuthenticationScheme="Anonymous" realm=""
                        useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

W przypadku działania w scenariuszu obejmującym wiele maszyn należy zmienić adres punktu końcowego klienta, aby odzwierciedlał nazwę hosta usługi.

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

3. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

    > [!IMPORTANT]
    > W przypadku uruchamiania klienta programu w konfiguracji obejmującej wiele komputerów Pamiętaj, aby zastąpić wartość "localhost" w `address` atrybucie [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) elementu i `clientBaseAddress` atrybutem [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) z nazwą odpowiedniej maszyny, jak pokazano w poniższym przykładzie.

    ```xml
    <endpoint name = ""
    address="http://service_machine_name/servicemodelsamples/service.svc" />
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />
    ```
