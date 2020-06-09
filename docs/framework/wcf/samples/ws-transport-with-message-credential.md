---
title: Transport WS z poświadczeniami komunikatu
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 0082a9df5c112b66315236aad91bc891b80d27c7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596387"
---
# <a name="ws-transport-with-message-credential"></a>Transport WS z poświadczeniami komunikatu
Ten przykład ilustruje użycie zabezpieczeń transportu SSL w połączeniu z poświadczeniami klienta, które są przeprowadzane w komunikacie. Ten przykład używa `wsHttpBinding` powiązania.  
  
 Domyślnie `wsHttpBinding` powiązanie zapewnia komunikację http. W przypadku skonfigurowania zabezpieczeń transportu powiązanie obsługuje komunikację HTTPS. Protokół HTTPS zapewnia poufność i ochronę integralności komunikatów przesyłanych przez sieć. Jednak zestaw mechanizmów uwierzytelniania, których można użyć do uwierzytelniania klienta w usłudze, jest ograniczony do tego, co obsługuje transport HTTPS. Windows Communication Foundation (WCF) oferuje `TransportWithMessageCredential` tryb zabezpieczeń, który jest przeznaczony do pokonania tego ograniczenia. W przypadku skonfigurowania tego trybu zabezpieczeń zabezpieczenia transportu są używane w celu zapewnienia poufności i integralności przesyłanych komunikatów oraz do przeprowadzania uwierzytelniania usługi. Uwierzytelnianie klienta jest jednak wykonywane przez umieszczenie poświadczenia klienta bezpośrednio w komunikacie. Dzięki temu można używać dowolnego typu poświadczeń, który jest obsługiwany przez tryb zabezpieczeń wiadomości na potrzeby uwierzytelniania klienta, zachowując korzyści z używania trybu zabezpieczeń transportu.  
  
 W tym przykładzie `UserName` Typ poświadczeń jest używany do uwierzytelniania klienta w usłudze.  
  
 Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md) , który implementuje usługę kalkulatora. `wsHttpBinding`Powiązanie jest określone i skonfigurowane w plikach konfiguracji aplikacji dla klienta i usługi.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kod programu w przykładzie jest niemal identyczny jak w przypadku usługi [wprowadzenie](getting-started-sample.md) . Kontrakt usługi zapewnia jedną dodatkową operację — `GetCallerIdentity` . Ta operacja zwraca nazwę tożsamości obiektu wywołującego do obiektu wywołującego.  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 Przed skompilowaniem i uruchomieniem przykładu należy utworzyć certyfikat i przypisać go przy użyciu kreatora certyfikatu serwera sieci Web. Definicja punktu końcowego i definicja powiązania w ustawieniach pliku konfiguracji Włącz `TransportWithMessageCredential` tryb zabezpieczeń, jak pokazano w poniższej konfiguracji przykładowej dla klienta.  
  
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
  
 Określony adres używa `https://` schematu. Konfiguracja powiązania ustawia tryb zabezpieczenia na `TransportWithMessageCredential` . Ten sam tryb zabezpieczeń musi być określony w pliku Web. config usługi.  
  
 Ponieważ certyfikat używany w tym przykładzie jest certyfikatem testowym utworzonym za pomocą Makecert. exe, podczas próby uzyskania dostępu do adresu https:, takiego jak, z przeglądarki, pojawia się Alert zabezpieczeń `https://localhost/servicemodelsamples/service.svc` . Aby umożliwić klientowi WCF współpracuję z certyfikatem testowym, do klienta został dodany dodatkowy kod, aby pominąć alert zabezpieczeń. Ten kod i Klasa towarzysząca nie są wymagane w przypadku korzystania z certyfikatów produkcyjnych.  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Upewnij się, że wykonano [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](iis-server-certificate-installation-instructions.md).  
  
3. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
