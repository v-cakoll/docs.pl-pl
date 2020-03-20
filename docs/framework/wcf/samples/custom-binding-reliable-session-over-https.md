---
title: Niestandardowe powiązanie niezawodnej sesji przez protokół HTTPS
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: 051e7f56662a2ca67018ae7dd29189ff50245fc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183876"
---
# <a name="custom-binding-reliable-session-over-https"></a>Niestandardowe powiązanie niezawodnej sesji przez protokół HTTPS
W tym przykładzie pokazano użycie zabezpieczeń transportu SSL z niezawodne sesje. Niezawodne sesje implementuje protokół WS-Reliable Messaging. Możesz mieć bezpieczną niezawodną sesję, redagując usługi WS-Security za pomocą niezawodnych sesji. Czasami jednak można użyć zabezpieczeń transportu HTTP za pomocą protokołu SSL.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a>Przykładowe szczegóły  
 SSL zapewnia, że same pakiety są zabezpieczone. Należy pamiętać, że różni się to od zabezpieczania niezawodnej sesji przy użyciu usługi WS-Secure Conversation.  
  
 Aby użyć niezawodnej sesji za pośrednictwem protokołu HTTPS, należy utworzyć niestandardowe powiązanie. Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora. Niestandardowe powiązanie jest tworzone przy użyciu elementu wiązania niezawodnej sesji i [ \<>httpsTransport ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md). Następująca konfiguracja jest niestandardowe powiązanie.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Kod programu w przykładzie jest identyczny z kodem usługi [Wprowadzenie.](../../../../docs/framework/wcf/samples/getting-started-sample.md) Przed utworzeniem i uruchomieniem przykładu należy utworzyć certyfikat i przypisać go przy użyciu Kreatora certyfikatów serwera sieci Web. Definicja punktu końcowego i definicja powiązania w ustawieniach pliku konfiguracji umożliwiają użycie wiązania niestandardowego, jak pokazano w poniższej konfiguracji przykładowej dla klienta.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"
                binding="customBinding"
                bindingConfiguration="reliableSessionOverHttps"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Podany adres używa schematu https://.  
  
 Ponieważ certyfikat używany w tym przykładzie jest certyfikatem testowym utworzonym za pomocą pliku Makecert.exe, https://localhost/servicemodelsamples/service.svcpodczas próby uzyskania dostępu do adresu https:, takiego jak , z przeglądarki, pojawia się alert zabezpieczeń. Aby umożliwić klientowi Programu Windows Communication Foundation (WCF) pracę z certyfikatem testowym, do klienta dodano dodatkowy kod w celu powstrzymania alertu zabezpieczeń. Ten kod i towarzysząca mu klasa nie jest wymagana podczas korzystania z certyfikatów produkcyjnych.  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Upewnij się, że wykonano [instrukcje instalacji certyfikatów serwera usług internetowych (IIS).](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)  
  
4. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
