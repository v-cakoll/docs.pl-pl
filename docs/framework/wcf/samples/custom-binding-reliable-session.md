---
title: Sesja niezawodna powiązania niestandardowego
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: 76c701aaae368171bc7047784e1dc126937c84f0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463938"
---
# <a name="custom-binding-reliable-session"></a>Sesja niezawodna powiązania niestandardowego

Powiązanie niestandardowe jest definiowane przez uporządkowaną listę dyskretnych elementów wiązania. W tym przykładzie pokazano, jak skonfigurować niestandardowe powiązanie z różnych elementów kodowania transportu i wiadomości, szczególnie włączenie niezawodne sesje.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`

## <a name="sample-details"></a>Przykładowe szczegóły

Niezawodne sesje zapewniają funkcje niezawodnej obsługi wiadomości i sesji. Niezawodne wiadomości ponawia komunikację na niepowodzenie i umożliwia zapewnienie dostarczania, takie jak nastawy wiadomości w kolejności, które mają być określone. Sesje utrzymują stan dla klientów między wywołaniami. Przykład implementuje sesje do utrzymania stanu klienta i określa gwarancje dostarczania w kolejności. Przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora. Niezawodne funkcje sesji są włączone i konfigurowane w plikach konfiguracyjnych aplikacji dla klienta i usługi.

> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Kolejność elementów wiązania jest ważna przy definiowaniu niestandardowego powiązania, ponieważ każdy reprezentuje warstwę w stosie kanałów (zobacz [Powiązania niestandardowe).](../../../../docs/framework/wcf/extending/custom-bindings.md)

Konfiguracja usługi dla przykładu jest zdefiniowana w sposób pokazany w poniższym przykładzie kodu.

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

Podczas uruchamiania w scenariuszu między komputerami, należy zmienić adres punktu końcowego klienta, aby odzwierciedlić nazwę hosta usługi.

Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę

1. Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia:

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

3. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).

    > [!IMPORTANT]
    > Podczas uruchamiania klienta w konfiguracji między komputerami, należy zastąpić "localhost" w obu `address` [ \<atrybutu elementu>punktu końcowego](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) i `clientBaseAddress` atrybut [ \<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) z nazwą odpowiedniego komputera, jak pokazano w poniższym przykładzie.

    ```xml
    <endpoint name = ""
    address="http://service_machine_name/servicemodelsamples/service.svc" />
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />
    ```
