---
title: Niestandardowe wiązanie niezawodnej sesji przez protokół HTTPS
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: d25a59b5921484c33a2b0c94febc97a04011f8d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643432"
---
# <a name="custom-binding-reliable-session-over-https"></a>Niestandardowe powiązanie niezawodnej sesji przez protokół HTTPS
Niniejszy przykład pokazuje użycie protokołu SSL zabezpieczeń transportu niezawodnej sesji. Niezawodne sesje implementuje elementy usługi WS-Reliable Messaging protocol. Masz bezpiecznej, niezawodnej sesji za pośrednictwem usługi WS-Security za pośrednictwem niezawodnej sesji. Jednak czasami możesz zamiast tego użyć zabezpieczenia transportu HTTP przy użyciu protokołu SSL.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a>Przykład szczegółów  
 SSL gwarantuje, że same pakiety są zabezpieczone. Należy zauważyć, że to różni się od zabezpieczanie niezawodnej sesji za pomocą zabezpieczenia WS konwersacji.  
  
 Aby użyć niezawodnej sesji za pośrednictwem protokołu HTTPS, należy utworzyć niestandardowego powiązania. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora. Powiązanie niestandardowe jest tworzony przy użyciu elementu powiązania niezawodnej sesji i [ \<httpsTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md). Jest następująca konfiguracja niestandardowego powiązania.  
  
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
  
 Kod programu, w przykładzie jest taka sama jak w przypadku [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) usługi. Należy utworzyć certyfikat i przypisz go za pomocą kreatora certyfikatu serwera sieci Web przed kompilowanie i uruchamianie przykładu. Definicji punktu końcowego i definicji powiązania w pliku ustawień konfiguracji umożliwić korzystanie z niestandardowego powiązania, jak pokazano w poniższym Przykładowa konfiguracja klienta.  
  
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
  
 Określony adres wykorzystuje schemat https://.  
  
 Ponieważ certyfikat używany w tym przykładzie jest utworzone za pomocą Makecert.exe certyfikat testowy, alert zabezpieczeń jest wyświetlany, gdy próbują uzyskać dostęp przy użyciu protokołu https: adres, takie jak https://localhost/servicemodelsamples/service.svc, z poziomu przeglądarki. Aby umożliwić klientowi usług Windows Communication Foundation (WCF) do pracy z certyfikatem testowym w miejscu, dodano dodatkowy kod klienta dla pomijania alertu zabezpieczeń. Ten kod i towarzyszące klasy, nie jest wymagane, podczas korzystania z certyfikatów w środowisku produkcyjnym.  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Upewnij się, że wykonano [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz także
