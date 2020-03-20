---
title: Transport WS z poświadczeniami komunikatu
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 076d4490f6edc6efa8eeb50ae8baa23d5c4e369a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183143"
---
# <a name="ws-transport-with-message-credential"></a>Transport WS z poświadczeniami komunikatu
W tym przykładzie pokazano użycie zabezpieczeń transportu SSL w połączeniu z poświadczeniami klienta przenoszonymi w wiadomości. W tym przykładzie użyto `wsHttpBinding` powiązania.  
  
 Domyślnie powiązanie zapewnia komunikację `wsHttpBinding` HTTP. Po skonfigurowaniu zabezpieczeń transportu powiązanie obsługuje komunikację HTTPS. Protokół HTTPS zapewnia ochronę poufności i integralności wiadomości przesyłanych przez sieć. Jednak zestaw mechanizmów uwierzytelniania, które mogą służyć do uwierzytelniania klienta do usługi jest ograniczona do tego, co obsługuje transport HTTPS. Windows Communication Foundation (WCF) oferuje tryb `TransportWithMessageCredential` zabezpieczeń, który jest przeznaczony do przezwyciężenia tego ograniczenia. Po skonfigurowaniu tego trybu zabezpieczeń zabezpieczenia transportu są używane do zapewnienia poufności i integralności przesyłanych wiadomości oraz do uwierzytelniania usługi. Jednak uwierzytelnianie klienta jest wykonywane przez umieszczenie poświadczenia klienta bezpośrednio w komunikacie. Dzięki temu można użyć dowolnego typu poświadczeń, który jest obsługiwany przez tryb zabezpieczeń wiadomości dla uwierzytelniania klienta przy zachowaniu korzyści wydajności transportu trybu zabezpieczeń.  
  
 W tym przykładzie `UserName` typ poświadczeń jest używany do uwierzytelniania klienta do usługi.  
  
 Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora. Powiązanie `wsHttpBinding` jest określone i skonfigurowane w plikach konfiguracji aplikacji dla klienta i usługi.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kod programu w przykładzie jest prawie identyczny z usługą [Wprowadzenie.](../../../../docs/framework/wcf/samples/getting-started-sample.md) Istnieje jedna dodatkowa operacja przewidziana `GetCallerIdentity`w umowie serwisowej - . Ta operacja zwraca nazwę tożsamości wywołującego do wywołującego.  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 Przed utworzeniem i uruchomieniem przykładu należy utworzyć certyfikat i przypisać go przy użyciu Kreatora certyfikatów serwera sieci Web. Definicja punktu końcowego i definicja `TransportWithMessageCredential` powiązania w ustawieniach pliku konfiguracji włączyć tryb zabezpieczeń, jak pokazano w poniższej konfiguracji przykładowej dla klienta.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Podany adres używa schematu https://. Konfiguracja powiązania ustawia tryb `TransportWithMessageCredential`zabezpieczeń na . Ten sam tryb zabezpieczeń musi być określony w pliku Web.config usługi.  
  
 Ponieważ certyfikat używany w tym przykładzie jest certyfikatem testowym utworzonym za pomocą pliku Makecert.exe, `https://localhost/servicemodelsamples/service.svc`podczas próby uzyskania dostępu do adresu https:, takiego jak , z przeglądarki, pojawia się alert zabezpieczeń. Aby umożliwić klientowi WCF pracę z certyfikatem testowym w miejscu, dodano do klienta dodatkowy kod w celu powstrzymania alertu zabezpieczeń. Ten kod i towarzysząca mu klasa nie jest wymagana podczas korzystania z certyfikatów produkcyjnych.  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:
YourDomainName\YourAccountName  
   Enter password:
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Upewnij się, że wykonano [instrukcje instalacji certyfikatów serwera usług internetowych (IIS).](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)  
  
3. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
