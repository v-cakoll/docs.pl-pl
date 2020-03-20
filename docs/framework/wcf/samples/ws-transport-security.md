---
title: Zabezpieczenia transportu WS
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
ms.openlocfilehash: 221bf2e0d304e93242bb5fea6854c1c9bb72aec2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143463"
---
# <a name="ws-transport-security"></a>Zabezpieczenia transportu WS
W tym przykładzie pokazano użycie zabezpieczeń transportu <xref:System.ServiceModel.WSHttpBinding> SSL z powiązaniem. Domyślnie powiązanie zapewnia komunikację `wsHttpBinding` HTTP. Po skonfigurowaniu zabezpieczeń transportu powiązanie obsługuje komunikację HTTPS. Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora. Jest `wsHttpBinding` określony i skonfigurowany w plikach konfiguracji aplikacji dla klienta i usługi.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 Kod programu w przykładzie jest identyczny z kodem usługi [Wprowadzenie.](../../../../docs/framework/wcf/samples/getting-started-sample.md) Przed utworzeniem i uruchomieniem przykładu należy utworzyć certyfikat i przypisać go przy użyciu Kreatora certyfikatów serwera sieci Web. Definicja punktu końcowego i definicja `Transport` powiązania w ustawieniach pliku konfiguracji włączyć tryb zabezpieczeń, jak pokazano w poniższej konfiguracji przykładowej dla klienta.  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address="https://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as None -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 Podany adres używa schematu https://. Konfiguracja powiązania ustawia tryb `Transport`zabezpieczeń na . Ten sam tryb zabezpieczeń musi być określony w pliku Web.config usługi.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Upewnij się, że wykonano [instrukcje instalacji certyfikatów serwera usług internetowych (IIS).](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)  
  
4. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
